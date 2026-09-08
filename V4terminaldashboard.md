```
┌────────────────────────────────────────────────────────────────────────────┐
│  gurpreet@production:~$ whoami --verbose                                   │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│   ██████╗ ██╗   ██╗██████╗ ██████╗ ██████╗ ███████╗███████╗████████╗       │
│  ██╔════╝ ██║   ██║██╔══██╗██╔══██╗██╔══██╗██╔════╝██╔════╝╚══██╔══╝       │
│  ██║  ███╗██║   ██║██████╔╝██████╔╝██████╔╝█████╗  █████╗     ██║          │
│  ██║   ██║██║   ██║██╔══██╗██╔═══╝ ██╔══██╗██╔══╝  ██╔══╝     ██║          │
│  ╚██████╔╝╚██████╔╝██║  ██║██║     ██║  ██║███████╗███████╗   ██║          │
│   ╚═════╝  ╚═════╝ ╚═╝  ╚═╝╚═╝     ╚═╝  ╚═╝╚══════╝╚══════╝   ╚═╝          │
│                                                                            │
│  ROLE      Senior SRE  ·  NatWest Group                                    │
│  DOMAIN    Platform Engineering · Observability · AIOps · FinOps           │
│  LOCATION  /dev/null  (nomadic)                                            │
│  STATUS    ● shipping   ● on-call   ● open to collaborate                  │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

<div align="center">

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/gurpreettsengh/)
[![Medium](https://img.shields.io/badge/Medium-000000?style=flat-square&logo=medium&logoColor=white)](https://medium.com/@gurpreet.singh_89)
[![Website](https://img.shields.io/badge/Website-F7B731?style=flat-square&logo=githubpages&logoColor=black)](https://supersaiyane.github.io/gurpreetsingh/)
[![Email](https://img.shields.io/badge/Email-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:senghgurpreett@gmail.com)

</div>

---

## `$ cat mission.txt`

```
I build the layer between "production is on fire" and "nobody had to wake up."

Banking-scale platforms. Regulated environments. Millions of users who will
never know my name — which is exactly the point.
```

---

## `$ grafana --panel=focus-areas`

```
┌─ RELIABILITY ──────────────────────────┐  ┌─ PLATFORM ─────────────────────────────┐
│                                        │  │                                        │
│  SLO design      ████████████████ deep │  │  IDP / Backstage  ████████████░░ strong │
│  Incident resp.  ████████████████ deep │  │  Golden paths     ████████████░░ strong │
│  Chaos eng.      ████████████░░░░ high │  │  GitOps / ArgoCD  ████████████░░ strong │
│  On-call design  ████████████████ deep │  │  Terraform        ████████████░░ strong │
│                                        │  │                                        │
└────────────────────────────────────────┘  └────────────────────────────────────────┘

┌─ OBSERVABILITY ────────────────────────┐  ┌─ AIOps + FINOPS ───────────────────────┐
│                                        │  │                                        │
│  Metrics/Prom    ████████████████ deep │  │  LLM triage / RCA ██████████░░░░ active │
│  Tracing/OTel    ████████████████ deep │  │  Agentic remediat ██████████░░░░ active │
│  Log pipelines   ████████████░░░░ high │  │  Cost intelligence████████████░░ strong │
│  Cardinality mgm ████████████░░░░ high │  │  Rightsizing auto ████████████░░ strong │
│                                        │  │                                        │
└────────────────────────────────────────┘  └────────────────────────────────────────┘
```

---

## `$ ls -lh ~/projects --sort=impact`

```
drwxr-xr-x  ⚡ auto-agent-k8s      Go · K8s · LLM        [ ACTIVE ]
```
**Kubernetes DaemonSet that auto-remediates, autoscales, ships logs to S3, raises GitOps PRs, fires Slack/Jira alerts and drafts LLM-powered RCA.**
→ *Most 3AM pages are a runbook a machine could have run.*
[`open →`](https://github.com/supersaiyane/auto-agent-k8s)

```
drwxr-xr-x  📚 crashcourse         Terraform · CLI       [ ACTIVE ]
```
**153 crash courses + 30 interactive CLI playgrounds** covering DevOps, SRE, Cloud, AI and Platform engineering.
→ *You don't learn reliability from slides.*
[`open →`](https://github.com/supersaiyane/crashcourse)

```
drwxr-xr-x  🏗️  IDP_Backstage       Backstage · GitOps    [ ACTIVE ]
```
**Internal Developer Platform** with guardrails, observability and incident workflows built in.
→ *Golden paths, not golden cages.*
[`open →`](https://github.com/supersaiyane/IDP_Backstage)

```
drwxr-xr-x  💰 FinOps              Python · Multi-cloud  [ ACTIVE ]
```
**Multi-tenant FinOps SaaS** — secure cloud onboarding, cost intelligence, optimisation automation across AWS/Azure/GCP.
→ *Unowned spend is an availability risk in disguise.*
[`open →`](https://github.com/supersaiyane/FinOps)

```
drwxr-xr-x  🔐 jogi-vault          Python · Crypto       [ STABLE ]
drwxr-xr-x  📡 RuView              Rust · WiFi CSI       [ R&D    ]
drwxr-xr-x  🤖 AmplifyrMCP         TypeScript · MCP      [ STABLE ]
drwxr-xr-x  🏠 Saints-desk         Python · LLM          [ ACTIVE ]
```
AES-256-GCM secret manager · WiFi-signal spatial sensing · Claude→LinkedIn/Medium/Telegram MCP bridge · local-first personal command centre.

**[`$ ls ~/projects --all` → all 87 repositories](https://github.com/supersaiyane?tab=repositories)**

---

## `$ stack --tree`

```
├── cloud/
│   ├── aws           ├── azure         └── gcp
├── orchestration/
│   ├── kubernetes    ├── docker        ├── helm
│   ├── argocd        ├── terraform     └── ansible
├── observability/
│   ├── prometheus    ├── grafana       ├── opentelemetry
│   ├── jaeger        ├── elastic       └── influxdb
├── languages/
│   ├── go            ├── python        ├── rust
│   ├── typescript    └── bash
├── data/
│   ├── kafka         ├── redis         ├── postgres
│   ├── mongodb       └── rabbitmq
└── delivery/
    ├── github-actions├── gitlab-ci     └── jenkins
```

---

## `$ tail -f principles.log`

```
[FATAL]  If it can fail, it will. Design for failure first.
[INFO]   You cannot fix what you cannot observe. Instrument before you optimise.
[WARN]   Automate the toil. Humanise the judgment. Never the reverse.
[DEBUG]  Chaos isn't a disaster — it's a rehearsal you scheduled.
[INFO]   Reliability has a price tag. Know it, or finance will find it for you.
[OK]     A great SRE makes the pager boring. Boring is the whole product.
```

---

## `$ curl medium.com/@gurpreet.singh_89 | head`

<!-- BLOG-POST-LIST:START -->
<!-- BLOG-POST-LIST:END -->

**[→ read all](https://medium.com/@gurpreet.singh_89)**

---

```
gurpreet@production:~$ ./connect.sh
```

<div align="center">

**Collabs · Talks · Open source · Architecture arguments**

[![LinkedIn](https://img.shields.io/badge/Connect%20on%20LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/gurpreettsengh/)
[![Email](https://img.shields.io/badge/Send%20an%20Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:senghgurpreett@gmail.com)

```
Connection established. ⚓ Nomadic by nature. Resilient by design.
```

</div>
