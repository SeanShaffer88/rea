# Free AI models that write code on GitHub

_Verified 2026-10-26. GitHub, Google, and the model vendors change these offers
often. Each section links its primary source so you can re-check before you
depend on it._

There is no single "free AI model" inside GitHub. What exists is a set of
access paths, and they are easy to confuse:

- **Free inside GitHub:** GitHub Copilot Free for any individual account, plus
  Copilot Student and free Copilot Pro for verified students, teachers, and
  popular open-source maintainers.
- **Free model weights:** open-licensed coding models you download and run
  yourself. No per-token bill, but you supply the hardware.
- **Free API tiers outside GitHub:** Google Gemini API free tier, Groq, and
  OpenRouter `:free` models, callable from a GitHub repo or Action.
- **Retired:** GitHub Models, the old answer to this question. It shut down on
  2026-07-30 and many lists still recommend it.

## 1. Copilot Free: the only model access built into GitHub

Sign in with any GitHub account, no payment method, and Copilot Free turns on
at <https://github.com/github-copilot/free_signup>.

| Item             | Copilot Free                                                                                                                |
| ---------------- | --------------------------------------------------------------------------------------------------------------------------- |
| Price            | $0, individual accounts only                                                                                                |
| Model choice     | Auto model selection only; no picker                                                                                        |
| Models reached   | Entry-level models routed by Auto. GitHub's feature page names Claude Haiku 4.5, GPT-5 mini, "and more"; the roster rotates |
| Code completions | 2,000 per month (inline suggestions and next-edit)                                                                          |
| Chat and agent   | "Limited" use drawn from an allowance of GitHub AI Credits. GitHub does not publish the Free-plan credit figure             |
| Surfaces         | Copilot Chat in the IDE, on GitHub, on Mobile, in Windows Terminal; Copilot CLI; the Copilot app                            |
| Agent and MCP    | Agent mode and Model Context Protocol servers are part of the Free plan, metered by the same credit allowance               |
| Code review      | Only "Review selection" in VS Code                                                                                          |

What that means in practice: you can drive a real multi-file coding agent on
GitHub for free, but your budget is completions plus an unpublished credit
allowance, and you cannot choose the model. The old "50 chat requests per
month" number that appears on blog comparisons is no longer the plan wording.

