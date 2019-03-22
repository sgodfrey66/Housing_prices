# ![](https://www.google.com/url?sa=i&source=images&cd=&cad=rja&uact=8&ved=2ahUKEwiTrKPh1pThAhUSOq0KHalWBboQjRx6BAgBEAU&url=https%3A%2F%2Fwww.traveliowa.com%2Fcities%2Fames-iowa%2F814%2F&psig=AOvVaw0X_1um4OmZsOSOxrF9vVBl&ust=1553307298094967) Project 2: Ames Housing Data and Kaggle Challenge


### Stephen Godfrey, DSI-CC7-San Francisco

### Problem Statement

Find a simple and explainable model to predict housing prices in Ames, IA.


### Executive Summary

This project examines housing data from Ames, IA with the goal of building a model to predict housing prices.   The objective is to construct a parsimonious model that is easily understood by users but that maintains some predictive power.  The task is addressed by examining some 80 housing-related variables and housing transactions between 2006 and 2010 to determine which combination of variables is most suited to explaining an individual price.  

For modeling and performance measurement, the data are separated into a training and a test set.  Modelings are built on a subset of the training data and then fitted on the entire training data set.  They are then applied to the test data set and measured by a Root Mean Squared Error score at the Kaggle website.  

The approach pursued here is to use several modeling techniques to narrow the number of variables to consider.  Variable combination and models are evaluated in three primary steps, referred to as Steps 1, 2 and 3.  Step 1 uses custom-built functions to evaluate large numbers of variable combinations in Ordinary Least Squares models.  Step 2 uses methods available in the SKlearn API to select the best variables and then recursively reduce these to a smaller subset.  Step 3 combines the output of Steps 1 and 2 and judgment to evaluate the resulting models.

### Conclusions and Recommendations

A wide range of models were evaluated and in doing so a trade off between explainability and predictability was observed.  With roughly 80 variables, many of which are categorical, there is the possibility to build models that depend on a large number of variables.  To see this, consider that the categorical variables where converted to dummy variables and the interaction terms among the numeric variables were also considered.

Employing large numbers of variables can improve explanatory power especially with the training data, but it does present the risk of overfitting resulting in prediction weakness in data not seen by the model.  Building large variable set models also presents other challenges.  Such models are likely to suffer from problems of multicollinearity since it is likely that many of the independent variables are correlated.  This turned out to be a particular problem with these data since many housing characteristics are related.  For example, a larger house is likely to have more bedrooms than a smaller one.  It is also difficult to appreciate the drivers of predictions in large variable models.  There are simply too many variables for a consumer to know which are most important in making a prediction. 

Here the objective was to find the most explanatory variables and maintain understandability. This may have led to a reduction in explanatory power and the models achieved average performance in the Kaggle competition.  However, they are useful and remain explainable. 

The recommended model incorporated the numerical variables of over quality, living area, age at time of sale, age of remodel at time of sale, lot area, fireplaces, finished basement area, size of open porch, a categorical variable for the home's neighborhood and the interaction variables of over quality and living area, overall quality and year sold and lot area and overall quality. 

One key learning in this effort is that judgment is needed in modeling.  The approach taken here was to select a variable set based solely on explanatory power.  The procedures in Steps 1 and 2 did not set a priori limits on the variables but rather selected those that performed best in explaining the target variable.  This approach has both benefits and limitations.  It is beneficial in that it does provide a methodology for selecting among a large number of potential variables.  Its limitations include its long running time which may not have been an efficient use of computing resources and the fact that it did not on its own produce a recommended solution.  Instead, the recommended solution relied on judgment.  However, it should be noted that this judgment was informed by the output of this process. 


### Data

Data sources:
* Training and test data were provided as a part of project materials.  The variable listing can be found in the dictionary below.  Categorical variable values can be seen in the attached Jupyter notebook.

Data dictionary.

