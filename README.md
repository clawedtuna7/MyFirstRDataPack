# MyFirstRDataPack

For this lab, I tried to create my own R package, one that included an old data set from GIS 2. I was not able to successfully complete this package, but am publishing it for the sake of completion. 

The tutorial was decent, it skipped some steps here and there, but I was ultimately able to figure out (most) of the steps I was supposed to take to go through the lab. What made it difficult was my system. I kept on getting error messages saying that some of the crucial packages I needed to create an r package were "not available for my version of R" (so close to the finish line too!), so I will be checking these things out as I go on to create a package for my final project, and hope that everything works by then.



####################################################################################################

#install/read in libraries

     setwd("~/MyFirstRDataPack")

     install.packages(c("usethis", "devtools", "roxygen2"), repos = "http://cran.us.r-project.org")

     library(devtools)
     library(roxygen2)
     library(usethis)


# Add Clean Data

     usethis::use_data_raw()
            # Creates a folder named "data-raw"
     anscombe_set1 <- anscombe[c(1,5)]
            # Data wrangled
     use_data(anscombe_set1, overwrite = TRUE)
            # Creates a folder named "data" with 'anscombe_set1' in it


#####################################################################################################

#Try w your own data

     install.packages("tidyverse", repos = "http://cran.us.r-project.org")

     library(tidyverse)

     census80_raw <- readr::read_csv("data-raw/1980_RawCount_Demography.csv")

     Dem1980 <- census80_raw %>% mutate(totpop1980Pr = (TotPop80/3005072)*100, hisplatPr80 = (HispLat80/TotPop80)*100, whitePr80 = (white80/TotPop80)*100, aframPr80 = (black80/TotPop80)*100, asianPr80 = (asian80/TotPop80)*100, AmIndAKNatPr80 = (AmIndAKNa80/TotPop80)*100) %>% select(GISJOIN, TotPop80, totpop1980Pr, hisplatPr80, whitePr80, aframPr80, asianPr80, AmIndAKNatPr80)
            # standardize data
     usethis::use_data(Dem1980, overwrite = TRUE)

#####################################################################################################

#Check!

#
