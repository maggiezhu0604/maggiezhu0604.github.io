# M7 Failure-Label Sensitivity Analysis

Date: 2026-08-06

## Purpose

    This analysis tests whether the M7 failure atlas depends strongly on arbitrary diagnostic thresholds. It re-labels existing M7 environment and hybrid failure outputs without retraining any model.

Primary hybrid labels are mutually exclusive and follow the manuscript rule order. The `any_*` columns are non-exclusive counts, so a hybrid can contribute to both `any_low_historical_phenotype_hybrids` and `any_low_genomic_relatedness_hybrids`.

## Layer Definitions

- **Layer A: absolute threshold grid** scans fixed, interpretable cutoffs around the current defaults: M3 absolute error <= 0.5 / 0.75 / 1.0 Mg/ha, M5 worsening >= 0.2 / 0.25 / 0.5 Mg/ha, large hybrid residual >= 1.5 / 2.0 / 2.5 Mg/ha, and low genomic relatedness < 0.35 / 0.45 / 0.55.
- **Layer B: data-adaptive threshold grid** keeps the default harmful-overcorrection definition for environment-level cases, but replaces large-residual and low-genomic-relatedness cutoffs with round-specific empirical quantiles. Large-residual quantiles are estimated from all evaluable final-model target residuals, then applied to the M7.2 top-hybrid heatmap subset.

## Output Files

- `work/g2f-competition/outputs/m7_failure_label_sensitivity/m7_failure_label_sensitivity_summary.csv`
- `work/g2f-competition/outputs/m7_failure_label_sensitivity/m7_failure_label_sensitivity_cases.csv`
- `output/g2f-competition-plan/m7-failure-label-sensitivity-report.md`

## Default Rule Snapshot

| threshold_set_id | harmful_envs_total | low_historical_phenotype_hybrids | low_genomic_relatedness_hybrids | parent_name_ambiguity_hybrids | high_residual_despite_support_hybrids | any_low_genomic_relatedness_hybrids | any_parent_name_ambiguity_hybrids | broadly_difficult_hybrids | environment_specific_failure_hybrids | mixed_or_mild_failure_hybrids |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| A_m3le0.75_worse0.25_resid2.0_grel0.45 | 9 | 187 | 0 | 5 | 8 | 9 | 5 | 33 | 5 | 2 |

## Stability Summary

| layer | n_threshold_sets | harmful_envs_min | harmful_envs_median | harmful_envs_max | median_harmful_env_jaccard | median_hybrid_label_jaccard | median_hybrid_pattern_jaccard |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Layer A absolute threshold grid | 81 | 4 | 6.0 | 9 | 0.666667 | 1.0 | 0.95122 |
| Layer B data-adaptive threshold grid | 9 | 9 | 9.0 | 9 | 1.0 | 1.0 | 0.311475 |

## Most Threshold-Sensitive Configurations

| layer | threshold_set_id | harmful_envs_total | harmful_env_jaccard_vs_default | hybrid_label_assignment_jaccard_vs_default | hybrid_pattern_assignment_jaccard_vs_default |
| --- | --- | --- | --- | --- | --- |
| Layer A absolute threshold grid | A_m3le0.5_worse0.5_resid1.5_grel0.35 | 4 | 0.444444 | 1.0 | 0.95122 |
| Layer A absolute threshold grid | A_m3le0.5_worse0.5_resid1.5_grel0.45 | 4 | 0.444444 | 1.0 | 0.95122 |
| Layer A absolute threshold grid | A_m3le0.5_worse0.5_resid1.5_grel0.55 | 4 | 0.444444 | 1.0 | 0.95122 |
| Layer A absolute threshold grid | A_m3le0.5_worse0.5_resid2.5_grel0.35 | 4 | 0.444444 | 1.0 | 0.95122 |
| Layer A absolute threshold grid | A_m3le0.5_worse0.5_resid2.5_grel0.45 | 4 | 0.444444 | 1.0 | 0.95122 |
| Layer A absolute threshold grid | A_m3le0.5_worse0.5_resid2.5_grel0.55 | 4 | 0.444444 | 1.0 | 0.95122 |
| Layer A absolute threshold grid | A_m3le0.5_worse0.5_resid2.0_grel0.35 | 4 | 0.444444 | 1.0 | 1.0 |
| Layer A absolute threshold grid | A_m3le0.5_worse0.5_resid2.0_grel0.45 | 4 | 0.444444 | 1.0 | 1.0 |
| Layer A absolute threshold grid | A_m3le0.5_worse0.5_resid2.0_grel0.55 | 4 | 0.444444 | 1.0 | 1.0 |
| Layer A absolute threshold grid | A_m3le0.5_worse0.2_resid1.5_grel0.35 | 6 | 0.666667 | 1.0 | 0.95122 |

## Interpretation

Use this as a robustness layer rather than as a new model result. If the main qualitative labels remain stable across Layer A and Layer B, the failure atlas is less likely to be dismissed as a threshold artifact. If a label changes substantially, that label should be reported as threshold-sensitive or moved to supplementary analysis.
