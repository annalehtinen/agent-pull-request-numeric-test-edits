# Data for: Coding agents and numeric test tolerances in scientific software: Limits of a public pull-request dataset

This repository is a data-only copy of the dataset "Data for: Coding agents and numeric test tolerances in scientific software: Limits of a public pull-request dataset" by Anna Lehtinen, deposited on Zenodo: https://doi.org/10.5281/zenodo.23144458 . Every file here is byte-identical to its copy in the Zenodo record; the SHA-256 of each file is listed in `MIRROR_MANIFEST.json`. The paper is a preprint on Preprints.org; its DOI is added here once it is posted.

## About the paper

In numerical code, test oracles are often tolerances, and loosening one is sometimes correct and sometimes a way to make a failing test pass. Coding agents now write a large share of pull requests merged into popular open-source projects. However, in the channels we searched we found no released label or measurement of agents changing existing numeric oracles in real pull requests. In this study, we tested whether the GitHub-Agentic-PR-Dataset, an extension of AIDev, can support that measurement with the 7,391 pull requests by four agents (Agent A to Agent D) in its bug-fix test-patch table. Our analysis reveals that its column documented as marking edits to existing expected values matched that description in 5 of 20 sampled agent pull requests it marks, none of them numeric, so it overcounts them. The table holds no energy-modelling repository we looked for, and in its scientific subset of 47 agent pull requests we found a single numeric oracle edit, a merged relaxation of GPU regression tolerances labelled agent-authored by the source table, though its public record shows no agent. Furthermore, our numeric-literal detector records no direction and misses common loosening idioms, such as an exact assertion becoming an approximate one. Researchers measuring such edits need fresh agent pull requests from scientific and energy-modelling repositories with verified authorship, a construct that also counts reference outputs, a direction label and a second rater.

## Files

| file | bytes |
|---|---|
| F12B_SALVAGE.md | 4,760 |
| t4_f12b_killcheck.json | 38,380 |
| t4c_adapted_labels.json | 12,202 |
| t4c_adjudication.json | 18,752 |
| t5_f12b_feasibility.json | 7,577 |
| t5a_detect.json | 3,232 |
| t5d_sensitivity.json | 1,489 |
| t5e_sci_census_labels.json | 6,070 |
| t6_f12b_decision.json | 1,394 |
| t7_privacy_audit.json | 368 |
| t8_base_rates_overcount.json | 2,568 |

## Not in this repository

4 file(s) of the supplement are code or logs; they are in the Zenodo record only (listed in `MIRROR_MANIFEST.json`).

## How to cite

Cite the data: Anna Lehtinen (2026). Data for: Coding agents and numeric test tolerances in scientific software: Limits of a public pull-request dataset [Data set]. Zenodo. https://doi.org/10.5281/zenodo.23144458 . `CITATION.cff` gives the citation (GitHub shows it under "Cite this repository").

## Licence

Creative Commons Attribution 4.0 International (CC BY 4.0), https://creativecommons.org/licenses/by/4.0/ .
