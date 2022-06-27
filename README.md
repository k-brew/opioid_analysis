## Executive Summary

The purpose of this project is to provide exploratory data analysis to better understand trends in opioid prescription rates that may exist among the different distinguishable characteristics of providers included in the data. There are adverse effects on health and finance resulting from higher national rates of drug abuse, including of drugs that are obtained through legal means (i.e. prescribed by a doctor). Over a million of Americans have misused opioids in the past year.

In this analysis, models were constructed to predict total number of opioid prescriptions written based on distinguishable characteries of a providers. Additional models were constructed to predict the gender of a provider based on provider characteristics. The best performing models were able to predict gender with an accuracy of 77.37 percent and predicted total opioid prescriptions with MSE of 109.4 (with standard deviation of 224).

### The Big Picture

In 2017, the US Department of Health and Human Services (HHS) decalared a public health emergency to combat the growing opioid crises in the US and the resulting strain. In 2016, more than 42000 deaths were contributed to opioid overdoses. According to the most recent figures provides by HHS, 1.6 million American had an opioiod use disoreder in the past year, 10.1 million people misued presciprtion, and more than 48,000 deaths were attributed to overdose on synthetic opiotoids other than methadone ([source](https://www.hhs.gov/opioids/about-the-epidemic/index.html))

This problem is also assoicated with an overall drug misuse problem in the country. The National Survey on Drug Use and Health (2019) found that 745,000 eople used heroid in the past year, 50,000 used heroin for the first time with around 14,500 deaths resulting from herioin oversode. 

According to the [National Insitute on Druge Abuse](https://nida.nih.gov/publications/research-reports/prescription-opioids-heroin/prescription-opioid-use-risk-factor-heroin-use), there is a correlation between misuse of opiooids and heoin usage. This is becuase hearoin is classified as an *[opiate](https://www.cdc.gov/opioids/basics/terms.html#:~:text=%E2%80%9COpiates%E2%80%9D%20vs.,%2C%20semisynthetic%2C%20and%20synthetic%20opioids.)*, a class of natural opioid, that has a similiar psyicological effects and potential for abuse as syntethically process opioiods (such as those prescirbed by a doctor).

In this analysis, I develop models using classification methods to look at trends involving the `gender` of the provider, and I use regression methods to look at trends in number of presciprtions written. I create a modified variable called `sum_var` to use for prescribing rates of opioiods, which the total number of opioiod perciption written by a provider in the year 2014).

### The Data

The data sets used in this analysis were fround from [Kaggle](https://www.kaggle.com/datasets/apryor6/us-opiate-prescriptions?select=prescriber-info.csv), sourced from [CMS.gov](https://www.cms.gov/Research-Statistics-Data-and-Systems/Statistics-Trends-and-Reports/Medicare-Provider-Charge-Data/Part-D-Prescriber) (Centers for Medicare & Medicaid Services)

One challenge working with this data was regarding the formatting. There were thousands of spelling inconsistencies for different providers specialties/credentials that resulted in some observations being lost when cleaning the data.

The year of the data’s collection being only 2014 also presented some issues. While there is some insight we can gain by examining characteristics of prodives from a single year, it would be difficult to understand how the trends have changed over time and how much can be explained by new policies (e.g. Prescription Drug Monitoring Programs) or developments in healthcare (e.g. technology; drug alternatives).

A time series panel of data with these same variables for multiple years would provide better insight into things considered worth knowing from a healthare or policy perspective. Pulling in additional sources of data alone with the time panel component would also help to enrich the insighted from this anaylsis. 

### Methods

Forward and backward stepwise selection was used to optimally select variables to be included in regression. For the classification models, variable importance and selection was algorthimally determined. Random Forest was also used in attempt to predict the `summ_var` variable. Binned grouping of means that are represented by different factor levels was able to convert the regression problem into a classification problem to proive a mroe generalizeable prediction model for presicprtion rates. 

###	Results and Conclusions

A variety of different measurement were used to assess the strengthen and out-of-sample accuracy of our data. Accuracy was an important measurement to consider for the classification models while MSE was used for the regression modeling. Different trends were discovered depending on the data manipulation perforemnd and teh selection algortihm used, but many of the same variables were still predicted to be highly significant for explaning the change in the outcome variables regardless of the model. 

Something that limited performance on this project was the computational capability of my computer. The rendering of the final HTML took a while to process since I didn’t I didn’t utilize parellization in the analysis. It also would have helpful to have looked for a time series panel for this data as well as additional soruces. Not only would this have enriched my findings, but also could provide insight in other trends, such as heroion usage/overdose rates when compared to opiooid prescirption rates over time. 


