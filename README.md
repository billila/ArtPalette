<!-- README.md is generated from README.Rmd. Please edit that file -->

# ArtPalette

`ArtPalette` is an R package designed to provide different color
palettes based of famous painting. This package allows users to easily
access and utilize color schemes derived from the works of renowned
artists.

## Giorgio De Chirico Palette

Giorgio de Chirico (1888-1978) was an Italian painter and a prominent
figure in the metaphysical art movement, which he co-founded in the
early 20th century. Born in Volos, Greece, de Chirico spent much of his
childhood in Italy, where he developed a unique artistic style
characterized by eerie, dreamlike landscapes and enigmatic figures. His
works often feature classical architecture, long shadows, and a sense of
stillness, evoking a sense of mystery and introspection.

![](figure/giorgiodechirico.jpeg)

``` ![](figure/giorgiodechirico.jpeg)

## Installation

``` r
devtools::install_github("billila/ArtPalette")
```

## Usage

``` r
library("ArtPalette")

# See all palettes
names(gdc_palettes)
#> [1] "PiazzaDItalia"         "LeMuseInquietanti"     "SoleSulCavalletto1972"
#> [4] "PiazzaDItalia1939"     "ArrivoDelTrasloco1965" "Zissou1Continuous"
```

## Palettes

### PiazzaDItalia

``` r
gdc_palette("PiazzaDItalia")
```

![](figure/PiazzaDItalia-1.png)

``` r
gdc_palette("PiazzaDItalia1939")
```

![](figure/PiazzaDItalia-2.png)

### LeMuseInquietanti

``` r
gdc_palette("LeMuseInquietanti")
```

![](figure/LeMuseInquietanti-1.png)

### SoleSulCavalletto1972

``` r
gdc_palette("SoleSulCavalletto1972")
```

![](figure/SoleSulCavalletto1972-1.png)

``` r
library("ggplot2")
ggplot(mtcars, aes(factor(cyl), fill=factor(gear))) +  geom_bar() +
  scale_fill_manual(values = gdc_palette("SoleSulCavalletto1972"))
```

![](figure/ggplot1-1.png)
