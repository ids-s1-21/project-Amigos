# data
Place data file(s) in this folder.

Then, include codebooks (variables, and their descriptions) for your data file(s)
using the following format.

## name of data file

- `ID`: ID of the person 
- `risk_flag`: Whether the person has defaulted on a loan or not
- `Income`: Yearly income of the person ranging from 10300 to 1000000 in Rupees
- `Age`: Age of the person
- `Experience`: Professional Experience of the person in years
- `Married/Single`: Whether the person is married or single
- `House_Ownership`: Whether the person owns or rents or neither
- `Car_Ownership`: Whether the person owns a car or not
- `Profession`: The profession of the person
- `CITY`: The city of residence of the person
- `STATE`: The state of residence of the person

Dimensions: 28000x13

Write-up:

Starting off, by looking at the above data, we decided that it would be suitable given the fact that it included categorical data ("risk_flag" which is binary and "Married.Single"), continuous data ("Income") and discrete numeric data ("Experience"). 
The most important variable is undoubtedly "risk_flag", which is the indicator whether a person has or hasn't defaulted on a loan. All of these factors can be used to draw a conclusion indicating whether they affect loan defaulting, at a large extent or not.
Our investigation was focused on finding out whether a person is more or less likely to default on their loan depending several aspects of their life.
To assess our question we decided to work with Marital Status, Experience and Income. 
In our proposal we wanted to see first if there was a positive relationship between Age and Income, however, upon testing the data we noticed that there was no correlation. Despite this being unusual, we thought that it was mainly due to the fact that the Indian economy is mostly based on the primary and secondary sector, so Incomes don't tend to change a lot with Age. 
Firstly, we needed to create a new dataset called "Loans_2", where we used the mutate function to make the "risk_flag" variable discrete, because it appeared as continuous when loading the data, despite getting values 0 or 1. This was also an opportunity to change the labels, since "0" and "1" weren't a clear indicator about the context of the data. As a result, "0" was changed to "No" (Didn't default on the loan) and "1" to Yes (Defaulted on the loan).
Furthermore, from our tests we observed that vast majority of the 

