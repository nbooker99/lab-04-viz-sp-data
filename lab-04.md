Lab 04 - La Quinta is Spanish for next to Denny’s, Pt. 1
================
Noah Booker
03/18/25

### Load packages and data

``` r
library(tidyverse) 
##library(dsbox) 
```

To install dsbox, it wanted me to update R. Instead I just downloaded
the two datasets manually.

``` r
states <- read_csv("data/states.csv")
```

### Exercise 1

``` r
load("~/Documents/Documents/Studies/School/WFU/DS4P/Lab_4/data/dennys.rda")
glimpse(dennys)
```

    ## Rows: 1,643
    ## Columns: 6
    ## $ address   <chr> "2900 Denali", "3850 Debarr Road", "1929 Airport Way", "230 …
    ## $ city      <chr> "Anchorage", "Anchorage", "Fairbanks", "Auburn", "Birmingham…
    ## $ state     <chr> "AK", "AK", "AK", "AL", "AL", "AL", "AL", "AL", "AL", "AL", …
    ## $ zip       <chr> "99503", "99508", "99701", "36849", "35207", "35294", "35056…
    ## $ longitude <dbl> -149.8767, -149.8090, -147.7600, -85.4681, -86.8317, -86.803…
    ## $ latitude  <dbl> 61.1953, 61.2097, 64.8366, 32.6033, 33.5615, 33.5007, 34.206…

The dennys dataset has 1,643 observations of 6 variables. The
observations represent Denny’s restaurants and the variables represent
various characteristics of each restaurant’s location (address, city,
state, zipcode, longitude, and latitude).

### Exercise 2

``` r
load("~/Documents/Documents/Studies/School/WFU/DS4P/Lab_4/data/laquinta.rda")
glimpse(laquinta)
```

    ## Rows: 909
    ## Columns: 6
    ## $ address   <chr> "793 W. Bel Air Avenue", "3018 CatClaw Dr", "3501 West Lake …
    ## $ city      <chr> "\nAberdeen", "\nAbilene", "\nAbilene", "\nAcworth", "\nAda"…
    ## $ state     <chr> "MD", "TX", "TX", "GA", "OK", "TX", "AG", "TX", "NM", "NM", …
    ## $ zip       <chr> "21001", "79606", "79601", "30102", "74820", "75254", "20345…
    ## $ longitude <dbl> -76.18846, -99.77877, -99.72269, -84.65609, -96.63652, -96.8…
    ## $ latitude  <dbl> 39.52322, 32.41349, 32.49136, 34.08204, 34.78180, 32.95164, …

The laquinta dataset has 909 observations of 6 variables. The
observations represent La Quinta locations and the variables represent
various characteristics of each hotel’s location (address, city, state,
zipcode, longitude, and latitude).

### Exercise 3

According to their website, there are La Quinta locations outside the
US. There are locations in Canada, Mexico, China, New Zealand, Turkey,
United Arab Emirates, Chile, Colombia, and Ecuador. Denny’s website only
allows me to either search locations using a city, zipcode, or my
current location or to browse US locations. So, I am ucertain whether
there are Denny’s locations outisde the US.

### Exercise 4

To examine the datasets to see whether La Quinta and Denny’s have
location outside of the US I could use something like dennys %\>%
distinct(state) for each dataset. Because they both have variables for
the state of the location, I could use the distinct function to visually
examine all the states that appear in the datasets to see if any seem
like non-US states.

### Exercise 5

``` r
dennys %>%
  filter(!(state %in% states$abbreviation))
```

    ## # A tibble: 0 × 6
    ## # ℹ 6 variables: address <chr>, city <chr>, state <chr>, zip <chr>,
    ## #   longitude <dbl>, latitude <dbl>

This filter gives a tibble with 0 rows, indicating that there are no
Denny’s locations in the dataset in states other than US states.

### Exercise 6

``` r
dennys <- dennys %>% 
  mutate(country = "United States")
```

Created a country variable for the dennys dataset. Add exercise headings
as needed.
