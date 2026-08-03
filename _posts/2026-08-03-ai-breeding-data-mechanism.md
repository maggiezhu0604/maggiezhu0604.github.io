---
layout: post
title: "Can AI Breed Crops by Itself? What a Robotics Debate Reveals About the Future of Plant Breeding"
subtitle: "A research blog on AI, biological knowledge, and crop breeding decisions"
date: 2026-08-03
cover-img: /assets/img/blog/ai-breeding-data-mechanism-cover.png
thumbnail-img: /assets/img/blog/ai-breeding-data-mechanism-cover.png
share-img: /assets/img/blog/ai-breeding-data-mechanism-cover.png
tags: [plant breeding, AI, foundation models, genotype-by-environment]
---

In robotics, researchers are arguing about a simple question: will data solve robotics and automation?

One side says yes, or at least almost yes. If we collect enough demonstrations, videos, sensor readings, and real-world examples, robots may learn how to act without humans manually programming every rule.

The other side is more cautious. Robots live in the physical world: they touch objects, lose balance, face friction, and move through changing environments. Data are powerful, but data alone may not teach a robot why the world works the way it does. Without physics, geometry, control theory, and good assumptions about the task, a data-driven system may look impressive in familiar settings but fail when the world changes.

The Science Robotics debate points to a broader question in science and engineering.[^amato2025] 

**Can large-scale data replace domain knowledge, or does it need domain knowledge to become useful?**

Plant breeding is beginning to face the same question.

## The Promise: Data Can Change Breeding

Modern plant breeding is becoming a data-rich field. Breeders now have a much larger toolbox, including genome-wide markers, field phenotypes, drone images, weather records, soil measurements, management data, and multi-year, multi-location trial results. In major crops such as maize, wheat, rice, and soybean, the amount of available data is far beyond what any individual breeder can manually inspect.

In textbook terms, conventional breeding starts with a breeding objective, creates or assembles genetic variability, selects promising plants or lines, evaluates them, and eventually releases cultivars.[^acquaah2020] The exact method depends on the crop's reproductive biology, such as whether it is self-pollinated, cross-pollinated, or clonally propagated.

AI does not replace this breeding cycle. It changes what breeders can see within it. A model can learn from thousands of lines tested across many environments and ask how the genome, the field environment, and the timing of stress interact to shape yield. It can combine signals that are too weak, too noisy, or too multidimensional for traditional analysis alone.

This is the optimistic view described in reviews on AI-supported data integration in plant breeding.[^sangjan2025] AI can connect genomics, phenotyping, environmental monitoring, management, and even economic information. It can support trait prediction, gene discovery, resource allocation, and breeding decisions.

In this view, AI is not simply a tool for doing larger computations faster. It becomes a way to organize breeding complexity by linking genotype, phenotype, environment, and management data into models that support prediction, interpretation, and decision-making.

Foundation models add another layer. In plant biology, they can be trained on large-scale DNA sequences, RNA data, protein sequences, images, single-cell data, or scientific literature.[^yu2026] A plant DNA foundation model, for example, may learn sequence patterns that help identify splice sites, gene boundaries, conserved regions, or potentially harmful variants.[^zhai2025]

Other foundation models operate on different data types. Vision models may help extract field phenotypes from images, including phenotype scoring or image segmentation.[^yu2026] Literature-oriented models can help researchers navigate a fast-growing body of plant science knowledge, especially when combined with retrieval, knowledge graphs, and citation-aware responses.[^yu2026][^plantscience2026]

Breeding often depends on detecting useful genetic and environmental patterns inside noisy field data. If foundation models turn raw sequence, image, or text data into useful representations, breeders may test patterns that were previously difficult to see.

## The Warning: More Data Does Not Automatically Mean Better Breeding

Plant breeding is not simply about predicting which line will perform best. It is a human-directed process of shaping plant populations for food, feed, fiber, resilience, and other goals under real field conditions.

Yield, drought tolerance, disease resistance, flowering time, and nutrient use efficiency emerge from many genes, regulatory networks, developmental stages, field conditions, and management practices. A genotype that performs well in one environment may fail in another. A drought-tolerant line may be useful under one stress pattern but not under heat and drought combined. A model trained on historical data may perform well in familiar regions but lose accuracy in a new climate zone.

This is where the cautionary side of the robotics debate becomes useful.

