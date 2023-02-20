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
Import the necessary Python libraries: <br/>
<img src="https://i.imgur.com/62TgaWL.png" height="80%" width="80%" alt="Import Libraries"/>
<br />
<br />
Select the disk:  <br/>
<img src="https://i.imgur.com/tcTyMUE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter the number of passes: <br/>
<img src="https://i.imgur.com/nCIbXbg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Confirm your selection:  <br/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Wait for process to complete (may take some time):  <br/>
<img src="https://i.imgur.com/JL945Ga.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Sanitization complete:  <br/>
<img src="https://i.imgur.com/K71yaM2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
