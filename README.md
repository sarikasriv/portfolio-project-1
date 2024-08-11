# portfolio-project-1
***
This project to estimate new product volume forecast within FMCG world
***
New Product Forecasting
<br/>
One of the challenges within FMCG industry is related to forecasting volume for New Product Development (NPD). It is important for almost every FMCG brand to keep innovating and bringing in new products. But very few product launches in the FMCG category are counted as successful (criteria may differ, for e.g., continued listing in market after a year, making the target value and volume in year 1 and onwards). If we combine it with the amount of time, effort, capital that goes in NPD launches, it can have a big effect on P/L account. Usually, a lot is riding on the success of these initiatives.
<br/><br/>
If you are not very familiar with the FMCG industry, here is some top line information that will give some perspective:
<br/>
1.	A Harvard Business School study estimates 95% of new product ideas that reach the development phase go no further.<br/>
2.	49% failure rate in grocery NPD, a 2004 study from the Product Development & Management Association<br/>
3.	Newton estimates food manufacturers and retailers in the UK grocery industry waste £2.7 billion annually on product innovations that consumers do not want, or prove too expensive to produce.<br/>
References:<br/>
https://www.thegrocer.co.uk/technology-and-supply-chain/why-brands-are-adding-ai-to-their-npd-mix/684431.article<br/>
https://solutions.shopmium.com/en/npd-fmcg-brands-must-innovate-to-grow/<br/>
***
**Challenge in a nutshell:** How can we improve the success of the NPDs by ensuring the best performing NPDs are launched?
***
**Objective:** Estimate a realistic volume (units) that can be achieved with the given NPD and launch plan by benchmarking it against historical sales
***
**Data and variable definitions:** Data for this problem will be sourced from many places. For e.g., past sales performances, past NPD launches and performances, NPD characteristics like, category, format, flavour, price, size etc., user reviews on product tests, Nielsen Bases test results and parameters among many others.
***
**Input Data variable and Sources:**

| Input Variable      | Description                                                                                      | Source        |
|---------------------|--------------------------------------------------------------------------------------------------|---------------|
| **Sales data value** | Past performances of similar products and NPDs launches within the category (time series by weeks – 104 weeks) | NielsenIQ     |
| **Sales data units** | Past performances of similar products and NPDs launches within the category (time series by weeks – 104 weeks) | NielsenIQ     |
| **Price per unit**   | Price per unit for similar products and NPDs launches within the category (time series by weeks – 104 weeks) | Kantar        |
| **Distribution**     | Distribution values between 0 and 100 both inclusive (time series by weeks – 104 weeks)         | NielsenIQ     |

**Data Sources** <br/>
The data used in this project is sourced from:

- **NielsenIQ**: For sales data value, sales data units, and distribution data.
- **Kantar**: For price per unit data.
There are multiple vendors within the industry that provide the such data required for this kind of modelling at a cost. For e.g., most FMCG businesses license for sales data from Nielsen, Kantar, IRI, Brand Bank and all of these can provide extensive quantity of data at a very granular level. For e.g., Nielsen will provide time series sales data for own brand and competitors at an SKU level which will have qualitative information about the products as well including but not limited to brand name, size, flavour, year of launch etc. Consumer panel vendors like Kantar will provide time series data at a granular level for own brand and competitors for consumers behaviour for past NPD for example, trial rates, repeat rates, penetration, demographics etc.
<br/>
For this project I am using a 5 year old data set from a major FMCG company. For confendentiality and copyrights, I will not be sharing the data set within this repository.



**Output variable:** Estimated sale units <br/>
The output from the model will an estimate of the unit sales for the NPD in question for 52 weeks of sales. <br/>

***

**Model**

**Problem Type:** This problem is Predictive, Supervised and Parametric. The best recommended technique (that has been successfully used in similar forecasting problems) is time series regression modelling. ARIMA or Exponential Smoothing. Selected model is ARIMA which has been used many time within this context by multiple organisations. The only key watch out for this algorithm is to ensure pre-processing is done diligently and all non-stationary (seasonality/trends) are removed from the data during modelling as a required step.
***

**Hyperparameters and optimisation**


There are two sets of hyperparameters that will require optimisation:


**1. ARIMA Model Hyperparameters (order=(p, d, q)):**
<br/>**p (Auto-Regressive term):** This represents the number of lag observations included in the model. It determines how many past observations are used to predict the current observation
<br/>**d (Differencing order):** This indicates the number of times that the raw observations are differenced to make the time series stationary. Given that differencing has already been applied to remove seasonality, you may set this to 0 or experiment with different values.
<br/>**q (Moving Average term):** This is the size of the moving average window, i.e., the number of lagged forecast errors that are fed into the model.

**Tuning Strategy:** Using grid search for autotuning

**2. Seasonal ARIMA Hyperparameters (seasonal_order=(P, D, Q, m)):**
<br/>**P (Seasonal Auto-Regressive term):** Number of seasonal lag observations.
<br/>**D (Seasonal Differencing order):** Number of times the seasonal component needs differencing.
<br/>**Q (Seasonal Moving Average term):** Size of the seasonal moving average window.
<br/>**m (Seasonal period):** The number of observations per season (set to 12 for monthly data for yearly seasonality).


**Tuning Strategy:** Using grid search for autotuning

***

