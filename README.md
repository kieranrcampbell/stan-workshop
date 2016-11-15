# stan-workshop
STAN workshop for GMS students

Date: 17-18 November 2016

Location: STRUBI Meeting Room, Wellcome Trust Centre for Human Genetics

Instructors: Justina Zurauskiene (JZ), Kieran Campbell (KC), Christopher Yau (CY)

## Timetable

*Thursday, 17 November, 2016*

> 10:00-10:30 Introduction to the course (CY/JZ)

> 10:30-11:30 Introduction to Bayesian Statistics (The GMS students!!!)

> 11:30-12:30 Introduction to STAN (KC)

> 12:30-13:30 Lunch

> 13:30-17:00 Practical (JZ/KC)

*Friday, 18 November, 2016*

> 09:30-12:30 Practical Continuation (JZ/KC)

> 12:30-13:30 Lunch

> 13:30-14:30 [Talk] [Professor Ahmed Ashour Ahmed](https://www.obs-gyn.ox.ac.uk/research/ovarian-cancer), Ovarian Cancer Laboratory, Nuffield Department of Obstetrics and Gynaecology and the Weatherall Institute of Molecular Medicine

> 14:30-15:30 [Talk] [Dr Edward Morrisey](https://scholar.google.co.uk/citations?user=JsJ5DkAAAAAJ&hl=en), Group Leader in Computational Biology, Weatherall Institute of Molecular Medicine


## Pre-requisites

### Knowledge

You should be familiar with the basic workings of R.

You should also have read about Bayesian Statistics as part of the pre-course exercise and be familiar with the following concepts:

- a random variable
- the basic rules of probability 
- a probability distribution
- Bayes' Rule
- prior probability distributions
- likelihood function
- posterior probability distribution

The mechanics of actually doing Bayesian inference is *not* required as this is the focus of the workshop practicals.

### Hardware and Software

Your own laptop with a copy of R and Rstudio (or your preferred development environment) installed.

Please install the following R packages:

- ggplot2
- Rstan
- devtools

### Getting the data

For exercise three 3 you need some real single cell data from the [Pollen et al. 2014](http://www.nature.com/nbt/journal/v32/n10/abs/nbt.2967.html) dataset. This comes as part of the R pacakge in this github repo. To install enter the following commands in the R console:

```{r installdata}
devtools::install_github("kieranrcampbell/stan-workshop/standata") 
```

Once this is installed, you can load the data any time via

```{r loaddata}
library(standata)
data(pollen2014)
data(celllibraries)
```

`pollen2014` is a gene-by-cell matrix of expression measurements for ~8000 genes in 300 cells. `celllibraries` is a `data.frame` that includes cell names, cell types and clusters.

*Tip:* when dealing with new data in RStudio, use the `View` command to easily explore, e.g. `View(pollen2014)` and `View(celllibs)`













