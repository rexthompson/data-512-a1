# English Wikipedia Page Views: 2008 - 2017

This project was performed for **Assignment 1: Data Curation** in my Human-Centered Data Science course (DATA 512, University of Washington, Autumn 2017). The assignment description can be found here (as of October 2017): https://wiki.communitydata.cc/HCDS_(Fall_2017)/Assignments#A1:_Data_curation

For this assignment I retrieve, aggregate and visualize the number of monthly visitors to English Wikipedia from January 2008 through September 2017. I group the data by the nature of the visit, whether via the desktop website, or via mobile, which includes the mobile website and the mobile application. I also present total visits by month, which is simply the sum of monthly desktop and mobile visits. I visualize the results (see below) and save the output to a .csv file.

The final plot (shown below) is meant to mimic that shown here:
https://wiki.communitydata.cc/upload/a/a8/PlotPageviewsEN_overlap.png

![alt text](https://github.com/rexthompson/data-512-a1/en-wikipedia_traffic_200801-201709.png "Final Visualization")

Aside from the relatively simple project workflow itself, the goal of the assignment was to allow me to demonstrate that I can follow best practices for open and reproducible research as discussed in class. As such, I intend this project to be fully reproducible: from data collection to data analysis, and every step along the way. I would certainly appreciate feedback if you ome across any shortcomings, or have any other suggestions, if you attempt to duplicate this analysis.

## Data Source

Monthly Wikipedia traffic counts were retrieved from two separate Wikimedia REST API endpoints:

* The legacy [Pagecounts API](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts) provides access to desktop and mobile traffic data from January 2008 through July 2016.
* The newer [Pageviews API](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews) provides access to desktop, mobile web, and mobile app traffic data starting in July 2015.

See the [License](#license) section below for important legal information.

## Output Data

The cleaned data table can be found in `en-wikipedia_traffic_200801-201709.csv` ([link](data/en-wikipedia_traffic_200801-201709.csv)). It consists of monthly visit counts grouped by API call (i.e. Pagecount, Pageview) and source (i.e. all, desktop, mobile). The schema is as follows:

| Column        				| Value 		|
|-------------------------------|---------------|
| **year** 						| year (YYYY)	|
| **month**						| month (MM)	|
| **pagecount_all_views**		| num_views 	|
| **pagecount_desktop_views**	| num_views		|
| **pagecount_mobile_views**	| num_views 	|
| **pageview_all_views**		| num_views 	|
| **pageview_desktop_views**	| num_views 	|
| **pageview_mobile_views**		| num_views		|


Data notes:

* The data from the Pageview API excludes spiders/crawlers, while the data from the Pagecounts API does not.
* The mobile data from the Pageview API includes view counts from both the mobile website and the mobile application.
* The raw data from the Pagecount API included erroneous values in August 2016. These values have been set to zero in the final dataset.
* The raw data in this repository was retrieved on 2017-10-18. It is possible the source data may change in the future. See the [Reproducibility](#reproducibility) section below for more on this concept.

## Directory Structure

```
data-512-a1/
    |- data/
        |- raw/ 					  // raw API data (five .json files)
            |- ...					  
        |- en-wikipedia_traffic_200801-201709_prelim.csv  // combined data table prior to cleaning 
        |- en-wikipedia_traffic_200801-201709.csv 	  // cleaned data table
    |- en-wikipedia_traffic_200801-201709.png 		  // final data visualization
    |- hcds-a1-data-curation.ipynb 			  // source code (Jupyter Notebook) 
    |- LICENSE 						  // standard MIT License
    |- README.md
 ```

## Reproducibility

As previously mentioned, a major goal of this work is to make it fully reproducible. This means that any user should be able to run my code and produce the exact same result as presented here.

To test this out, simply `git clone` this repository, and open and run `hcds-a1-data-curation.ipynb`. The results should be exactly reproduced.

However, note that the code is configured to refer to local data files if they exist. This was done for two reasons:

* to create checkpoints (with reproducibility in mind)
* to prevent redundant API calls

To truly duplicate this analysis from scratch, delete all the data in `/data` and `/data/raw`, and then run the notebook. The data will be re-retrieved from Wikimedia, and new .csv files will be written. The final visualization is always regenerated regardless of whether new or existing source data is used.

If differences are found in results between code run with a clean slate vs. otherwise, they should be able to be traced to differences in the source data itself, or in modules upon which the code was written. Hopefully the "data checkpoints" will help with troubleshooting if this is ever found to be the case.

## License

Documentation on both Wikimedia REST API endpoints endpoints can be found here:
https://wikimedia.org/api/rest_v1/. For the endpoints used in this project, the content is available under the [CC0 1.0 license](https://creativecommons.org/publicdomain/zero/1.0/).

**IMPORTANT:** If you plan to modify the code to call to different API endpoints, note that these may fall under different licensing (e.g. CC-BY-SA 3.0 and GFDL licenses). Please be sure to refer to the endpoint documentation above for terms and conditions before using any API endpints other than the two use in this original project.

Please also refer to the Wikimedia Foundation Terms of Use prior to use:
https://wikimediafoundation.org/wiki/Terms_of_Use/en
