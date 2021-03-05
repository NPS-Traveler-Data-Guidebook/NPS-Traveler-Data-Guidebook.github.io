# NPS website information

## Example Project Summary

In 2016, NPS and USDOT Volpe Center created the [NPS National Long Range Transportation Plan (NLRTP)](https://rosap.ntl.bts.gov/view/dot/32531). This effort proposed a number of goals, objectives, and performance measures that would support the 20-year strategic direction and planning of NPS national parks and other public lands.

One goal area is to maintain and enhance the quality of visitor experience. The objectives under this goal are:
- Improve ease of access to and within national park units for all people
- Create a range of appropriate transportation options that support a network of seamless connections within each park unit and to surrounding communities
- Provide state-of-the-art traveler information and wayfinding and, where appropriate, interpretation and education opportunities that complement transportation options

NPS park unit websites can have major influence on visitors and their planning for visiting a park. NPS created nine essential pieces of traveler information that answer important questions for some groups of visitors (i.e. where is the parking? How do I get to the major sites? Can I take public transportation? Is it accessible?)

### Approach

There are 10 measures that NPS park sites can be scored as meeting or not meeting:
- Description of transportation experience
- Driving directions
- Public transportation
- Bike & pedestrian information
- Parking
- Congestion
- Travel distances and time to key sites
- Accessibility of transportation systems and sites
- Alternative fueling stations


The historical approach for this type of task is to have people manually look through websites for measures. This approach can work for smaller tasks, but there are over 400 NPS park units with websites to monitor. This is likely too lofty a task for a consistent and timely results at the end.

This Github repo contains Python code that will scrape all the NPS websites, score on the essential elements for visitors, and create a final Excel sheet with the final scores.

### Analytical Methods

Generally, the program works in two parts:
## 1.  Web Scraping:
The objective of this program is to scrape the nps.gov websites to get all of the paragraph texts for all of the national park units with a current website. To do so, the scraper starts at the index.htm site for each park unit and looks for links to other nps.gov websites. Once it gets these links, it will go to those sites and look for new links. This will be repeated until there are no new links on any site.

Once all the links are collected then the scraper starts looking for text. To target the information we want, only the “Plan Your Visit” part of the park websites are scraped for text. Each of these is compiled into a big data table that is saved as an Excel file.

Note on the NPS site scraping: This function does not do a fully exhaustive scrape, but instead goes 2 links from the NPS park home page. An alternative method might involve going to every possible site with the scraper. However, as we are thinking that this is made for visitors, we want to make sure people can easily access the information, so 2 clicks seemed appropriate.


## 2. Natural Language Processing:
The program takes this raw output of text, does some cleaning to make more data-interpretable, and looks for keywords that align with the field. In general, the keyword search can be done to flag if a word or term shows up on a single page or can be used to count the number of times a single word shows up on a page. Although simple, using these two methods and a group of keywords, the model can generally identify web pages that have the visitor experience information.
To build the keywords, a comparative search was done of websites and their ranking in previous years. The specific criteria were created by limiting false positive and false negative responses when comparing with 2018 results. As shown in Table 1, all of the fields are within 7% when aggregated at the national level.



### Repo Overview

Code can be found in two files:

1. **VE_scraper_functions.py**: This file has functions for scraping the different "Planning your visit" parts of each NPS website and classifying/scoring the parks for the essential elements.  
2. **NPS Site Scrape.ipynb**: This is a jupyter notebook where the park information is loaded and the functions are run, with quality checks.


source: `{{ page.path }}`
