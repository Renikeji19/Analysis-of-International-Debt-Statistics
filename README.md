# ANALYSIS OF INTERNATIONAL DEBT STATISTICS IN SQL

![image](https://user-images.githubusercontent.com/97131888/193831338-6e0a38e0-00a0-4588-acdc-5b33e7db84cc.png)

## AUTHOR

ADEPEJU SHITTU


## INTRODUCTION 
Just like humans take debts to manage necessities, countries also take debt to manage their economies.
The World Bank provides debt to countries for them to meet needs such as providing infrastructure for citizens to live comfortably.
This project analyzes international debt data collected by The World Bank. 


## PROBLEM QUESTIONS
The dataset contains information about the amount of debt (in USD) owed by developing countries across several categories. 
The analysis provides answers to questions questions such as:

What is the total amount of debt that is owed by the countries listed in the dataset?
Which country owes the maximum amount of debt and what does that amount look like?
What is the average amount of debt owed by countries across different debt indicators?

## THE DATA
The dataset consists of 1 CSV file; with 2,358 rows and 5 coulumns each representing country, country code, indicator name, indicator code and debt.  


![image](https://user-images.githubusercontent.com/97131888/193833495-91a1ef98-dfb3-4e8c-99d3-8e39bb9a4ce1.png)


  


## DATA ANALYSIS
The first line of code connects us to the international_debt database where the table international_debt is residing. 
To inspect the details of the world bank's international debt data, we first SELECT all of the columns from the international_debt table and limit the output to the first ten rows to keep the output clean.

![image](https://user-images.githubusercontent.com/97131888/193852077-8a9cb045-cc37-436c-9786-0776ed7a7b34.png)

Although we see the amount of debt owed by Afghanistan in the different debt indicators from the first ten rows, we cannot determine the number of different countries we have on the table. This is due to repetitions in the country names because a country is most likely to have debt in more than one debt indicator.

To find the number of distinct countries in the table, the DISTINCT clause and the COUNT() function are used in pair on the country_name column, aliasing the resulting column as total_distinct_countries.


![image](https://user-images.githubusercontent.com/97131888/194054108-276ebeee-10af-404c-b538-e8236fb41ff0.png)


The results shows there are a total of 124 countries present on the table.


Next, to understand the areas in which a country can possibly be indebted to, we can investigate the indicator_name (which briefly specifies the purpose of taking the debt) and indicator_code columns (which symbolizes the category of these debts).

To extract the unique debt indicators in the table we Use the DISTINCT clause on the indicator_code column and alias the resulting column as distinct_debt_indicators,
Ordering the results by distinct_debt_indicators.

![image](https://user-images.githubusercontent.com/97131888/194057402-3167a7b1-f9ae-4316-a790-757cde97d9cc.png)


The financial debt of a particular country represents its economic state. We can find out the total amount of debt (in USD) that is owed by the different countries, to give a sense of how the overall economy of the world is holding up.

To find out the total amount of debt as reflected in the table, we use the SUM function on the debt column, then divide it by 1000000 and round the result to 2 decimal places so that the output is fathomable, aliasing the resulting column as total_debt.

![image](https://user-images.githubusercontent.com/97131888/194065131-17e0362b-666a-4a36-8ded-6b9a697ad0fe.png)

The total debt owed by all countries in the table is $3,079,734.49 MM


Now that we have the exact total of the amounts of debt owed by several countries, we can find out the country that owes the highest amount of debt along with the amount. The debt is the sum of different debts owed by a country across several categories. This will help to understand more about the country in terms of its socio-economic scenarios. 

To find out the country owing to the highest debt we select the country_name and debt columns, apply the SUM function on the debt column and alias the column resulted from the summation as total_debt. We then GROUP the results BY country_name and ORDER them BY the new alias total_debt in a descending manner.
LIMIT the number of rows to be one.

![image](https://user-images.githubusercontent.com/97131888/194071149-ab2468a4-d316-4d9e-9394-19f6203a45e3.png)

China has the highest amount of debt.

Furthermore, finding out on an average how much debt a country owes will give us a better sense of the distribution of the amount of debt across different indicators.

To Determine the average amount of debt owed across the categories we select indicator_code aliased as debt_indicator, then select indicator_name and debt.
Applying an aggregate function on the debt column averages out its values. We Group the results by the newly created debt_indicator and already present indicator_name columns. Lastly, we sort the output with respect to the average_debt column in a descending manner and limit the results to ten.

![image](https://user-images.githubusercontent.com/97131888/194078706-ef1fc088-b454-4b20-8baf-b394fe390bf2.png)

The indicator DT.AMT.DLXF.CD tops the chart of average debt. This category includes repayment of long term debts which Countries take on to acquire immediate capital. 
Interestingly, there is a huge difference in the amounts of the indicators after the second one. This indicates that the first two indicators might be the most severe categories in which the countries owe their debts.


To further investigate this, we can find out which country owes the highest amount of debt in the category of long term debts (DT.AMT.DLXF.CD). Since not all the countries suffer from the same kind of economic disturbances, this finding will allow us to understand that particular country's economic condition a bit more specifically.
To discover, the country with the highest amount of principal repayments we select the country_name and indicator_name columns and add a WHERE clause to filter out the maximum debt in DT.AMT.DLXF.CD category.

![image](https://user-images.githubusercontent.com/97131888/194081159-160273d1-cd96-4a70-bb5f-45bf0dfed54b.png)

China has the highest amount of debt in the long-term debt (DT.AMT.DLXF.CD) category. Also, the long-term debt is the topmost category when it comes to the average amount of debt. 

Next we can find the most common indicator in which the countries owe their debt. Selecting the indicator_code column, we apply an aggregate function to count its values and alias the column resulting from the counting as indicator_count. Grouping the results by indicator_code and ordering them first by the newly created indicator_count column then the indicator_code column, both in a descending manner, Limiting the resulting number of rows to 20, would help us find the debt indicator that appears most frequently.

![image](https://user-images.githubusercontent.com/97131888/194089254-86e704e3-bdc1-4bcc-b516-e0c926a75ab2.png)
![image](https://user-images.githubusercontent.com/97131888/194089366-7a2641d6-7032-4f40-a131-d59c1c015ed7.png)

## CONCLUSION
There are a total of six debt indicators in which all the countries listed in the dataset have taken debt. The indicator DT.AMT.DLXF.CD is also shown in the list. This gives a clue that all these countries are suffering from a common economic issue. 


![image](https://user-images.githubusercontent.com/97131888/194091517-b0f47459-5183-4c6c-b477-5e28e8c4c411.png)
![image](https://user-images.githubusercontent.com/97131888/194092390-7ccb6115-832b-4010-9238-0266c5f9b262.png)