Caveat: GitHub renders the per-plan feature matrix on that page as icons, so
confirm the current limits on your own
[Copilot settings](https://github.com/settings/copilot) page before planning
around them.

Sources:
[Copilot plans](https://docs.github.com/en/copilot/get-started/plans),
[Copilot feature page](https://github.com/features/copilot),
[Copilot billing](https://docs.github.com/en/billing/concepts/product-billing/github-copilot-licenses).

## 2. Free upgrades to Copilot Pro-level access

These are the genuinely free paths to better models, and they are worth ten
minutes of checking.

| Offer            | Who qualifies                                                  | What changes                                                                                                                          |
| ---------------- | -------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| Copilot Student  | Verified students via GitHub Education                         | No 2,000-completion cap (reported as unlimited), a larger AI Credit allowance, auto model selection only, third-party agents excluded |
| Free Copilot Pro | Verified teachers and maintainers of popular open-source repos | Full model picker (Opus-class models excluded), Pro credit allowance                                                                  |

Eligibility is re-evaluated monthly. Check it at
<https://github.com/settings/copilot>; the docs walk through both flows:
[Copilot Student](https://docs.github.com/copilot/how-tos/manage-your-account/free-access-with-copilot-student),
[teachers and maintainers](https://docs.github.com/en/copilot/how-tos/copilot-on-github/set-up-copilot/enable-copilot/set-up-for-teachers-and-os-maintainers).

## 3. Open-weight coding models: free to run, no token bill

These are the models that actually cost nothing per token. Download the
weights, run them locally or on a machine you already pay for, and connect any
BYOK agent (Copilot, OpenCode, Cline, Continue, Aider, your own script).

| Model                      | Maker        | Size (total / active)   | License         | Why it is here                                                                                         |
| -------------------------- | ------------ | ----------------------- | --------------- | ------------------------------------------------------------------------------------------------------ |
| Qwen3.8-27B                | Alibaba      | 27.8B dense             | Apache 2.0      | Best strong model that fits one consumer GPU or a 32 GB Mac                                            |
| Qwen3-Coder-Next           | Alibaba      | 80B / 3B                | Apache 2.0      | Sparse MoE built for local coding agents; fast on modest hardware                                      |
| Qwen3-Coder-480B-A35B      | Alibaba      | 480B / 35B              | Apache 2.0      | Frontier-class agentic coding, needs a multi-GPU host                                                  |
| DeepSeek V4.1 Flash        | DeepSeek     | 552B / 16B              | MIT             | Cleanest license among frontier-class open coding models                                               |
| DeepSeek V4 Pro            | DeepSeek     | 1.6T / 49B              | MIT             | Top SWE-bench scores, cluster-scale hardware                                                           |
| GLM-5.3-Flash              | Z.ai (Zhipu) | 321B / 18B              | MIT             | Strong long-horizon coding at mid-size footprint                                                       |
| GLM-5.3                    | Z.ai (Zhipu) | 753B / 40B              | GLM-5.3 license | Near-frontier agentic coding; MIT-style with a security-review clause for model-as-a-service operators |
| Kimi K2.7-Code             | Moonshot AI  | 1T / 32B                | Modified MIT    | Coding specialist with a commercial branding condition                                                 |
| Kimi K3                    | Moonshot AI  | 2.8T / 104B             | Kimi K3 license | Current top open-weight model; custom, non-OSI license                                                 |
| gpt-oss-120b / gpt-oss-20b | OpenAI       | 117B / 5.1B, 21B / 3.6B | Apache 2.0      | The 20b runs on a 16 GB laptop; the 120b on one 80 GB GPU                                              |
| Devstral Small 2           | Mistral      | ~24B dense              | Apache 2.0      | Fits a single 24 GB GPU, tuned for agentic repo edits                                                  |
| Gemma 4                    | Google       | 4B–31B                  | Gemma license   | Small, fast, permissive-ish; good for tinkering                                                        |

Runners, all free: [Ollama](https://ollama.com/),
[llama.cpp](https://github.com/ggml-org/llama.cpp),
[LM Studio](https://lmstudio.ai/), [vLLM](https://github.com/vllm-project/vllm),
[SGLang](https://github.com/sgl-project/sglang).

Read the license, not just the parameter count. Apache 2.0 and MIT (Qwen,
DeepSeek Flash/Pro, GLM-5.3-Flash, gpt-oss, Devstral) are the safe choices for
commercial work. GLM-5.3, Kimi K3, and the modified-MIT Kimi models carry
clauses that matter if you resell inference or ship at very large scale.

One trap to avoid: GitHub Actions on public repositories is free and
unlimited, but it is CI infrastructure, not free GPU hosting. Running a model
there for anything beyond a workflow that genuinely needs inference sits
outside the acceptable-use terms, and hosted runners have no GPU.

## 4. Free API tiers you can call from a GitHub repo

These are not GitHub products, but they are what you wire into a GitHub
Action, a bot, or a BYOK agent when you want hosted models at zero cost.

| Provider                      | Free coding models                                                  | Limits (as published)                                                                  | Catch                                                                                             |
| ----------------------------- | ------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| Groq                          | `openai/gpt-oss-120b`, `openai/gpt-oss-20b`, `qwen/qwen3.8-27b`     | 30 RPM, 1,000 RPD, 8k TPM, 200k TPD per model; per organisation, not per key           | Very fast, but the daily cap stops long agent runs                                                |
| OpenRouter                    | Any model whose ID ends in `:free`, or the `openrouter/free` router | 20 RPM; 50 requests/day, raised to 1,000/day after a one-time $10 credit purchase      | Free variants rotate and can be withdrawn without notice                                          |
| Google Gemini API / AI Studio | Gemini Flash and Flash-Lite class models, plus Gemma                | Per-model RPM/TPM/RPD, visible only in AI Studio; Google no longer publishes the table | Free-tier prompts and outputs may be used to improve Google products, so do not send private code |
| Mistral                       | Codestral, Mistral Small                                            | "Experiment" free tier, roughly 1B tokens/month, opt-in training                       | Terms favour evaluation; verify on the console                                                    |
| Cerebras                      | gpt-oss-120b, Qwen3.8-27B                                           | No permanent free tier since 2026-07-16: $5 credit for 30 days after adding a card     | Not actually free; listed because many guides still say otherwise                                 |

Sources:
[Groq rate limits](https://console.groq.com/docs/rate-limits),
[OpenRouter limits](https://openrouter.ai/docs/api-reference/limits),
[Gemini API billing](https://ai.google.dev/gemini-api/docs/billing),
[Cerebras free tier FAQ](https://www.cerebras.ai/pricing).

Data-handling rule that saves people from a bad week: free tiers are for code
you can afford to leak. Copilot Free is covered by GitHub's Copilot data terms;
Gemini's unpaid tier and Mistral's Experiment tier may train on what you send;
OpenRouter free models inherit whatever the serving provider does. Keep private
repositories on a paid plan, a local model, or an enterprise agreement.

## 5. Dead ends: do not trust older recommendation lists

| Thing                                                    | Status                                                                                                                                               |
| -------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| GitHub Models (playground, catalog, inference API, BYOK) | Fully retired 2026-07-30 for every customer. Calls now fail; use Copilot for in-GitHub work or Microsoft Foundry for a model catalog                 |
| Gemini CLI free tier (1,000 requests/day)                | Ended 2026-06-18 for free, AI Pro, and Ultra accounts. Google points individuals at the closed-source Antigravity CLI with an unpublished weekly cap |
| Qwen Code free OAuth tier                                | Cut to 100 requests/day in February 2026, discontinued 2026-04-15. Needs an API key or Alibaba Cloud plan                                            |
| Manual model selection on Copilot Free and Student       | Removed 2026-06-24; Auto is the only option                                                                                                          |
| Cerebras permanent free tier                             | Replaced by a card-gated 30-day trial on 2026-07-16                                                                                                  |
| Roo Code, Continue.dev, Aider                            | Roo archived read-only, Continue wound down after the Cursor acquisition, Aider dormant. The tools still run; the free hosted perks do not           |

The pattern is consistent: 2025-era free tiers were scaled back during 2026 as
agentic usage grew. Treat any list without a 2026 verification date as
historical.

## 6. What I would pick

| Situation                                            | Free choice                                                                      |
| ---------------------------------------------------- | -------------------------------------------------------------------------------- |
| You just want an agent inside GitHub, today          | Copilot Free in VS Code, the GitHub web UI, or Copilot CLI                       |
| You are a student                                    | Claim Copilot Student first: no completion cap, bigger credit allowance          |
| You are a teacher or OSS maintainer                  | Claim free Copilot Pro: that is the only free plan with a model picker           |
| Private code, no budget, decent GPU or Apple silicon | Qwen3.8-27B or Devstral Small 2 via Ollama, wired to Copilot or OpenCode         |
| Private code, no GPU                                 | Groq free tier with `gpt-oss-120b` for interactive work, accepting the daily cap |
| Automation in CI                                     | OpenRouter `:free` behind the `openrouter/free` router, with a fallback to Groq  |
| Frontier-quality open weights, no cost per token     | DeepSeek V4.1 Flash or GLM-5.3-Flash on rented compute you already have          |

## 7. Primary sources and verification dates

- GitHub Copilot plans, models, and limits (2026-10-11):
  <https://docs.github.com/en/copilot/get-started/plans>
- Copilot billing and free use of Copilot (2026-06-04):
  <https://docs.github.com/en/billing/concepts/product-billing/github-copilot-licenses>
- Copilot Free signup: <https://github.com/github-copilot/free_signup>
- Copilot Student: <https://docs.github.com/copilot/how-tos/manage-your-account/free-access-with-copilot-student>
- Copilot Pro for teachers and maintainers:
  <https://docs.github.com/en/copilot/how-tos/copilot-on-github/set-up-copilot/enable-copilot/set-up-for-teachers-and-os-maintainers>
- GitHub Models retirement (2026-07-30):
  <https://github.blog/changelog/2026-07-30-github-models-is-now-retired/>
- GitHub Actions billing, free standard runners on public repos:
  <https://docs.github.com/en/billing/concepts/product-billing/github-actions>
- Groq rate limits: <https://console.groq.com/docs/rate-limits>
- OpenRouter limits: <https://openrouter.ai/docs/api-reference/limits>
- Gemini API pricing and free tier: <https://ai.google.dev/gemini-api/docs/billing>

Model names, parameter counts, and licenses in section 3 come from the
publishers' model cards on Hugging Face; confirm them there before you download
tens of gigabytes. Licenses, benchmark claims, and free quotas all changed at
least once during 2026.
