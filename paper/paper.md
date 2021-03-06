---
title: "ggsignif: R Package for Displaying Significance Brackets for 'ggplot2'"
tags:
  - R
  - ggplot2
  - ggplot2-extension
authors:
  - name: Constantin Ahlmann-Eltze
    orcid: 0000-0002-3762-068X
    affiliation: 1
  - name: Indrajeet Patil
    orcid: 0000-0003-1995-6531
    affiliation: 2
affiliations:
  - index: 1
    name: The European Molecular Biology Laboratory, Heidelberg, Germany
  - index: 2
    name: Center for Humans and Machines, Max Planck Institute for Human Development, Berlin, Germany
date: "2021-03-26"
bibliography: paper.bib
---



# Summary

Research hypotheses are often concerned with the difference between two groups and
statistical tests provide indicators (like *p*-values or Bayes factors) about
the evidence for or against such differences. The R package, `ggsignif` provides
a quick way to visualize such pairwise indicators as an annotation in a plot,
for example showing if a difference is statistically significant. `ggsignif`
follows the principles of the grammar of graphics [@Wilkinson2012] and provides
a new layer that can be added to plots made with the `ggplot2` package
[@Wickham2016].

# Statement of Need

During the exploratory analysis of data with discrete covariates, researchers
commonly start with a one-way ANOVA to see if there are any differences in the
group means. This is typically followed up with multiple comparisons to see if
specific levels of the discrete covariates differ significantly. The `ggsignif`
package provides a way to graphically display all or a few (depending on the
context of the research hypotheses) of such comparisons. It is also used by
other R package developers as the back-end for graphical display of pairwise
comparisons, such as `ggpubr` [@Kassambara2020], `ggstatsplot` [@Patil2018], and
more. These packages demonstrate how `ggsignif` can be extended to display
results from any type of pairwise comparisons test (e.g., Bayesian *t*-test,
Dunn test, etc.).

# Features

The following is a simple example demonstrating how a group difference can be
annotated using `geom_signif` layers from `ggsignif` package.


```r
set.seed(123)
library(ggplot2)
library(ggsignif)

ggplot(mpg, aes(class, hwy)) +
  geom_boxplot() +
  geom_signif(
    comparisons = list(c("compact", "midsize"), c("minivan", "suv")),
    map_signif_level = TRUE
  ) +
  ylim(NA, 48)
```


\includegraphics[width=1\linewidth]{paper_files/figure-latex/simpe_comparison-1} 

For more advanced examples, the readers are encouraged to read the package
website: <https://const-ae.github.io/ggsignif/>.

# Licensing and Availability

`ggsignif` is licensed under the GNU General Public License (v3.0), with all
source code stored at [GitHub](https://github.com/const-ae/ggsignif), and with a
corresponding issue tracker for bug reporting and feature enhancements. In the
spirit of honest and open science, we encourage requests/tips for fixes, feature
updates, as well as general questions and concerns via direct interaction with
contributors and developers, by [filing an issue](https://github.com/const-ae/ggsignif/issues). See the
[*Contribution Guidelines*](https://github.com/const-ae/ggsignif/blob/master/CODE_OF_CONDUCT.md) for this package.

# Acknowledgements

We would like to thank the users of `ggsignif` package for reporting bugs and
for providing valuable feedback.

This work was supported by the EMBL International PhD Programme (C.A.E.).

# References
