---
layout: post
title:  "Single cell heterogeneity analysis in mouse embryonic stem cells"
author: Jens Preussner
tags: methods
cover: "assets/dyes.jpg"
categories: reading bioinformatics
---

Results from publications in low impact journals are often underrated in the scientific community. Even worse, if those publications additionally contain negative results, e.g. reporting a non-correlation or that no enrichment was found. 
Today, such a publication was made available online, at **Comp. Biol. Chem.**. Mantsoki et. al. provide a reanalysis of two published datasets from mouse and human embryonic stem cells. Analysis steps are described in full detail and also contain *negative results*, thereby providing very valuable insights into single cell heterogeneity.

The authors start by reducing their input data from more than 40,000 genes to around 4000 genes by binning (bin size 1000) according to the mean expression and calculating the correlation of each gene to the top 229 and 217 mouse and human highly expressed genes.
Genes showing significantly higher correlation compared to the lowest expressed genes were kept. After that, the coefficient of variation (CV) was calculated as standard deviation to mean ratio for all genes. The remainder of the analysis is purely based on the two numbers, mean and CV.
The first observation made is that CV negatively correlates with expression, i.e. highly expressed genes show a low value of CV. Certainly, a part of this effect can be attributed to reduced technical noise.
Next, the authors looked for functional enrichments within low CV and high CV genes. No result was mentioned for high CV genes, but for low CV genes an enrichment in cell cycle processes was found. Looking purely at high expressed genes, the same enrichment was observed.
To study transcriptional control of low and high CV genes, transcription factor binding data was incorporated. Among promoters with more than ten transcription factors bound were mostly genes with a low CV. Accordingly, promoters of genes with high CV were often bound by less than ten transcription factors. 
This result is intuitive: Genes under tight transcriptional control also have a very controlled range of (low) expression, since their activity might affect the whole system. 
Additionally, the study tested if also the regulation by miRNAs or the protein-protein-interactions are reflected in low or high CV genes, but could not observed any enrichment, leading to the conclution that miRNAs and PPIs do not play a major role in transcriptional control.

Focusing on high CV genes, the authors asked wether transcription factor or chromatin remodellers preferentially bind or avoid promoters based on the genes CV. Promoter specific factors, like *E2F1*, *TAF1* or *YY1* did not show a preference for any CV class. Transcription factors, like *NCOA3*, *p300*, *p53* and *MCAF1* showed an preferential binding to promoters from genes with a high CV.
Terms like *cellular response to stress*, *response to DNA damage stimulus* or *DNA repair* were enriched accordingly. It is thought that *p53* is also a marker for stem cell differentiation that represses self-renewal genes.
Further, it has been reported that key developmental genes exhibit a distinct chromatin structure called bivalent, with large stretches of H3K27me3 (negative regulation of transcription by promoting a compact chromatin structure) interspersed with smaller H3K4me3 marks (promoting transcription by recruiting nucleosome remodelling). 
Interestingly, genes with bivalent promoters (from bulk studies) had a significantly higher CV than those with an active promoter (only H3K4me3). Despite that high CV genes in general were not enriched for embryonic development and transcriptional control, the results indicate that on a single cell level, promoters seem not to be bivalent.

When focusing on the top 25% of genes with a high CV correlation among each other, genes tend to cluster into co-expression networks. However, a more detailed investigation revealed that only one or a few cells were driving the observed pattern, making the use of CV (or its mean across genes) questionable in the detection of biologically relevant genes.

Anna Mantsoki, Guillaume Devailly and Anagha Joshi. Gene expression variability in mammalian embryonic stem cells using single cell RNA-seq data. **Computational Biology and Chemistry** (*2016*), doi: 10.1016/j.compbiolchem.2016.02.004 [weblink](http://www.sciencedirect.com/science/article/pii/S1476927116300330)