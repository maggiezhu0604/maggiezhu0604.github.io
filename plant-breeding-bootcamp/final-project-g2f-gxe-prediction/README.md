# Final Project: G2F Genotype-By-Environment Prediction

## Project Summary

This project uses public Genomes to Fields (G2F) data to study genotype-by-environment prediction in maize. The goal is to evaluate how genotype, phenotype, and environmental information can be combined to predict crop performance across field environments.

The project is intended as a research portfolio artifact for computational plant breeding PhD applications.

## Research Question

How accurately can maize performance be predicted across environments using genotype, phenotype, and environmental covariates from G2F data?

## Biological Motivation

Plant breeders need to select genotypes that perform well across target environments or that are specifically adapted to particular environmental conditions. Genotype-by-environment interaction makes this task difficult because the best genotype in one environment may not be the best genotype in another. Prediction models can help breeders make earlier and more informed selection decisions.

## Planned Data

- G2F phenotype data from multi-environment maize field trials.
- Genotype marker data for tested hybrids or lines.
- Environmental covariates such as weather, location, year, and management metadata.

## Possible Analysis Plan

1. Define the target trait, such as grain yield.
2. Select years and environments with sufficient data completeness.
3. Clean phenotype and environment metadata.
4. Prepare genotype marker data or derived relationship information.
5. Build baseline prediction models.
6. Compare models that include genotype, environment, and GxE-related features.
7. Evaluate prediction accuracy using cross-validation strategies relevant to breeding.
8. Interpret results in terms of breeding decisions and biological limitations.

## Candidate Methods

- Linear models for baseline comparison.
- Mixed models for genotype and environment effects.
- Genomic prediction models such as GBLUP or ridge regression.
- Machine learning models such as random forest or gradient boosting.
- Cross-validation by genotype, environment, year, or environment cluster.

## Expected Outputs

- Clean project README.
- Data dictionary.
- Reproducible analysis scripts or notebooks.
- Exploratory data visualizations.
- Model performance table.
- Short scientific discussion of results, limitations, and future work.

## Suggested Folder Structure

```text
final-project-g2f-gxe-prediction/
├── README.md
├── data-dictionary.md
├── methods.md
├── results.md
├── figures/
├── notebooks/
└── scripts/
```

## Reproducibility Checklist

- Data sources are cited.
- Data processing decisions are documented.
- Code runs from a clean checkout or clearly states required setup.
- Random seeds are recorded for stochastic models.
- Model evaluation strategy is explained.
- Results distinguish observed findings from interpretation.

## Future Directions

- Compare environment-specific and across-environment prediction strategies.
- Explore environmental similarity and stress covariates.
- Test whether prediction improves when environmental covariates are included.
- Connect model interpretation to breeding program decisions.
