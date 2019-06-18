[![https://www.singularity-hub.org/static/img/hosted-singularity--hub-%23e32929.svg](https://www.singularity-hub.org/static/img/hosted-singularity--hub-%23e32929.svg)](https://singularity-hub.org/collections/2878)

# bioinfo_singularity_recipes
Singularity recipies for bioinformatic pipelines

GUERIN Pierre-Edouard, 2019-05-05

______


We provide ready to run versions of [Singularity containers](https://www.sylabs.io/)



# 1 Singularity containers

## 1.1 Install Singularity
See [https://www.sylabs.io/docs/](https://www.sylabs.io/docs/) for instructions to install Singularity.

## 1.2 Obitools

- The [OBITools package 1.0](http://metabarcoding.org/obitools) is a set of programs specifically designed for analyzing NGS data in a DNA metabarcoding context, taking into account taxonomic information.
- [ecoPrimers 1.0.1](https://git.metabarcoding.org/obitools/ecoprimers/) is a software that finds primers from a set of sequences.
- [ecoPCR 0.5](https://git.metabarcoding.org/obitools/ecopcr/) simulate _in silico_ PCR digestion.


### 1.2.1 Download the Obitools container

```
singularity pull --name obitools.img shub://Grelot/bioinfo_singularity_recipes:obitools
```

Alternatively, if you're using the [Montpellier Bioinformatics Biodiversity platform](https://mbb.univ-montp2.fr/MBB/index.php), download this custom container :
```
singularity pull --name obitools.img shub://Grelot/bioinfo_singularity_recipes:obitoolsmbb
```

### 1.2.2 Run the Obitools container

```
singularity run obitools.img
```
it should output:
```
Opening container...ubuntu xenial: OBITOOLS,ecoPRIMERS,ecoPCR
```

### 1.2.3 Execute some programs from the container

```
## OBITOOLS: illuminapairedend 
singularity exec obitools.img illuminapairedend --help
## OBITOOLS: ngsfilter
singularity exec obitools.img ngsfilter --help
## OBITOOLS: obigrep
singularity exec obitools.img obigrep --help
## OBITOOLS: obiclean
singularity exec obitools.img obiclean --help
## OBITOOLS: ecotag
singularity exec obitools.img obiclean --help
## ecoPCR
singularity exec obitools.img ecoPCR --help
## ecoPrimers
singularity exec obitools.img ecoPrimers --help
```

## 1.3 Useful programs for eDNA analysis

- [vsearch 2.13.4](https://github.com/torognes/vsearch) supports de novo and reference based chimera detection, clustering, full-length and prefix dereplication, rereplication, reverse complementation, masking, all-vs-all pairwise global alignment, exact and global alignment searching, shuffling, subsampling and sorting. It also supports FASTQ file analysis, filtering, conversion and merging of paired-end reads.
- [pear 0.9.11](https://cme.h-its.org/exelixis/web/software/pear/) is an ultrafast, memory-efficient and highly accurate pair-end read merger
- [fastq-join 1.3.1](https://github.com/brwnj/fastq-join) joins two paired-end reads on the overlapping ends.
- [pandaseq 2.11](https://github.com/neufeld/pandaseq) aligns Illumina reads, optionally with PCR primers embedded in the sequence, and reconstruct an overlapping sequence.
- [jellyfish 2.2.6](https://github.com/gmarcais/Jellyfish) reads FASTA and multi-FASTA files containing DNA sequences. It outputs its k-mer counts.
- [casper 0.8.2](http://best.snu.ac.kr/casper/) (Context-Aware Scheme for Paired-End Read) is state-of-the art paired-end reads merging tool.
- [FLASh 1.2.11](http://ccb.jhu.edu/software/FLASH/index.shtml) (Fast Length Adjustment of SHort reads) is a very fast and accurate software tool to merge paired-end reads from next-generation sequencing experiments.
- [fastq-multx](https://github.com/ExpressionAnalysis/ea-utils/blob/wiki/FastqMultx.md) 1.3.1 demultiplexes a fastq. Capable of auto-determining barcode id's based on a master set fields.
- [cutadapt 2.3](https://cutadapt.readthedocs.io/en/stable/guide.html) removes adapter sequences from high-throughput sequencing reads.
- [SWARM 2.2.2](https://github.com/torognes/swarm) performs clustering method for amplicon-based studies.
- [Reaper 13.274](https://www.ebi.ac.uk/research/enright/software/kraken) is a program for demultiplexing, trimming and filtering short read sequencing data. It can handle barcodes, trim adapter sequences, strip low quality bases and low complexity sequence, and has many more features. 
- [TAGcleaner 0.16](http://tagcleaner.sourceforge.net/) detects and trims tag sequences from sequence data.
- [Flexbar 3.0.3](https://github.com/seqan/flexbar) preprocesses high-throughput sequencing data efficiently. It demultiplexes barcoded runs and removes adapter sequences. Several adapter removal presets for Illumina libraries are included. 
- [usearch 11.0.667](https://www.drive5.com/usearch/) offers search and clustering algorithms that are often orders of magnitude faster than BLAST. 
- [deML 1.0](https://grenaud.github.io/deML/) demultiplexes Illumina sequences.

### 1.3.1 Download the eDNA analysis container

```
singularity pull --name ednatools.img shub://Grelot/bioinfo_singularity_recipes:ednatools
```
Alternatively, if you're using the [Montpellier Bioinformatics Biodiversity platform](https://mbb.univ-montp2.fr/MBB/index.php), download this custom container :
```
singularity pull --name ednatools.img shub://Grelot/bioinfo_singularity_recipes:ednatoolsmbb
```

### 1.3.2 Run the eDNA analysis  container

```
singularity run ednatools.img
```
it should output:
```
Opening container...ubuntu beaver: vsearch, PEAR, fastq-join, pandaseq, jellyfish, casper, FLASH, fastq-multx, cutadapt, SWARM, REAPER, tally, minion, swan, tagCleaner, flexbar, usearch, deML 
```

### 1.3.3 Execute some programs from the container


```
## vsearch
singularity exec ednatools.img vsearch -h
## pear
singularity exec ednatools.img pear -h
## pandaseq
singularity exec ednatools.img pandaseq -h
## casper
singularity exec ednatools.img casper -h
## FLASh
singularity exec ednatools.img flash -h
## fastq-multx
singularity exec ednatools.img fastq-multx -h
## fastq-join
singularity exec ednatools.img fastq-join -h
## cutadapt
singularity exec ednatools.img cutadapt -h
## SWARM
singularity exec ednatools.img swarm -h
## Reaper
singularity exec ednatools.img reaper -h
singularity exec ednatools.img tally -h
singularity exec ednatools.img minion -h
## TAGcleaner
singularity exec ednatools.img tagcleaner -h
## Flexbar
singularity exec ednatools.img flexbar -h
## usearch
singularity exec ednatools.img usearch
## deML
singularity exec ednatools.img deML -h
```
