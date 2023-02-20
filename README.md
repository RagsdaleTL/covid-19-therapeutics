<h1>Python Coding Sample</h1>

<h2>COVID-19 Therapeutic Availability</h2>



<h2>Description</h2>
This project consists of a simple descriptive analysis regarding availability of therapeutic drugs for coronavirus disease 2019 (COVID-19) in the Commonwealth of Virginia. The project makes use of a public dataset from the US Department of Health and Human Services, as well as a geographic shapefile from the Virginia Geographic Information Network. This coding exercise covers importing, cleaning, and reshaping data; joining datasets from different sources; and descriptive visualizations in the form of bar charts and chloropleth maps.
<br />


<h2>Skills</h2>

- <b>Python programming language</b> 
- <b>Data Visualizations</b>

<h2>Environments Used</h2>

- <b>Windows 11</b>
- <b>Jupyter Notebook</b>

<h2>Python Libraries</h2>

- <b>pandas</b>
- <b>geopandas</b>
- <b>numpy</b>
- <b>matplotlib</b>
- <b>requests</b>

<h2>Data Preparation:</h2>

The United States Department of Health and Human Services (HHS) has compiled a locator tool for the public which lists providers of COVID-19 therapeutic drugs and reports the availability of different kinds of these drugs. This data table is available via the __[HealthData.gov API](https://healthdata.gov/Health/COVID-19-Public-Therapeutic-Locator/rxn6-qnx8)__. For this analysis, we will use the `requests` library to import a subset of the data containing only information for Virginia.

For more information on the dataset, click the following link: __[https://healthdata.gov/Health/COVID-19-Public-Therapeutic-Locator/rxn6-qnx8](https://healthdata.gov/Health/COVID-19-Public-Therapeutic-Locator/rxn6-qnx8)__

<p align="center">
Import the necessary Python libraries:<br/>
<img src="https://imgur.com/jEXgz6X.png" height="80%" width="80%" alt="Import Libraries"/>
<br />
<br />
Import the data:  <br/>
<img src="https://imgur.com/xVwBnFV.png" height="80%" width="80%" alt="Data Import"/>
<br />
<br />
Preview of the datafile: <br/>
<img src="https://imgur.com/vXrxsC5.png" height="80%" width="80%" alt="Therapeutics describe"/>
<br />
<br />
  
At the time of writing (Feb 2023), this dataset contains 77 entries with the __"provider_status"__ variable listed as "UNKNOWN INVENTORY". We are only concerned with "ACTIVE" providers, so any other values for this variable will need to be filtered out. Additionally, we will convert the __"courses_available"__ (available doses) and __"zip"__ (postal code) columns to integer format.
<br/>

<p align="center">
Confirm your selection:  <br/>
<img src="https://imgur.com/rSkQVwW.png" height="80%" width="80%" alt="Subset ACTIVE"/>
<br />
<br />
Reformat the data to integers: <br/>
<img src="https://imgur.com/9tbRdXa.png" height="80%" width="80%" alt="Reformat"/>
<br />
<br />
Notice the two columns on the right: <br/>
<img src="https://imgur.com/wvJ0BPR.png" height="80%" width="80%" alt="Reformat result"/>
<br />
<br />

<h2>Descriptive Statistics</h2>

Now we will calculate the number of courses available for the four labels of medicine in this dataset: _Paxlovid&#8482;_, _renal Paxlovid&#8482;_, _Lagevrio&#8482;_, and _remdesivir_. We will visualize the result in a bar chart.

<p align="center">
Create a list of the four drugs exactly as they appear in the dataset:  <br/>
<img src="https://imgur.com/Ba7jXJP.png" height="80%" width="80%" alt="List of 4 drug labels"/>
<br />
<br />
Calculate the totals with a for loop:  <br/>
<img src="https://imgur.com/m8gMCjo.png" height="80%" width="80%" alt="for loop"/>
<br />
<br />

These are the total counts by drug label:
 -  <b>Paxlovid&#8482;: 37,493</b>
 -  <b>Lagevrio&#8482;: 35,664</b>
 -  <b>Renal Paxlovid&#8482;: 9,196</b>
 -  <b>Remdesivir: 0</b>
  
Now to put it in a bar chart:

<p align="center">
Code to create the bar chart: <br/>
<img src="https://imgur.com/JDhtbW1.png" height="80%" width="80%" alt="Bar chart code"/>
<br />
<br />
<img src="https://imgur.com/mV5izmq.png" height="80%" width="80%" alt="Bar chart out"/>
<br/>
<br/>

<h2>Geographic Analysis</h2>
The HHS dataset contains geocoded data about therapeutic drug providers in the form of ZIP codes and latitude-longitude coordinates. In this section, we will visualize the prevalence of COVID-19 therapeutics across ZIP codes using a chloropleth (aka color scale) map.

A geographic json shapefile of Virginia ZIP codes is available from the Virginia Geographic Information Network (VGIN) via the __[ArcGIS website](https://hub.arcgis.com/datasets/VGIN::virginia-zip-codes/about)__. At the time of writing, I was unable to connect to the datafile via API, as I did with the HHS dataset. In the meantime, the geojson file can be downloaded at this link: __[https://hub.arcgis.com/datasets/VGIN::virginia-zip-codes/about](https://hub.arcgis.com/datasets/VGIN::virginia-zip-codes/about)__.

<p align="center">
Read in the geojson file:  <br/>
<img src="https://imgur.com/GlZiqEz.png" height="80%" width="80%" alt="GEOJSON readin"/>
<br />
<br />
Subset to remove bordering North Carolina counties:  <br/>
<img src="https://imgur.com/DPlrNdq.png" height="80%" width="80%" alt="VA subset"/>
<br />
<br />
Pivot the HHS data to fit the new dataset:  <br/>
<img src="https://imgur.com/kL9eyx4.png" height="80%" width="80%" alt="Pivot table"/>
<br />
<br />
Perform a left-join:  <br/>
<img src="https://imgur.com/MfK6gda.png" height="80%" width="80%" alt="Leftjoin 1"/>
<br />
<br />
Create the chloropleth map:  <br/>
<img src="https://imgur.com/x0hSumZ.png" height="80%" width="80%" alt="Chloropleth code 1"/>
<br />
<br />
<img src="https://imgur.com/hAg2Hw9.png" height="80%" width="80%" alt="Map result 1"/>
<br />
<br />

<h3>Unfortunately, this map is not a very helpful visual.</h3>
Suffolk, VA seems to be skewing the data to the point that the viewer cannot see a difference among the other counties. Let's investigate:
<br />
<br />

<p align="center">
Sort the ZIP codes to find outliers: <br/>
<img src="https://imgur.com/2kxdfc5.png" height="80%" width="80%" alt="Sort for outliers"/>
<br />
<br />

As the first map indicated, there are two unusually high outliers in the dataset: ZIP codes 23434 (Suffolk) and 23060 (Glen Allen). For the sake of simple exploration, I will _temporarily_ remove these two outliers to see how the map visualization changes.

<p align="center">
Create a subset with courses less than or equal to 2,000: <br/>
<img src="https://imgur.com/DhRBspc.png" height="80%" width="80%" alt="Subset to 2000 or less"/>
<br/>
<br/>
Create a second chloropleth map: <br/>
<img src="https://imgur.com/EYqVU0e.png" height="80%" width="80%" alt="Chloropleth code 2"/>
<br/>
<br/>
<img src="https://imgur.com/x2kId8L.png" height="80%" width="80%" alt="Chloropleth map 2"/>

This map shows the differences among localities more clearly (except for the two ZIP codes that were filtered out). As one might expect, there appear to be larger amounts of therapeutics near more highly populated areas, namely Richmond, Virginia Beach, and the D.C. metro area.
<br/>
<br/>
  
<h2>Thank you for reading and following along!</h2>
Stay tuned for a possible continuation in the near future. Please reach out if you have any questions or constructive comments.
