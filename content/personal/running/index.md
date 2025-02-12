---
title: Running
summary: Providing a record of my running
date: "2025-02-12T00:00:00Z"

reading_time: false
share: false
profile: false
comments: false

# Information on header: https://bootstrap.hugoblox.com/content/pages/

---

Around the end of 2023, I decided to devote more of my time to keeping my body (and mind) in shape. In order to maintain a good habit like this, I need accountability and I need a goal. I decided to get into running. To provide myself with a goal, I signed up for the Utah Valley Marathon (and have since run multiple half-marathons in the area). To provide myself with accountability, I started recording my runs, and posting to this website is another form of accountability.

The data linked here are a spreadsheet of my runs since I began this process. There are a number of metrics I keep track of, and I use a `gam` model in the programming language `R` to try to predict the pace I should run for regular exercise and for a race.

This is a link to the data:

[Running Data](https://docs.google.com/spreadsheets/d/1O_r313XFN5TJK8Edr80UpJcLwDXKNep2gI0Ga8LmnHE/edit?usp=sharing)

The most pertinent portion of my code reads in the data and produces the `gam` model:

```r
library(tidyverse)
library(lubridate)
library(hms)
library(mgcv)
library(googlesheets4)
theme_set(theme_minimal())
running <- read_sheet("https://docs.google.com/spreadsheets/d/1O_r313XFN5TJK8Edr80UpJcLwDXKNep2gI0Ga8LmnHE/edit?usp=sharing",
                      skip = 2)
running <- running %>%
  mutate(date = as.numeric(ymd(date)),
         time = as_hms(time),
         dist_fac = cut(dist, breaks = c(0, 2.5, 7.5, 15, 30, Inf),
                        labels = c("0-2.5", "2.5-7.5", "7.5-15", "15-30", "30+")),
         duration = ymd_hms(duration) - ymd_hms("1899-12-30 00:00:00"),
         pace = as.numeric(ymd_hms(pace) - ymd_hms("1899-12-30 00:00:00")),
         type = factor(type, levels = c("Regular", "Race")),
         surface = factor(surface, levels = c("Road", "Treadmill", "Track")),
         elevation = elevation)
my_mod <- gam(pace ~ s(date, k = 6) + s(dist, k = 7) + afternoon +
                s(gain_per_km, k = 5) + change_per_km +
                injury + sleep + surface + elevation +
                s(temp, k = 3) + s(dew, k = 4) + type,
              data = running, method = "REML", family = scat())
```

Which I then use to produce the following figures, which include predicted paces for different distances (all in kilometers because I'm weird like that). This image shows the predicted paces for a regular run:

<iframe src="https://drive.google.com/file/d/1-xTBOLDbhk4chsJ3lpzJfMXJx4XSbqZk/preview" width="640" height="480" allow="autoplay"></iframe>

While this image shows the predicted paces for a race:

<iframe src="https://drive.google.com/file/d/11PVDSpnKrFgkCcCB0xWu2_xMRT8mRgC_/preview" width="640" height="480" allow="autoplay"></iframe>

I hope to one day be able to run the Boston Marathon; realistically, that goal is still a couple years off (and would be represented by my marathon race pace getting close to the dashed horizontal line on the graph). For the Utah Valley Marathon in 2025, I hope to be able to run a time under 4 hours, and maybe close to 3:50.




