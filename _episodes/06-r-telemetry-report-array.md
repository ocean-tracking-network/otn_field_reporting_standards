---
title: Telemetry Reports for Array Operators
teaching: 30
exercises: 0
questions:
    - "How do I summarize and plot my deployments?"
    - "How do I summarize and plot my detections?"
---

## MigraMar Node

### Mapping our stations - Static map

This section will use a set of receiver metadata from the ACT Network, showing stations which may not be included in our Array. We will make a static map of all the receiver stations in three steps, using the package `ggmap`. 

First, we set a basemap using the aesthetics and bounding box we desire. Then, we will filter our stations dataset for those which we would like to plot on the map. Next, we add the stations onto the basemap and look at our creation! If we are happy with the product, we can export the map as a `.tiff` file using the `ggsave` function, to use outside of R. Other possible export formats include: `.png`, `.jpeg`, `.pdf` and more.
~~~
library(ggmap)

names(gmr_deploy)

base <- get_stamenmap(
  bbox = c(left = min(gmr_deploy$DEPLOY_LONG),
           bottom = min(gmr_deploy$DEPLOY_LAT),
           right = max(gmr_deploy$DEPLOY_LONG),
           top = max(gmr_deploy$DEPLOY_LAT)),
  maptype = "terrain",
  crop = FALSE,
  zoom = 12)

#filter for stations you want to plot - this is very customizable

gmr_deploy_plot <- gmr_deploy %>% 
  dplyr::mutate(deploy_date=ymd_hms(`DEPLOY_DATE_TIME   (yyyy-mm-ddThh:mm:ss)`)) %>% #make a datetime
  dplyr::mutate(recover_date=ymd_hms(`RECOVER_DATE_TIME (yyyy-mm-ddThh:mm:ss)`)) %>% #make a datetime
  dplyr::filter(!is.na(deploy_date)) %>% #no null deploys
  dplyr::filter(deploy_date > '2017-07-03') %>% #only looking at certain deployments, can add start/end dates here
  dplyr::group_by(STATION_NO) %>% 
  dplyr::summarise(MeanLat=mean(DEPLOY_LAT), MeanLong=mean(DEPLOY_LONG)) #get the mean location per station, in case there is >1 deployment


#add your stations onto your basemap

gmr_map <- 
  ggmap(base) + 
  ylab("Latitude") +
  xlab("Longitude") +
  geom_point(data = gmr_deploy_plot, #filtering for recent deployments
             aes(x = MeanLong,y = MeanLat, colour = STATION_NO), #specify the data
             shape = 19, size = 2, alpha = 1) #lots of aesthetic options here!

#view your receiver map!
gmr_map

#save your receiver map into your working directory

ggsave(plot = gmr_map, filename = "gmr_map.tiff", units="in", width=8, height=15) 

#can specify location, file type and dimensions
~~~
{: .language-r}

### Mapping my stations - Interactive map

An interactive map can contain more information than a static map. Here we will explore the package `plotly` to create interactive "slippy" maps. These allow you to explore your map in different ways by clicking and scrolling through the output.

First, we will set our basemap's aesthetics and bounding box and assign this information (as a list) to a geo_styling variable.
~~~
library(plotly)

#set your basemap

geo_styling <- list(
  scope = 'galapagos',
  #fitbounds = "locations", visible = TRUE, #fits the bounds to your data!
  showland = TRUE,
  showlakes = TRUE,
  lakecolor = toRGB("blue", alpha = 0.2), #make it transparent
  showcountries = TRUE,
  landcolor = toRGB("gray95"),
  countrycolor = toRGB("gray85"),
  lonaxis = list(
    showgrid = TRUE,
    range = c(-92.5, -90)),
  lataxis = list(
    showgrid = TRUE,
    range = c(0, 2)),
  resolution = 50
)
~~~
{: .language-r}

Then, we choose which Deployment Metadata dataset we wish to use and identify the columns containing Latitude and Longitude, using the `plot_geo` function. 

