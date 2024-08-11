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

## Data Sources
The data used in this project is sourced from:

- **NielsenIQ**: For sales data value, sales data units, and distribution data.
- **Kantar**: For price per unit data.
There are multiple vendors within the industry that provide the such data required for this kind of modelling at a cost. For e.g., most FMCG businesses license for sales data from Nielsen, Kantar, IRI, Brand Bank and all of these can provide extensive quantity of data at a very granular level. For e.g., Nielsen will provide time series sales data for own brand and competitors at an SKU level which will have qualitative information about the products as well including but not limited to brand name, size, flavour, year of launch etc. Consumer panel vendors like Kantar will provide time series data at a granular level for own brand and competitors for consumers behaviour for past NPD for example, trial rates, repeat rates, penetration, demographics etc.
<br/>
For this project I am using a 5 year old data set from a major FMCG company. For confendentiality and copyrights, I will not be sharing the data set within this repository. 
<br/>
***
**Output variable:** Estimated sale units
<br/>
**Problem Type:** This problem is Predictive, Supervised and Parametric. The best recommended technique (that has been successfully used in similar forecasting problems) is time series regression modelling. ARIMA or Exponential Smoothing.
<br/>
**Use purpose:** The model produced will be for repeated use purpose for key stakeholders internally within Marketing, Logistics, Demand planning, Sales and Insights and Reporting functions.
