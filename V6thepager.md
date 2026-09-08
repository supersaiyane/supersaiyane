<div align="center">

<sub>`▸ this page is interactive — click the grey arrows`</sub>

</div>

---

> **3:47 AM.**
>
> Your phone doesn't ring. It *vibrates* — which is worse, because it means the
> system already tried the polite escalation and nobody answered.

```
┌─ P1 ─────────────────────────────────────────── ALERTMANAGER ──┐
│                                                                 │
│  ALERT    SLOBurnRateCritical                                   │
│  SERVICE  payments-api            ENV   prod-eu-west-1          │
│  SLI      checkout_success_ratio                                │
│  BUDGET   14.2% remaining         BURN  36x   (1h window)       │
│  FIRING   03:41:12Z               ACK   —                       │
│                                                                 │
│  ▸ "At current burn, the 30-day error budget is gone in 41m."   │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

You are awake now. You have three moves.

<br>

<details>
<summary><b>&nbsp;🔴&nbsp; Restart the pods. It usually works.</b></summary>

<br>

It does usually work. That's the trap.

A rollout restart will almost certainly clear the symptom, and you will be back in
bed by 4:05. You will also have destroyed the connection-pool state, the in-flight
traces, and the only evidence of what actually happened. On Thursday the pager
fires again and you'll have nothing but a memory of being tired.

> **Restarting isn't a fix. It's a way of losing the argument slowly.**

The instinct is right — *reduce the blast radius now, understand it later*. The
mistake is skipping "later" for six months until it becomes an architecture review
with an executive in the room.

`▸ Wrong move. The pods were never the problem. Try again.`

</details>

<details>
<summary><b>&nbsp;📊&nbsp; Open the dashboard.</b></summary>

<br>

The dashboard is green.

```
checkout_success_ratio   ▁▂▂▁▂▁▂▂▁▂▂▁▂  99.4%   ✅ within SLO
p50 latency              ▁▁▂▁▁▂▁▁▂▁▁▂▁  118ms   ✅ nominal
error rate               ▁▁▁▁▁▁▁▁▁▁▁▁▁   0.6%   ✅ nominal
```

It's green because it's an **average**, and the average is where user pain goes to
hide. Break it apart and the story changes completely:

```
p99 latency  · issuer BIN 4532xx  ▁▁▁▂▃▅█████████  9,400ms  🔴
              · everyone else      ▁▁▂▁▁▂▁▁▂▁▁▂▁▁    141ms  ✅
