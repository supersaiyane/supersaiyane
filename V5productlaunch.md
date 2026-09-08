<div align="center">

<h1>Gurpreet Singh</h1>

**Senior SRE @ NatWest Group** · Platform Engineering · Observability · AIOps · FinOps

*I ship reliability tooling. Below is the catalogue — every one of them started as a 3AM problem.*

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/gurpreettsengh/)
[![Medium](https://img.shields.io/badge/Blog-000000?style=for-the-badge&logo=medium&logoColor=white)](https://medium.com/@gurpreet.singh_89)
[![Website](https://img.shields.io/badge/Portfolio-F7B731?style=for-the-badge&logo=githubpages&logoColor=black)](https://supersaiyane.github.io/gurpreetsingh/)
[![Email](https://img.shields.io/badge/Hire%20%2F%20Collab-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:senghgurpreett@gmail.com)

</div>

---

<div align="center">

## 🛰️ The Catalogue

*Four flagship builds. Each one solves a problem I actually had.*

</div>

---

### ⚡ auto-agent-k8s
> **The self-healing cluster agent**

[![Go](https://img.shields.io/badge/Go-00ADD8?style=flat-square&logo=go&logoColor=white)](#)
[![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)](#)
[![LLM](https://img.shields.io/badge/LLM_RCA-8A2BE2?style=flat-square)](#)
[![Stars](https://img.shields.io/github/stars/supersaiyane/auto-agent-k8s?style=flat-square&color=F7B731)](https://github.com/supersaiyane/auto-agent-k8s)

|  |  |
|:--|:--|
| **The problem** | Most 3AM pages are a runbook a human executes while half-asleep. The knowledge exists — it just isn't wired to the alert. |
| **The build** | A Kubernetes DaemonSet that watches the cluster and *acts*: auto-remediation, scaling decisions, S3 log shipping, GitOps pull requests for durable fixes, Slack/Jira notification, and an LLM-drafted root-cause analysis attached to the ticket. |
| **Why it matters** | The machine does first response. The human does judgment — and arrives with the timeline, the diff and a hypothesis already written. |
| **Status** | 🟢 Active · production-shaped, not a demo |

**[→ Explore auto-agent-k8s](https://github.com/supersaiyane/auto-agent-k8s)**

---

### 📚 crashcourse
> **153 crash courses. 30 interactive CLI playgrounds.**

[![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white)](#)
[![CLI](https://img.shields.io/badge/Interactive_CLI-000000?style=flat-square&logo=gnubash&logoColor=white)](#)
[![Stars](https://img.shields.io/github/stars/supersaiyane/crashcourse?style=flat-square&color=F7B731)](https://github.com/supersaiyane/crashcourse)

|  |  |
|:--|:--|
| **The problem** | Every DevOps/SRE learning path is a reading list. You cannot learn failure handling by reading about failure handling. |
| **The build** | 153 structured crash courses across DevOps, SRE, Cloud, AI and Product engineering — plus **30 interactive CLI playgrounds** where you break things on purpose and watch what happens. |
| **Why it matters** | This is the curriculum I wish someone had handed me in year one. It's free, it's hands-on, and it assumes you're smart. |
| **Status** | 🟢 Active · growing |

**[→ Start learning](https://github.com/supersaiyane/crashcourse)**

---

### 🏗️ IDP_Backstage
> **An Internal Developer Platform that doesn't fight you**

[![Backstage](https://img.shields.io/badge/Backstage-9BF0E1?style=flat-square&logo=backstage&logoColor=black)](#)
[![GitOps](https://img.shields.io/badge/GitOps-EF7B4D?style=flat-square&logo=argo&logoColor=white)](#)
[![Stars](https://img.shields.io/github/stars/supersaiyane/IDP_Backstage?style=flat-square&color=F7B731)](https://github.com/supersaiyane/IDP_Backstage)

|  |  |
|:--|:--|
| **The problem** | Platform teams build guardrails; developers route around them. The guardrail loses because the golden path is slower than the shortcut. |
| **The build** | A Backstage-powered IDP with GitOps delivery, guardrails, observability and incident workflows wired in from day one — self-service that a regulator would also sign off on. |
| **Why it matters** | Developer velocity *is* a reliability feature. Make the safe path the fast path and compliance stops being a tax. |
| **Status** | 🟢 Active |

**[→ Explore the platform](https://github.com/supersaiyane/IDP_Backstage)**

---

### 💰 FinOps
> **Cloud spend as a first-class telemetry stream**

[![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)](#)
[![Multi-cloud](https://img.shields.io/badge/AWS_·_Azure_·_GCP-232F3E?style=flat-square&logo=icloud&logoColor=white)](#)
[![Stars](https://img.shields.io/github/stars/supersaiyane/FinOps?style=flat-square&color=F7B731)](https://github.com/supersaiyane/FinOps)

|  |  |
|:--|:--|
| **The problem** | Nobody owns the bill until it's a board slide. By then the architectural decision that caused it is two years old. |
| **The build** | Multi-tenant FinOps SaaS: secure cloud onboarding, cross-cloud cost intelligence, and optimisation automation that proposes changes instead of just charting them. |
| **Why it matters** | Unowned spend is an availability risk wearing a disguise — the emergency cost cut always lands on the redundancy you needed. |
| **Status** | 🟢 Active |

**[→ Explore FinOps](https://github.com/supersaiyane/FinOps)**

---

<div align="center">

## 🧪 The Lab

*Smaller builds, sharper edges.*

</div>

| Project | One line | Stack |
|:---|:---|:---|
| [**🔐 jogi-vault**](https://github.com/supersaiyane/jogi-vault) | AES-256-GCM secret manager with TOTP 2FA, Web UI, REST API and encrypted off-site backup | `Python` `Cryptography` |
| [**📡 RuView**](https://github.com/supersaiyane/RuView) | Turns commodity WiFi signals into spatial intelligence and vital-sign monitoring — no cameras, no wearables | `Rust` `Signal Processing` |
| [**🤖 AmplifyrMCP**](https://github.com/supersaiyane/AmplifyrMCP) | MCP server wiring Claude Desktop into LinkedIn, Medium and Telegram — publish natively from an AI session | `TypeScript` `MCP` |
| [**🏠 Saints-desk**](https://github.com/supersaiyane/Saints-desk) | Local-first personal command centre: Notes-level fluency, Notion-level structure, an LLM as co-editor | `Python` `LLM` |
| [**☁️ gitops_aws**](https://github.com/supersaiyane/gitops_aws) | Opinionated GitOps reference architecture on AWS | `Terraform` |

<div align="center">

**[→ Browse all 87 repositories](https://github.com/supersaiyane?tab=repositories)**

</div>

---

<div align="center">

## 🧭 The Operating System Behind All Of It

</div>

| | |
|:---|:---|
| **Design for failure first** | Everything after that is decoration. |
| **Instrument before you optimise** | You cannot fix what you cannot observe. |
| **Automate the toil, humanise the judgment** | Never the other way round. |
| **Chaos is a rehearsal** | Not a disaster — one you scheduled. |
| **Reliability has a price tag** | Know it, or finance will find it for you. |
| **Make the pager boring** | Boring is the entire product. |

---

<div align="center">

## ✍️ I Write Too

</div>

<!-- BLOG-POST-LIST:START -->
<!-- BLOG-POST-LIST:END -->

<div align="center">

**[→ All articles on Medium](https://medium.com/@gurpreet.singh_89)**

</div>

---

<div align="center">

## 📮 Let's Build Something

**Collaborations · Talks · Open-source · Consulting on observability, IDPs and AIOps**

[![LinkedIn](https://img.shields.io/badge/Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/gurpreettsengh/)
[![Email](https://img.shields.io/badge/Email%20Me-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:senghgurpreett@gmail.com)

⭐ *If any of these solved a problem for you, a star tells me which ones to keep building.*

<sub>⚓ Nomadic by nature. Resilient by design. Always shipping.</sub>

</div>
