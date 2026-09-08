<div align="center">

# `● ALL SYSTEMS OPERATIONAL`

### Gurpreet Singh
**Senior SRE @ NatWest Group** · Platform Engineering · AIOps · FinOps

`region: /dev/null` &nbsp;·&nbsp; `oncall: always` &nbsp;·&nbsp; `error budget: spent wisely`

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/gurpreettsengh/)
[![Medium](https://img.shields.io/badge/Medium-000000?style=flat-square&logo=medium&logoColor=white)](https://medium.com/@gurpreet.singh_89)
[![Site](https://img.shields.io/badge/Site-F7B731?style=flat-square&logo=githubpages&logoColor=black)](https://supersaiyane.github.io/gurpreetsingh/)
[![Email](https://img.shields.io/badge/Email-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:senghgurpreett@gmail.com)

</div>

---

## 📟 INC-0001 — "Career" · Severity: Ongoing · Status: Mitigated, monitoring

**Impact:** Platforms serving millions of banking customers stayed up.
**Root cause:** Someone decided pagers should be boring.

| Time | Event |
|:---|:---|
| `T-11y` | 🟡 First production outage. Learned that hope is not a strategy. |
| `T-8y`  | 🟢 Automated the runbook instead of following it. Toil down, sleep up. |
| `T-5y`  | 🔵 Moved from "we monitor servers" to "we measure user journeys". SLOs over CPU graphs. |
| `T-2y`  | 🟣 Started letting agents do first-response RCA. Humans review, machines triage. |
| `NOW`   | ⚪ Building the platform layer that makes the above the default, not the heroics. |

---

## 🎯 What I Actually Do

I make large systems **fail predictably instead of catastrophically.**

```
   ┌──────────────┐    signal    ┌──────────────┐   decision   ┌──────────────┐
   │  PRODUCTION  │ ───────────► │ OBSERVABILITY│ ───────────► │  AUTOMATION  │
   │  (it breaks) │              │ (I see it)   │              │  (it heals)  │
   └──────▲───────┘              └──────────────┘              └───────┬──────┘
          │                                                            │
          └──────────────────  remediation / GitOps PR  ───────────────┘
                        human reviews · machine executes
```

**The three loops I build for a living:**

| Loop | Question it answers | Where I've shipped it |
|:---|:---|:---|
| 🔭 **Observe** | *Is the user actually having a good time?* | SLO/SLI platforms, distributed tracing, log pipelines |
| 🔁 **Remediate** | *Can this fix itself before a human wakes up?* | [`auto-agent-k8s`](https://github.com/supersaiyane/auto-agent-k8s) |
| 💰 **Account** | *What is reliability costing us, and is it worth it?* | [`FinOps`](https://github.com/supersaiyane/FinOps) |

---

## 🔧 Runbooks I Open-Sourced

> These aren't demos. They're the things I wished existed when I was on call.

<table>
<tr>
<td width="50%" valign="top">

### ⚡ [auto-agent-k8s](https://github.com/supersaiyane/auto-agent-k8s)
`Go` · `Kubernetes` · `LLM`

A DaemonSet that watches your cluster and **acts**: auto-remediation, scaling,
S3 log shipping, GitOps PRs, Slack/Jira alerts, and LLM-generated RCA.

> **The bet:** most 3AM pages are a runbook a machine could have run.

</td>
<td width="50%" valign="top">

### 📚 [crashcourse](https://github.com/supersaiyane/crashcourse)
`HCL` · `Terraform` · `CLI`

**153 crash courses + 30 interactive CLI playgrounds** for DevOps, SRE, Cloud,
AI and Platform engineers. Learn by breaking things safely.

> **The bet:** you don't learn reliability from slides.

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 🏗️ [IDP_Backstage](https://github.com/supersaiyane/IDP_Backstage)
`Backstage` · `GitOps` · `Shell`

An Internal Developer Platform with guardrails, observability and incident
workflows baked in — golden paths, not golden cages.

> **The bet:** developer velocity is a reliability feature.

</td>
<td width="50%" valign="top">

### 💰 [FinOps](https://github.com/supersaiyane/FinOps)
`Python` · `AWS/Azure/GCP`

Multi-tenant FinOps SaaS: secure cloud onboarding, cost intelligence,
optimisation automation across three clouds.

> **The bet:** unowned spend is an availability risk in disguise.

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 🔐 [jogi-vault](https://github.com/supersaiyane/jogi-vault)
`Python` · `AES-256-GCM` · `TOTP`

Encrypted secret manager with 2FA, Web UI, REST API and encrypted off-site backup.

</td>
<td width="50%" valign="top">

### 📡 [RuView](https://github.com/supersaiyane/RuView)
`Rust` · `WiFi CSI`

Turns commodity WiFi into spatial intelligence and vital-sign monitoring.
No cameras, no wearables.

</td>
</tr>
</table>

<div align="center">

**[→ All 87 repositories](https://github.com/supersaiyane?tab=repositories)**

</div>

---

## 🧰 Stack (what I reach for, and when)

| Layer | Tools | I pick these because |
|:---|:---|:---|
| **Cloud** | AWS · Azure · GCP | Multi-cloud is a compliance reality in banking, not a buzzword |
| **Orchestration** | Kubernetes · Docker · ArgoCD · Terraform | Declarative or it didn't happen |
| **Observability** | Prometheus · Grafana · Elastic · Jaeger · OTel | Metrics for alerting, traces for blame, logs for regret |
| **Automation** | Python · Go · Ansible · GitHub Actions · Jenkins | Go for daemons, Python for glue, YAML under protest |
| **Data path** | Kafka · Redis · Postgres · MongoDB | Backpressure is a design decision, not an accident |

---

## 🧭 Six Things I Believe

```
1.  Design for failure first — everything else is decoration.
2.  You cannot fix what you cannot observe. Instrument before you optimise.
3.  Automate the toil. Humanise the judgment. Never the other way round.
4.  Chaos engineering isn't a disaster. It's a rehearsal you scheduled.
5.  Reliability has a price tag. Know it, or finance will find it for you.
6.  A great SRE makes the pager boring. Boring is the whole product.
```

---

## ✍️ Latest Postmortems (a.k.a. blog)

<!-- BLOG-POST-LIST:START -->
<!-- BLOG-POST-LIST:END -->

**[→ Read everything on Medium](https://medium.com/@gurpreet.singh_89)**

---

<div align="center">

### 📮 Page Me

**Collabs · Talks · Open-source · Just a good architecture argument**

[![LinkedIn](https://img.shields.io/badge/Escalate%20to%20LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/gurpreettsengh/)
[![Email](https://img.shields.io/badge/Open%20a%20Ticket-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:senghgurpreett@gmail.com)

`⚓ Nomadic by nature. Resilient by design. Always shipping.`

</div>
