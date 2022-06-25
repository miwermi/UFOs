
                                                                                           Michelle Werner (6/19/2022)
# UFO Data Search
---

<!--![alt](resources/___.png)-->
<img src="https://github.com/miwermi/ufos/blob/main/static/images/banner.png" alt ="graphic: UFOs">
(Above: Banner graphic from the webpage)

## Project Overview

The town of McMinnville, Oregon has had many UFO sightings over the years and has an annual UFO enthusiast event celebrating the first sighting there in 1950 and all sightings since.  A data journalist from the town is covering the event and has requested help creating a web page that allows users to search UFO sighting data.

Using Javascript, HTML and CSS, and a dataset provided by the client, I've created a webpage that allows several different search parameters through the dataset.

## Results


At it's initial creation, the page only allowed for one search category, Date, which was triggered after date entry with a button event using javascript's d3.select.property: 

    function handleClick() {
      // Def variables:
      let date = d3.select("#datetime").property("value");
      let filteredData = tableData;

       // If a date is entered...
      if (date) {
        filteredData = filteredData.filter(row => row.datetime === date);
      }

       // Rebuild the table using the filteredData
      buildTable(filteredData);
    }
  

Further development was done to add additional search options for City, State, Country and Shape. Instead of creating a handleClick/filter button for each category,  and so multiple filters could be selected to narrow search results, the search trigger was moved to a "change" event on each input box, activated whenever a user hits enter.  

The refactored code with addtional search capability:

    // Def variable and function to store all filter values as an object:
    var srchFilters = {};

    function updateFilters() {

      let srchInput = d3.select(this);
      let srchValue = srchInput.property("value");
      let filterID = srchInput.attr("id");

      // Add any changed filter to to the filters list (or clear values):
      if (srchValue) {
          srchFilters[filterID] = srchValue;
      }
      else {
          delete srchFilters[filterID];
      }

      // Call next fitler function
      filterTable();

    }
  

    function filterTable() {
      let filteredData = tableData;

      // Loop through all of the filters and store filter data
      Object.entries(srchFilters).forEach(([key, value]) => {
          filteredData = filteredData.filter(row => row[key] === value);
      });  

      // Rebuild the table using the filteredData
      buildTable(filteredData);
    }
    
### Search Results:

<img src="https://github.com/miwermi/ufos/blob/main/static/images/datefilter.png" align="left" width="400" height="236" alt ="screenshot: Date Filter">  <img src="https://github.com/miwermi/ufos/blob/main/static/images/statefilter.png" align="right" width="400" height="236" alt ="screenshot: State Filter">

Figures 1 & 2: Results of a Date Filter,  Results of a State Filter

<br clear="all" />
    
<img src="https://github.com/miwermi/ufos/blob/main/static/images/shapefilter.png" align="left" width="400" height="236" alt ="screenshot: Shape Filter"><img src="https://github.com/miwermi/ufos/blob/main/static/images/city+shapefilter.png" align="right" width="400" height="236" alt ="screenshot: City & Shape">

Figures 3 & 4: Results of a Shape Filter, Results of a City & Shape Filter

<br clear="all" />   
<br clear="all" /> 

These addtional searches work well enough, and are somewhat intuitive, but the dataset is sparse and there are many search posibilities that will return nothing. Becuase it seemed nearly impossible that a user would be able to come up with any of the "shape" values in the data, I added an example list under the shape search input box that reads, "Note: Common shapes include: triangle, disk, light, etc..."

The example screenshots above illustrate the results when a search value that DOES exist is entered and the results of each.  The fourth image shows a result that is limited by two search values.  This feature of the additional development seems as if it would prove extremely useful to users.


## Summary

The main drawback of the page in its current format is that it is not clear what values users may enter that will actually return results. Searching will likely be frustrating to a user who isn't already familiar with the dataset. This could be resolved by creating select options from the data and adding drop down menus to the search boxes for each category based on actual values from values that exist in each field in the dataset.  Example: The shapes mentioned above: triangle, disk, light, etc...  This could easily be done with an initial select distinct query to populate the select options.
Also, the data could be more comprehensive, perhaps using an API for some significant source would provide not only MORE data but also the possibility of regular updates. These features would make the webpage capability much more robust and the user experience more satistfying.
