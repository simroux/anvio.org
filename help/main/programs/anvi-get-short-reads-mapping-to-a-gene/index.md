---
layout: program
title: anvi-get-short-reads-mapping-to-a-gene
excerpt: An anvi'o program. Recover short reads from BAM files that were mapped to genes you are interested in.
categories: [anvio]
comments: false
redirect_from: /m/anvi-get-short-reads-mapping-to-a-gene
image:
  featurerelative: ../../../images/header.png
  display: true
---

Recover short reads from BAM files that were mapped to genes you are interested in. It is possible to work with a single gene call, or a bunch of them. Similarly, you can get short reads from a single BAM file, or from many of them.

🔙 **[To the main page](../../)** of anvi'o programs and artifacts.


{% include _toc.html %}
<div id="svg" class="subnetwork"></div>
{% capture network_path %}{{ "network.json" }}{% endcapture %}
{% capture network_height %}{{ 300 }}{% endcapture %}
{% include _project-anvio-graph.html %}


## Authors

<div class="anvio-person"><div class="anvio-person-info"><div class="anvio-person-photo"><img class="anvio-person-photo-img" src="../../images/authors/meren.jpg" /></div><div class="anvio-person-info-box"><a href="/people/meren" target="_blank"><span class="anvio-person-name">A. Murat Eren (Meren)</span></a><div class="anvio-person-social-box"><a href="http://merenlab.org" class="person-social" target="_blank"><i class="fa fa-fw fa-home"></i>Web</a><a href="mailto:a.murat.eren@gmail.com" class="person-social" target="_blank"><i class="fa fa-fw fa-envelope-square"></i>Email</a><a href="http://twitter.com/merenbey" class="person-social" target="_blank"><i class="fa fa-fw fa-twitter-square"></i>Twitter</a><a href="http://github.com/meren" class="person-social" target="_blank"><i class="fa fa-fw fa-github"></i>Github</a></div></div></div></div>



## Can consume


<p style="text-align: left" markdown="1"><span class="artifact-r">[contigs-db](../../artifacts/contigs-db) <img src="../../images/icons/DB.png" class="artifact-icon-mini" /></span> <span class="artifact-r">[bam-file](../../artifacts/bam-file) <img src="../../images/icons/BAM.png" class="artifact-icon-mini" /></span></p>


## Can provide


<p style="text-align: left" markdown="1"><span class="artifact-p">[short-reads-fasta](../../artifacts/short-reads-fasta) <img src="../../images/icons/FASTA.png" class="artifact-icon-mini" /></span></p>


## Usage


This program finds all short reads from (<span class="artifact-n">[bam-file](/help/main/artifacts/bam-file)</span>) that align to a specific gene and returns them as a <span class="artifact-n">[short-reads-fasta](/help/main/artifacts/short-reads-fasta)</span>.

If instead you want to extract these short reads from a FASTQ file, get your gene sequence with <span class="artifact-p">[anvi-export-gene-calls](/help/main/programs/anvi-export-gene-calls)</span> and take a look at <span class="artifact-p">[anvi-script-get-primer-matches](/help/main/programs/anvi-script-get-primer-matches)</span>.

To run this program, just specify the bam files you're looking at and the gene of interest. To do this, name the <span class="artifact-n">[contigs-db](/help/main/artifacts/contigs-db)</span> containing your gene and the gene caller ID (either directly through the parameter `--gene-caller-id` or through a file). Here is an example:

<div class="codeblock" markdown="1">
anvi&#45;get&#45;short&#45;reads&#45;mapping&#45;to&#45;a&#45;gene &#45;c <span class="artifact&#45;n">[contigs&#45;db](/help/main/artifacts/contigs&#45;db)</span> \
                                       &#45;&#45;gene&#45;caller&#45;id 2 \
                                       &#45;i BAM_FILE_ONE.bam \
                                       &#45;O GENE_2_MATCHES
</div>

The output of this will be a file named `GENE_2_MATCHES_BAM_FILE_ONE.fasta` (prefix + bam file name), which will contain all short reads that aligned to gene 2 with more than 100 nucleotides.

You also have the option to provide multiple bam files; in this case, there will be an output files for each bam file inputted.

Additionally, you can change the number of nucleotides required to map to a short read for it to be reported. For example, to expand your search, you could decrease the required mapping length to 50 nucleotides, as so:

<div class="codeblock" markdown="1">
anvi&#45;get&#45;short&#45;reads&#45;mapping&#45;to&#45;a&#45;gene &#45;c <span class="artifact&#45;n">[contigs&#45;db](/help/main/artifacts/contigs&#45;db)</span> \
                                       &#45;&#45;gene&#45;caller&#45;id 2 \
                                       &#45;i Bam_file_one.bam Bam_file_two.bam \
                                       &#45;O GENE_2_MATCHES \
                                       &#45;&#45;leeway 50
</div>


{:.notice}
Edit [this file](https://github.com/merenlab/anvio/tree/master/anvio/docs/programs/anvi-get-short-reads-mapping-to-a-gene.md) to update this information.


## Additional Resources



{:.notice}
Are you aware of resources that may help users better understand the utility of this program? Please feel free to edit [this file](https://github.com/merenlab/anvio/tree/master/bin/anvi-get-short-reads-mapping-to-a-gene) on GitHub. If you are not sure how to do that, find the `__resources__` tag in [this file](https://github.com/merenlab/anvio/blob/master/bin/anvi-interactive) to see an example.
