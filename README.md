---
title: "Using Block Rand for Stratified Random Sampling for Ongoing Studies"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```
For many studies, enrollment is on going.  However, the same problems are around random assignment as with any study in that randomize sometimes does not always randomize.  Therefore, one common approach is to stratify on key variables (e.g. gender, race).  

The blockrand package is designed for this kind of study

First we want to library (install if you have not already) the blockrand package.
```{r}
library(blockrand)
```
For this example, we are assuming about 20 people and we think that gender (male and female) is critical to ensure that they are equally spread throughout the different treatments, which in our case we are using A (treatment) and B (control).  The code below from the blockrand guide demonstrates how to produce this random sequence.  


```{r}
male = blockrand(n = 10, id.prefix = "M", block.prefix = "M", stratum = "Male")
female = blockrand(n = 10, id.prefix = "M", block.prefix = "M", stratum = "Female")

random_assign = rbind(male, female)
random_assign
```
With this data, a researcher can split this information into a spreadsheet and when a male comes in they can look at the male spread sheet and see which treatment package this person will get.  Or the researcher can just provide a set on envolopes that is in two piles male and female that has the treatment assignment and the researcher could just hand the treatment assignment to the participant.
