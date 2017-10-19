# English Wikipedia Page Views: 2008 - 2017

This project was performed as **Assignment 1: Data Curation** for my Human-Centered Data Science course (DATA 512, University of Washington, Autumn 2017). The assignment description can be found here (as of October 2017): https://wiki.communitydata.cc/HCDS_(Fall_2017)/Assignments#A1:_Data_curation

For this assignment I retrieve, aggregate and visualize the number of monthly visitors to English Wikipedia from January 2008 through September 2017. I group the data by the nature of the visit, whether via the desktop website, or via mobile, which includes the mobile website and the mobile application. I also present total visits by month, which is simply the sum of monthly desktop and mobile visits. I visualize the results and save the output to a .csv file.

Aside from the relatively simple project workflow itself, the goal of the assignment was to allow me to demonstrate that I can follow best practices for open and reproducible research as discussed in class. As such, I intend this project to be fully reproducible: from data collection to data analysis, and every step along the way. Thus, I would appreciate feedback if you attempt to duplicate the analysis and come across any shortcomings, or have any other suggestions.

## Directory Structure

```
data-512-a1/
    |- data/
        |- raw/
            |- ...					  // raw API data (five .json files)
        |- en-wikipedia_traffic_200801-201709_prelim.csv  // combined data table prior to cleaning 
        |- en-wikipedia_traffic_200801-201709.csv 	  // cleaned data table
    |- en-wikipedia_traffic_200801-201709.png 		  // final data visualization
    |- hcds-a1-data-curation.ipynb 			  // source code (Jupyter Notebook) 
    |- LICENSE
    |- README.md
 ```

## Reproducibility

As previously mentioned, a major goal of this work is to make it fully reproducible. This means that any user should be able to run my code and produce the exact same result as presented here.

To test this out, simply `git clone` this repository, and open and run hcds-a1-data-curation.ipynb. The results should be exactly reproduced.

Note that to prevent unnecessary API calls, the code is configured to refer to local data files if they exist. Thus, to truly start from scratch, delete all the data in the `/data` folder and subfolder (i.e. `/data/raw`), and then run the notebook.

## Data Source and License

Monthly Wikipedia traffic counts were retrieved from two separate Wikimedia REST API endpoints:

* The legacy [Pagecounts API](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts) provides access to desktop and mobile traffic data from January 2008 through July 2016.
* The newer [Pageviews API](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews) provides access to desktop, mobile web, and mobile app traffic data starting in July 2015.

Documentation on both endpoints can be found here:
https://wikimedia.org/api/rest_v1/

For the endpoints used in this project, the content is available under the [CC0 1.0 license](https://creativecommons.org/publicdomain/zero/1.0/). However, note that other endpoints may fall under different licensing (e.g. CC-BY-SA 3.0 and GFDL licenses). Please be sure to refer to the endpoint documentation above for terms and conditions before using any other API endpints.

Please also refer to the Wikimedia Foundation Terms of Use prior to use:
https://wikimediafoundation.org/wiki/Terms_of_Use/en


## Next Header

Things to include: 
* “This data was provided by X and can be found at Y URL”
* Mention the bad data in August 2016 or whenever that was.
* Include outline structure for data and other files.





At minimum, you README file should

*Describe the goal of the project.
*List the license of the source data and a link to the Wikimedia Foundation terms of use (LINK)
*Link to all relevant API documentation
*Describe the values of all fields in your final data file.
*List any known issues or special considerations with the data that would be useful for another researcher to know. For example, you should describe that data from the Pageview API excludes spiders/crawlers, while data from the Pagecounts API does not.