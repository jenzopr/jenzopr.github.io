---
layout: post
title:  "N1-methyladenosine exhibits post-transcriptional regulatory effects"
author: Jens Preussner
tags: methods
cover: "assets/dyes.jpg"
categories: reading bioinformatics
---

A report published in *Nature* this week adds N<sup>1</sup>-methylation of adenosine to the list of functional post-transcriptional modifications of messenger RNAs.
To study the modification in greater detail, the authors characterized the N<sup>1</sup>methyl-adenosine methylome with a method termed N<sup>1</sup>-methyladenosine sequencing (m<sup>1</sup>A-seq). 
Therefore, Dan Dominissini et. al. altered a similar method reported previously, m<sup>6</sup>A-seq, to capture the N<sup>1</sup>-methylated adenosines using anti-m<sup>1</sup>A antibodies and mapped sequenced reads back to the genome.
To validate specificity, the authors showed that a known adenosine N<sup>1</sup>-methylation site on the human 28S rRNA is marked by a single peak from m<sup>1</sup>A-seq. 

As with other post-transcriptional modifications, the amount of the modification in the total mRNA fraction is crucial to be able to assign a functional or regulatory role.
Using expression estimates from before and after immunodepletion of N<sup>1</sup>-methylated adenosine containing mRNAs, the authors found 20% of the transcripts from modification-containing genes to actually carry the modification.
To investigate further, the evolutionary conservation of m<sup>1</sup>A presence was verified in mouse using multiple tissues and cell types, with as of 15% transcripts from modified genes showed the modification. 
The conservation of peaks in different locations between mouse and human was highest in the 5'-UTR and a window of 300bp around the AUG start codon (44-46%), compared to other gene segments (3-16%).
Furthermore, conservation was evaluated in yeast. Albeit the mammalian patterns of modification did not reoccur, the modification was present also in yeast. Additionally, when yeast was transferred to a nitrogen-source deficient medium, the authors observed noticeable changes in the transcriptome.
Taken together and according to the authors, the m<sup>1</sup>A presence of observed levels across species and the conservation between species suggest the possibility of functionally effects on mRNA metabolism. 

To investigate structural properties of m<sup>1</sup>A, Dominissini et. al. created metagene profiles that revealed the clustering of m<sup>1</sup>A around the start codon in all three tested human cell lines.
Furthermore, the number of modification sites on a transcript was positively correlated to the number of translation initiation sites (TIS). When binning the m<sup>1</sup>A modification according to the exon that contains the start codon,
the authors observed shifted profiles of distance to the TSS for different bins. Especially when the start codon is in the 2<sup>nd</sup> or 3<sup>rd</sup> exon, the modified adenosine is closer to the TSS, as compared to when the start codon is in the 1<sup>st</sup> exon.
Compared to the TIS, the position of the first splicing event mirrored the observations better, suggesting that the first splice site is used as an *anchor* for N<sup>1</sup>-methyladenosine formation.

Since both structure and sequence features of the 5' UTR and start codon affect the ribosomal scanning and translation initiation process, the authors investigated translation efficiency of modified transcripts.
In general, translational efficiency and ribosome release scores of genes with m<sup>1</sup>A peaks are higher compared to genes without a peak. Also when normalized to mRNA abundance levels, the protein levels were higher for modified transcripts.
In their concluding remarks, the authors suggest a positive and dynamic role of m<sup>1</sup>A for translation by altering the properties of the RNA-ribomsome interaction.
Together with m<sup>6</sup>A, which is enriched around the stop codon and 3'-UTR, the two modifications could act as modulator of mRNA metabolism and add a new dimension to post-transcriptional control of gene expression.

Dan Dominissini, Sigrid Nachtergaele, Sharon Moshitch-Moshkovitz, Eyal Peer, Nitzan Kol, Moshe Shay Ben-Haim, Qing Dai, Ayelet Di Segni, Mali Salmon-Divon, Wesley C. Clark, Guanqun Zheng, Tao Pan, Oz Solomon, Eran Eyal, Vera Hershkovitz, Dali Han, Louis C. Doré, Ninette Amariglio, Gideon Rechavi and Chuan He. The dynamic N<up>1</sup>-methyladenosine methylome in eukaryotic messenger RNA. **Nature** (*2016*), doi: 10.1038/nature16998 [weblink](http://www.nature.com/nature/journal/vaop/ncurrent/full/nature16998.html)
