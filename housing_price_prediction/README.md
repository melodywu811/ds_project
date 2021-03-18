# Project 2: Using the Housing Data to Predict Home Prices
**Submitted by: Melody Wu**  
**Feburary 22, 2021**

<img src="./image/cover_pic.jpg" style="height: 300px">   

[Image source](https://inception-app-prod.s3.amazonaws.com/MzAzMmY0NWQtMjg2ZS00NmEwLTg5MTMtMWVhYTM3YWU1MTBl/content/2017/04/jve.jpg)  

This README serves as the executive summary of this project.

---
## Contents  
The rest of the report is organized as below:  
1. Problem Statement - *in this current file*
2. Data Pre-Processing - *in the EDA notebook*
3. Exploratory Data Analysis (EDA) - *in the EDA notebook*
4. Modeling and Validation - *in the modeling notebook*
5. Interpretation - *in this current file*
7. Conclusions and Recommendations - *in this current file*
---

## Problem Statement

Since houses do not come with a price tag, sellers and buyers often have to make their best estimation when listing or bidding. In some cases, people can get ripped off when sellers underestimate or when buyers overestimate the values. However, on the other hand, there is a great opportunity for real estate investors to make a good fortune in this market. There two problems I hope to solve here by building and evaluating a regression model for predicting the home values when given a list of property characteristics:
1. to provide a tool for sellers and buyers to make accurate estimations on home values and reach fair deals (this tool will be free of charge for everyone!)
2. to provide insights real estate investors to identify "undervalued homes" and consulting services for potential improvement to increase the home values.  

### Background Info on the Dataset
The dataset used in this project contains information from the Ames Assessor’s Office used in computing assessed values for individual residential properties sold in Ames, IA from 2006 to 2010. This dataset doesn't have a significant number of outliers.

[SOURCES](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt):
Ames, Iowa Assessor’s Office

### Data Dictionary

|Feature|Type|Description|
|---|---|---|
|**`saleprice`**|*float*|Sale price in dollars|
|**`lot_frontage`**|*float*|Linear feet of street connected to property|
|**`overall_qual`**|*integer*|Rates the overall material and finish of the house|
|**`year_built`**|*float*|Original construction year|
|**`year_remod/add`**|*float*|Remodel year (same as construction date if no remodeling or additions)|
|**`mas_vnr_area`**|*float*|Masonry veneer area in square feet|
|**`bsmtfin_sf_1`**|*float*|Type 1 finished square feet|
|**`total_bsmt_sf`**|*float*|Total square feet of basement area|
|**`1st_flr_sf`**|*float*|First Floor square feet|
|**`gr_liv_area`**|*float*|Above ground living area square feet|
|**`full_bath`**|*integer*|Full bathrooms above ground|
|**`totrms_abvgrd`**|*integer*|Total rooms above grade (does not include bathrooms)|
|**`fireplaces`**|*integer*|Number of fireplaces|
|**`garage_cars`**|*integer*|Size of garage in car capacity|
|**`garage_area`**|*float*|Size of garage in square feet|
|**`wood_deck_sf`**|*float*|Wood deck area in square feet|
|**`open_porch_sf`**|*float*|Open porch area in square feet|
|**`lot_regular`**|*binary*|1: general shape of property is regular, 0: irregular|
|**`more_than_1story`**|*binary*|1: the property has more than one story, 0|
|**`exter_ex`**|*binary*|1: the quality of the material on the exterior is excellent|
|**`foundation_PConc`**|*binary*|1: the foundation is poured concrete|
|**`bsmt_ex`**|*binary*|1: the quality of the basement is excellent|
|**`has_bsmt_exposure`**|*binary*|1: basement has above average garden/outside exposure|
|**`heating_ex`**|*binary*|1: the heating system quality is excellent|
|**`kitchen_ex`**|*binary*|1: the kitchen quality is excellent|
|**`garage_finish_dum`**|*binary*|1: the nterior the garage is finish|
|**`has_central_air`**|*binary*|1: has central air|
|**`bsmtfin_type_GLQ`**|*binary*|1: the rating of the basement finished area is 'Good Living Quarters|
|**`neighborhood`**|*categorical*|Neighborhood where the property is located|
|**`neighborhood_code_2`**|*binary*|Located in the one of the home value 3rd Quartile neighborhoods|
|**`neighborhood_code_3`**|*binary*|Located in the one of the home value 2nd Quartile neighborhoods|
|**`neighborhood_code_4`**|*binary*|Located in the one of the home value 1st Quartile neighborhoods|


|Neighborhoods|Home Value Quartile Neighborhood|
|---|---|
|StoneBr|4th Quartile|
|NridgHt|4th Quartile|
|NoRidge|4th Quartile|
|GrnHill|4th Quartile|
|Veenker|4th Quartile|
|Timber|4th Quartile|
|Somerst|4th Quartile|
|ClearCr|4th Quartile|
|Crawfor|3rd Quartile|
|CollgCr|3rd Quartile|
|Blmngtn|3rd Quartile|
|NWAmes|3rd Quartile|
|Gilbert|3rd Quartile|
|Greens|3rd Quartile|
|SawyerW|3rd Quartile|
|Mitchel|3rd Quartile|
|NAmes|2nd Quartile|
|Blueste|2nd Quartile|
|NPkVill|2nd Quartile|
|Sawyer|2nd Quartile|
|Landmrk|2nd Quartile|
|SWISU|2nd Quartile|
|Edwards|2nd Quartile|
|BrkSide|1st Quartile|
|OldTown|1st Quartile|
|BrDale|1st Quartile|
|IDOTRR|1st Quartile|
|MeadowV|1st Quartile|


## Modeling
### Model Development
A multi-linear regression (MLR) model is developed, with the log transformed sale price as the dependent variable. The general assumptions of linear regression is met. The independent variables/feature included are:

`'lot_frontage', 'overall_qual', 'year_built', 'year_remod/add', 'mas_vnr_area', 'bsmtfin_sf_1', 'total_bsmt_sf', '1st_flr_sf', 'gr_liv_area', 'full_bath', 'totrms_abvgrd', 'fireplaces', 'garage_cars', 'garage_area', 'wood_deck_sf', 'open_porch_sf', 'lot_regular', 'more_than_1story', 'exter_ex', 'foundation_PConc', 'bsmt_ex', 'has_bsmt_exposure', 'heating_ex', 'kitchen_ex', 'garage_finish_dum', 'has_central_air', 'bsmtfin_type_GLQ', 'neighborhood_code_2', 'neighborhood_code_3', 'neighborhood_code_4'.
`

Description of the features are available in the above data Dictionary. Some data transformation, such as log transformation, is performed. The numeric features were selected based their correlations with `log_saleprice`, the dependent variable. The categorical features were selected based on qualitative review.

### Evaluation

Based on the R-squared comparison, I chose Model 4 as the final model as the training and testing R-squares are the closest.


| Model                                               | Training R-square | Testing R-square |
|-----------------------------------------------------|-------------------|------------------|
| Model 1: Linear Regression (numeric variables only) | 0.837             | 0.844            |
| Model 2: LASSO Regularized Regression               | 0.908             | 0.854            |
| Model 3: Ridget Regularized Regression              | 0.882             | 0.854            |
| Model 4: Linear Regression (numeric + categorical)  | 0.861             | 0.858            |

### Interpretation

The below table summaries the selected regression coefficient of the model and their Interpretation. A full list of the coefficient Interpretation is availabe in the modeling and validation notebook.

Holding everthings else constant

|Feature|Coefficient|Interpretation|
|---|---|---|
|has_central_air|0.168|Having central air predicts an 0.168 increase of the log home value|
|overall_qual|0.085|One rating increase (e.g., from 5 to 6 or from 6 to 7) predicts a 0.085 increase of the log home value|
|kitchen_ex|0.069|Having kitchen quality evaluated as "excellent" predicts a 0.069 increase of the log home value|
|fireplaces|0.047|An additional fireplaces in the property predicts a 0.047 increase of the log home value|
|garage_cars|0.046|One unit increase of garage area (in car capacity) predict a 0.046 increase of the log home price|
|heating_ex|0.032|Having heating quality evaluated as "excellent" predicts a 0.032 increase of the log home value|
|gr_liv_area|0.000176|An square feet increase in ground living area predict an 0.000176 increase of log home price|

## Recommendations
These Recommendations are suggested for home sellers and real estate investors:
- preferred neighborhoods for investment: Stone Brook, Northridge Heights, Northridge, Green Hills, Veenker, Timberland, and Somerset
- Overall quality is more important than other single-item qualities (e.g., kitchen, heating, basement, etc.). Try improving the overall quality of the property before listing.
- Improve evaluation from Good to Excellent for all itemized evaluations. There is a significant increase of values from Good to Excellent.
- Remodel the properties as much as the budget is allowed.
- Consider purchasing properties without features like central air, fireplace,  full bath, wood deck, then install these features before selling.
- Don’t forget to improve the quality of the basement and garage.


**Limitation:** This model has critical limitations. Since home valuations differ significantly in different locations, these model is only applicable for using to predict home values in Ames, IA (ideally from 2006 to 2010). However, the model design (i.e., the type of model, data transformation strategies, selected features) can be used as a reference for future housing model development.
