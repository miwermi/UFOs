
                                                                                           Michelle Werner (6/19/2022)
# UFO Data Search
---

<!--![alt](resources/___.png)-->
<img src="https://github.com/miwermi/ufos/blob/main/static/images/banner.png" alt ="graphic: UFOs">

## Project Overview

The town of McMinnville, Oregon has had many UFO sightings over the yeras and has an annual UFO enthusiast event celebrating the first sighting there in 1950 and all sightings since.  A datajournalist from the town is covering the event and has requested help creating a web page that allows users to search UFO sighting data.

Using Javascript, HTML and CSS, and a dataset provided by the client, I've created a webpage that allows several different search parameters through the dataset.


## Results
<img src="https://github.com/miwermi/ufos/blob/main/static/images/datefilter.png" align="right" width="500" height="293" alt ="screenshot: Date Filter">

<img src="https://github.com/miwermi/ufos/blob/main/static/images/statefilter.png" align="right" width="500" height="293" alt ="screenshot: State Filter">

<img src="https://github.com/miwermi/ufos/blob/main/static/images/shapefilter.png" align="right" width="500" height="293" alt ="screenshot: Shape Filter">

<img src="https://github.com/miwermi/ufos/blob/main/static/images/city+shapefilter.png" align="right" width="500" height="293" alt ="screenshot: City & Shape Filter">

At it's initial creation, the page only allowed for one search category, Date, which was triggered after date entry with a button event.  Further development added addtional search optiosn for City, State, Country and Shape, and the search trigger was moved to a "change" event on each input box when the user hits enter.  This works well enough, and is somewhat intuitive, but the dataset is sparse and there are many search posibilities that will return nothing.  

Figure 1: Results of a Date Filter
Figure 2: Results of a State Filter
Figure 3: Results of a Shape Filter
Figure 4: Results of a City & Shape Filter


## Summary

The main drawback of the page as it is, is that it is not clear what parameters will return results and so searching will likely be frustrating to a user who isn't already familiar with the dataset.  This could be resolved by creating select options from the data and adding drop down menus to the search boxes for each category based on actual values for each field in the dataset.  Example: The shapes mentioned above.  Also, the data could be more comprehensive... perhaps using an API for some significant source could provide regular updates. These features would make the webpage capability much more robust and the user experience more satistfying.
