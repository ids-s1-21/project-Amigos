# data
Place data file(s) in this folder.

Then, include codebooks (variables, and their descriptions) for your data file(s)
using the following format.

## Loans

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

Starting off, by looking at our data frame, we decided that it would be suitable, given the fact that it included categorical data ("risk_flag" which is binary and "Married.Single"), continuous data ("Income") and discrete numeric data ("Experience"). 
The most important variable is undoubtedly "risk_flag", which is the indicator whether a person has or hasn't defaulted on a loan. All of these factors can be used to draw a conclusion indicating whether they affect loan defaulting, at a large extent or not.
Our investigation was focused on finding out whether a person is more or less likely to default on their loan depending several aspects of their life.
To assess our question we decided to work with Marital Status, Experience and Income. 
In our proposal we wanted to see first if there was a positive relationship between Age and Income, however, upon testing the data we noticed that there was no correlation. Despite this being unusual, we thought that it was mainly due to the fact that the Indian economy is mostly based on the primary and secondary sector, so Incomes don't tend to change a lot with Age. 
Firstly, we needed to create a new data frame, called "Loans_2", where we used the mutate function to make the "risk_flag" variable discrete, because it appeared as continuous when loading the data, despite getting values 0 or 1. This was also an opportunity to change the labels, since "0" and "1" weren't a clear indicator about the context of the data. As a result, "0" was changed to "No" (Didn't default on the loan) and "1" to Yes (Defaulted on the loan).
Furthermore, from our tests we observed that for clients with a low income, despite their loan defaulting status, there was no consistency or a visible relationship with experience. Thus we decided to create another data frame, called "Loans_3", where we filtered out all observations with a lower than the median income, in order to work with a more evenly distributed data frame.
In this new data frame we also split our data into training and testing data, where the training data represented 80% of the data frame and the testing data represented the remaining 20%. This was done because the testing data already contains known values for loan defaulting and it makes it easy to determine whether the model's estimations are correct. The training data was used to construct our visualisations.
In order to assess our investigation we first needed some background information on our variables. So, we plotted a graph of experience vs median (high) income per year of experience, faceted for married and single clients. This visualisation helped as determine any relationships between income and experience and whether it was affected by the clients' marital status.
After obtaining this information, and concluding that income remains relatively steady throughout a 20 year period of experience, we decided to plot a graph to see the proportion of high income earners defaulting on a loan or not. It was clear that the large majority did not default on their loans, which was something that we expected since they are wealthier.
Advancing, once again with reference to our first graph, we decided to further explore the effect of a client's marital status on the above graph and, by extension, to the probability of defaulting on his loan. To accomplish this, we faceted the previous graph by marital status as well. We observed that married clients have a larger proportion of loan defaulting compared to single ones. Thus, we concluded that married clients are less likely to repay their loans than single clients.
Additionally, to cross reference our conclusions, we created logistic regressions for both of the previous graphs. Our code suggests that both of the variables do affect loan defaulting (risk_flag).
Concluding, we wanted to test how accurate our test data is in predicting loan defaulting, given the above variables. This was done by creating a recipe, a workflow and fitting the train data onto "Loans_fit". This was used in "Loans_pred" which ultimately helped us assess the predictive power of the model onto the test data. Finally, we plotted an ROC curve, where we observed that the curve was very close to y=x. This indicates that our model is randomly guessing future cases. Upon further investigation, using the mutate and if_else functions, we observed that there was no prediction of loan defaulting exceeding the threshold percentage of 50%. This is probably due to the fact that our model does not predict loan defaulting, as it assumes every future client will be able to repay their loan and those who will not be able to are not granted the loan to begin with.
Although our data was able to back up the initial predicted relationships, the loans data is imbalanced and there are limitations that require more advanced techniques to correct.