---
title: Telemetry Reports - Imports
teaching: 10
exercises: 0
questions:
    - "What datasets do I need from the Network?"
    - "How do I import all the datasets?"
---

## MigraMar Node 

## Importing all the datasets
Now that we have an idea of what an exploratory workflow might look like with Tidyverse libraries like `dplyr` and `ggplot2`, let's look at how we might implement a common telemetry workflow using these tools. 

We are going to use OTN-style detection extracts for this lesson. If you're unfamiliar with detection extracts formats from OTN-style database nodes, see the documentation [here](https://members.oceantrack.org/data/otn-detection-extract-documentation-matched-to-animals). 

For the ACT Network you will receive Detection Extracts which include (1) Matched to Animals YYYY, (2) Detections Mapped to Other Trackers YYYY (also called Qualified) and (3) Unqualified Detections YYYY. In each case, the YYYY in the filename indicates the single year of data contained in the file. The types of detection extracts you receive will differ depending on the type of project you have regitered with the Network. ex: Tag-only projects will not receive Qualified and Unqualified detection extracts.

To illustrate the many meaningful summary reports which can be created use detection extracts, we will import an example of Matched and Qualified extracts.

First, we will comfirm we have our Tag Matches stored in a dataframe.
~~~
view(gmr_matched_18_19) #Check to make sure we already have our tag matches, from a previous episode

# if you do not have the variable created from a previous lesson, you can use the following code to re-create it:

#gmr_matched_2018 <- read_csv("gmr_matched_detections_2018.csv") #Import 2018 detections
#gmr_matched_2019 <- read_csv("gmr_matched_detections_2019.csv") # Import 2019 detections
#gmr_matched_18_19 <- rbind(gmr_matched_2018, gmr_matched_2019) #Now join the two dataframes
# release records for animals often appear in >1 year, this will remove the duplicates
#gmr_matched_18_19 <- gmr_matched_18_19 %>% distinct() # Use distinct to remove duplicates. 

~~~
{: .language-r}


Next, we will load in and join our Array matches. Ensure you replace the filepath to show the files as they appear in your working directory.

~~~
gmr_qual_2018 <- read_csv("gmr_qualified_detections_2018.csv")
gmr_qual_2019 <- read_csv("gmr_qualified_detections_2019.csv")
gmr_qual_18_19 <- rbind(gmr_qual_2018, gmr_qual_2019) 
~~~
{: .language-r}

To give meaning to these detections we should import our Instrument Deployment Metadata and Tagging Metadata as well. These are in the standard OTN-style templates which can be found [here](https://members.oceantrack.org/data/data-collection).

~~~
#These are saved as XLS/XLSX files, so we need a different library to read them in. 
library(readxl)

# Deployment Metadata
gmr_deploy <- read_excel("gmr-deployment-short-form.xls", sheet = "Deployment")
view(gmr_deploy)

# Tag metadata
gmr_tag <- read_excel("gmr_tagging_metadata.xls", sheet = "Tag Metadata") 
view(gmr_tag)

#remember: we learned how to switch timezone of datetime columns above, 
# if that is something you need to do with your dataset!
~~~
{: .language-r}

