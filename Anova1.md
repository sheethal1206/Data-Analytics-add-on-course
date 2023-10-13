## ANOVA Test

The one-way analysis of variance (ANOVA), also known as one-factor ANOVA, is an extension of independent two-samples t-test for comparing means in a situation where there are more than two groups. In one-way ANOVA, the data is organized into several groups base on one single grouping variable (also called factor variable). This tutorial describes the basic principle of the one-way ANOVA test and provides practical anova test examples in R software.

## Assumptions of ANOVA test

- The observations are obtained independently and randomly from the population defined by the factor levels
- The data of each factor level are normally distributed.
- These normal populations have a common variance. (Levene's test can be used to check this.)

## ANOVA test hypotheses:


- Null hypothesis, ($H_0$): the means of the different groups are the same
- Alternative hypothesis ($H_1$): At least one sample mean is not equal to the others.

### Note that, if you have only two groups, you can use t-test. In this case the F-test and the t-test are equivalent.

##  How one-way ANOVA test works?

Assume that we have 3 groups ($ A, B, C$ ) to compare:

1.  Compute the common variance, which is called variance within samples ($S^2_{within}$) or residual variance.
2. Compute the variance between sample means as follow:
- Compute the mean of each group
- Compute the variance between sample means ($S^2_{between}$)
3. Produce F-statistic as the ratio of $S^2_{between}/S^2_{within}$.

### Note that, a lower ratio (ratio < 1) indicates that there are no significant difference between the means of the samples being compared. However, a higher ratio implies that the variation among group means are significant.

## Packges used

- dplyr

- ggplot2

- ggpubr

- car

## Import data into R

Here, we'll use the built-in R data set named PlantGrowth. It contains the weight of plants obtained under a control and two different treatment conditions. There are still various methods to import data into R.

```{r, import data}
my_data <- PlantGrowth
```
### Creating a summary based on group

```{r}
library(dplyr)
group_by(my_data, group) %>%
  summarise(
    count = n(),
    mean = mean(weight, na.rm = TRUE),
    sd = sd(weight, na.rm = TRUE)
  )
```
