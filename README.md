## Executive Summary

The purpose of this project is to provide exploratory data analysis to better understand trends in opioid prescription rates and trends that may exist among the different distinguishable characteritics of providers included in the data.

## The Big Picture

After reviewing the data and existing literature on the topic, 

I construed classification methods were used to look at trends in the `gender` variable and regression modeling to predict the modified variable `sum_var` (representing the total number of opioiod perciption written by a provider in the year 2014).

## The Data

The data sets were downloaded from [Kaggle](https://www.kaggle.com/datasets/apryor6/us-opiate-prescriptions?select=prescriber-info.csv), sourced from [CMS.gov](https://www.cms.gov/Research-Statistics-Data-and-Systems/Statistics-Trends-and-Reports/Medicare-Provider-Charge-Data/Part-D-Prescriber) (Centers for Medicare & Medicaid Services)

## Challenges

One challenge I faced working with this data was regarding its formatting. There were thousands of spelling inconsistencies for different providers specialties/credentials that resulted in some observations being lost when cleaning the data. The year of the data’s sourcing also presented some issues. At the time (2014), not all states had Presciprtion Drug Monitoring Programs (PDMP). While there is some insight we can gain regarding how these trends looked in 2014, it would be difficult to understand how the trends is/will be shaped over time since additional policies across states have been implemented in the meantime.

## Methods

I used forward and backward stepwise selection was used to determine which variables would be ideal to include in the regression model. For the classification models, the optimal decision was plotted given the hyperparameters and tuning. Random Forest was also used in attempting classify the `summ_var` variable into binned groups with means represented as a factor variable. 

##	Results and Conclusions

A variety of different measurement were used to assess the strengthen and out-of-sample accuracy of our data. Accuracy was an important measurement to consider for the classification models and the MSE was important for the regression modeling. Multiple algorithms were run to determine which variables were explaining the trends we found in the data, but many of the same variables were still predicted to be highly significant for explaning the change in the outcome variable regardless of the model. 

Something that limited performance on this project was the computational capability of my computer. The rendering of the final HTML took a while to process since I didn’t I didn’t utilize parellization in this project. It also would have been nice to obtain data from more than one year as aforementions in order to understand a time-dimension of the trends that we see in this analysis.