In robotics, a model trained on many demonstrations may still fail if it has not learned the physical structure of the task. In breeding, a model can fail in the same way if it misses the biological and environmental structure behind performance.

For example, a model may learn that a group of hybrids performs well in historically high-yielding locations. If a new target environment experiences heat and drought during flowering, that historical pattern may no longer hold. The model may still recognize the genotype or location, but miss the reason performance changed: stress timing, reproductive sensitivity, and genotype-by-environment interaction.[^berlingeri2025]

A purely data-driven breeding model might find correlations without understanding mechanisms. It may learn that certain markers, locations, or weather patterns are associated with high yield in the training data. But are those signals causal, stable, and biologically meaningful, or are they artifacts of trial design, population structure, or historical sampling?

This matters because breeders rarely care about prediction in the past. They care about selection for the future.

In this view, prediction alone is not enough. Breeding also depends on useful variation: whether it exists in the population, whether recombination can bring favorable alleles together, and whether new mutations or introgressed alleles can become breeding-relevant.[^deleon2025]

Breeding needs models that can travel across years, locations, genetic backgrounds, stress patterns, and management systems.

This is why several crop genomics and breeding perspectives remain cautious about "data alone." Crop translational genomics has been especially successful for traits with large-effect genes. For complex quantitative traits such as yield, however, genomic data still need to be connected with regulation, gene interactions, phenotyping, and environmental context.[^mascher2024] Precision breeding makes a related point: breeding should move from markers associated with traits toward variants that cause useful biological effects.[^ramstein2026]

## The Better Question: What Should We Tell the Model?

The debate does not have to end with a choice between mechanism and AI.

It points toward another question:

**What biological knowledge should guide the model, and where should the model be allowed to learn from data?**

Consider maize under a warming climate. The obvious target might seem to be heat tolerance. But another strategy is to improve cold or frost tolerance during germination and early growth, so maize can be planted earlier and make better use of early-season light and soil nitrogen.[^ojeda2025] In that case, the breeder is not only predicting climate risk. The breeder is deciding which crop-management system the model should help evaluate.

The same logic applies within a trait. For drought tolerance, biological knowledge can shape what the model pays attention to. Root architecture affects water access. Flowering time defines when reproductive tissues are most vulnerable. Heat and drought should not be treated as generic "bad weather," because their timing, duration, and combination can produce different effects. Metabolic pathways, hormone signaling, stomatal regulation, and carbon allocation may all shape how a plant responds to stress.[^berlingeri2025]

These are not "limitations" placed on AI. They are biological landmarks.

Aude Billard makes a useful comparison in the robotics debate: astronomy did not emerge simply because millions of people looked at the sky. Careful observation mattered, but so did the process of building hypothetical models and testing them against data.[^amato2025]

Plant breeding faces a similar challenge. Large field datasets become more powerful when organized by biological hypotheses. Which developmental stage matters? Which stress window matters? Which traits are likely to influence performance? Which genetic variants are biologically plausible?

In breeding, these landmarks can become model structure. Growth stage can define environmental windows. Crop physiology can guide which weather variables matter. Known pathways can help prioritize candidate genes. Functional variant scores from DNA foundation models can weight markers by biological plausibility. Genomic relationship models can capture inherited similarity.

Field trial design also matters. It tells us what kind of generalization we are testing: new genotypes, new environments, new years, new stress patterns, or combinations of them.[^berlingeri2025]

These examples point toward a hybrid route: not hand-coded biology alone, and not black-box data alone.

## Where Foundation Models Fit

Foundation models are powerful, but they do not escape biology. Their outputs are shaped by the training data, the objective, and the biological structure built into the model.

For example, a DNA foundation model such as PlantCaduceus does not directly solve yield prediction. It can learn sequence patterns across plant genomes and help predict gene annotation, evolutionary constraint, or variant effects.[^zhai2025] That information may support breeding by prioritizing functional variants, weighting markers, identifying deleterious alleles, or narrowing candidate variants in a GWAS region.[^ramstein2026]

That is useful, but it is not the same as predicting which hybrid will yield best in Nebraska under a hot, dry summer. For that kind of decision, foundation model outputs must be connected to genomic prediction, genotype-by-environment interaction, field phenotypes, environmental covariates, crop development, and validation across years and locations.

