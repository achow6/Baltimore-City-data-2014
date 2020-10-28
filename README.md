# Looking at How Different Parent Variables Can Affect Children's Education in Baltimore City

Studies in the United Kingdom have shown that [environmental/parental factors can have a large impact on children's education](https://www.iser.essex.ac.uk/files/iser_working_papers/2010-16.pdf). This project serves to determine if environmental factors, such as income, crime rate, and racial demographics, can be related to children's educations in Baltimore. This project also looks at how different Baltimore neighborhoods can be clustered based on these environmental factors and education outcomes.

Baltimore City is generally characterized by the ["Black Butterfly"](https://apps.urban.org/features/baltimore-investment-flows/), the butterfly shaped area of the city consisting of segregated black communities, and "White L", the "L" shaped area of the city home to white communities. Studies have shown that underpriviledged areas in Baltimore are most typically inhabited by [African American populations ("Black Butterfly" with low household income and high incarceration rates](http://www.justicepolicy.org/news/10376). Although Baltimore receives more public school funding than the [national average](https://www.census.gov/newsroom/press-releases/2020/school-system-finances.html#:~:text=MAY%2011%2C%202020%20%E2%80%94The%20amount,released%20today%20by%20the%20U.S.) and is a hub for higher education, [K-12 schools are not delivering great results](https://foxbaltimore.com/news/project-baltimore/city-teacher-email-school-more-concerned-about-quotas-than-education). 

Considering the reports from the United Kingdom, this project uses Baltimore Vital Signs Open Data to determine if there is a relationship between environmental factors, such as percent of African Americans per neighborhood, violent crime rate per 1,000, and percentage of family households living under the poverty line, and children's education, measured through percent passing Maryland School Assessment (MSA) reading and math.

# Business Question
How different parent variables, such as poverty rate, crime rate, and racial demographics affect children’s education in Baltimore City? 

# Data Question
1. Cluster Analysis: How can different neighborhoods be grouped based on percent of African Americans per neighborhood, violent crime rate per 1,000, percentage of family households living under the poverty line, and percent passing Maryland School Assessment (MSA) reading and math?
2. Pivot Table/Histogram: What are the average percentage of African Americans, violent crime rate, and percentage of households living under the poverty line in each quartile of percentage of students passing MSA reading and math (top 25%, top middle, bottom middle, and bottom 25%)? Do variables show a unique trend in each quartile?
3. Multiple Linear Regression: Can we predict 8th grade students’ percentage of passing MSA reading and math based on percentage of African Americans per neighborhood, violent crimet rate per 1,000, and percentage of family households living under the poverty line? Simply, how well do these different parent variables explain the percentage passing MSA reading and math?


# Data Source
**Vital Signs Open Data:** This is a collection of publically available data on Baltimore City neighborhoods to paint a picture of each neighborhood's quality of life and overall health. It includes information and datasets on census demographics, housing and community development, children and family health, crime and safety, workforce and economic development, arts and culture, education and youth, and sustainability. Data from 2014 were used in this project.
1. [Violent Crime Rate per 1,000 Residents](https://vital-signs-bniajfi.hub.arcgis.com/datasets/ab03385abf3b4f50aec0b090caa8877a_0?geometry=-76.908%2C39.192%2C-76.333%2C39.378) - This dataset measures the number of violent crimes (homicide, rape, aggravated assault, robbery) reported to the Baltimore Police Department per 1,000 Baltimore residents.
2. [Percentage of 8th Grade Students Passing MSA Math](https://vital-signs-bniajfi.hub.arcgis.com/datasets/71df589c744440e49d67335124ee7c6b_0) - This dataset shows the percentage of Baltimore City students per neighborhood passing Maryland School Assessment exams in math. In MSA exams, there are three grades: advanced, proficient, or having basic knowledge. Advanced or proficient were considered passing grades.
3. [Percentage of 8th Grade Students Passing MSA Reading](https://vital-signs-bniajfi.hub.arcgis.com/datasets/e33449861c954ffcbb47c3efc585c181_0) - This dataset shows the percentage of Baltimore City students per neighborhood passing Maryland School Assessment exams in reading. In MSA exams, there are three grades: advanced, proficient, or having basic knowledge. Advanced or proficient were considered passing grades.
4. [Median Household Income](https://vital-signs-bniajfi.hub.arcgis.com/datasets/8613366cfbc7447a9efd9123604c65c1_0) - This dataset shows median household in each Baltimore neighborhood.
5. [Percent of Residents - Black/African-American (Non-Hispanic)](https://vital-signs-bniajfi.hub.arcgis.com/datasets/3b27c89864714b109bde250c628d73e5_0) - This dataset shows the percentage of Baltimore City residents who identify as non-Hispanic Black/African American per neighborhood.

# Data Answer

**Cluster Analysis**

![alt text](https://github.com/achow6/Baltimore-City-data-2014/blob/main/Scatterplot.png)

During the data analysis process, scatterplots were created for each pairing of variables (i.e. comparing "Pct African American" and "Violence per 1,000" or "Pct 8th Math" and "Pct Living Under Poverty Line") as an intial investigation for the cluster analysis. This is an example of one of the scatterplot comparisons. It compares percent of African Americans living in a neighborhood to percent of 8th graders passing MSA math in the same neighborhood. All of the scatterplots generally exhibited three clusters similar to the ones in this scatterplot, so a three-cluster analysis was conducted. It is also interesting to note that there appears to be a negative relationship between percent of African Americans and percent of 8th graders passing MSA math.

![alt text](https://github.com/achow6/Baltimore-City-data-2014/blob/main/Cluster.png)

This is the Solver output for the three-cluster analysis.

The first cluster is represented by neighborhoods like Midtown. The percent of 8th graders passing MSA math is below the overall average, but the percent of 8th graders passing MSA reading is above the overall average. There is a low percentage of African Americans, below average violence rate, and most residents are living above the poverty line.

The second cluster is represented by neighborhoods like Forest Park/Walbrook. The percent of 8th graders passing MSA math and reading are slightly below the overall average. There is a high percentage of African American residents, below average violence rates, and residents are generally living below the poverty line.

The third cluster is represented by neighborhoods like Cedonia/Frankford. The percent of 8th graders passing MSA math and reading are slightly below the overall average. There is an above average percentage of African American residents (but not as high as the second cluster), below average violence rate (but higher than the first and second clusters), and residents are generally living above the poverty line.

![alt text](https://github.com/achow6/Baltimore-City-data-2014/blob/main/Bar%20Chart.png)

This shows the relative number of neighborhoods in each cluster. In cluster 1, there are 16 neighborhoods. In cluster 2, there are 25 neighborhoods. In cluster 3, there are 14 neighborhoods.

**Multiple Regression**

![alt text](https://github.com/achow6/Baltimore-City-data-2014/blob/main/Screen%20Shot%202020-10-24%20at%2010.09.03%20PM.png)

R^2 value tells us how well the linear regression line predicts the outcome data. Here, the R^2 value is approximately 0.71, which means 71% of the percentage of 8th grade students passing the MSA reading can be explained by different parent factors, including the percentage of household below poverty, crime rate, and the percentage of African American. Even though 29% of the outcome is explained by other variables, 71% indicates that these three factors are pretty good at predicting the outcome. 

![alt text](https://github.com/achow6/Baltimore-City-data-2014/blob/main/Screen%20Shot%202020-10-24%20at%2010.09.15%20PM.png)

R^2 value for MSA Math is about 0.66, which means 66% of the percentage of the outcome is explained by the three factors, including the percentage of household below poverty, violence rate, and percentage of African American, and 34% of the outcome can be explained by other factors. R^2 of 0.66 indicates that these factors are pretty good at predicting the outcome. However, the factors are slightly better at predicting the MSA reading outcome than math outcome given that the R^2 value of reading is 71%.

![alt text](https://github.com/achow6/Baltimore-City-data-2014/blob/main/Screen%20Shot%202020-10-24%20at%2010.17.14%20PM.png)
![alt text](https://github.com/achow6/Baltimore-City-data-2014/blob/main/Screen%20Shot%202020-10-24%20at%2010.17.25%20PM.png)

Next, P-value is the probability that the null hypothesis is true. Here, all the factors have p-values lower than 0.05. Thus, both independent variables are significant in predicting the outcome.
Here, based on the coefficients, the multiple regression line for MSA Reading is **Percentage passing MSA Reading = 83.28 - 0.36 Pct household below poverty - 0.28 Violence rate - 0.2 Pct African American.** Similarly for MSA Math, the multiple regression line is **Percentage passing MSA Math = 60.11 - 0.48 Pct household below poverty - 0.26 Violence rate - 0.21 Pct African American.** You can easily see that all three factors are negatively correlated with the outcome. 

![alt text](https://github.com/achow6/Baltimore-City-data-2014/blob/main/Screen%20Shot%202020-10-24%20at%2010.24.18%20PM.png)

Especially looking at the correlation table, we can find out that all of the factors have negative correlation rate with the percentage of 8th grade passing MSA reading and math. Also, in both math and reading exams, percentage of household below poverty and percentage of African American tend to have higher correlation than violence rate. This indicates that percentage of poverty rate and percentage of African American are doing a better job explaining the outcome than the violence rate and have much more effect on their children’s education.

**Pivot Table/Histogram**

![alt text](https://github.com/achow6/Baltimore-City-data-2014/blob/main/Screen%20Shot%202020-10-24%20at%2010.30.07%20PM.png)
![alt text](https://github.com/achow6/Baltimore-City-data-2014/blob/main/Screen%20Shot%202020-10-24%20at%2010.31.03%20PM.png)

For pivot table analysis, we divided the data on the percentage of 8th grade students passing MSA Reading into 4 quartiles. First quartile is the top 25% of percentage of students passing MSA Reading. Second quartile is the top middle of percentage of students passing MSA Reading, and third quartile and fourth quartile are the bottom middle and bottom 25% respectively. For each quartile, by using pivot table, we calculated the average percentage of housdhold below poverty line, average violence rate, and avergae percenatge of African Americans. 

The histogram tells us that for both MSA reading and math, as the percentage of students passing the exam decreases, all of the factors, including average percentage of household below poverty, average violence rate, and average percentage of African Americans increase except for MSA math's crime rate (crime rate from Q3 to Q4 slightly decreased, but almost the same). Violence rate does relatively remain constant as the quartile changes. Interesting fact is that the average percentage of African American is significantly high for both quartile 3 and 4 for MSA reading and for quartile 2, 3, 4 for MSA math. This shows that children with non-African American parents tend to have higher passing percentage.  

# Business Answer

The cluster analysis suggests that Baltimore City neighborhoods can be grouped into three clusters based on the variables analyzed in this project. In general, the percent of 8th graders passing MSA math in all clusters is below average. This suggests that outliers with high percentages of 8th graders passing MSA math, such as Greater Roland Park/Poplar Hill where almost 89% of students passed MSA math, could be pulling up the average. Further research is needed to determine why there is such a discrepancy between these neighborhoods. The first cluster exhibited an above average percentage of 8th graders passing MSA reading compared to the other two clusters (which were below average). The main distinctions between the first cluster and the other two clusters is its low percentage of African American residents and high percentage of households living above the poverty line. The R^2 value of 71% and 66% for MSA reading and math respectively show that three factors together can explain the outcome pretty well, and negative coefficients of the multiple regression equation indicates the all three factors have negative correlaiton with the outcome. Especially, according to the correlation data, parent's poverty rate and percentage of African Americans, which have a higher absolute value of correlation than crime rate, would have more negative impact on their children's education result. And lastly, pivot table and histogram show that overall, as the percentage of students passing MSA reading and math increase, all three factors decrease except the crime rate for MSA math which decreased slightly in the last quarter. Average percentage of African Americans shows a most drastic increase from quartile 1 to 4 whereas crime rate shows a least drastic change from quartile 1 to 4. This also indicates that children with African-American parents below poverty line are more vulnerable in terms of education. Based on these analyses, although these three factors together can explain the outcome well, high percentage of African American and percentage of households under poverty line negatively effect thier children's education result the most. 

# Recommendation
In Baltimore City, low socioeconomic status of African American parents negatively affect their children’s educational outcome. According to McKinsey & Company, this achievement gap is not just affecting the African American children, their families, and the community but also the country as a whole. Researchers found out that [“the persistence of the educational achievement gap imposes on the United States the economic equivalent of a permanent national recession](https://www.naeyc.org/resources/pubs/yc/may2018/achievement-gap)." Thus, it is really important to come up with solutions that could bring equity in education in Baltimore City.
As mentioned in the beginning, the UK found that [parental and environmental factors affect child education outcomes](https://www.iser.essex.ac.uk/files/iser_working_papers/2010-16.pdf). With that in mind, Baltimore City should consider adult education programs and greater public funding for businesses in neighborhoods with high percentages of African American residents. This will hopefully help raise household income in underpriviledged neighborhoods, and therefore, also decrease the gap between predominantly African American and white neighborhoods.
Several studies found that parental involvement leads to a positive educational outcome, including increased achievement in reading and math exams. Specifically, [research](https://files.eric.ed.gov/fulltext/ED573649.pdf) shows that parental involvement for students of color and those from low household income impacts their children’s education outcome more significantly. An existing program called “Parent Institute for Quality Education (PIQE) is a program that effectively increases parental involvement by teaching and supporting low-income and ethnically-diverse parents. This program trains parents to support their children to be successful in school and create a home learning environment. PIQE also partnered with Baltimore City schools, but it is a “do it yourself” version of training since the [PIQE](https://www.piqe.org/) does not have a presence in Baltimore. Thus, if Baltimore City government can invest in this program to be a stable government supported program for neighborhoods in cluster 2 and 3 (where they had a high African American percentage and high below-poverty rate), this would help supporting the educational development of the children in those areas.

Additional Informaiton Needed for Better Solution:
- Recent data on parent variables to see if parent variables have the same effect on their children’s educational outcome even during the pandemic, where most of the classes are held virtually
- Data on parents' education levels and occupations
- Data on why low-income African American parents lack parental involvement. Is it because they lack financial resources? or because of time constraint? 

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
1. Selected complete data set in Multiple Regression tab and inserted pivot table into a new tab
2. For MSA Reading, I created four pivot tables. For the first pivot table, I used "Percentage 8th Reading" as my filters and CSA2010 as my rows, and "Average of Pct African American", "Average of Pct Household Living Below Poverty", and "Average of Violence Per 1,000" as my values
3. I followed the same steps to create rest of the pivot tables
4. Starting from first pivot table, for my filters, I selected the bottom 14 values, and then for second pivot table, for filters, I selected the next bottom middle 14 values
5. Similarly, for the third pivot table, for filters, I selected top middle 14 values, and for my final pivot table, for filters, I selected the rest of the data
6. Then to create histogram, I copied and pasted all the grand total row of each pivot table on the side and created histogram
7. I followed the same exact steps for MSA Math pivot tables and histogram

**Multiple Linear Regression:**
1. For multiple regression summary, I used the regression function under Data Analysis, and I selected columns of "Pct Household Living Below Poverty", "Violence Per 1,000", and "Pct African American" as my x input values and selected the "MSA 8th Grade Reading" as my y input value
2.	I followed the same steps for MSA Math regression except that my y input value was "MSA 8th Grade Math" column
3.	For MSA reading correlation, I first selected "Pct Household Below Poverty" column and "MSA 8th Grade Reading" column and used the correlation function under Data Analysis. Then I did the same thing for rest of the factors including "Violence Per 1,000" and "Pct African America"
4.	I followed the same steps for MSA Math correlation except that for MSA math correlation, I used "MSA 8th Grade Math" column instead of the reading column




