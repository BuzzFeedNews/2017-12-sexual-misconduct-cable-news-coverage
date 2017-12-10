# Analysis: Cable News Coverage of Sexual Misconduct Allegations

By [David Martin](http://dcmart.in/)

This repository contains data and analysis supporting the BuzzFeed News article, ["What Sexual Misconduct Allegations Are Getting The Most Attention On Cable News?,"](https://www.buzzfeed.com/davidcmartin/sexual-misconduct-cable-news-coverage) published December 10, 2017.

## Methodology

For this analysis we compiled a list of prominent men accused of sexual misconduct. No list can be comprehensive, but we drew on several sources, including lists from the [Atlanta Journal-Constitution](http://www.ajc.com/news/world/from-weinstein-lauer-timeline-2017-sexual-harassment-scandals/qBKJmUSZRJqgOzeB9yN2JK/) and the [New York Times](https://www.nytimes.com/interactive/2017/11/10/us/men-accused-sexual-misconduct-weinstein.html/). To obtain cable news coverage data, we used [TV Explorer](https://television.gdeltproject.org/cgi-bin/iatv_ftxtsearch/iatv_ftxtsearch), a tool from the Television News Archive and the GDELT Project that uses broadcast transcripts to count the number of sentences that mention a given phrase. In this case, the input phrases were each person’s name. To be more confident that we were counting only mentions of the person of interest, we searched only for counts of that person’s full name (that is, “Roy Moore”, not “Moore” or “Roy”).

Since closed captions may have occasional errors — misspelled words or words left out — these counts may be slightly off. We dropped from our analysis names that had only a few mentions, as comparisons between these small numbers were unlikely to be accurate.

For data on internet searches, we used Google Trends, a service that provides a measure of the relative amount of Google searches that have been made in a given time and place for a specific word or phrase. As with the TV data, we searched for the full names of individuals on our list. Google does not report the total number of searches, but does report a score that indicates the relative amount of searches when comparing across more than one search term. This means that we cannot say how many times Americans searched for “Matt Lauer”, but we can say, for example, that on the day that “Matt Lauer” received the highest number of searches during the time period we analyzed, that number was a little over three times the maximum number of searches for “Kevin Spacey,” about a month earlier.

## Structure of the repository

### Data

* [List of accused names](data/alleg_list.csv)
* [Daily TV data](data/tv_daily/)
* [Hourly TV data](data/tv_hourly/)
* [Google Trends](data/google_trends/)

### Code (Jupyter notebooks, written in R)

* [Data collection](code/00-collect-data.ipynb)
* [Data visualization](code/01-visualize-data.ipynb)

## Required Packages

Available from CRAN:

* `tidyverse`
* `lubridate`
* `magrittr`
* `stringr`
* `ggalt`
* `ggthemes`
* `hrbrthemes`
* `forcats`

The analysis also uses two packages that, respectively, wrap the [Google Trends](https://trends.google.com/trends/?geo=AU) and [TV Explorer](https://television.gdeltproject.org/cgi-bin/iatv_ftxtsearch/iatv_ftxtsearch) APIs. Specifically, it uses the development versions for both:

* [`gtrendsR`](https://github.com/PMassicotte/gtrendsR)
* [`newsflash`](https://github.com/hrbrmstr/newsflash)

To install all the necessary packages:

```R
install.packages(c(
  "tidyverse", "lubridate", "magrittr", "stringr", 
  "ggalt", "ggthemes", "hrbrthemes", "forcats"
))

if (!require("devtools")) install.packages("devtools")
devtools::install_github("PMassicotte/gtrendsR")
devtools::install_github("hrbrmstr/newsflash")
```

## Feedback / Questions?

Contact David Martin at mail@davidcmart.in.

Looking for more from BuzzFeed News? [Click here for a list of our open-sourced projects, data, and code](https://github.com/BuzzFeedNews/everything).
