---
layout: post
title: "Toward Plant Genomic Foundation Models for Breeding Success"
subtitle: "From sequence representation to breeding decision making"
date: 2026-08-12
permalink: /blog/plant-genomic-foundation-models-breeding-success/
cover-img: /assets/img/blog/plant-genomic-foundation-models-breeding-decisions-cover.png
thumbnail-img: /assets/img/blog/plant-genomic-foundation-models-breeding-decisions-cover.png
share-img: /assets/img/blog/plant-genomic-foundation-models-breeding-decisions-cover.png
tags: [plant breeding, genomic foundation models, genomic language models, genotype-by-environment, precision breeding]
---

Plant breeding contains a large prediction problem. Breeders decide which parents to cross, which lines to advance, which hybrids to test more deeply, and which environments matter most for deployment. Genomic selection made that prediction problem more quantitative by using markers across the genome, but a persistent question remains: when a model predicts well, what has it learned? Has it learned functional biology, or mostly genetic relatedness, environment means, and historical structure?

Plant genomic foundation models make this question sharper. They promise to learn useful representations directly from plant genome sequences. But for breeding, the relevant question is not whether a model can predict masked nucleotides or produce impressive embeddings. The question is whether learned sequence representations can become functional priors that improve breeding decisions under real genetic, environmental, and management uncertainty.[^benegas2025]

## What Genomic Language Models Can Already Do

Genomic language models are self-supervised models trained on DNA sequences. A recent review organizes their major opportunities into functional constraint or variant-effect prediction, sequence design, and transfer learning.[^benegas2025] This classification is useful because it separates several claims that are sometimes conflated. A model that is good at variant scoring is not automatically a model for yield prediction, and a model that transfers across annotation tasks is not automatically a decision engine for breeders.

In plant genomics, several models and pipelines already mark the outline of the field. PlantCaduceus is a plant-specific DNA language model trained across angiosperm genomes and evaluated on cross-species annotation, evolutionary constraint, and zero-shot variant-effect scoring.[^zhai2025] PlantCAD2 extends this family toward longer-context plant genome representation, while GeneCAD uses PlantCAD2 embeddings together with a biological grammar decoder to predict plant gene models from DNA sequence alone.[^liugenecad2025] AgroNT offers a crop- and edible-plant-centered baseline, while GPN-MSA and GPN-Star represent alignment- and phylogeny-aware routes for functional constraint prediction.

These models are not all solving the same problem. Some are closer to annotation, some to variant prioritization, some to regulatory sequence interpretation, and some to evolutionary constraint. For many breeding applications, that distinction matters. A near-term role of plant genomic foundation models may be genotype-side functional interpretation: which variants are likely deleterious, which regions look constrained, which gene models are reliable, and which candidate alleles deserve more attention in a breeding pipeline.[^ramstein2026]

## The Missing Link: From Representation To Decision

Breeding decisions are not made on DNA sequence alone. A hybrid does not succeed because its genome looks plausible under a language model. It succeeds in a target population of environments, under management practices, disease pressure, heat or drought windows, soil constraints, and economic selection goals.

That means the useful path is not:

```text
DNA sequence -> foundation model -> yield prediction
```

A more realistic path is:

```text
DNA sequence
-> foundation model representation
-> functional prior for variants, genes, or haplotypes
-> GxE-aware prediction model
-> breeding decision benchmark
```

This distinction is central to precision breeding. Ramstein, Zhai, Buckler, Tenaillon, and Jannink frame biological and genomic language models as tools for prioritizing candidate variants, then calibrating those candidates through field trials, phenotyping, and breeding-line contexts.[^ramstein2026] In that framing, a zero-shot score is not the final answer. It is a prior that needs to be tested against trait- and environment-specific outcomes.

For example, a plant genomic foundation model might assign a deleteriousness score to variants in a maize line. That score could be summarized into gene-level burden, regulatory-region burden, or haplotype-level functional features. Those features could then enter a genomic prediction or reaction-norm model:

```text
phenotype = genotype effect + environment effect + genotype x environment interaction + error
```

