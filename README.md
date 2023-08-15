# Kickstarter
 **Data Description** 
Data was collected from the Kaggle data repository (https://www.kaggle.com/datasets/kemical/kickstarter-projects). The author of the data gathered the data from the crowdfunding web platform known as Kickstarter in the year 2016 and has been updated till the year 2018. Kickstarter is a global crowdfunding platform that is focused on creativity by gathering money from the public to support projects. The dataset was in the comma-separated values (CSV) file format. The data consisted of 378661 observations with 15 feature variables. The features, their data types and descriptions are shown in the table below

**Project Objective** 
Can the state of a project (whether a project will be successful, failed, suspended or cancelled) be predicted using a machine learning model when given enough data about all projects listed on the Kickstarter platform

**Data Preparation and Cleaning**
The data was prepared and cleaned using the R and Python programming languages. The steps taken were as follows:
1.	Importing the data and inspecting dataset characteristics
Libraries necessary for the data cleaning and preparation were loaded using the “library” package in R, and others were imported in Python. Libraries imported included tidyverse, skimr, corrplot and ggplot2 for R and pandas, numpy, seaborn and dython for Python. The dataset was imported into R using the read_csv function into a variable. This function returns the data as a data frame. Summary characteristics of each column were examined with the summary function, and values of the count, min, max, standard
deviation, and percentiles were obtained. The summary results indicate that almost all of the numerical variables had outliers that needed to be addressed. Column names were also inspected. 

2.	Inspecting Data types and Missing values
All columns were inspected for missing values using the is.na () function. The percentage of missing values in each column was calculated.  Only the column usd_pledged had missing values. The number of missing values in this column was 3797, with a percentage of 0.01002744 %.  The columns category, main_category, state, currency and country are categorical variables, but data types were found to be “objects”. These columns were converted to categorical variable types using the as—factor function. 

3.	Data Wangling 
•	The number of missing values of usd_pledged were just a few, and removing them from the data will have no significant effect on the data analysis and modelling for our research question. These missing values were dropped from the data.
•	Eye ball categorical data inspection using the “table” function revealed that the country variable contained some unusual characters, specifically “N, O”, which needed to be fixed as they had corresponding currencies in the currency column. All countries with “N, O” were replaced with their related countries using the currency column as a reference.
•	The datatypes of the timestamp variables, namely deadline and launched, were objects in the original data. We needed to convert these columns to the date datatypes. This conversion used the as.date() function in R.
•	After the conversion of these timestamp columns, a further inspection of these timestamp columns using the min and max functions on these columns (deadline, launched) revealed some outlier dates, such as the ones in “1970”, which needed to be removed. These wrong date entries were removed.
•	Also, the difference between the time projects were launched (launched date) and the project deadlines were calculated and placed in a new column called the launched gap. 
•	< UNK> Some projects are “undefined” in the state column. These projects have zero (0) backers and zero (0) pledges. These values were removed as they will not contribute to the model's success.
•	Live projects were also removed because their outcome is unknown and hence will not contribute to the success of the research question.
•	Also, there are some successful projects with no backers. This part of the data will not contribute to answering the research question, and hence they were all removed. They were 105 observations in total, and therefore they were released. 
•	Inspection of the dataset characteristics at the beginning revealed that some numerical variables could have outliers. A deep analysis of the numerical columns using boxplot showed that backers, usd_goal_real, and usd_pledged variables have outliers. These outliers were duly removed. 
•	Columns deemed non-essential and may not contribute to the building of the model were dropped. These columns included the ID, name, goal, and USD. Pledged.
•	Columns usd_pledged_real and usd_goal_real were also renamed to usd_pledged and usd_goal respectively
•	The cleaned data was finally saved as comma-separated values (CSV) file and used in the next step, which is the exploratory data analysis 