|Feature|Description|
|---|----|
|SalePrice:| the property's sale price in dollars|
|MSSubClass:| The building class|
|MSZoning:| Identifies the general zoning classification of the sale|
|LotFrontage:| Linear feet of street connected to property|
|LotArea:| Lot size in square feet|
|Street:| Type of road access to property|
|Alley:| Type of alley access to property|
|LotShape:| General shape of property|
|LandContour:| Flatness of the property|
|Utilities:| Type of utilities available|
|LotConfig:| Lot configuration|
|LandSlope:| Slope of property|
|Neighborhood:| Physical locations within Ames city limits|
|Condition1:| Proximity to main road or railroad|
|Condition2:| Proximity to main road or railroad (if a second is present)|
|BldgType:| Type of dwelling|
|HouseStyle:| Style of dwelling|
|OverallQual:| Overall material and finish quality|
|OverallCond:| Overall condition rating|
|YearBuilt:|Original construction date|
|YearRemodAdd:| Remodel date (same as construction date if no remodeling or additions)|
|RoofStyle:| Type of roof|
|RoofMatl:| Roof material|
|Exterior1st:| Exterior covering on house|
|Exterior2nd:| Exterior covering on house (if more than one material)|
|MasVnrType:| Masonry veneer type|
|MasVnrArea:| Masonry veneer area in square feet|
|ExterQual:| Exterior material quality|
|ExterCond:| Present condition of the material on the exterior|
|Foundation:| Type of foundation|
|BsmtQual:| Height of the basement|
|BsmtCond:| General condition of the basement|
|BsmtExposure:| Walkout or garden level basement walls|
|BsmtFinType1:| Quality of basement finished area|
|BsmtFinSF1:| Type 1 finished square feet|
|BsmtFinType2:| Quality of second finished area (if present)|
|BsmtFinSF2:| Type 2 finished square feet|
|BsmtUnfSF:|Unfinished square feet of basement area|
|TotalBsmtSF:| Total square feet of basement area|
|Heating:| Type of heating|
|HeatingQC:| Heating quality and condition|
|entralAir:| Central air conditioning|
|Electrical:| Electrical system|
|1stFlrSF:| First Floor square feet|
|2ndFlrSF:| Second floor square feet|
|LowQualFinSF:| Low quality finished square feet (all floors)|
|GrLivArea:| Above grade (ground) living area square feet|
|BsmtFullBath:| Basement full bathrooms|
|BsmtHalfBath:| Basement half bathrooms|
|FullBath:| Full bathrooms above grade|
|HalfBath:| Half baths above grade|
|Bedroom:| Number of bedrooms above basement level|
|Kitchen:| Number of kitchens|
|KitchenQual:| Kitchen quality|
|TotRmsAbvGrd:| Total rooms above grade (does not include bathrooms)|
|Functional:|Home functionality rating|
|Fireplaces:| Number of fireplaces|
|FireplaceQu:| Fireplace quality|
|GarageType:| Garage location|
|GarageYrBlt:| Year garage was built|
|GarageFinish:| Interior finish of the garage|
|GarageCars:| Size of garage in car capacity|
|GarageArea:| Size of garage in square feet|
|GarageQual:| Garage quality|
|GarageCond:| Garage condition|
|PavedDrive:| Paved driveway|
|WoodDeckSF:| Wood deck area in square feet|
|OpenPorchSF:| Open porch area in square feet|
|EnclosedPorch:| Enclosed porch area in square feet|
|3SsnPorch:| Three season porch area in square feet|
|ScreenPorch:| Screen porch area in square feet|
|PoolArea:| Pool area in square feet|
|PoolQC:| Pool quality|
|Fence:| Fence quality|
|MiscFeature:| Miscellaneous feature not covered in other categories|
|MiscVal:| $Value of miscellaneous feature|
|MoSold:| Month Sold|
|YrSold:| Year Sold|
|SaleType:| Type of sale|
