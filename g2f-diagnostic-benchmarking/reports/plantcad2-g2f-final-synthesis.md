# PlantCAD2-G2F Final Synthesis

## Objective

[依据] This extension connected PlantCAD2 zero-shot variant scores to the G2F maize prediction workflow as a functional prior, then tested whether that prior improved out-of-sample prediction beyond ordinary genotype-based and environment-based baselines.

[边界] The analysis evaluates predictive utility in the current 2024 2,383-scored-marker pilot. It does not identify yield-causal SNPs, validate gene function, or prove that PlantCAD2 has no useful biological signal in maize.

## One-Sentence Argument

[结论] In this G2F maize pilot, PlantCAD2 was successfully wired into SNP-level marker weighting, PlantCAD2 x environment GxE kernel smoothing, and a 5Mb region-burden route, but all frozen claim gates were negative or exploratory negative, indicating that the current score-to-feature transforms did not add robust predictive structure beyond matched non-PlantCAD2 baselines.

## What Was Tested

### 1. SNP-level marker weighting

[依据] The SNP-level marker weighting route used 2,383 PlantCAD2-scored canonical SNVs from the 2024 2,425-marker genotype panel.

[依据] The frozen transform used `abs(plantCAD_zero_shot)`, rank-normalized the absolute scores, and rescaled marker weights to mean 1.

[依据] The primary comparison was an ordinary 2,383-marker SNP kernel / genomic KNN baseline versus a PlantCAD2-weighted SNP kernel, with random-weight, MAF-weight, and position-smoothed negative controls.

[结论] This route received claim label = negative.

### 2. PlantCAD2 x environment GxE kernel

[依据] The PlantCAD2 x environment GxE kernel route combined a training-standardized environmental kernel from RD_EP-style environmental covariates with genomic kernels built from ordinary, PlantCAD2-weighted, random, MAF, and position-smoothed marker weights.

[依据] The PlantCAD2 GxE comparison was explicitly frozen as an exploratory extension rather than a confirmatory primary claim.

[依据] For PlantCAD2 GxE versus ordinary GxE, RMSE delta was -0.00035748 with 95% CI [-0.00291906, 0.00221181] and p = 0.80519; mean within-environment Pearson r delta was -0.00520896 with 95% CI [-0.01091797, -0.00047883] and p = 0.05295.

[结论] This route received claim label = exploratory_negative.

### 3. 5Mb region-burden route

[依据] The region-burden route aggregated 2,383 scored markers into 359 fixed 5Mb chromosome-position windows and built ordinary, PlantCAD2-weighted, random, MAF, and position-smoothed burden feature matrices.

[依据] For PlantCAD2 region burden versus ordinary burden, RMSE delta was 0.00201717 with 95% CI [-0.00370799, 0.00759589] and p = 0.49451; mean within-environment Pearson r delta was -0.00201355 with 95% CI [-0.00623247, 0.00218239] and p = 0.42058.

[结论] This route received claim label = exploratory_negative.

## Main Interpretation

[结论] The negative result is scientifically interpretable rather than a simple pipeline failure.

[依据] The M11 diagnostic report found 2,383 scored markers, no missing PlantCAD2 score import among scoring-ready variants, finite marker weights, and valid kernel numerics.

[依据 + 推论] The strongest diagnostic warning was kernel similarity: PlantCAD2 genomic kernel correlation to ordinary and non-PlantCAD2 control kernels had min = 0.995659, mean = 0.998195, and max = 0.999321. This indicates that the current weight transform barely changed the genotype relationship geometry.

[推论] Under this transform, the PlantCAD2 prior was consumed by the prediction models but did not create enough incremental structure to change held-out environment-level prediction.

## Trivial-Baseline Robustness Addendum

[依据] Decision set v13 added four interpretation baselines without tuning PlantCAD2 transforms and without opening a new primary claim.

[依据] The genotype-free `site_year_context_mean_hierarchy` baseline had mean environment RMSE = 2.82291735 and mean within-environment Pearson r approximately 0, confirming that pure context calibration is weaker for hybrid ranking.

[依据] The `parent_only_baseline` had mean environment RMSE = 2.73686879 and mean within-environment Pearson r = 0.31723073, showing that parent history alone carries nontrivial residual-ranking signal.

[依据] The `score_shuffled_plantcad2_baseline` had mean environment RMSE = 2.73168091 and mean within-environment Pearson r = 0.36288201, while the `chromosome_block_shuffled_plantcad2_baseline` had mean environment RMSE = 2.72807718 and mean within-environment Pearson r = 0.36597863.

[依据 + 推论] These shuffled-score controls perform close to the original ordinary and PlantCAD2-weighted SNP-kernel layer, supporting the M11 interpretation that the current PlantCAD2 score-to-weight transform contributes little marker-specific incremental structure beyond generic genotype relationship geometry.

