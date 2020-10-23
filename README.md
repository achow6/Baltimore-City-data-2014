# Looking at How Different Parent Variables Can Affect Children's Education in Baltimore City

Studies in the United Kingdom have shown that [environmental/parental factors can have a large impact on children's education](https://www.iser.essex.ac.uk/files/iser_working_papers/2010-16.pdf). This project serves to determine if environmental factors, such as income, crime rate, and racial demographics, can be related to children's educations in Baltimore. This project also looks at how different Baltimore neighborhoods can be clustered based on these environmental factors and education outcomes.

Baltimore City is generally characterized by the ["Black Butterfly"](https://apps.urban.org/features/baltimore-investment-flows/), the butterfly shaped area of the city consisting of segregated black communities, and "White L", the "L" shaped area of the city home to white communities. Studies have shown that underpriviledged areas in Baltimore are most typically inhabited by [African American populations ("Black Butterfly" with low household income and high incarceration rates](http://www.justicepolicy.org/news/10376). Although Baltimore receives more public school funding than the [national average](https://www.census.gov/newsroom/press-releases/2020/school-system-finances.html#:~:text=MAY%2011%2C%202020%20%E2%80%94The%20amount,released%20today%20by%20the%20U.S.) and is a hub for higher education, [K-12 schools are not delivering great results](https://foxbaltimore.com/news/project-baltimore/city-teacher-email-school-more-concerned-about-quotas-than-education). 

Considering the reports from the United Kingdom, this project uses Baltimore Vital Signs Open Data to determine if there is a relationship between environmental factors, such as percent of African Americans per neighborhood, violent crime rate per 1,000, and percentage of family households living under the poverty line, and children's education, measured through percent passing Maryland School Assessment (MSA) reading and math.

# Business Question

# Data Question
1. Cluster Analysis: How can different neighborhoods be grouped based on percent of African Americans per neighborhood, violent crime rate per 1,000, percentage of family households living under the poverty line, and percent passing Maryland School Assessment (MSA) reading and math?
2. Pivot Table/Histogram:
3. Multiple Linear Regression:


# Data Source
**Vital Signs Open Data:** This is a collection of publically available data on Baltimore City neighborhoods to paint a picture of each neighborhood's quality of life and overall health. It includes information and datasets on census demographics, housing and community development, children and family health, crime and safety, workforce and economic development, arts and culture, education and youth, and sustainability. Data from 2014 were used in this project.
1. [Violent Crime Rate per 1,000 Residents](https://vital-signs-bniajfi.hub.arcgis.com/datasets/ab03385abf3b4f50aec0b090caa8877a_0?geometry=-76.908%2C39.192%2C-76.333%2C39.378) - This dataset measures the number of violent crimes (homicide, rape, aggravated assault, robbery) reported to the Baltimore Police Department per 1,000 Baltimore residents.
2. [Percentage of 8th Grade Students Passing MSA Math](https://vital-signs-bniajfi.hub.arcgis.com/datasets/71df589c744440e49d67335124ee7c6b_0) - This dataset shows the percentage of Baltimore City students per neighborhood passing Maryland School Assessment exams in math. In MSA exams, there are three grades: advanced, proficient, or having basic knowledge. Advanced or proficient were considered passing grades.
3. [Percentage of 8th Grade Students Passing MSA Reading](https://vital-signs-bniajfi.hub.arcgis.com/datasets/e33449861c954ffcbb47c3efc585c181_0) - This dataset shows the percentage of Baltimore City students per neighborhood passing Maryland School Assessment exams in reading. In MSA exams, there are three grades: advanced, proficient, or having basic knowledge. Advanced or proficient were considered passing grades.
4. [Median Household Income](https://vital-signs-bniajfi.hub.arcgis.com/datasets/8613366cfbc7447a9efd9123604c65c1_0) - This dataset shows median household in each Baltimore neighborhood.
5. [Percent of Residents - Black/African-American (Non-Hispanic)](https://vital-signs-bniajfi.hub.arcgis.com/datasets/3b27c89864714b109bde250c628d73e5_0) - This dataset shows the percentage of Baltimore City residents who identify as non-Hispanic Black/African American per neighborhood.

# Data Answer
![alt text](https://github.com/achow6/Baltimore-City-data-2014/blob/main/Scatterplot.png)

During the data analysis process, scatterplots were created for each pairing of variables (i.e. comparing "Pct African American" and "Violence per 1,000" or "Pct 8th Math" and "Pct Living Under Poverty Line") as an intial investigation for the cluster analysis. This is an example of one of the scatterplot comparisons. It compares percent of African Americans living in a neighborhood to percent of 8th graders passing MSA math in the same neighborhood. All of the scatterplots generally exhibited three clusters similar to the ones in this scatterplot, so a three-cluster analysis was conducted. It is also interesting to note that there appears to be a negative relationship between percent of African Americans and percent of 8th graders passing MSA math.

![alt text](https://github.com/achow6/Baltimore-City-data-2014/blob/main/Cluster.png)

This is the Solver output for the three-cluster analysis.

The first cluster is represented by neighborhoods like Midtown. The percent of 8th graders passing MSA math is below the overall average, but the percent of 8th graders passing MSA reading is above the overall average. There is a low percentage of African Americans, below average violence rate, and most residents are living above the poverty line.

The second cluster is represented by neighborhoods like Forest Park/Walbrook. The percent of 8th graders passing MSA math and reading are slightly below the overall average. There is a high percentage of African American residents, below average violence rates, and residents are generally living below the poverty line.

The third cluster is represented by neighborhoods like Cedonia/Frankford. The percent of 8th graders passing MSA math and reading are slightly below the overall average. There is an above average percentage of African American residents (but not as high as the second cluster), below average violence rate (but higher than the first and second clusters), and residents are generally living above the poverty line.

![alt text](https://github.com/achow6/Baltimore-City-data-2014/blob/main/Bar%20Chart.png)

This shows the relative number of neighborhoods in each cluster. In cluster 1, there are 16 neighborhoods. In cluster 2, there are 25 neighborhoods. In cluster 3, there are 14 neighborhoods.

# Business Answer

The cluster analysis suggests that Baltimore City neighborhoods can be grouped into three clusters based on the variables analyzed in this project. In general, the percent of 8th graders passing MSA math in all clusters is below average. This suggests that outliers with high percentages of 8th graders passing MSA math, such as Greater Roland Park/Poplar Hill where almost 89% of students passed MSA math, could be pulling up the average. Further research is needed to determine why there is such a discrepancy between these neighborhoods. The first cluster exhibited an above average percentage of 8th graders passing MSA reading compared to the other two clusters (which were below average). The main distinctions between the first cluster and the other two clusters is its low percentage of African American residents and high percentage of households living above the poverty line.

# Step-by-Step Data Analysis
**Data Cleaning:**
1. Datasets were downloaded from Vital Signs Open Data
2. Data from 2014 were compiled into one dataset using VLOOKUP

**Cluster Analysis:**
1. Scatterplots comparing two variables at a time were created to visually determine approximately how many clusters exist in the dataset
2. Mean and standard deviation of the independent variables ("Pct 8th Math", "Pct 8th Reading",	"Pct African American",	"Violence per 1,000",	"Pct Living Under Poverty Line") using the AVERAGE and STDEV functions
3. "Pct 8th Math", "Pct 8th Reading",	"Pct African American",	"Violence per 1,000",	"Pct Living Under Poverty Line" were normalized using the STANDARDIZE function and put into the "z Pct 8th Math", "z Pct 8th Reading",	"z Pct African American",	"z Violence per 1,000",	"z Pct Living Under Poverty Line" columns
4. An anchor table was created using the VLOOKUP function, which contained Anchor Number, "OBJECTID", "Neighborhood", "z Pct 8th Math", "z Pct 8th Reading",	"z Pct African American",	"z Violence per 1,000",	"z Pct Living Under Poverty Line"
5. SUMXMY2 function was used to calculate the distance squared between the first, second, and third points
6. Minimum distance squared and sum of minimum distance squared were calculated for each row using the MIN and SUM functions
7. MATCH function was then used to calculate which row of z scores is associated with which anchor
8. Excel Solver was used to evaluate optimal clusters on the anchor table based on the minimum distance to each of the cluster nodes
9. A bar chart was created to visually show how many neighborhoods are in each cluster

**Histogram/Pivot Table:**

**Multiple Linear Regression:**




