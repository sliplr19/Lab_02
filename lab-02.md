Lab 02 - Plastic waste
================
Lindley Slipetz
02/3/2021

## Load packages and data

``` r
library(tidyverse) 
```

``` r
plastic_waste <- read_csv("data/plastic-waste.csv")
```

## Exercises

### Exercise 1

``` r
ggplot(data = plastic_waste, aes(x = plastic_waste_per_cap)) +
  geom_histogram(binwidth = 0.2)
```

![](lab-02_files/figure-gfm/plastic-per-cap-1.png)<!-- -->

``` r
plastic_waste %>%
  filter(plastic_waste_per_cap > 3.5)
```

    ## # A tibble: 1 x 10
    ##   code  entity continent  year gdp_per_cap plastic_waste_p~ mismanaged_plas~
    ##   <chr> <chr>  <chr>     <dbl>       <dbl>            <dbl>            <dbl>
    ## 1 TTO   Trini~ North Am~  2010      31261.              3.6             0.19
    ## # ... with 3 more variables: mismanaged_plastic_waste <dbl>, coastal_pop <dbl>,
    ## #   total_pop <dbl>

``` r
ggplot(data = plastic_waste, aes(x = plastic_waste_per_cap)) +
  geom_histogram(binwidth = 0.2) +
  facet_wrap(~continent)
```

![](lab-02_files/figure-gfm/continent-1.png)<!-- -->

Generally, there are similar trends across continents: most countries
are clusted under 1. The only outlier is Trinidad and Tobago.

### Exercise 2

``` r
ggplot(data = plastic_waste, 
       mapping = aes(x = plastic_waste_per_cap, 
                     color = continent, 
                     fill = continent)) +
  geom_density(alpha = 0.2) +
  scale_fill_viridis_d()
```

    ## Warning: Removed 51 rows containing non-finite values (stat_density).

![](lab-02_files/figure-gfm/plastic-waste-density-1.png)<!-- -->

The color and fill of the curves were mapped to aesthetics because they
are variable dependent. The alpha level applies to all data (not by
variable), so it is defined in the plotting geom.

### Exercise 3

``` r
ggplot(data = plastic_waste, 
       mapping = aes(x = continent, 
                     y = plastic_waste_per_cap)) +
  geom_boxplot()
```

![](lab-02_files/figure-gfm/box-plot-1.png)<!-- -->

``` r
ggplot(data = plastic_waste, 
       mapping = aes(x = continent, 
                     y = plastic_waste_per_cap)) +
  geom_violin()
```

![](lab-02_files/figure-gfm/violin-1.png)<!-- -->

The violin plots reveal the shape of the distributions, while the box
plots do not. The outliers for continents other than North America are
more apparent in the box plots than the violin plots.

### Exercise 4

``` r
ggplot(data = plastic_waste, 
       mapping = aes(x =       
                 mismanaged_plastic_waste_per_cap,
                     y = plastic_waste_per_cap)) +
  geom_point() +
  labs(title = "Mismanaged plastic waste per capita vs plastic waste per capita",
       x = "Mismanaged plastic waste per capita",
       y = "Plastic waste per capita")
```

![](lab-02_files/figure-gfm/scatter-1.png)<!-- -->

Most of the countries are grouped towards the origin of the graph. There
seems to be a slight positive linear relationship.

### Exercise 5

color the points in the scatterplot by continent. Does there seem to be
any clear distinctions between continents with respect to how plastic
waste per capita and mismanaged plastic waste per capita are associated?

``` r
ggplot(data = plastic_waste, 
       mapping = aes(x =       
                 mismanaged_plastic_waste_per_cap,
                     y = plastic_waste_per_cap,
                 color = continent)) +
  geom_point() +
  labs(title = "Mismanaged plastic waste per capita vs plastic waste per capita",
       x = "Mismanaged plastic waste per capita",
       y = "Plastic waste per capita")
```

![](lab-02_files/figure-gfm/scatter-cont-1.png)<!-- -->

North America seems to have points with higher plastic waste per capita;
though, for most, they are low in mismanaged plastic waste per capita
(like the other continents). Africa seems to do the best job of
mismanaged plastic waste per capita as the maximum of the its values on
the x axis is lower than the other continents. Asia has the worst
mismanaged plastic waste per capita.

### Exercise 6

Remove this text, and add your answer for Exercise 6 here.

``` r
# insert code here
```

### Exercise 7

Remove this text, and add your answer for Exercise 7 here.

``` r
# insert code here
```

``` r
# insert code here
```

### Exercise 8

Remove this text, and add your answer for Exercise 8 here.

``` r
# insert code here
```