The scientific question is whether foundation-model-derived features explain performance beyond ordinary markers or kinship. The breeding question is whether they improve decisions such as hybrid ranking, parent selection, stress-specific deployment, or candidate variant prioritization.

## Pattern Is Not Process

There is a danger in treating embeddings as explanations. A foundation model can reveal patterns: clusters of sequences, high conservation scores, low reference-to-alternate likelihood ratios, or confident gene-structure predictions. But a pattern is not automatically a process.

This is where Matt Pennell's evolutionary perspective is especially relevant. Uyeda, Zenil-Ferguson, and Pennell argue that phylogenetic comparative methods should not be reduced to a generic correction for non-independence; phylogeny is part of the historical and causal structure of the hypothesis being tested.[^uyeda2018] The same warning applies to genomic foundation models. A sequence representation may capture functional constraint, but it may also capture phylogenetic relatedness, mutation bias, repeat structure, annotation artifacts, or population history.

For breeding, that distinction is not philosophical. If a model improves prediction only because it encodes relatedness among training and test genotypes, it may fail when deployed in a new breeding population. If a cross-species model looks strong because the train-test split contains close relatives or shared annotation pipelines, it may overstate its biological generality. If a variant score reflects evolutionary constraint but not trait-specific agronomic value, it may help identify deleterious alleles but still fail to predict which hybrid performs best under drought.

This suggests a useful research principle:

```text
Use foundation models to generate genomic patterns.
Use explicit statistical models to test biological and breeding hypotheses.
```

Under this principle, plant genomic foundation models are not substitutes for biological reasoning. Biological insight should guide what signals the model is asked to learn, while mathematical and statistical models test whether the learned representations sharpen our understanding of functional variation and breeding value.

## Tree Thinking For Plant Foundation Models

Tree thinking can make plant genomic foundation models more rigorous. It asks: what is the ancestry structure behind the data, and what does that structure allow us to infer?

In model evaluation, tree thinking changes the split. A random sequence split may test local interpolation. A species split tests cross-species transfer. A clade split tests whether the model generalizes beyond a lineage. A breeding-population split tests whether learned features survive population structure. An environment split tests whether genotype representations still matter when field context changes.

Schraiber, Edge, and Pennell provide a useful bridge between statistical genetics and phylogenetics by showing how genomic relationship matrices, kinship, and phylogenetic variance-covariance matrices can be viewed as forms of shared genetic covariance.[^schraiber2024] That framework maps directly onto foundation-model evaluation. A breeding-facing model can ask:

```text
Does the foundation model add functional information after controlling for ancestry?
```

One possible model is:

```text
y = X beta + FM(seq) gamma + u_ancestry + error
u_ancestry ~ N(0, Sigma sigma^2)
```

Here, `FM(seq)` is the representation or score from a plant genomic foundation model, while `Sigma` captures kinship, population structure, or phylogenetic covariance. The key test is whether the foundation model contributes information beyond ancestry. This distinction matters because a model can perform well by encoding shared history without necessarily adding functional information that transfers to new populations or environments.

## A Breeding-Centered Research Agenda

Three research directions follow from this framing.

First, plant genomic foundation models need breeding-relevant benchmarks. Current benchmarks often focus on annotation, variant scoring, conservation, or transfer learning. Those tasks are essential, but breeding success requires additional tests: held-out germplasm, held-out environments, stress-regime transfer, hybrid ranking, parent selection, and calibration under field-trial noise.

Second, foundation-model scores should be tested as functional priors in genomic prediction. Instead of treating all markers equally, variants can be weighted by predicted constraint, deleteriousness, regulatory importance, or gene-model confidence. A useful benchmark would compare raw SNPs, kinship, annotation-based features, and foundation-model-derived features under the same GxE split design.

Third, plant genomic foundation models should be connected to environmental representation. Many breeding failures are not genotype-only failures. They are genotype-by-environment failures: heat around flowering, drought during grain fill, soil constraints, disease pressure, or management history. A foundation model can improve the genotype branch, but breeding decisions require an interaction model between genotype representation and environment representation.

