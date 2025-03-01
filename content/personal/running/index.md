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

To run my model, I read in my data from [this link](https://docs.google.com/spreadsheets/d/1O_r313XFN5TJK8Edr80UpJcLwDXKNep2gI0Ga8LmnHE/edit?usp=sharing) and then use [this script](https://drive.google.com/file/d/1-wIgjN5oaljMaTtWZbD0oZ0jwSl9jnFc/view?usp=sharing) to produce the `gam` model.

The following figures summarize the predictive results from the model, which include predicted paces for different distances (all in kilometers because I'm weird like that). This image shows the predicted paces for a regular run:

<div style="padding: 10px 0;">
    <div style="position: relative; width: 100%; padding-top: 56.25%;">
        <iframe
            src="https://drive.google.com/file/d/1-xTBOLDbhk4chsJ3lpzJfMXJx4XSbqZk/preview"
            style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border: none;"
            allow="autoplay">
        </iframe>
    </div>
</div>

While this image shows the predicted paces for a race:

<div style="padding: 10px 0;">
    <div style="position: relative; width: 100%; padding-top: 56.25%;">
        <iframe
            src="https://drive.google.com/file/d/11PVDSpnKrFgkCcCB0xWu2_xMRT8mRgC_/preview"
            style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border: none;"
            allow="autoplay">
        </iframe>
    </div>
</div>

Some things to note based on my exploration of these data:

* The metrics I include in my model are: the date, the distance of the run, whether it occurs in the afternoon, the elevation gain (in km) per kilometer for the run, the change in elevation (in km) from beginning to end per kilometer for the run, whether I recently had an injury, my sleep score for the night before (from FitBit), the type of surface I'm running on (road, treadmill, or track), the elevation of my run, the temperature of my run, the dewpoint for my run, and whether my run is a regular workout or a race
* Because I am using a `gam` model, I use smooth terms on some of these variables, and I vary the dimensions of the smooth term based on the output of `gam.check()`. There are six dimensions for date, seven for distance, three for temperature, and four for dew point. Based on what I have read, worrying about these exact values is probably not useful; however, with a small n-size I try to minimize the number of dimensions.
* I included most of the variables I have in my model for theoretical reasons; as it turns out, many of them are not all that useful. Just checking p-values in the model is probably not a sound approach, but if you want to know mine, I find that date matters (I've been improving over time!), and so do distance, gain, having a recent injury, running on a track, and the run being a race instead of a regular run.

Lastly, this image shows the running distance over time. The black line provides the daily running totals (so there are many days with 0 kilometers); the pink line provides weekly running totals; lastly, the blue line provides monthly running totals.

<div style="padding: 10px 0;">
    <div style="position: relative; width: 100%; padding-top: 56.25%;">
        <iframe
            src="https://drive.google.com/file/d/130vqO10yH8ohjDrgW1kkN0o_4bVOzJ6T/preview"
            style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border: none;"
            allow="autoplay">
        </iframe>
    </div>
</div>

I hope to one day be able to run the Boston Marathon; realistically, that goal is still a couple years off (and would be represented by my marathon race pace getting close to the dashed horizontal line on the graph). For the Utah Valley Marathon in 2025, I hope to be able to run a time under 4 hours, and maybe close to 3:50.

