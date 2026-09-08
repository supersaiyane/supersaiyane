```
$ git log --author="Gurpreet Singh" --since="11.years" --oneline --reverse --graph
```

```
* a3f9c21  feat: first production deploy                          [ 2015 ]
* 7d2e884  fix: hope is not a strategy
* c19b4f0  revert: "perf: add caching layer"                       ⚠
* 4e8a1d3  refactor: alert on symptoms, not causes                 [ 2018 ]
* 90fc662  feat(observability): SLOs replace CPU dashboards
* b71d5a9  chore: automate the runbook instead of following it     [ 2021 ]
* 2c4e0f7  feat(platform): golden paths, not golden cages
* e88b3c1  feat(finops): treat cloud spend as telemetry            [ 2024 ]
* 5a7f9d2  feat(aiops): let the agent take first response          [ 2026 ]
* d0c1e44  (HEAD -> main, origin/main) docs: you are here
```

<div align="center">

**Gurpreet Singh** · Senior SRE @ **NatWest Group**
*Platform · Observability · AIOps · FinOps*

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/gurpreettsengh/)
[![Medium](https://img.shields.io/badge/Writing-000000?style=flat-square&logo=medium&logoColor=white)](https://medium.com/@gurpreet.singh_89)
[![Site](https://img.shields.io/badge/Portfolio-F7B731?style=flat-square&logo=githubpages&logoColor=black)](https://supersaiyane.github.io/gurpreetsingh/)
[![Email](https://img.shields.io/badge/Email-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:senghgurpreett@gmail.com)

<sub>`▸ the interesting commits are expandable`</sub>

</div>

---

<details>
<summary><code>git show 7d2e884</code> &nbsp;·&nbsp; <b>fix: hope is not a strategy</b></summary>

<br>

```diff
  Date:   the night I learned what "single point of failure" means

- if (probablyFine) { ship(); }
+ if (canFail) { assumeItWill(); designAround(); }
```

We had one database. Everyone knew we had one database. Nobody had written down
what happens when it goes away, because writing it down would have meant admitting
we'd need to do something about it.

The outage lasted four hours. The **conversation** we should have had would have
lasted twenty minutes, eighteen months earlier.

> **Every incident is a design review you postponed until it was expensive.**

</details>

<details>
<summary><code>git show c19b4f0</code> &nbsp;·&nbsp; <b>revert: "perf: add caching layer"</b> ⚠</summary>

<br>

```diff
  Date:   the commit I keep in my pocket

- // 40% faster reads! ship it 🚀
+ // 40% faster reads, and one stale-cache path that served
+ // the wrong customer's balance for 90 seconds.
```

This is my favourite commit in the log, because it's the one where I was **right
about the metric and wrong about the system**. Latency went down. Correctness went
sideways. I had optimised the thing I was measuring and broken the thing I wasn't.

> **A performance win you can't reason about is a correctness bug with good PR.**

I now ask one question of every optimisation: *what invariant am I trading away,
and who finds out first — me, or the customer?*

</details>

<details>
<summary><code>git show 4e8a1d3</code> &nbsp;·&nbsp; <b>refactor: alert on symptoms, not causes</b></summary>

<br>

```diff
- alert: HighCPU
-   expr: node_cpu_usage > 0.8
-   for: 5m
-   # pages you about a machine nobody is using

+ alert: SLOBurnRateCritical
+   expr: checkout_error_budget_burn_rate_1h > 14.4
+   for: 2m
+   # pages you when money is leaving
```

We deleted 340 alerts in one quarter and replaced them with eleven.

Page volume dropped ~70%. Acknowledged-within-2-minutes went to nearly 100%,
because for the first time the pager was **believable**. That's the actual product
of alerting: not coverage, *credibility*. An alert nobody trusts is worse than no
alert, because it trains a human to ignore a class of signal.

> **Every cause-based alert you delete makes the pager more trustworthy.**

</details>

<details>
<summary><code>git show b71d5a9</code> &nbsp;·&nbsp; <b>chore: automate the runbook instead of following it</b></summary>

<br>

```diff
- ## Runbook: pool saturation
- 1. SSH to the node
- 2. Check the pool metrics
- 3. Scale maxConnections
- 4. Raise a change ticket
- 5. Go back to bed (optional)

+ // runbooks/pool_saturation.go
+ // the same five steps, executed in 90 seconds, with a PR attached
```

The runbook was already the automation. It was just written in English and executed
by a sleep-deprived primate. Porting it to Go was the least creative and most
valuable quarter of my career.

> **Toil is measurable. Measure it, or you'll romanticise it.**

</details>

<details>
<summary><code>git show 5a7f9d2</code> &nbsp;·&nbsp; <b>feat(aiops): let the agent take first response</b></summary>

<br>

```
[03:41:14] burn-rate breach · payments-api · 36x
[03:41:23] diff scan: pool.maxConnections 200 → 50   ⚠
[03:42:02] ✅ mitigated   [03:42:09] ✅ GitOps PR opened
[03:42:11] ✅ RCA drafted [03:47:00] ▸ human paged — for REVIEW
```

The current commit. The bet: **the machine does first response, the human does
judgment.** Not because machines are better at incidents — they aren't — but
because the first six minutes of an incident are almost always mechanical, and
humans are terrible at mechanical work at 3AM.

The part that actually matters isn't the auto-remediation. It's that the human
arrives to a **timeline, a diff and a hypothesis already written.**

Live and open source → [**auto-agent-k8s**](https://github.com/supersaiyane/auto-agent-k8s)

</details>

---

```
$ git branch -a --sort=-committerdate
```

| Branch | What's on it |
|:---|:---|
| ⚡ [`auto-agent-k8s`](https://github.com/supersaiyane/auto-agent-k8s) | Self-healing K8s DaemonSet — remediation, GitOps PRs, LLM-drafted RCA · `Go` |
| 📚 [`crashcourse`](https://github.com/supersaiyane/crashcourse) | 153 crash courses + 30 interactive CLI playgrounds · `Terraform` `CLI` |
| 🏗️ [`IDP_Backstage`](https://github.com/supersaiyane/IDP_Backstage) | Internal Developer Platform — guardrails, observability, incident flow · `Backstage` |
| 💰 [`FinOps`](https://github.com/supersaiyane/FinOps) | Multi-tenant cloud cost intelligence + optimisation automation · `Python` |
| 🔐 [`jogi-vault`](https://github.com/supersaiyane/jogi-vault) | AES-256-GCM secret manager, TOTP 2FA, REST API · `Python` |
| 📡 [`RuView`](https://github.com/supersaiyane/RuView) | Commodity WiFi → spatial intelligence + vital signs. No cameras. · `Rust` |
| 🤖 [`AmplifyrMCP`](https://github.com/supersaiyane/AmplifyrMCP) | MCP bridge: Claude Desktop → LinkedIn, Medium, Telegram · `TypeScript` |

```
$ git branch -a | wc -l
87
```

**[→ check out any of them](https://github.com/supersaiyane?tab=repositories)**

---

```
$ git blame PRINCIPLES.md
```

```
a3f9c21  1) Design for failure first. Everything after is decoration.
90fc662  2) You can't fix what you can't observe. Instrument, then optimise.
b71d5a9  3) Automate the toil. Humanise the judgment. Never the reverse.
4e8a1d3  4) Chaos isn't a disaster — it's a rehearsal you scheduled.
e88b3c1  5) Reliability has a price tag. Know it, or finance will find it.
d0c1e44  6) A great SRE makes the pager boring. Boring is the whole product.
```

---

```
$ git log --grep="published" --author=Gurpreet
```

<!-- BLOG-POST-LIST:START -->
<!-- BLOG-POST-LIST:END -->

**[→ full history on Medium](https://medium.com/@gurpreet.singh_89)**

---

<div align="center">

```
$ git remote -v
```

| remote | url |
|:---|:---|
| `linkedin` | [in/gurpreettsengh](https://www.linkedin.com/in/gurpreettsengh/) `(fetch) (push)` |
| `medium` | [@gurpreet.singh_89](https://medium.com/@gurpreet.singh_89) `(push)` |
| `email` | [senghgurpreett@gmail.com](mailto:senghgurpreett@gmail.com) `(fetch) (push)` |

<br>

```
$ git merge --no-ff your-project
```

**Open to collaborations, talks, and open source. Bring conflicts, I like resolving them.**

<sub>⚓ Nomadic by nature. Resilient by design. Always shipping.</sub>

</div>
