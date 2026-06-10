# Data Dictionary

This file will describe the variables used in the G2F genotype-by-environment prediction project.

## Phenotype Variables

| Variable | Description | Unit | Notes |
| --- | --- | --- | --- |
| `trait` | Target agronomic trait | Varies | Example: grain yield |
| `genotype_id` | Genotype or hybrid identifier | Text | Must align with genotype data |
| `environment_id` | Field trial environment identifier | Text | Often location-year specific |
| `year` | Trial year | Year | Useful for temporal validation |

## Genotype Variables

| Variable | Description | Notes |
| --- | --- | --- |
| `marker_id` | Marker identifier | Usually SNP-level |
| `allele_call` | Encoded genotype call | Encoding should be documented |
| `missing_rate` | Marker or sample missingness | Used during quality control |

## Environment Variables

| Variable | Description | Unit | Notes |
| --- | --- | --- | --- |
| `location` | Trial location | Text | May include state or station |
| `temperature` | Temperature summary | Degrees | Define time window |
| `precipitation` | Rainfall or water availability | mm | Define time window |
| `management` | Field management metadata | Text | May include planting date or irrigation |
