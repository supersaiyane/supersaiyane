```
GURPREET(1)                  Site Reliability Manual                 GURPREET(1)



NAME
       gurpreet — senior site reliability engineer; makes pagers boring


SYNOPSIS
       gurpreet [--observability] [--platform] [--aiops] [--finops]
                [--incident-response] [--verbose] TARGET_SYSTEM

       gurpreet --collaborate < your_idea


DESCRIPTION
       gurpreet builds the layer between "production is on fire" and
       "nobody had to wake up."

       Eleven years at banking scale, currently at NatWest Group. Operates on
       large regulated systems where downtime is a headline and the best work
       is invisible by design. Millions of users depend on the output daily
       and will never know the name, which is the intended behaviour.

       Accepts chaos on stdin. Emits reliability on stdout. Writes the
       postmortem to stderr, in public.
```

<div align="center">

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/gurpreettsengh/)
[![Medium](https://img.shields.io/badge/Writing-000000?style=flat-square&logo=medium&logoColor=white)](https://medium.com/@gurpreet.singh_89)
[![Site](https://img.shields.io/badge/Portfolio-F7B731?style=flat-square&logo=githubpages&logoColor=black)](https://supersaiyane.github.io/gurpreetsingh/)
[![Email](https://img.shields.io/badge/Email-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:senghgurpreett@gmail.com)

</div>

```
OPTIONS
       --observability
              Replace averages with percentiles. Design SLIs that correlate
              with a customer giving up. Enforce a metric cardinality budget
              before the bill becomes an incident. Sample traces on purpose.
              Stack: Prometheus, Grafana, OpenTelemetry, Jaeger, Elastic.

       --platform
              Build the Internal Developer Platform where the safe path is
              also the fast path. Golden paths, not golden cages. Guardrails
              a regulator signs off and a developer doesn't route around.
              Stack: Backstage, ArgoCD, Terraform, Kubernetes.

       --aiops
              Let automation take first response; keep humans on judgment.
              LLMs write the timeline, the hypothesis and the RCA — never the
              approval. Deterministic triggers, reversible actions, human gate
              on anything that touches state or money.

       --finops
              Treat cloud spend as a telemetry stream. Per-team allocation,
              unit economics, rightsizing that proposes changes instead of
              charting them. Prevents the emergency cost-cut from landing on
              the redundancy you needed.

       --incident-response
              Delete the alerts that lie. Automate the runbooks. Make the
              pager believable, then make it quiet. Blameless postmortems
              that produce a diff, not a feeling.

       -v, --verbose
              Explains the reasoning, the tradeoff, and the invariant being
              sold. Enabled by default. Cannot be disabled.


EXAMPLES
       Heal a cluster before a human is paged:

           $ gurpreet --aiops --incident-response ./your-k8s-cluster
```

### ⚡ [auto-agent-k8s](https://github.com/supersaiyane/auto-agent-k8s) · `Go` `Kubernetes` `LLM`
Kubernetes DaemonSet that triages, auto-remediates, scales, ships logs to S3,
opens a **GitOps PR for the durable fix**, and drafts the RCA before you've
opened the laptop. Every action reversible or human-gated.

```
       Learn the whole discipline by breaking things on purpose:

           $ gurpreet --teach --interactive
```

### 📚 [crashcourse](https://github.com/supersaiyane/crashcourse) · `Terraform` `CLI`
**153 crash courses + 30 interactive CLI playgrounds** across DevOps, SRE,
Cloud, AI and Platform engineering. You cannot learn failure handling by
reading about failure handling.

```
       Give developers self-service that survives an audit:

           $ gurpreet --platform --guardrails ./your-org
```

### 🏗️ [IDP_Backstage](https://github.com/supersaiyane/IDP_Backstage) · `Backstage` `GitOps`
Internal Developer Platform with observability and incident workflow built in
rather than bolted on. Developer velocity treated as a reliability feature.

```
       Find out what reliability is actually costing you:

           $ gurpreet --finops --clouds aws,azure,gcp
```

### 💰 [FinOps](https://github.com/supersaiyane/FinOps) · `Python` `Multi-cloud`
Multi-tenant FinOps SaaS: secure onboarding, cross-cloud cost intelligence,
optimisation automation. Unowned spend is an availability risk in disguise.

```
FILES
       ~/.gurpreet/repos/
              87 public repositories. The ones above are load-bearing.
              Also present:
                jogi-vault      AES-256-GCM secret manager, TOTP 2FA, REST API
                RuView          commodity WiFi -> spatial sensing        (Rust)
                AmplifyrMCP     Claude Desktop -> LinkedIn/Medium/Telegram
                Saints-desk     local-first command centre, LLM co-editor
                gitops_aws      opinionated GitOps reference arch on AWS
```

**[→ browse all 87](https://github.com/supersaiyane?tab=repositories)**

```
ENVIRONMENT
       CLOUD          aws azure gcp
       ORCHESTRATION  kubernetes docker helm argocd terraform ansible
       OBSERVE        prometheus grafana opentelemetry jaeger elastic influxdb
       LANGUAGES      go python rust typescript bash
       DATA           kafka redis postgres mongodb rabbitmq
       DELIVERY       github-actions gitlab-ci jenkins
       REGION         /dev/null   (nomadic; will relocate for a good problem)


DIAGNOSTICS
       The following messages are emitted, unprompted, in most meetings:

       "Design for failure first — everything after that is decoration."
       "You can't fix what you can't observe. Instrument, then optimise."
       "Automate the toil. Humanise the judgment. Never the reverse."
       "Chaos isn't a disaster. It's a rehearsal you scheduled."
       "Reliability has a price tag. Know it, or finance will find it."
       "A great SRE makes the pager boring. Boring is the whole product."


EXIT STATUS
       0      System is boring. Pager silent. Correct outcome.
       1      Incident detected, auto-remediated, PR raised, human notified.
       2      Incident escalated to a human — with timeline and RCA attached.
       130    Interrupted for a genuinely good architecture argument.
              This is not an error and will not be fixed.


BUGS
       Will ask "what's the SLI?" in meetings about frontend colour choices.

       Has rewritten a working bash script in Go for no operational reason
       whatsoever. Refuses to accept this as a defect.

       Once built a year of beautiful dashboards that nobody opened. Now
       treats adoption as a feature and brings it up more than is welcome.

       Cannot be talked out of percentiles.

       Frontend: will make your dashboard load; will not make it beautiful.
       WONTFIX.

       Report bugs to: senghgurpreett@gmail.com
```

```
SEE ALSO
       medium(1)    long-form arguments about observability and SRE practice
       linkedin(1)  the professional-tone build of the same binary
       site(1)      https://supersaiyane.github.io/gurpreetsingh/
```

<!-- BLOG-POST-LIST:START -->
<!-- BLOG-POST-LIST:END -->

**[→ full manual on Medium](https://medium.com/@gurpreet.singh_89)**

```
AUTHOR
       Written by Gurpreet Singh.
       Nomadic by nature. Resilient by design. Always shipping.


COPYRIGHT
       Opinions are my own. Outages are everyone's.
```

<div align="center">

<br>

### `$ man gurpreet | grep -i collaborate`

**Open to collaborations, talks, open source, and hostile design reviews.**

[![LinkedIn](https://img.shields.io/badge/Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/gurpreettsengh/)
[![Email](https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:senghgurpreett@gmail.com)

<br>

```
GNU SRE Utilities                  2026                          GURPREET(1)
```

</div>
