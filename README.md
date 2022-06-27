## Executive Summary

The purpose of this project is to provide exploratory data analysis to better understand trends in opioid prescription rates that may exist among the different distinguishable characteristics of providers included in the data.

### The Big Picture

In 2017, the US Department of Health and Human Services (HHS) declared a public health emergency to combat the growing opioid crises in the US and the resulting strain. In 2016, more than 42,000 deaths were contributed to opioid overdoses. According to the most recent figures provides by HHS, 1.6 million American had an opioid use disorder in the past year, 10.1 million people misused prescriptions, and more than 48,000 deaths were attributed to overdose on synthetic opioids other than methadone (more on terms and definitions by [HHS](https://www.hhs.gov/opioids/about-the-epidemic/index.html))

This problem is also associated with an overall drug misuse problem in the country. The National Survey on Drug Use and Health (2019) found that 745,000 people used heroin in the past year, 50,000 used heroin for the first time with around 14,500 deaths resulting from heroin overdose. 

According to the [National Institute on Drug Abuse](https://nida.nih.gov/publications/research-reports/prescription-opioids-heroin/prescription-opioid-use-risk-factor-heroin-use), there is a correlation between misuse of opioids and heroin usage. This is because heroin is classified as an *[opiate](https://www.cdc.gov/opioids/basics/terms.html#:~:text=%E2%80%9COpiates%E2%80%9D%20vs.,%2C%20semisynthetic%2C%20and%20synthetic%20opioids.)*, a class of natural opioid, that has induce similar bodily reactions and provide similar potential for abuse as synthetically processed opioids (such as those prescribed by a doctor).

In this analysis, I develop models using classification methods to look at trends involving gender of the provider, and I use regression methods to look at trends in number of prescriptions written. I created a variable called `summ_var` to use for modeling prescribing rates of opioids that is the sum of all opioid prescriptions from a single provider. The original data only had total prescriptions written for each different drug in the data which also included many non-opioid medications, so the `summ_var` variable was helpful to provide insight from a broader scope. 

### The Data

The data sets used in this analysis were found from [Kaggle](https://www.kaggle.com/datasets/apryor6/us-opiate-prescriptions?select=prescriber-info.csv), sourced from [CMS.gov](https://www.cms.gov/Research-Statistics-Data-and-Systems/Statistics-Trends-and-Reports/Medicare-Provider-Charge-Data/Part-D-Prescriber) (Centers for Medicare & Medicaid Services)

One challenge working with this data was regarding the formatting. There were thousands of spelling inconsistencies for different providers specialties/credentials that resulted in some observations being lost when cleaning the data.

The year of the data’s collection being only 2014 also presented some issues. While there is some insight we can gain by examining characteristics of providers from a single year, it would be difficult to understand how the trends have changed over time and how much can be explained by new policies (e.g. Prescription Drug Monitoring Programs) or developments in healthcare (e.g. technology; drug alternatives).

A time series panel of data with these same variables for multiple years would provide better insight into things considered worth knowing from a healthcare or policy perspective. Pulling in additional sources of data alone with the time panel component would also help to enrich the insight from this analysis. 

### Methods

Forward and backward stepwise selection was used to optimally select variables to be included in regression. For the classification models, variable importance and selection was algorithmically determined. Random Forest was also used in attempt to predict the `summ_var` variable. Binned grouping of means that are represented by different factor levels was able to convert the regression problem into a classification problem to provide a more generalizable prediction model for prescribing rates. 

### Results and Conclusions

MSE was used to assess accuracy when predicting the numeric outcomes. The out-of-sample MSE for the multivariate regression model was 109.4 when predicting the `summ_var` variable (with training MSE of 103.6). While it would be ideal that this value is closer to zero, it doesn’t nicely indicate that the model performed poorly since the standard deviation was above 220 for training/testing and the residuals were evenly distributed.

Accuracy was an important measurement for the classification models. The support vector machine model performed the best out-of-sample when predicting gender with an accuracy of 77.37%. A random forest was used when predicting the `summ_var`  variable as a classification problem predicting different levels determined by  bins of means. When the number of bins was set to `n = 30` the accuracy was 61.4%, but became more accurate as the number of bins used decreased. 

Something that limited performance on this project was the computational capability of my computer. The rendering of the final HTML took a while to process since I didn’t I didn’t utilize parallelization in the analysis. It also would have helpful to have looked for a time series panel for this data as well as additional sources. Not only would this have enriched my findings, but also could provide insight in other trends, such as heroin usage/overdose rates when compared to opioid prescription rates over time.
