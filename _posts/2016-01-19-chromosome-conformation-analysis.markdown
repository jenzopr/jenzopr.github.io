---
layout: post
title:  "Redesigned chromosome conformation capture with increased scalability and sensitivity"
author: Jens Preussner
tags: chromosome capture methods
cover: "assets/dyes.jpg"
categories: reading
---

The expression of genes is seen as the one of the big determinants that shape the phenotypic and functional outcome of a cell.
But in order to be expressed, a mostly complicated interplay of regulatory elements influences the when and how a gene is expressed. A large library of regulatory elements was defined during the rise of next-generation sequencing methods, using RNA-seq, ChIP-seq, DNase-seq and ATAC-seq. 
Nevertheless, the big challenge to understand mechanisms by which regulatory elements influence the expression of specific target genes is still under active research.
Conventional methods, that capture the chromosomal conformation at specific loci (viewpoints) are not sensitive enough to detect weak interactions and mostly limited to only a few viewpoints per sample.
A recent redesign of the Capture-C protocol tries to address these issues with increased sensitivity, throughput and enhanced convenience.

In general, the number of unique interactions between a viewpoint and distant regulatory elements is limited to four per cell. This means that the number of cells as well as the complexity of the library generated determines the number of captured interactions.
Additionally, an efficient pull-down of viewpoints is determined by the sequence and hybridization efficiency of the capture probe. Davies et. al. address these limitations by using

* sonication: it allows the acurate quantification of randomly generated fragments, since PCR duplicates can be excluded in a downstream analysis,
* complex libraries: two library preparations were conducted in parallel and pooled before adding sequencing adaptors,
* double-capture: pulldown of biotinylated oligo sequences was done twice - and reduced the background signal of uncaptured material.

With these steps, the authors were able to scale the method up to 35 genes in seven samples, which is a total of 245 interaction profiles and achieved a genome-wide correlation of 97% for all genes of two replicates.
When only taking fragments with more than 10 interactions (after normalization) into account, the coefficient of variation dropped below 50%.

Until now, there is no general way to analyze such interaction data and consistently call all interactions per viewpoint. In their paper, Davies et. al. show a very clever way of extracting the true, functional interactions by using subtractive analysis of their normalized data.
The approach relies on changes between active states between two cell populations. Calculating a **differential track** from both Capture-C profiles allows to exclude all constitutive structural interaction and uncovered the tissue-specific regulation of genes that changed their active state.
Additionally, since the method provides enough coverage depth, popular **raw count-based** methods, like DESeq2 or EdgeR can be used to estimate the relative qunatitation between weak and strong interactions.

James O J Davies, Jelena M Telenius, Simon J McGowan, Nigel A Roberts, Stephen Taylor, Douglas R Higgs and Jim R Hughes. Multiplexed analysis of chromosome conformation at vastly improved sensitivity. **Nature Methods** (*2016*), doi: 10.1038/nmeth.3664 [weblink](http://www.nature.com/nmeth/journal/v13/n1/full/nmeth.3664.html)