## The Fusion Route: AI on a Biological Map

Across these examples, AI appears most useful when it makes biological knowledge operational at larger scale. AI can search through large biological and environmental spaces; biological knowledge gives that search direction, structure, and meaning.

This fusion is already visible in several areas. AI-supported data integration aims to combine genomics, phenotyping, environment, management, and multi-omics.[^sangjan2025] Crop modeling and sensing can connect field observations with physiological processes and molecular breeding.[^berlingeri2025] Precision breeding aims to move from anonymous markers toward causal variants and functional knowledge.[^ramstein2026]

Foundation models fit into this landscape because their representations can feed into larger breeding models, but they still need validation and biological interpretation.[^yu2026]

This integrated approach is especially important for complex traits. Drought tolerance, yield, and climate adaptation are shaped by many small genetic effects, developmental timing, environmental stress, and management practices. A useful breeding model needs to connect genetic variation with the conditions under which that variation becomes visible.

A large model can be useful, but size alone does not show whether it represents the biological structure most relevant to breeding decisions.

## My View

The robotics debate is useful because it warns us against two extremes. One is believing that enough data will automatically reveal everything important. The other is believing that only detailed mechanistic understanding can guide breeding progress.

Plant breeding needs a middle path. We need data-rich models because the genotype-by-environment landscape is too complex for intuition alone. We also need biological structure because historical correlations are not the same as future reliability. Foundation models, genomic prediction, crop models, sensors, and field trials are different ways of seeing the same biological system.

My research interest sits in this space: how to make breeding models that are both predictive and interpretable, especially across environments. I am interested in how environmental covariates, genomic relationships, field trial structure, and functional biological priors can be combined to improve crop prediction. The long-term goal is not simply to rank genotypes on a leaderboard, but to understand when a model works, when it fails, and what that failure teaches us about crops.

If AI is going to help breed future crops, the question is not only how much data it receives.

It is what kind of map breeders choose to give it.

## References

[^amato2025]: Nancy M. Amato et al., "Data will solve robotics and automation: True or false? A debate," *Science Robotics* 10, eaea7897, 2025. DOI: 10.1126/scirobotics.aea7897.

[^deleon2025]: Natalia de Leon, "Plant Breeding & the Infinitesimal Model: Cause or Consequence," NC State Plant Breeding Consortium talk, 2025.

[^acquaah2020]: George Acquaah, *Principles of Plant Genetics and Breeding*, 3rd ed., John Wiley & Sons, 2020. See also Acquaah, "Conventional Plant Breeding Principles and Techniques," 2015, DOI: 10.1007/978-3-319-22521-0_5.

[^sangjan2025]: Worasit Sangjan, Daniel R. Kick, and Jacob D. Washburn, "Improving plant breeding through AI-supported data integration," *Theoretical and Applied Genetics*, 2025. DOI: 10.1007/s00122-025-04910-2.

[^berlingeri2025]: Jonathan Berlingeri et al., "Integration of crop modeling and sensing into molecular breeding for nutritional quality and stress tolerance," *Theoretical and Applied Genetics*, 2025. DOI: 10.1007/s00122-025-04984-y.

[^ojeda2025]: Jonathan Odilon Ojeda-Rivera et al., "Designing a nitrogen-efficient cold-tolerant maize for modern agricultural systems," *The Plant Cell*, 2025. DOI: 10.1093/plcell/koaf139.

[^yu2026]: Haopeng Yu, "AI foundation models in plant biology," *New Phytologist*, 2026. DOI: 10.1111/nph.71395.

[^plantscience2026]: Haopeng Yu et al., "PlantScience.ai: An LLM-powered virtual scientist for plant science," *Molecular Plant*, 2026.

[^ramstein2026]: Guillaume P. Ramstein et al., "Translating functional molecular knowledge into crop-breeding success," *Nature Reviews Genetics*, 2026. DOI: 10.1038/s41576-026-00968-w.

[^mascher2024]: Martin Mascher et al., "Promises and challenges of crop translational genomics," *Nature*, 2024. DOI: 10.1038/s41586-024-07713-5.

[^zhai2025]: Jingjing Zhai et al., "Cross-species modeling of plant genomes at single-nucleotide resolution using a pretrained DNA language model," *PNAS*, 2025. DOI: 10.1073/pnas.2421738122.
