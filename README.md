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

- The [OBITools package](http://metabarcoding.org/obitools) is a set of programs specifically designed for analyzing NGS data in a DNA metabarcoding context, taking into account taxonomic information.

- [ecoPrimers](https://git.metabarcoding.org/obitools/ecoprimers/) is a software that finds primers from a set of sequences.

- [ecoPCR](https://git.metabarcoding.org/obitools/ecopcr/) simulate _in silico_ PCR digestion.



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
##output:
## Opening container...ubuntu xenial: OBITOOLS,ecoPRIMERS,ecoPCR
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

