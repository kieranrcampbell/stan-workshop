# stan-workshop
STAN workshop for GMS students

Date: 17-18 November 2016

Location: STRUBI Meeting Room, Wellcome Trust Centre for Human Genetics

Instructors: Justina Zurauskiene (JZ), Kieran Campbell (KC), Christopher Yau (CY)

[Slides](https://kieranrcampbell.github.io/stan-workshop/)

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

For exercise 3 you need some real single cell data from the [Pollen et al. 2014](http://www.nature.com/nbt/journal/v32/n10/abs/nbt.2967.html) dataset. This comes as part of the R package in this github repo. To install enter the following commands in the R console:

```{r installdata}
devtools::install_github("kieranrcampbell/stan-workshop/standata") 
```

Once this is installed you can load the data any time via

```{r loaddata}
library(standata)
data(pollen2014)
data(celllibs)
```

`pollen2014` is a gene-by-cell matrix of expression measurements for ~8000 genes in 300 cells. `celllibs` is a `data.frame` that includes cell names, cell types and clusters.

**Tip:** when dealing with new data in RStudio, use the `View` command to easily explore, e.g. `View(pollen2014)` and `View(celllibs)`



## Practical

### 1. Basic linear regression

As per the lecture, reimplement the basic linear regression from simulated $y$ and $x$, and check model diagnostics. Play around with the priors on $\beta_1$ - how strong does the prior have to be to have an effect? How does this change with the number of data samples?

### 2. Multiple linear regression

Using the Cirrhosis death rate data, implement multiple linear regression in Stan. Try to interperet the posterior parameter estimates - is there a similarity to frequentist hypothesis testing here? Compare to a frequentist model using `lm`.

Now extend your model to include Automatic Relevance Determination (Kieran will explain model). Does this change your interpretation at all?

### 3. Count regression and generalized linear models

What happens if the data isn't continuous? Here we consider count data. The issue is if we have a mean function $\beta_0 * x_1 + \beta_1 * x_2 + ...$ the mean can easily be negative but the data must be positive! How do we get round this using generalized linear models?

As an example, we use the warpbreaks dataset built in to R, which can be loaded via `data(warpbreaks)`. Use the number of breaks as the dependent variable, and compare this to [standard glm](https://www.tutorialspoint.com/r/r_poisson_regression.htm).

Note to get the design matrix into Stan you should call `model.matrix`, ie

```{r dmat}
model.matrix(breaks ~ wool + tension, data = warpbreaks)
```











