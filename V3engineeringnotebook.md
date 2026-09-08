<div align="center">

# Gurpreet Singh
**Senior SRE @ NatWest Group** · Platform · Observability · AIOps · FinOps

*I keep large regulated systems boring. This page is the notebook.*

[LinkedIn](https://www.linkedin.com/in/gurpreettsengh/) · [Medium](https://medium.com/@gurpreet.singh_89) · [Site](https://supersaiyane.github.io/gurpreetsingh/) · [Email](mailto:senghgurpreett@gmail.com)

</div>

---

## The system I spend my life inside

Most reliability work is one control loop, repeated at different altitudes. Here's the one I build:

```
                         ┌───────────────────────────────────────────┐
                         │              USER JOURNEY                  │
                         │      (the only SLI that actually pays)     │
                         └────────────────────┬──────────────────────┘
                                              │ emits
        ┌─────────────────────────────────────▼─────────────────────────────────────┐
        │                            TELEMETRY PLANE                                │
        │   metrics ──► alerting     traces ──► causality     logs ──► forensics    │
        │   (Prometheus)             (OTel / Jaeger)          (Elastic / S3)        │
        └─────────────────────────────────────┬─────────────────────────────────────┘
                                              │ SLO burn rate
                          ┌───────────────────▼───────────────────┐
                          │            DECISION PLANE             │
                          │  Is this worth a human? ─── no ──┐    │
                          │  LLM triage · runbook match      │    │
                          └───────────┬──────────────────────┼────┘
                                 yes  │                      │ no
                     ┌────────────────▼──────┐   ┌───────────▼─────────────┐
                     │   PAGE A HUMAN        │   │   AUTO-REMEDIATE        │
                     │  context pre-attached │   │  scale · restart · shift│
                     │  RCA draft in ticket  │   │  GitOps PR for the fix  │
                     └───────────────────────┘   └───────────┬─────────────┘
                                                             │
                          ◄────── feedback: did it work? ─────┘
```

**Everything I open-source is a piece of this diagram.**

| Plane | My implementation |
|:---|:---|
| Decision + Remediation | [`auto-agent-k8s`](https://github.com/supersaiyane/auto-agent-k8s) — DaemonSet that triages, heals, and opens the PR |
| Developer surface | [`IDP_Backstage`](https://github.com/supersaiyane/IDP_Backstage) — the IDP that makes the golden path the easy path |
| Cost as a signal | [`FinOps`](https://github.com/supersaiyane/FinOps) — multi-cloud spend as a first-class telemetry stream |
| Teaching the loop | [`crashcourse`](https://github.com/supersaiyane/crashcourse) — 153 courses, 30 CLI playgrounds |

---

## Field notes — things production taught me the hard way

**① Alerting on causes doesn't scale. Alerting on symptoms does.**
"CPU > 80%" pages you at 3AM for a system nobody is using. "Checkout p99 > 2s, burning 5% of the monthly error budget per hour" pages you when it matters. Every cause-based alert you delete makes the pager more trustworthy.

**② The error budget is a negotiation tool, not a metric.**
Its real job isn't measuring reliability — it's giving engineering and product a shared, non-emotional way to argue about whether to ship or to stabilise. The number is the excuse to have the conversation.

**③ Dashboards lie by omission.**
Averages hide the users you're failing. If a panel doesn't have a percentile, a cardinality note, and a "what would make this wrong" caption, it's decoration. I wrote about this: *[Why Your Observability Platform Is Lying to You](https://medium.com/@gurpreet.singh_89)*.

**④ Automation that can't explain itself won't be trusted, and untrusted automation gets disabled.**
This is why LLM-assisted RCA matters more than LLM-assisted *action*. The value isn't the machine fixing it — it's the machine handing a human the timeline, the diff, and the hypothesis before they've finished opening the laptop.

**⑤ Toil is measurable. Measure it, or you'll romanticise it.**
Hours per week, per person, per class of task. The number is always worse than the vibe. Once it's on a dashboard, the automation gets funded.

**⑥ In regulated environments, the constraint is auditability, not technology.**
Multi-cloud isn't a resume line in banking, it's a regulator's question. GitOps isn't fashion — it's "who approved this change and when", answered by `git log`.

---

## What I'm good at, honestly

| Area | Depth | Shape of the work |
|:---|:---|:---|
| **Observability architecture** | Deep | SLI/SLO design, metric cardinality budgets, trace sampling strategy, log pipeline economics |
| **Kubernetes at scale** | Deep | Multi-tenant clusters, admission control, autoscaling behaviour, failure-domain design |
| **Incident response** | Deep | On-call design, escalation paths, blameless postmortems, MTTR reduction as a programme |
| **Platform / IDP** | Strong | Backstage, golden paths, self-service with guardrails, developer experience metrics |
| **IaC & GitOps** | Strong | Terraform module design, ArgoCD, drift detection, promotion pipelines |
| **AIOps** | Building | LLM triage, runbook retrieval, agentic remediation with human-in-the-loop |
| **FinOps** | Strong | Multi-cloud allocation, unit economics, rightsizing automation |

---

## Toolbox

```
cloud         AWS · Azure · GCP
orchestrate   Kubernetes · Docker · Helm · ArgoCD · Terraform · Ansible
observe       Prometheus · Grafana · OpenTelemetry · Jaeger · Elastic · InfluxDB
build         Go · Python · Rust · TypeScript · Bash
pipe          Kafka · Redis · RabbitMQ · Postgres · MongoDB
ship          GitHub Actions · GitLab CI · Jenkins
```

---

## Writing

I publish long-form on SRE practice, observability and platform engineering.

<!-- BLOG-POST-LIST:START -->
<!-- BLOG-POST-LIST:END -->

**[→ All articles on Medium](https://medium.com/@gurpreet.singh_89)**

---

<div align="center">

### Let's talk

If you're wrestling with an observability rewrite, an IDP rollout, an on-call
that's eating your team, or an AIOps proof-of-concept that needs to survive an
audit — I'd genuinely enjoy that conversation.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/gurpreettsengh/)
[![Email](https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:senghgurpreett@gmail.com)

<sub>⚓ Nomadic by nature. Resilient by design. Always shipping.</sub>

</div>
