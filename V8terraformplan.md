```hcl
# main.tf

resource "engineer" "gurpreet" {
  name        = "Gurpreet Singh"
  role        = "Senior Site Reliability Engineer"
  employer    = "NatWest Group"
  region      = "/dev/null"          # nomadic
  lifecycle {
    prevent_destroy = true           # resilient by design
  }

  domains = [
    "platform-engineering",
    "observability",
    "aiops",
    "finops",
    "incident-response",
  ]

  mission = <<-EOT
    Build the layer between "production is on fire"
    and "nobody had to wake up."
  EOT
}
```

<div align="center">

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/gurpreettsengh/)
[![Medium](https://img.shields.io/badge/Writing-000000?style=flat-square&logo=medium&logoColor=white)](https://medium.com/@gurpreet.singh_89)
[![Site](https://img.shields.io/badge/Portfolio-F7B731?style=flat-square&logo=githubpages&logoColor=black)](https://supersaiyane.github.io/gurpreetsingh/)
[![Email](https://img.shields.io/badge/Email-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:senghgurpreett@gmail.com)

</div>

---

## `$ terraform plan`

```
Terraform used the selected providers to generate the following execution plan.
Resource actions are indicated with the following symbols:
  + create
  ~ update in-place
  - destroy

Terraform will perform the following actions:
```

<br>

```diff
  # module.reliability will be updated in-place
  ~ resource "on_call_rotation" "your_team" {
+     alerting_strategy      = "symptom-based (SLO burn rate)"
-     alerting_strategy      = "cause-based (CPU, memory, disk)"
+     first_responder        = "automation"
-     first_responder        = "whoever is awake"
~     pager_volume           = "high"          -> "believable"
~     mean_time_to_diagnosis = "measured in coffees" -> "measured in minutes"
~     runbooks               = "markdown"      -> "executable"
    }
```

```diff
  # module.observability will be updated in-place
  ~ resource "telemetry_plane" "yours" {
~     dashboards        = "averages"           -> "percentiles + cardinality budgets"
~     traces            = "sampled by accident"-> "sampled by strategy"
~     logs              = "cost centre"        -> "forensics tier"
+     slos              = "defined, agreed, and argued about in public"
-     slos              = null
    }
```

```diff
  # module.platform will be created
+ resource "internal_developer_platform" "golden_path" {
+     backstage         = true
+     guardrails        = "self-service, audit-ready"
+     shortcut_is_safe  = true   # developers stop routing around you
+     incident_workflow = "built in, not bolted on"
    }
```

```diff
  # module.finops will be created
+ resource "cost_intelligence" "multi_cloud" {
+     clouds            = ["aws", "azure", "gcp"]
+     allocation        = "per-team, per-service, unowned = zero"
+     optimisation      = "proposes changes, not just charts"
+     emergency_cuts    = "no longer land on the redundancy you needed"
    }
```

```diff
  # module.toil will be destroyed
- resource "manual_work" "3am" {
-     ssh_to_the_node        = true
-     copy_paste_the_runbook = true
-     forget_the_change_tkt  = true
    }
```

```
Plan: 12 to add, 9 to change, 1 to destroy.
```

> **The one destroy is the point.**

---

## `$ terraform state list` — modules I've already published

```
module.remediation.auto_agent_k8s
module.education.crashcourse
module.platform.idp_backstage
module.finops.cost_platform
module.security.jogi_vault
module.research.ruview
```

<table>
<tr><td width="50%" valign="top">

**⚡ [auto-agent-k8s](https://github.com/supersaiyane/auto-agent-k8s)** · `Go` `K8s` `LLM`

```hcl
module "remediation" {
  watches   = "your cluster"
  acts      = ["heal", "scale", "ship_logs"]
  opens     = "GitOps PR for the durable fix"
  drafts    = "LLM root-cause analysis"
  pages     = "a human, for review only"
}
```

</td><td width="50%" valign="top">

**📚 [crashcourse](https://github.com/supersaiyane/crashcourse)** · `Terraform` `CLI`

```hcl
module "education" {
  courses     = 153
  playgrounds = 30   # interactive CLI
  covers      = ["devops","sre","cloud","ai"]
  method      = "break it on purpose"
}
```

</td></tr>
<tr><td width="50%" valign="top">

**🏗️ [IDP_Backstage](https://github.com/supersaiyane/IDP_Backstage)** · `Backstage` `GitOps`

```hcl
module "platform" {
  golden_paths  = true
  golden_cages  = false
  observability = "default on"
}
```

</td><td width="50%" valign="top">

**💰 [FinOps](https://github.com/supersaiyane/FinOps)** · `Python` `Multi-cloud`

```hcl
module "finops" {
  tenancy      = "multi"
  onboarding   = "secure by default"
  spend        = "a telemetry stream"
}
```

</td></tr>
</table>

Also on state: **🔐 [jogi-vault](https://github.com/supersaiyane/jogi-vault)** (AES-256-GCM + TOTP secret manager) · **📡 [RuView](https://github.com/supersaiyane/RuView)** (WiFi → spatial sensing, `Rust`) · **🤖 [AmplifyrMCP](https://github.com/supersaiyane/AmplifyrMCP)** (Claude → LinkedIn/Medium/Telegram MCP bridge)

**[→ all 87 resources in state](https://github.com/supersaiyane?tab=repositories)**

---

## `$ cat variables.tf` — the stack I default to

```hcl
variable "cloud"        { default = ["aws", "azure", "gcp"] }
variable "orchestration"{ default = ["kubernetes","docker","helm","argocd","terraform","ansible"] }
variable "observability"{ default = ["prometheus","grafana","opentelemetry","jaeger","elastic"] }
variable "languages"    { default = ["go","python","rust","typescript","bash"] }
variable "data"         { default = ["kafka","redis","postgres","mongodb","rabbitmq"] }
variable "delivery"     { default = ["github-actions","gitlab-ci","jenkins"] }
```

---

## `$ cat locals.tf` — non-negotiables

```hcl
locals {
  principles = [
    "Design for failure first. Everything after is decoration.",
    "You can't fix what you can't observe. Instrument, then optimise.",
    "Automate the toil. Humanise the judgment. Never the reverse.",
    "Chaos isn't a disaster — it's a rehearsal you scheduled.",
    "Reliability has a price tag. Know it, or finance will find it.",
    "A great SRE makes the pager boring. Boring is the whole product.",
  ]

  # applied to every resource, no exceptions
  default_tags = {
    auditable    = true
    reversible   = true
    observable   = true
    owner        = "someone with a name, not a team alias"
  }
}
```

---

## `$ cat outputs.tf`

```hcl
output "writing"  { value = "https://medium.com/@gurpreet.singh_89" }
output "linkedin" { value = "https://linkedin.com/in/gurpreettsengh" }
output "site"     { value = "https://supersaiyane.github.io/gurpreetsingh/" }
output "contact"  { value = "senghgurpreett@gmail.com" }
```

<!-- BLOG-POST-LIST:START -->
<!-- BLOG-POST-LIST:END -->

**[→ everything on Medium](https://medium.com/@gurpreet.singh_89)**

---

<div align="center">

## `$ terraform apply`

```
Do you want to perform these actions?
  Terraform will perform the actions described above.
  Only 'yes' will be accepted to approve.

  Enter a value: _
```

[![yes](https://img.shields.io/badge/yes-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/gurpreettsengh/)
[![yes](https://img.shields.io/badge/yes-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:senghgurpreett@gmail.com)

<br>

<sub>⚓ Nomadic by nature. Resilient by design. `prevent_destroy = true`.</sub>

</div>