This framing connects naturally to model diagnostics in public Genomes to Fields maize data. When a prediction model performs well or poorly, one can ask whether it is learning environment calibration, hybrid ranking, genomic relatedness, or stress-related failure modes. Plant genomic foundation models offer a next step: instead of asking only whether markers predict, one can ask whether learned sequence representations provide functional information that changes breeding decisions.

## What This Framework Does Not Cover

The framework above is biased toward data-rich breeding systems where foundation-model features can be evaluated inside genomic prediction, GxE models, or field-trial benchmarks. That is an important setting, but it is not the only route by which foundation models could have breeding value.

In gene-editing-oriented breeding, the value of a foundation model may not appear as higher genomic selection accuracy. A model could still be useful if it enriches beneficial edit candidates, filters out damaging targets, prioritizes promoter modifications, or reduces the number of transformations that need to be tested experimentally. In that setting, the relevant benchmark is not only prediction accuracy for natural genetic variation, but also the degree to which the model reduces the experimental search space for directed allele creation, promoter engineering, or multiplex editing.[^ramstein2026]

The framework is also less suited to data-scarce systems. In de novo domestication, pre-breeding, orphan crops, and crop wild relatives, there may be no mature genomic selection training population. Cross-species and zero-shot sequence priors may be among the few available sources of functional guidance. In these cases, the question is not whether foundation-model features improve an existing GS pipeline, but whether they provide usable biological priors when phenotypic training data are limited.

Finally, this post has focused mainly on representation and scoring of existing natural variation. It does not fully cover sequence generation: de novo regulatory elements, synthetic promoters, artificial gene modules, or designed alleles that do not yet exist in natural germplasm. That route connects plant genomic foundation models to synthetic biology and breeding by design. Its success should be evaluated by designability, biological activity, safety, and experimental validation, not only by marker-based prediction performance.

## Closing

Plant genomic foundation models should not be judged only by language-model loss, embedding visualizations, or annotation metrics. For breeding, additional standards are needed: do these models help identify functional variants, control for ancestry, interpret GxE, prioritize edits, or guide decisions under environmental uncertainty?

The goal is not to replace field trials or breeders. The goal is to build a better bridge from sequence to function to phenotype to decision.

## Further Reading

- Benegas et al. 2025, "Genomic language models: opportunities and challenges."
- Zhai et al. 2025, "Cross-species modeling of plant genomes at single-nucleotide resolution using a pretrained DNA language model."
- Liu et al. 2025, "GeneCAD: Plant Genome Annotation with a DNA Foundation Model."
- Ramstein et al. 2026, "Translating functional molecular knowledge into crop-breeding success."
- Uyeda, Zenil-Ferguson, and Pennell 2018, "Rethinking phylogenetic comparative methods."
- Schraiber, Edge, and Pennell 2024, "Unifying approaches from statistical genetics and phylogenetics for mapping phenotypes in structured populations."

## References

[^benegas2025]: Benegas et al., "Genomic language models: opportunities and challenges," *Trends in Genetics*, 2025. DOI: 10.1016/j.tig.2024.11.013.

[^zhai2025]: Zhai et al., "Cross-species modeling of plant genomes at single-nucleotide resolution using a pretrained DNA language model," *PNAS*, 2025. DOI: 10.1073/pnas.2421738122.

[^liugenecad2025]: Liu et al., "GeneCAD: Plant Genome Annotation with a DNA Foundation Model," *bioRxiv*, 2025. DOI: 10.1101/2025.10.31.685877.

[^ramstein2026]: Ramstein et al., "Translating functional molecular knowledge into crop-breeding success," *Nature Reviews Genetics*, 2026. DOI: 10.1038/s41576-026-00968-w.

[^uyeda2018]: Uyeda, Zenil-Ferguson, and Pennell, "Rethinking phylogenetic comparative methods," *Systematic Biology*, 2018. DOI: 10.1093/sysbio/syy031.

[^schraiber2024]: Schraiber, Edge, and Pennell, "Unifying approaches from statistical genetics and phylogenetics for mapping phenotypes in structured populations," *PLOS Biology*, 2024. DOI: 10.1371/journal.pbio.3002847.
