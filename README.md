# Zack Wilde

**An LLM-judge (Claude Haiku) scoring a blind pool of 56 coding solutions caught 7 of 10 planted bugs, with zero false positives across the other 46.**

That's from an evaluation study I designed and ran myself — not a benchmark I'm quoting. I build the evaluation, validation, and audit layers that make unreliable AI safer to ship: ground-truth harnesses, LLM-as-judge pipelines, schema validation, and fallback logic for when models fail.

## The finding, in detail

`ai-eval-study` v2 planted 10 known-bad solutions (each with one subtle, documented defect) into a blind pool of 56, then re-judged with the same prompt as before:

- **7/10** seeded bugs caught, **0 false positives** across 46 clean solutions. Control-arm judge mean 3.40 vs 5.00 for both subject models.
- The 7 catches were locally pattern-visible (a wrong operator, a missing bounds check); the 3 misses all required simulating program state across iterations. Reading: an LLM-judge behaves like a strong linter, not a correctness oracle.
- This **refuted my own v1 hypothesis** — I'd suspected judge leniency; v2 showed the judge discriminates sharply once there's something to find, and I recorded the reversal.
- Ground truth was independently oracle-verified: **11,239 checks, 0 mismatches** across 7 oracles. The analysis plan was pre-registered before any v2 result existed.
- What it doesn't show: no Cohen's kappa (the blind human-rating pass was built but never run), and it's one judge model on one task family — 10 seeded items shows a pattern, not a law.

## Selected work

- **[ai-eval-study](https://github.com/zackwildebusiness-glitch/ai-eval-study)** — the study above: unit tests, an LLM-judge, and oracle-verified ground truth, plus the planted-bug sensitivity analysis.
- **[eval-graph](https://github.com/zackwildebusiness-glitch/eval-graph)** — a LangGraph judge-escalation loop: conditional routing, cycles, human-in-the-loop interrupt. Validated against an offline mock judge; the real-model path exists in code but hasn't been run live.
- **[opportunity-scanner](https://github.com/zackwildebusiness-glitch/opportunity-scanner)** — a website-audit engine where deterministic rules produce every finding and the LLM only rephrases them; it never originates a claim.
- **[daily-sixty](https://github.com/zackwildebusiness-glitch/daily-sixty)** — an Expo app whose AI plan-generation backend never throws: schema validation, a static fallback plan, quota refund on model failure.
- **[referral-tracker](https://github.com/zackwildebusiness-glitch/referral-tracker)** — multi-tenant Postgres with row-level-security isolation, verified by tests that a tenant can't reach another's records even with tampered IDs.
- **[ai-eval-notes](https://github.com/zackwildebusiness-glitch/ai-eval-notes)** — working notes on evaluation methodology as these projects develop.

## Looking for

AI-evaluation, LLM-reliability, or applied-AI engineering roles — remote or Hamilton/GTA, Canada.

## Contact

zackwildebusiness@gmail.com · https://zackwilde-dev.netlify.app/
