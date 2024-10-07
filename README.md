# Data 512 Homework 1
## Overview
This repository contains the contents of an analysis into page views of specified disease articles on Wikimedia from July 2015 up until the present. Specifically, this analysis performs API calls to collect the number of page views per article, per month, and per access method. Additionally, this analysis generates three figures, showcasing:
- Figure 1: Maximum Average and Minimum Average
- Figure 2: Top 10 Peak Page Views
- Figure 3: Fewest Months of Data

## Licenses and API Documentation
The source data is used under #TODO

The Article Page Views API  was the [Wikimedia REST API](https://www.mediawiki.org/wiki/Wikimedia_REST_API) (Terms of Use [Here](https://foundation.wikimedia.org/wiki/Policy:Terms_of_Use)). Here, the terms of use applies to the dataset I have created in that I am Reading, Printing, Contributing To and Editing the data from Wikimedia, all while engaging in lawful behavior and doing no harm. Additionally, the API code was adapted from an example developed by Dr. David W. McDonald for use in DATA 512, a course in the UW MS Data Science degree program. This code is provided under the [Creative Commons](https://creativecommons.org) [CC-BY license](https://creativecommons.org/licenses/by/4.0/). Revision 1.3 - August 16, 2024


## Repository Structure

├── data_clean/                                           # Folder containing the cleaned data
│   ├── rare-disease_monthly_combined_201507_202409.json  # JSON with the page view counts for both access types (mobile and desktop)
│   ├── rare-disease_monthly_desktop_201507_202409.json   # JSON with the page view counts for mobile
│   └── rare-disease_monthly_mobile_201507_202409.json    # JSON with the page view counts for desktop
├── data_raw/                                             # Folder containing the raw data
│   └── rare-disease_cleaned.AUG.2024.csv                 # CSV with the article names
├── results/                                              # Folder containing the generated figures
│   ├── figure1.png                                       # PNG with the Maximum Average and Minimum Average figure
│   ├── figure2.png                                       # PNG with the Top 10 Peak Page Views figure
│   └── figure3.png                                       # PNG with the Fewest Months of Data figure
├── src/                                                  # Source code
│   ├── analysis.ipynb                                    # Notebook to perform the data processing and graphing of the three figures
│   └── data_acquisition.ipynb                            # Notebook to perform the API calls and generate the cleaned data for the different access types
├── LICENSE                                               # License documentation
└── README.md                                             # README for the repo


## Data Schema
The output json files generated and stored in the "data_clean" folder have the following schema:

'''json
{
    "type": "object",
    "properties":{
        "article": {
            "type": "array",
            "items":{
                "project": {
                    "type": "string",
                    "description": "Project Name (e.g. en.wikipedia)"
                },
                "article": {
                    "type": "string",
                    "description": "Article Name"
                },
                "granularity": {
                    "type": "string",
                    "description": "Range of API Call (e.g. monthly)"
                },
                "timestamp": {
                    "type": "string",
                    "description": "Year and month"
                },
                "agent": {
                    "type": "string",
                    "description": "Type of agent (e.g. user)"
                },
                "views": {
                    "type": "int",
                    "description": "Number of page views for the given timestamp and article"
                },                
            }

        }
    }
}


## Additional Notes
Overall, one special consideration when using the repo or data would be to consider investigating improved methods for executing the API calls. Currently, the code takes ~1.5 hrs to complete all the API calls, which could likely be optimized. Additionally, there are a handful of urls from the raw data that were unable to be accessed, so future usage should note that there may be some article names without corresponding page view data.
