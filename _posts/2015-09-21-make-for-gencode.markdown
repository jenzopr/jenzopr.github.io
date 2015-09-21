---
layout: post
title:  "Make for GENCODE annotations"
author: Jens Preussner
tags: gencode make
categories: bioinformatics
---

The [GENCODE](http://www.gencodegenes.org/) annotation is our primary resource for gene, transcript and exon boundary definition on the human and mouse genome.
Internally, we keep a network share for flatfiles that allows every member of our group to work on the same set of files. Since GENCODE releases new annotations
about two times a year, our flatfile share has to keep up to date, too. This post will show how we minimized the work to switch to a new GENCODE release.

GENCODE annotations come in various data files, available in both [GTF](http://www.gencodegenes.org/data_format.html) and [GFF3](http://www.sequenceontology.org/gff3.shtml) format. 
The main files that we use are the *basic gene annotation* and information on *long non-coding RNAs*. However, for some of our pipelines, we need subsets of these files, e.g. containing only 
exons, or files having a different data format (e.g. BED) - which is possible by parsing with simple linux commands and/or awk. To minimize the steps to recreate needed files for every new release, 
we made use of GNU's make utility. Makefiles are like recipes, containing information on how to create one or more files from a number of other files. 
For example, to create a BED 6 file from a GTF file, I would run awk on the GTF to extract the neccesary information:

{% highlight bash %}
cat file.gtf | awk 'BEGIN{FS="\t";OFS="\t"}{split($9,a,";");print $1,$4-1,$5,a[1],".",$7}' | sed 's/gene_id //g' | tr -d '"' > file.bed
{% endhighlight %}

Similarly, we collected a bunch of command line file transformations to download, extract, filter and reformat files from any [GENCODE](http://www.gencodegenes.org/) release:

{% highlight bash %}
#
# The first few lines are for reporting
#
.SECONDARY:
.PHONY: gencode.% 
.SILENT: %

%: gencode.%.genes.gtf.gz gencode.%.exons.gtf.gz gencode.%.introns.gtf.gz gencode.%.polyAs.gtf.gz gencode.%.long_noncoding_RNAs.gtf.gz gencode.%.exons.bed
	echo "Done creating annotation $@"

#
# The next few lines are for downloading neccecary files in various formats
#
gencode.%.long_noncoding_RNAs.gtf.gz:
	wget ftp://ftp.sanger.ac.uk/pub/gencode/Gencode_mouse/release_$(subst v,,$*)/gencode.$*.long_noncoding_RNAs.gtf.gz -O tmp
	zcat tmp | sed -e 's/chrM/chrMT/g' | gzip > $@
	rm tmp

gencode.%.polyAs.gtf.gz:
	wget ftp://ftp.sanger.ac.uk/pub/gencode/Gencode_mouse/release_$(subst v,,$*)/gencode.$*.polyAs.gtf.gz -O tmp
	zcat tmp | sed -e 's/chrM/chrMT/g' | gzip > $@
	rm tmp

gencode.%.annotation.gtf.gz:
	wget ftp://ftp.sanger.ac.uk/pub/gencode/Gencode_mouse/release_$(subst v,,$*)/gencode.$*.basic.annotation.gtf.gz -O tmp
	zcat tmp | sed -e 's/chrM/chrMT/g' | gzip > $@
	rm tmp

gencode.%.annotation.gff3.gz:
	wget ftp://ftp.sanger.ac.uk/pub/gencode/Gencode_mouse/release_$(subst v,,$*)/gencode.$*.basic.annotation.gff3.gz -O tmp
	zcat tmp | sed -e 's/chrM/chrMT/g' | gzip > $@
	rm tmp

#
# Now, lets do some work..
#
gencode.%.genes.gtf.gz: gencode.%.annotation.gtf.gz 
	zcat $< | grep -P '\tgene\t' | gzip > $@

gencode.%.exons.gtf.gz: gencode.%.annotation.gtf.gz
	zcat $< | grep -P '\texon\t' | awk 'BEGIN{FS="\t"}{if(!($$1$$4$$5 in a)){a[$$1$$4$$5]=$$0}}END{for (i in a){print a[i]}}' | bedtools sort -i - | gzip > $@

gencode.%.introns.gtf.gz: gencode.%.exons.gtf.gz gencode.%.genes.gtf
	zcat $< | bedtools merge -s -i - -c 6,8,7 -o distinct | bedtools subtract -s -b - -a gencode.$*.genes.gtf | awk 'BEGIN{FS="\t";OFS="\t"}{split($$9,attributes,";");split(attributes[1],gene," ");gene_id=substr(gene[2],2,20);if(!(gene_id in introns)){introns[gene_id]=1};print $$1,$$2,"intron",$$4,$$5,$$6,$$7,$$8,"intron_number "introns[gene_id]"; "$$9; introns[gene_id]=introns[gene_id]+1}' | gzip > $@

gencode.%.exons.bed: gencode.%.exons.gtf.gz
	zcat $< | awk 'BEGIN{FS="\t";OFS="\t"}{split($$9,a,";");print $$1,$$4-1,$$5,a[1],".",$$7}' | sed 's/gene_id //g' | tr -d '"' > $@

gencode.%.genes.gff3: gencode.%.annotation.gff3.gz
	zcat $< | grep -P '\tgene\t' > $@

gencode.%.exons.gff3: gencode.%.annotation.gff3.gz
	zcat $< | grep -P '\texon\t' | awk 'BEGIN{FS="\t"}{if(!($$1$$4$$5 in a)){a[$$1$$4$$5]=$$0}}END{for (i in a){print a[i]}}' | bedtools sort -i - > $@

.INTERMEDIATE: gencode.%.genes.gtf
gencode.%.genes.gtf: gencode.%.genes.gtf.gz
	zcat $< > $@
{% endhighlight %}

If you have the make utility installed and save the above code in a file called *Makefile*, a simple call like
{% highlight bash %}
make vM6
{% endhighlight %}

will download, extract and reformat some files from the current [GENCODE](http://www.gencodegenes.org/) release vM6. The *Makefile* can easily be adjusted to work for human releases, too!