```

0.6% of transactions. One card issuer. One retry loop with no jitter, hammering a
saturated connection pool. Statistically invisible. Commercially expensive. And
every single one of those users is *certain* your bank is broken.

> **A dashboard without percentiles is decoration with a budget line.**

I wrote 2,000 words on exactly this failure mode:
**[Why Your Observability Platform Is Lying to You →](https://medium.com/@gurpreet.singh_89)**

`▸ Warmer. But something already found this. Keep going.`

</details>

<details>
<summary><b>&nbsp;🤖&nbsp; Check what already looked.</b></summary>

<br>

**03:41:14** — two seconds after the SLI moved — the cluster agent woke up first.

```
[03:41:14] burn-rate breach detected · payments-api · 36x
[03:41:19] correlating: 1 deploy in window → payments-api v2.19.3 (-42m)
[03:41:23] diff scan: pool.maxConnections 200 → 50   ⚠️  suspicious
[03:41:31] trace sample: 94% of slow spans blocked on pool acquire
[03:41:38] blast radius: 1 issuer BIN · 0.6% txns · p99 9.4s
[03:41:44] runbook match: "connection pool saturation" (confidence 0.91)
[03:42:02] ✅ mitigation applied  · pool scaled 50 → 220
[03:42:09] ✅ GitOps PR opened    · #4471 "fix: restore pool ceiling"
[03:42:11] ✅ RCA drafted         · attached to INC-8842
[03:42:14] ✅ Slack thread posted · #sre-incidents
[03:47:00] ▸ human paged — for REVIEW, not response
```

By the time your phone buzzed, the incident was six minutes old, mitigated,
diagnosed, and waiting for a signature.

**You weren't paged to fix it. You were paged to approve it.**

That agent is real, it's open source, and it's the thing I'm proudest of:

### ⚡ [auto-agent-k8s](https://github.com/supersaiyane/auto-agent-k8s) &nbsp;·&nbsp; `Go` `Kubernetes` `LLM`

A DaemonSet that watches your cluster and *acts* — auto-remediation, scaling, S3
log shipping, GitOps PRs for the durable fix, Slack/Jira alerts, and LLM-drafted
root-cause analysis attached to the ticket before you've opened the laptop.

`▸ Correct move. Go back to sleep.`

</details>

<br>

---

<div align="center">

### That gap — between *"production is on fire"* and *"nobody had to wake up"* —<br>is the only thing I build.

</div>

---

## `whoami`

**Gurpreet Singh.** Senior SRE at **NatWest Group**. I make banking platforms fail
predictably instead of catastrophically, for millions of people who will never know
my name — which is precisely the point.

Eleven years of being woken up taught me one lesson, and I've been implementing it
ever since: **every 3AM page is a runbook someone didn't automate, attached to a
dashboard that didn't tell the truth.**

So I automate the runbooks and I fix the dashboards. Everything below is a piece
of that.

<div align="center">

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/gurpreettsengh/)
[![Medium](https://img.shields.io/badge/Writing-000000?style=for-the-badge&logo=medium&logoColor=white)](https://medium.com/@gurpreet.singh_89)
[![Site](https://img.shields.io/badge/Portfolio-F7B731?style=for-the-badge&logo=githubpages&logoColor=black)](https://supersaiyane.github.io/gurpreetsingh/)
[![Email](https://img.shields.io/badge/Collab-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:senghgurpreett@gmail.com)

</div>

---

## Built after nights like that one

<table>
<tr><td width="50%" valign="top">

#### ⚡ [auto-agent-k8s](https://github.com/supersaiyane/auto-agent-k8s)
`Go` · `Kubernetes` · `LLM`

The agent from the story. Triages, heals, opens the PR, writes the RCA.

*Built because the knowledge to fix it always existed — it just wasn't wired to the alert.*

</td><td width="50%" valign="top">

#### 📚 [crashcourse](https://github.com/supersaiyane/crashcourse)
`Terraform` · `Interactive CLI`

**153 crash courses. 30 CLI playgrounds.** DevOps, SRE, Cloud, AI, Platform.

*Built because you cannot learn failure handling by reading about failure handling.*

</td></tr>
<tr><td width="50%" valign="top">

#### 🏗️ [IDP_Backstage](https://github.com/supersaiyane/IDP_Backstage)
`Backstage` · `GitOps` · `Guardrails`

An Internal Developer Platform with observability and incident workflow built in.

*Built because developers route around guardrails when the shortcut is faster. Golden paths, not golden cages.*

</td><td width="50%" valign="top">

#### 💰 [FinOps](https://github.com/supersaiyane/FinOps)
`Python` · `AWS · Azure · GCP`

Multi-tenant cost intelligence and optimisation automation across three clouds.

*Built because the emergency cost-cut always lands on the redundancy you needed.*

</td></tr>
<tr><td width="50%" valign="top">

#### 🔐 [jogi-vault](https://github.com/supersaiyane/jogi-vault)
`Python` · `AES-256-GCM` · `TOTP`

Encrypted secret manager. 2FA, Web UI, REST API, encrypted off-site backup.

</td><td width="50%" valign="top">

#### 📡 [RuView](https://github.com/supersaiyane/RuView)
`Rust` · `WiFi CSI`

Commodity WiFi → spatial intelligence and vital-sign monitoring. No cameras. No wearables.

</td></tr>
</table>

<div align="center">

**[→ all 87 repositories](https://github.com/supersaiyane?tab=repositories)**

</div>

---

## Field notes

<details>
<summary><b>&nbsp;Six things production charged me tuition for</b></summary>

<br>

**① Alert on symptoms, never on causes.**
`CPU > 80%` pages you about a system nobody is using. `checkout p99 breaching, 36x
burn` pages you when money is leaving. Every cause-based alert you delete makes the
pager more trustworthy, and a trustworthy pager is the entire game.

**② The error budget isn't a metric. It's a negotiation tool.**
Its real job is giving product and engineering a shared, unemotional way to argue
about ship-versus-stabilise. The number is just the excuse to have the conversation.

**③ Automation that can't explain itself gets disabled.**
Which is why LLM-assisted *RCA* matters more than LLM-assisted *action*. The win
isn't a machine fixing it. The win is a human arriving to a timeline, a diff, and a
hypothesis already written.

**④ Toil is measurable, so measure it — otherwise you'll romanticise it.**
Hours per week, per person, per class of task. The number is always uglier than the
vibe. Once it's on a dashboard, the automation gets funded.

**⑤ In regulated environments the constraint is auditability, not technology.**
Multi-cloud isn't a résumé line in banking, it's a regulator's question. GitOps
isn't fashion — it's *"who approved this change and when"*, answered by `git log`.

**⑥ Chaos engineering isn't a disaster. It's a rehearsal you scheduled.**
You are going to have the outage either way. The only variable is whether you're
holding a coffee or a pager when it happens.

</details>

<details>
<summary><b>&nbsp;What I'm actually good at (no inflation)</b></summary>

<br>

| Area | Depth | The work looks like |
|:---|:---|:---|
| Observability architecture | **Deep** | SLI/SLO design, cardinality budgets, trace sampling strategy, log pipeline economics |
| Kubernetes at scale | **Deep** | Multi-tenant clusters, admission control, autoscaling behaviour, failure-domain design |
| Incident response | **Deep** | On-call design, escalation paths, blameless postmortems, MTTR as a programme |
| Platform / IDP | **Strong** | Backstage, golden paths, self-service with guardrails, DX metrics |
| IaC & GitOps | **Strong** | Terraform module design, ArgoCD, drift detection, promotion pipelines |
| FinOps | **Strong** | Multi-cloud allocation, unit economics, rightsizing automation |
| AIOps | **Building** | LLM triage, runbook retrieval, agentic remediation with human-in-the-loop |

</details>

<details>
<summary><b>&nbsp;The toolbox</b></summary>

<br>

```
cloud         aws · azure · gcp
orchestrate   kubernetes · docker · helm · argocd · terraform · ansible
observe       prometheus · grafana · opentelemetry · jaeger · elastic · influxdb
build         go · python · rust · typescript · bash
pipe          kafka · redis · postgres · mongodb · rabbitmq
ship          github-actions · gitlab-ci · jenkins
```

</details>

---

## Longer arguments, made in public

<!-- BLOG-POST-LIST:START -->
<!-- BLOG-POST-LIST:END -->

**[→ everything on Medium](https://medium.com/@gurpreet.singh_89)**

---

<div align="center">

## `./connect.sh`

If you're wrestling with an observability rewrite, an IDP rollout, an on-call
rotation that's eating your team, or an AIOps proof-of-concept that has to survive
an audit — that's my favourite kind of conversation.

[![LinkedIn](https://img.shields.io/badge/Escalate%20to%20LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/gurpreettsengh/)
[![Email](https://img.shields.io/badge/Open%20a%20Ticket-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:senghgurpreett@gmail.com)

<br>

**If you read this far, the pager worked.**

<sub>⚓ Nomadic by nature. Resilient by design. Always shipping.</sub>

</div>

<!--
  ╔═══════════════════════════════════════════════════════════════╗
  ║  You clicked "Raw". Of course you did.                        ║
  ║                                                               ║
  ║  $ kubectl get pods -n curiosity                              ║
  ║    NAME                READY   STATUS      RESTARTS   AGE     ║
  ║    you-1               1/1     Running     0          8s      ║
  ║                                                               ║
  ║  People who read the source are the people I want to hire,    ║
  ║  work with, or argue with about distributed systems.          ║
  ║  Pick one: senghgurpreett@gmail.com                           ║
  ╚═══════════════════════════════════════════════════════════════╝
-->
