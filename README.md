# Coursera Capstone Project
By: Mario Sanchez, Jr.

# Where Should You Open Your Fitness Business in the City of Chicago?

## Introduction/Business Problem

### Introduction:

Business owners must consider many different things before opening their doors to the public. Among all the other concerns one might have, 
arguably the most important detail is location. Depending on the type of business, their ideal location will depend on many different factors 
such as amount of foot traffic, proximity to other similar businesses and access to public transportation. A deep analysis of a city can be done 
leveraging the power of machine learning to reveal the answers to these most critical questions. 

As a former fitness entrepreneur, I can directly relate to these concerns. Critical details about the area such as median income and number of 
other similar business can impact your bottom line greatly and possibly mean the difference between a successful business or not.

### Business Problem: 

Where in the city of Chicago would be a good location/neighborhood to open a fitness facility/ business?


## Data

In order to answer the above question, I obtained important business information utilizing the Foursquare API as well as neighborhood data scraped
from [Wikipedia](https://en.wikipedia.org/wiki/Community_areas_in_Chicago). Public health data was downloaded from the [official data portal](https://data.cityofchicago.org/Health-Human-Services/Public-Health-Statistics-Selected-public-health-in/iqnk-2tcu) for the City of Chicago. Foursquare was ultimately the largest source of data with critical information such as venue names, types, and location. From Wikipedia zip codes, neighborhood names and location coordinates were also obtained.

## Methodology
1. Scraped Wikipedia with [Beautiful Soup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/#) to get a list of community area names.
2. This list of names was then used to scrape each community area page, obtain zip codes and coordinates.
3. Utilized Pandas to explore and clean the unstructured data and assemble into a DataFrame object.
4. "Public Health Statistics- Selected public health indicators by Chicago community area" dataset was downloaded from the city of Chicago's data portal.      
5. Foursquare API was then used to get venue information for the list of 77 community areas.
6. Calculated important statistics such as the frequency of each unique business category found in each area.
7. Determined which of the categories would best fall under the category of 'health-related' and decided on: 

  'Farmers Market', 'Fruit & Vegetable Store', 'Park', 'Climbing Gym', 'Sporting Goods Shop', 'Gym', 'Yoga Studio',
  'Gym / Fitness Center', 'Dance Studio', 'Massage Studio', 'Supplement Shop', 'Field', 'Soccer Field', 'Health & Beauty Service',
  'Organic Grocery', 'College Gym', 'Basketball Court', 'Tennis Court', 'Health Food Store' and 'Baseball Field'.

8. Finally these health statistics plus the frequency of business category types was used as input into the KMeans unsupervised clustering algorithm.
9. In order to determine the proper choice of K, or clusters, I utilized the 'elbow method' plotting K vs distortion and K vs inertia.

![KMeans Distortion vs K](/chicago_final/assets/dist_k_elbow.png "KMeans Distortion vs K")

![KMeans Inertia vs K](/chicago_final/assets/inertia_k_elbow.png "KMeans Inertia vs K")

10. Cluster labels were then assigned to each community area and finally plotted on a map using Folium.

## Results
1. From the public health statistics the most interesting results I found was:
  
  The average rate per 100,000 residents for the whole city: 
       - 'Birth Rate': 15.7 
       - 'Breast cancer in females': 26 
       - 'Colorectal Cancer': 21.6
       - 'Diabetes-related': 71.9
       - 'Lung Cancer': 51.5
       - 'Prostate Cancer in Males': 36.8
       - 'Stroke (Cerebrovascular Disease)': 46.5
       - 'Per Capita Income': $25107
       - 'Unemployment': 13.3
       
This data is very useful when considering what clients you plan on targeting. Depending on the part of town, their dominant health 
concerns may vary widely. 

2. There were 219 unique venue categories found throughout the city of Chicago.

3. The top ten community areas with the most health related venues including gyms, spas and parks in Chicago are:

![Largest Number of Health Related Venues](/chicago_final/assets/num_health_venues.png "Number of Health Related Venues")

![Largest Number of Health Related Venues Chart](/chicago_final/assets/top_10_comms.png "Number of Health Related Venues Chart")

4. From Foursquare, the most common venues in these neighborhoods are:

![Most common venues in areas with most health related venues](/chicago_final/assets/most_common_venues.png "Most common venues in areas with most health related venues")

5. Community areas of Chicago mapped:

![Map of Community Areas of Chicago](/chicago_final/assets/chicago_cluster_map.png "Map of Community Areas of Chicago")

6. A closer look at cluster 2 which is mostly located in the central/northwest area of the city:

![Closer Look at Cluster 2](/chicago_final/assets/cluster1.png "Closer Look at Cluster 2")

## Discussion
Main observations:

  - Chicago is a very diverse and dynamic city which can be seen in the vast distribution of venues. However, our model revealed that despite this, when grouped based on health and venue data, distinct patterns arise. We can see that communities in the center of the city are quite different than those on the periphery and intuitively, this would make sense. With the information that was obtained we can visually see this and determine the personality of each area. 
  
  - These representations I believe can greatly assist with making a determination on where you may want to open your fitness business. The center of the city as well as communities to the immediate north and northwest have higher incomes and a larger business presence. As for the communities on the edges of the city, their characteristics change drastically and are much more suburban, while those on the far south side are much more industrial. 

Recommendations:

  - The Loop and Lincoln Park area are great business districts but are also going to be highly competitive and expensive to start. However, income in these
  areas allow for the targeting of a more affluent crowd.
  
  - If space is more important, the communities further away from the center of the city look to be great areas with high business activity as well as a more suburban setting.
  
## Conclusion
Opening a business is a huge undertaking and can very quickly become overwhelming when trying to find a location in a major metropolitan area. In a city like Chicago with 77 different communities, picking the right one takes research and smart decision making. With the results we obtained, I am confident that you will be able to make the most informed possible decision. Plus, you will learn more about the community you pick as well as scout any future sites as your
business grows!
