
<!-- README.md is generated from README.Rmd. Please edit that file -->

# nasaprograminsights

``` r
devtools::install_github(repo="NASA-Ecological-Conservation/nasaprograminsights", dependencies = FALSE, quiet = TRUE)
pkgs <- c("nasaprograminsights","dplyr","ggplot2")
lapply(pkgs, require, character.only = TRUE)
```

``` r
# Make a list of data frames using NSPIRES internal data ---------------------------------------------------------------
dir <-
  "/Users/jlburne3/Library/CloudStorage/OneDrive-NASA/bdecprogrameval/nspires-data/" # where is the internal data stored
nspires <-
  make_nspires(
    dir,
    removeppl = TRUE,
    tokeep = c(
      "selected",
      "declined",
      "submitted",
      "selectable",
      "invited",
      "awarded",
      "rejected"
    )
  )
# nspires contains 3 elements (data.frames):
##    lookup table to link program names and NOFOs
##    people: people listed on proposals
##    proposals: information regarding individual proposals
```

``` r
# Inspect Data ------------------------------------------------------------
# here is a list of programs. note that not all solicitations are assigned a program.
(programs <- sort(unique(nspires$lookup$`program name`))
 # here is a list of the programs for which we have proposal data:
# nspires$proposals[!nspires$proposals$`solicitation id` %in% nspires$lookup$`solciitation id`,] 
```
