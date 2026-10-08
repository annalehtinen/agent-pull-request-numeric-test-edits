# F12B salvage: agent PRs that edit numeric test oracles in scientific software (negative result)
Paper_0005 / DPO-F12b, 2026-09-28. Decision: UNTESTABLE [t6_f12b_decision.json]. Every number below names its file.

## Finding
The public test-patch table of agent PRs cannot answer whether AI coding agents silently change validated
numbers (expected values, tolerances) in the tests of scientific or energy-modelling software. It covers 5
scientific repositories and 0 of the 17 named energy-modelling repositories; its 47 scientific agent PRs hold
exactly 1 numeric oracle edit [t5e_sci_census_labels.json]; the lead's Stage-1 threshold is 30 flagged PRs.

## What exists [t4_f12b_killcheck.json, t4c_adjudication.json]
- No released PR-level label of agent edits to numeric expected values or tolerances. 60 queries on 6 channels
  (arXiv 15, OpenAlex 11, Hugging Face 11, Google Scholar 8, GitHub 8, Crossref 7); 214 flagged candidates
  read; 16 close entries adjudicated from full text or released files; none triggers the kill rule.
- Nearest: column `adapted` of pr_test_quality in mabujadallah/GitHub-Agentic-PR-Dataset (CC-BY-4.0, rev
  8a44bdb6, added 2026-07-21). Stated: "The fix edits an existing test's expected values rather than adding a
  new test." Measured: 5 of 20 adapted agent PRs edit an existing expected value (Wilson 0.11-0.47), none of
  them numeric; 0 of 20 non-adapted PRs that modify a test file do (0-0.16). It behaves as "an existing test
  was edited" [t4c_adapted_labels.json].
- Adjacent: arXiv 2607.18057 ("Modifies Tests", structural); 2601.21194 (Add/Mod/Del, 339 agent PRs);
  2606.18168 (oracle strength of added lines); ImpossibleBench 2510.20270 and EvilGenie 2511.21654 (test
  edits in benchmark runs, not PRs).

## What the public table holds [t5_f12b_feasibility.json, t5a_detect.json]
- pr_test_patches: 222,208 test-file patches, 49,042 bug-fix PRs, 173 repositories, 7,391 agent PRs.
- Detector v2 (oracle_edit_detector.py: an existing numeric literal changed on an assertion or tolerance line):
  2,626 hunks; 1,218 PRs; 151 agent PRs (120 merged; Agent A 74, Agent B 54, Agent C 14, Agent D 9);
  1,067 human PRs.
- Precision, fresh stratified sample of 48 flagged hunks: 42/48 = 0.875 (Wilson 0.753-0.941); agent 22/24.
- Recall, 44 unflagged hunks in 3 strata: point 0.31, conservative 0.03-0.63. Misses: expected values more
  than 12 lines below the assertion, removed symbolic tolerances, reference-output files (5 numeric
  reference-output edits among the 44). The detector-independent sample (40 PRs) held no numeric edit.
- Scientific subset (declared rule; JuliaLang/julia, JuliaSymbolics/Symbolics.jl, SciML/DiffEqGPU.jl,
  acts-project/acts, tier4/scenario_simulator_v2): 47 agent PRs, 1 flagged. The census read every mixed hunk
  of all 47 and found 1. A wider rule gives 9 flagged [t5d_sensitivity.json]. Energy: 0 of 17 present.

## The one case, and what the definition misses
SciML/DiffEqGPU.jl #348 (agent PR, merged) relaxed GPU ODE regression tolerances: norm(bench_sol.u -
sol[1].u) < 7e-4 became < 2e-3 (two tests), and < 4e-3 became < 5e-3. Human PRs in the same repository do the
same (#344, #396, #413; 16 human PRs flagged in the subset). Two agent PRs in acts (#4185, #4591) replaced
stored regression hashes of simulation output. DiffEqGPU #367 narrowed the compared quantity to the end
point. These are oracle changes that a numeric-literal definition does not count.

## What a Stage 2 would need
- Fresh agent PRs from scientific and energy repositories: AIDev-7.6M ingests 8 of the 17 named energy
  repositories in its full diff table (DPO-F12 census; not counted here), or the GitHub API (tokens: 401).
- The author's recorded legal basis (GDPR Art. 6(1)(e) with Art. 89(1); Data Protection Act 1050/2018 s.4)
  before any login-bearing data.
- A construct that also counts reference-output and compared-quantity changes.

## Limits
- One rater (an AI model) for all hand labels; the table holds bug-fix PRs only; the v1 detector
  was repaired on a development sample (t5b_devlabels_v1.json) and the estimates come from a fresh v2 sample.
- OpenAlex topical positive control failed on ranking (paper indexed, t4d_rerun.json); one GitHub query was
  rate-limited; ACM full text of 10.1145/3793302.3793618 returned 403 (judged on its abstract).

## Reproduce
build/: t4_f12b_killcheck.py, t4b_reads.py, t4b2_reads.py, t4c_adjudication_table.py, t4c_verdict.py,
t4d_rerun.py; t5a_ingest.py, oracle_edit_detector.py, t5a_detect.py, t5b_write_labels.py, t5c_feasibility.py,
t5d_sensitivity.py, t5e_sci_census.py, t5e_census_labels.py; t6_decision.py. Data: [internal record]
Paper_0005_GenAI_Agent_PRs_Energy_Modelling\hf_agentic_pr (no person columns, t7_privacy_audit.json).
