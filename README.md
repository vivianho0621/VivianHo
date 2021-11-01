# VivianHo
Lab 01
---
title: "Lab 01"
output:
  html_document:
    df_print: paged
  pdf_document: default
---

### Instructions

Your solutions must be written in an R Markdown (Rmd) file called `lab-01.Rmd`. This file must include your code and write up for each question. Your “submission” will be whatever is in your lab repository at the deadline. In order to receive full credit, your notebook must knit to HTML without any errors.

This lab is open book, open internet, closed other people. You may use any online or book based resource you would like, but you must include citations for any code that you use. You may not consult with anyone else about this lab other than the Professor or TA for this course.

You have until 11:59pm on Sunday, October 31 to complete this lab and turn it in via your personal GitHub repo - late work will not be accepted. Technical difficulties are not an excuse for late work - do not wait until the last minute to knit / commit / push.

On questions asking you to produce a graph, be sure to include an appropriate title and labels. Graphs should include a brief (one or two sentence) narrative describing the graph and what it reveals about the data. For this lab, you can only use base R (**do not use any third-party libraries such as `ggplot`, `dplyr`, etc.**).

### Getting help

You are not allowed to post any questions on the Canvas Discussion board. Any questions about the lab must be asked during office hours or via email to the Professor or the TA.

### Grading and feedback

The total points for the questions add up to 90 points. The remaining 10 points are allocated to code style, overall organization, spelling, grammar, etc. There is also an extra credit question that is worth 5 points. You will receive feedback as an issue posted to your repository, and your grade will also be recorded on Canvas.

### The data

The data can be found inside the `data` folder in the main directory. `ppauto_pos` contains information on private passenger auto liability/medical claims for various property-casualty insurers that write business in the US. A description of each field is below:

- `GRCODE` NAIC company code (including insurer groups and single insurers)
- `GRNAME` NAIC company name (including insurer groups and single insurers)
- `AccidentYear` Accident year(1988 to 1997)
- `DevelopmentYear` Development year (1988 to 1997)
- `DevelopmentLag` Development year (AY-1987 + DY-1987 - 1)
- `IncurLoss_B` Incurred losses and allocated expenses reported at year end
- `CumPaidLoss_B` Cumulative paid losses and allocated expenses at year end
- `BulkLoss_B` Bulk and IBNR reserves on net losses and defense and cost containment expenses reported at year end
- `PostedReserve97_B` Posted reserves in year 1997 taken from the Underwriting and Investment Exhibit – Part 2A, including net losses unpaid and unpaid loss adjustment expenses
- `EarnedPremDIR_B` Premiums earned at incurral year - direct and assumed
- `EarnedPremCeded_B` Premiums earned at incurral year - ceded
- `EarnedPremNet_B` Premiums earned at incurral year - net
- `Single` 1 indicates a single entity, 0 indicates a group insurer

### Questions

**Question 1 (5 points)**: Load the file `data/ppauto_pos.csv` into R and assign it to a variable `ppauto`.

```{r}
ppauto=read.csv(ppauto_pos.csv,header=TRUE)
head(ppauto)
```

**Question 2 (20 points)**: Create a bar plot showing paid losses (`CumPaidLoss_B`) for `State Farm Mut Grp` by accident year at development lag (`DevelopmentLag`) 10.

```{r}
library(ggplot2)
dat=subset(ppauto_pos,ppauto_pos$GRNAME=="State Farm Mut Grp"&ppauto_pos$DevelopmentLag==10)
ggplot(dat,aes(x=AccidentYear, y= CumPaidLoss_B)) + geom_col(position = "dodge")
```