~~~
#decide what data you're going to use. Let's use proj61_deploy_plot, which we created above for our static map.

gmr_map_plotly <- plot_geo(gmr_deploy_plot, lat = ~MeanLat, lon = ~MeanLong)   
~~~
{: .language-r}

Next, we use the `add_markers` function to write out what information we would like to have displayed when we hover our mouse over a station in our interactive map. In this case, we chose to use `paste` to join together the Station Name and its lat/long.
~~~
#add your markers for the interactive map

gmr_map_plotly <- gmr_map_plotly %>% add_markers(
  text = ~paste(STATION_NO, MeanLat, MeanLong, sep = "<br />"),
  symbol = I("square"), size = I(8), hoverinfo = "text" 
)
~~~
{: .language-r}

Finally, we add all this information together, along with a title, using the `layout` function, and now we can explore our interactive map!
~~~
#Add layout (title + geo stying)

gmr_map_plotly <- gmr_map_plotly %>% layout(
  title = 'GMR Deployments<br />(> 2017-07-03)', geo = geo_styling)


#View map

gmr_map_plotly
~~~
{: .language-r}

To save this interactive map as an `.html` file, you can explore the function htmlwidgets::saveWidget(), which is beyond the scope of this lesson.

### Summary of Animals Detected

Let's find out more about the animals detected by our array! These summary statistics, created using `dplyr` functions, could be used to help determine the how successful each of your stations has been at detecting tagged animals. We will also learn how to export our results using `write_csv`.

~~~
# How many of each animal did we detect from each collaborator, per station
library(dplyr) #to ensure no functions have been masked by plotly

gmr_qual_summary <- gmr_qual_18_19 %>% 
  dplyr::filter(datecollected > '2018-06-01') %>% #select timeframe, stations etc.
  group_by(trackercode, station, tag_contact_pi, tag_contact_poc) %>% 
  summarize(count = n()) %>% 
  dplyr::select(trackercode, tag_contact_pi, tag_contact_poc, station, count)

#view our summary table

gmr_qual_summary #reminder: this is filtered for certain dates!

#export our summary table

write_csv(gmr_qual_summary, "gmr_array_summary.csv", col_names = TRUE)
~~~
{: .language-r}

### Summary of Detections

These `dplyr` summaries can suggest array performance, hotspot stations, and be used as a metric for funders.

~~~
# number of detections per month/year per station 

gmr_det_summary  <- gmr_qual_18_19  %>% 
  mutate(datecollected=ymd_hms(datecollected))  %>% 
  group_by(station, year = year(datecollected), month = month(datecollected)) %>% 
  summarize(count =n())

gmr_det_summary

# Create a new data product, det_days, that give you the unique dates that an animal was seen by a station
stationsum <- gmr_qual_18_19 %>% 
  group_by(station) %>%
  summarise(num_detections = length(datecollected),
            start = min(datecollected),
            end = max(datecollected),
            uniqueIDs = length(unique(fieldnumber)), 
            det_days=length(unique(as.Date(datecollected))))
view(stationsum)

~~~
{: .language-r}

### Plot of Detections 

Lets make an informative plot using `ggplot` showing the number of matched detections, per year and month. Remember: we can combine `dplyr` data manipulation and plotting into one step, using pipes!

~~~

gmr_qual_18_19 %>%  
  mutate(datecollected=ymd_hms(datecollected)) %>% #make datetime
  mutate(year_month = floor_date(datecollected, "months")) %>% #round to month
  group_by(year_month) %>% #can group by station, collaborator etc.
  summarize(count =n()) %>% #how many dets per year_month
  ggplot(aes(x = (month(year_month) %>% as.factor()), 
             y = count, 
             fill = (year(year_month) %>% as.factor())
  )
  )+ 
  geom_bar(stat = "identity", position = "dodge2")+ 
  xlab("Month")+
  ylab("Total Detection Count")+
  ggtitle('GMR Collected Detections by Month')+ #title
  labs(fill = "Year") #legend title

~~~
{: .language-r}
