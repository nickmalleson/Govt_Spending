UK Public Spending Visualisation
========================================================

This is a treemap visualisation of 2011-12 UK public spending.

Data are from the Guardian: http://www.theguardian.com/news/datablog/2012/dec/04/government-spending-department-2011-12

Load the library:


```r
# install.packages('treemap')
library("treemap")
```


Read data:


```r
setwd("~/mapping/projects/blog/Govt_Spending/code/")
# d <- read.csv('../data/test_data2.csv')
d <- read.csv("../data/spending_data.csv")
```


Make a treemap using percentage change as colour:


```r
treemap(d,
        index=c("Department", "Description"), # Columns in order of aggregation
        vSize="spend_2011_12", # Size of rectangles
        vColor="pct_change", # How to colour rectangles
        type="value",
        title="UK Government spending by department",
        title.legend="Change (ignore inflation) in spending, 2010/11 - 2011/12")
```

![plot of chunk treemap1](figure/treemap1.png) 


Another map, this time using hierarchical colours (change 'index')


```r
treemap(d,
        index=c("Department", "Description"), # Columns in order of aggregation
        vSize="spend_2011_12", # Size of rectangles
        type="index",
        title="UK Government spending by department")
```

![plot of chunk treemap2](figure/treemap2.png) 


Finally make a pdf (better for final edits)


```r
pdf ("Spending_Treemap.pdf")
treemap(d,
        index=c("Department", "Description"), # Columns in order of aggregation
        vSize="spend_2011_12", # Size of rectangles
        type="index",
        title="UK Government spending by department")
dev.off()
```

```
## pdf 
##   2
```


