<div align="center">

# The Architecture Review

**Gurpreet Singh** · Senior SRE @ **NatWest Group**
*Platform · Observability · AIOps · FinOps*

</div>

> Six people in a room. One of them is the staff engineer who has read everything
> and believes nothing. I'm presenting. Here's how it goes.
>
> <sub>`▸ every question below is one I've actually been asked. Click to see the answer.`</sub>

---

<details>
<summary><b>&nbsp;❓ "Before we start — you have 87 repos and eleven followers. Why should I care?"</b></summary>

<br>

Fair. Let me not defend the number.

Follower count measures **distribution**, not **judgment**, and I have spent eleven
years optimising for the second one inside a bank where the best work is invisible
by design. Nobody tweets about the outage that didn't happen.

So don't evaluate me on the graph. Evaluate me on this: open
[**auto-agent-k8s**](https://github.com/supersaiyane/auto-agent-k8s) and read how it
decides *not* to act. Open [**crashcourse**](https://github.com/supersaiyane/crashcourse)
and see whether 153 courses and 30 CLI playgrounds look like someone padding a
profile or someone who has explained this material a hundred times and got tired of
repeating himself.

If those don't convince you, the follower count wouldn't have either.

</details>

<details>
<summary><b>&nbsp;❓ "Why build any of this? Just buy Datadog."</b></summary>

<br>

Often you should. I'll say that in the room, and I've said it in rooms where it
cost me the project.

Buy the platform. **You cannot buy the practice.** A vendor will sell you ingestion,
storage and beautiful dashboards. What they cannot sell you:

- which SLI actually correlates with a customer abandoning a payment
- what your metric cardinality budget is before the bill becomes an incident
- which of your 340 alerts are lying to you
- what your on-call rotation does at 3AM when the runbook is three years stale

Every organisation I've seen fail at observability failed at those four, on a tool
that was working perfectly. **The tool was never the constraint.**

Where I do build: the seams. Auto-remediation, GitOps-native fixes, cost-as-telemetry,
LLM triage. Those live in *your* domain logic, and no vendor knows your domain.

</details>

<details>
<summary><b>&nbsp;❓ "Your agent auto-remediates in production. What happens when it's wrong?"</b></summary>

<br>

**The best question in the deck.** Here's the honest answer: it *will* be wrong,
and the design assumes that from the first line.

Three constraints, non-negotiable:

**1. Every action is reversible or it doesn't ship.**
Scaling a connection pool: reversible. Restarting a pod: reversible. Deleting data,
failing over a region, mutating state: **human gate, always.** The blast radius of
being wrong is a design input, not an afterthought.

**2. The durable fix is a pull request, not a mutation.**
The agent mitigates live, then opens a **GitOps PR** for the actual change. So the
permanent fix goes through the same review, the same audit trail, the same
`git log` as any human change. A regulator asking *"who approved this"* gets an
answer with a name on it.

**3. It shows its work, or it gets switched off.**
Correlation, diff scan, trace evidence, confidence score, runbook match — all in
the Slack thread before a human reads it. **Automation that can't explain itself
gets disabled by the first team that doesn't trust it**, and a disabled agent has
negative value: you paid for it *and* you lost the runbook.

The failure mode I actually protect against isn't "the agent breaks prod." It's
**"the agent is subtly wrong for six weeks and everyone stops reading it."**

</details>

<details>
<summary><b>&nbsp;❓ "An LLM in the incident path. How does that survive an audit?"</b></summary>

<br>

By keeping it out of the decision and in the **explanation**.

```
LLM writes:      the timeline, the hypothesis, the RCA draft, the summary
LLM never:       approves, merges, deletes, fails over, touches money
```

The distinction that matters to an auditor is *determinism at the point of change*.
Remediation is triggered by deterministic rules — burn-rate thresholds, runbook
matches with a confidence floor, an allowlist of reversible actions. That path is
testable, replayable, and reads the same way in a control review as any other
automation.

The model's job is the part humans are worst at under stress and that carries **no
authority**: assembling context and writing it down clearly at 3:41 AM.

Every generated artefact is labelled as generated, versioned with the model and
prompt, and attached to the ticket as *evidence for a human*, never as an approval.
If the model hallucinates, a human catches it in review — which is exactly where a
hallucination is cheap.

</details>

<details>
<summary><b>&nbsp;❓ "Multi-cloud is a tax. Why are you paying it?"</b></summary>

<br>

You're right that it's a tax. In banking, **it's a tax with a regulator attached.**

Concentration risk is a supervisory question, not an architecture preference.
"What happens to your critical services if this provider has a regional event, or a
contractual one?" is a question you answer in writing, to someone empowered to fine
you. Nobody chose portability for fun.

The engineering answer is to be honest about which tier you're paying for:

| Tier | What it costs | When it's worth it |
|:---|:---|:---|
| **Portable by accident** | Nothing | Never. This is just "we haven't been tested." |
| **Portable at the platform layer** (K8s, Terraform, OTel) | Moderate | Almost always. This is where I live. |
| **Portable at the data layer** | Enormous | Only when regulation or exit risk demands it |

Most "multi-cloud" disasters are teams paying tier-three prices for tier-two
benefits. [**FinOps**](https://github.com/supersaiyane/FinOps) exists partly to make
that tax *visible*, because an invisible tax never gets argued down.

</details>

<details>
<summary><b>&nbsp;❓ "What have you gotten wrong?"</b></summary>

<br>

A caching layer, early on. 40% faster reads. It also served a stale balance to the
wrong customer for ninety seconds.

I was **right about the metric and wrong about the system.** Latency went down;
correctness went sideways. I'd optimised the thing I was measuring and broken the
thing I wasn't.

What it changed permanently: I now ask of every optimisation — *what invariant am I
trading away, and who finds out first, me or the customer?*

Second one, less dramatic and more expensive: I spent a year building beautiful
dashboards nobody opened. Adoption is a feature. **A platform nobody uses is a
hobby with a budget line**, and platform engineers are structurally bad at
admitting this because the artefact looks finished.

</details>

<details>
<summary><b>&nbsp;❓ "Fine. What are you actually deep in, and where are you bluffing?"</b></summary>

<br>

| Area | Honest level | What that means |
|:---|:---|:---|
| Observability architecture | **Deep** | SLI/SLO design, cardinality budgets, sampling strategy, log pipeline economics |
| Kubernetes at scale | **Deep** | Multi-tenant clusters, admission control, autoscaling behaviour, failure domains |
| Incident response | **Deep** | On-call design, escalation, blameless postmortems, MTTR as a programme |
| Platform / IDP | **Strong** | Backstage, golden paths, self-service with guardrails, DX metrics |
| IaC & GitOps | **Strong** | Terraform module design, ArgoCD, drift detection, promotion pipelines |
| FinOps | **Strong** | Multi-cloud allocation, unit economics, rightsizing automation |
| AIOps | **Building** | LLM triage, runbook retrieval, agentic remediation with human-in-the-loop |
| Frontend | **Not my seat** | I will make your dashboard load. I will not make it beautiful. |

The last row is the one I'd check first if I were you.

</details>

---

<div align="center">

### The review ends. The system ships.

</div>

## What I brought to the room

| | |
|:---|:---|
| ⚡ **[auto-agent-k8s](https://github.com/supersaiyane/auto-agent-k8s)** | Self-healing K8s DaemonSet — reversible remediation, GitOps PRs, LLM-drafted RCA · `Go` |
| 📚 **[crashcourse](https://github.com/supersaiyane/crashcourse)** | 153 crash courses + 30 interactive CLI playgrounds · `Terraform` `CLI` |
| 🏗️ **[IDP_Backstage](https://github.com/supersaiyane/IDP_Backstage)** | IDP with guardrails, observability and incident workflow built in · `Backstage` |
| 💰 **[FinOps](https://github.com/supersaiyane/FinOps)** | Multi-tenant cloud cost intelligence + optimisation automation · `Python` |
| 🔐 **[jogi-vault](https://github.com/supersaiyane/jogi-vault)** | AES-256-GCM secret manager, TOTP 2FA, REST API · `Python` |
| 📡 **[RuView](https://github.com/supersaiyane/RuView)** | Commodity WiFi → spatial intelligence + vital signs. No cameras. · `Rust` |

**[→ all 87 repositories](https://github.com/supersaiyane?tab=repositories)**

---

## Arguments I've made at greater length

<!-- BLOG-POST-LIST:START -->
<!-- BLOG-POST-LIST:END -->

**[→ Medium](https://medium.com/@gurpreet.singh_89)**

---

<div align="center">

### Book the next review

**Observability rewrites · IDP rollouts · on-call that's eating your team · AIOps that has to pass an audit**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/gurpreettsengh/)
[![Email](https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:senghgurpreett@gmail.com)
[![Site](https://img.shields.io/badge/Portfolio-F7B731?style=for-the-badge&logo=githubpages&logoColor=black)](https://supersaiyane.github.io/gurpreetsingh/)

**Bring the hostile questions. Those are the useful ones.**

<sub>⚓ Nomadic by nature. Resilient by design. Always shipping.</sub>

</div>
