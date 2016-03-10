---
layout: post
title:  "A high throughput CRISPR-Cas9 featured system discoveres unmarked regulatory elements"
author: Jens Preussner
tags: methods
cover: "assets/mera-crispr-cas-grna.jpg"
categories: reading bioinformatics
---

In the past years, the catalogue of elements involved in gene regulation has been filled up with many classic *cis*-regulating elements, like promoter or enhancers, with a variety of histone modifications, with distal DNA interactions and with different chromatin states, such as active or poised.
But still, the prediction of effects of regulatory variants on gene expression is challenging. A novel approach, described in Nature Biotechnology by Gifford and Sherwood, combines CRISPR-Cas9 with high-throughput library generation and deep sequencing in order to map effects on gene expression induced by DNA variants.
Traditionally, reporter assays focus on elements that are sufficient to activate a gene and do not test those (multiple) elements systematically in a high-thoughput fashion.
In the study, the authors exploited the use of thousands of guide RNAs (gRNAs) for Cas9 to target thousands of sites within regulatory regions, inducing small insertions or deletings by error-prone repair of Cas9-induced double strand breaks. By comparing phenotypes that either did or did not show an altered gene expression, variants can be assigned a likelihood to have an effect.

For the assay, the authors first generated cells with four GFP-tagged mESC-specific genes, *Nanog*, *Rpp25*, *Tdgf1* and *Zfp42*. For each gene, a specific library of approx. 4000 gRNAs was created and introduced into the cells.
To prevent that more than one gRNA will be active with Cas9 in a single cell, the authors developed a construct expressing a single-copy of a dummy gRNA hairpin. Then, CRISPR-Cas9 mediated homologous recombination is used to replace the dummy gRNA with a random gRNAs from the gene-specific library.
FAC sorting into GFP<sup>pos</sup> and GFP<sup>neg</sup> followed by high-throughput sequencing are then used to identify induced loss of gene expression.

The first result obtained by Rajagopal and colleagues is that the gRNA abundance from GFP<sup>neg<sup> cells is distributed over a variety of *cis*-regulatory elements, like promoters, enhancer and also external promoters, i.e. from other genes. As expected, the highest density was achieved at known promoter sites.
Surprisingly, the authors also observed a novel class of regulatory elements downstream of the gene (URE, *Tgf1*), which did not colocate with any known marker of regulatory activity, like H3K4me3, TF-binding sites, or DNA hypersensitivity sites (*see figure above*). 
Two approaches were used to rule out potential off-target effects of the gRNA-Cas9 construct: First, all gRNAs with potential off-target effects were eliminated in the analysis, but the observed distribution across regulatory sites was not altered. Second, the gene-specific libraries were switched to rule out that gRNAs from the *Tdgf1* library would also act on expression of *Zfp42* and vice versa.
Besides a much small number of cells showed lost GFP expression, sequencing confirmed that gRNAs in GFP<sup>neg</sup> cells were predominantly GFP control gRNAs.

The primary analysis was followed by a functional motif discovery, that could help to identify sequence features that differ between GFP<sup>pos</sup> and GFP<sup>neg</sup> populations at a given site. The researchers discovered two required motifs in a *Tdgf1* proximal enhancer region that contain a *Stat3* binding site and a *Nrd1* binding site in a *Zfp42* enhancer.
When applies to two gRNAs located in an URE 12kB downstream of *Tdgf1*, consecutive bases were identified whose deletion correlates with GFP loss. For validation, the authors used homologous recombination with flanking gRNAs to delete the required regulatory sites in enhancers and UREs. As expected, the subset of cells that were GPF<sup>neg</sup> also showed the deletion genotype.

Nisha Rajagopal, Sharanya Srinivasan, Kameron Kooshesh, Yuchun Guo, Matthew D Edwards, Budhaditya Banerjee, Tahin Syed, Bart J M Emons, David K Gifford and Richard I Sherwood. High-throughput mapping of regulatory DNA. **Nature Biotech.** (*2016*), doi: 10.1038/nbt.3468 [weblink](http://www.nature.com/nbt/journal/v34/n2/full/nbt.3468.html) 