[边界] M14 is an interpretation robustness check only. It does not replace the frozen M7/M10/M12 claim gates and does not create a new positive or negative biological claim.

## Residual-Rescue Addendum

[依据] Decision set v14 stops further empirical PlantCAD2 expansion after M14 v3 and treats M14 v3 only as diagnostic support.

[依据] M14 v3 used leave-one-environment-out splitting with held-out residual defined as observed yield minus the frozen M61 baseline prediction.

[依据] The primary endpoint was held-out residual RMSE reduction, and the secondary endpoint was residual R2.

[结论] `plantcad2_snp_delta` did not explain frozen M61 held-out residuals: RMSE reduction = -0.02334616 and residual R2 = -0.01688556.

[依据 + 推论] The best diagnostic residual-correction signal was `site_year_context_delta`, but its effect was very small: RMSE reduction = 0.00421828 and residual R2 = 0.00303587.

[结论] M14 v3 residual-rescue diagnostic strengthens the existing negative interpretation: after a strong frozen M61 baseline, PlantCAD2 SNP delta did not provide held-out residual rescue.

[边界] This addendum does not change the primary claim labels. The PlantCAD2 empirical extension remains negative / exploratory_negative, with no leaderboard claim and no biological claim.

## Discussion

[结论] The main contribution of the PlantCAD2 extension is not a positive accuracy gain; it is a reproducible test of whether a sequence-model functional prior can be converted into a useful G2F prediction component under frozen hypotheses and matched controls.

[依据] The analysis covered three model-consumption routes: marker weights, GxE kernels, and region burdens. Each route included a frozen comparison, paired environment-level testing, negative controls, and claim-gate boundaries.

[推论] The most plausible current explanation is that sparse marker coverage and rank-normalized absolute weighting preserved nearly the same relationship geometry as ordinary SNP similarity. This is consistent with the high kernel correlations and with the absence of robust RMSE or within-environment Pearson-r improvement.

[边界] This interpretation should not be generalized to all PlantCAD2 uses. The pilot used a small G2F marker panel, simple absolute-score weighting, and fixed 5Mb windows; richer marker coverage, directional allele effects, LD-aware regions, or gene annotations could produce a different result.

## Future Directions

[推论] The next PlantCAD2-G2F route should be hypothesis-frozen before execution, not tuned after seeing negative results.

[推论] A defensible next step is LD/block-aware sensitivity analysis: preserve local marker correlation structure, define chromosome blocks or LD blocks before testing, and evaluate whether PlantCAD2 high-score blocks alter prediction beyond block-matched random controls.

[推论] A second route is annotation-aware gene-set burden analysis: map scored variants to genes or regulatory windows, define stress-response or development-related sets from external annotation before prediction, and test burden x environment interactions against matched nonfunctional gene-set controls.

[推论] A third route is richer score encoding: compare signed score, allele-orientation-aware score, absolute score, quantile thresholding, and nonlinear transforms only under a prespecified family-wise testing plan.

[边界] These future routes should remain predictive-hypothesis tests unless supported by separate functional genomics or causal evidence.

## Claim-Evidence Map

| Claim | Evidence | Status |
|---|---|---|
| PlantCAD2 scores were successfully connected to G2F prediction features. | M4-M5 score parsing and marker-weight audits; M10 GxE kernel diagnostics; M12 region-burden features. | supported |
| SNP-level marker weighting did not improve prediction under the frozen gate. | M7/M8 claim label = negative. | supported |
| PlantCAD2 x environment GxE did not provide robust exploratory improvement. | M10 RMSE and Pearson-r paired tests; claim label = exploratory_negative. | supported |
| 5Mb region burden did not improve beyond ordinary burden. | M12 paired tests and claim gate; claim label = exploratory_negative. | supported |
| PlantCAD2 did not rescue residuals after frozen M61 baseline. | M14 v3 LOEO residual-rescue diagnostic; RMSE reduction = -0.02334616; residual R2 = -0.01688556. | supported |
| The likely failure mode is low incremental structure, not missing scores or invalid kernels. | M11 kernel similarity and numerical diagnostics. | supported/inferred |
| PlantCAD2 has no biological value for maize yield. | Not tested. | unsupported; excluded |

## Reproducibility Pointers

[依据] Primary full report: `output/g2f-competition-plan/plantcad2-functional-prior-hypothesis-test-report.md`.

[依据] Negative-result diagnostics: `work/g2f-competition/outputs/m4_functional_prior/m11_plantcad2_negative_result_diagnostic_report.md`.

[依据] Region-burden hypothesis test: `work/g2f-competition/outputs/m4_functional_prior/m12_region_burden_hypothesis_test_report.md`.

[依据] M14 v3 residual-rescue diagnostic: `work/g2f-competition/outputs/m14_cross_validated_residual_explanation/m14_v3_report.md`.

[依据] Checklist and frozen decisions: `output/g2f-competition-plan/plantcad2-functional-prior-hypothesis-testing-checklist.md`.
