---
layout: post
title:  "Novel insights into the interplay between DNA methylation and transcription factor activity"
author: Jens Preussner
tags: methylation transcription nrf1 nature
cover: "assets/dyes.jpg"
categories: bioinformatics reading
---

In a recent study published in *Nature* this week, the authors Silvia Domcke and Anaïs Flore Bardet were interested in finding transcription factors that are affected in their DNA binding abilities by DNA methylation.
As argued by the authors, previous studies have shown that transcription factors bound to regulatory regions go along with low levels of DNA methylation during regulation of gene expression, but it is still a matter of debate if transcription factor binding is the cause for low methylation or *vice versa*. 
To study the interplay, they created a triple knockout of *de novo* DNA methyltransferases that normally maintain the methylation of DNA, which is one of the epigenetic mechanisms that regulate gene expression.
Their expectation was that truncated DNA methylation may result in sites newly bound by transcription factors, that were not able to bind before.
Since potentially affected transcription factors are not known *a priori*, the authors used hypersensitivity to DNase I digestion, a method to generally identify regions of active regulation (DHSs).
Although most of the DHSs remained unchanged between wild-type and knockout cells, Domcke and colleagues observed around 1500 knockdown-specific DHSs and motif-search using known transcription factor binding motifs identified Nrf1 as the most promising candidate.

A following ChIP-Seq experiment validated the increased binding of Nrf1 in regions that were methylated in wildtype cells before, and a matched RNA-Seq experiment revealed elevated expression at loci that were newly bound by Nrf1. 
To mimick the downregulation of *de novo* DNA methyltransferases in a more physiological setting, the authors transferred wild type cells into a medium containing two kinase inhibitors. Still, Nrf1 binding was increased at knockdown-specific DHSs.
Transferring cells back to the original medium enabled the authors to test whether newly bound knockdown-specific DHSs are prevented from remethylation.
Observed results revealed the competition of *de novo* methylation and Nrf1 binding, with the winner being methylation - it outcompeted the binding of Nrf1, implying that binding and creation of a DHS is not enough to protect against *de novo* methylation.

The results suggest that Nrf1 binding is methylation-dependent (or *sensitive* for methylation) and requires additional features that keep its binding site in an unmethylated state.
Put in a more general idea, the authors describe transcription factor hierarchies in which Nrf1 is a so-called *settler*, that requires active demethylation and/or efficient downregulation of *de novo* methylation for establishing and maintaining its binding.
Notably, this implies that non-physical interactions between two transcription factors can be mediated by epigenetic marks: a methylation-*insensitive* transcription factor could remove blocking epigenetic marks and clear the DNA for binding of *sensitive* transcription factors.
In this model, *settler* transcription factors that are inhibited to bind DNA through DNA methylation depend on indirect cooperation with specific *insensitive* factors, as well as the local activity of methylating and demethylating enzymes. 

Silvia Domcke, Anaïs Flore Bardet, Paul Adrian Ginno, Dominik Hartl, Lukas Burger and Dirk Schübeler. Competition between DNA methylation and transcription factors determines binding of NRF1. **Nature** (*2015*), doi: 10.1038/nature16462 [[weblink](http://www.nature.com/nature/journal/v528/n7583/full/nature16462.html)]