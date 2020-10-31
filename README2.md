
# Module 2 Final Project


## Introduction

We will be exploring the King County House Sale dataset with a multivariable linear regression to predict the sale price of homes in the area. Hopefully, we'll be able to leverage the insights in this analysis to determing the most important features of a home before we open our own construction business.

Key questions:

- Which features of a home have the greatest impact on home price?

- Which areas of King County should we consider building in?

- How can we improve the potential sale price of a home?


## The Dataset

The King County House Sales dataset is made up of the following columns:

ID
Date
Price
bedrooms
bathrooms
sqrft_living (square footage of entire living space)
sqft_lot (swaure footage of plot of land)
floors
waterfront
view
condition
grade
sqft_above (square footage above the first floor)
sqft_basement (square footage of the basement)
yr_built
yr_renovated
zipcode
lat
long
sqft_living15 (square footage of living space in nearest 15 homes)
sqft_lot15 (square footage of lots in nearest 15 homes)

## Approach

1. Cleaning the data. Removing outliers and unnecessary columns.
2. Exploring the data to prepare for modeling. Bucketing variables as categorical or numerical and creatign dummy variables.
3. Creation of baseline model.
4. Refining the model.
5. Interpretations of and recommmendations based on the final model.

## Baseline Model

For this project, the baseline model was created immmediately after cleaning and creating dummy variables. Our inital R^2 is 0.841. However, multiple features have p-values greater than 0.05. Furthermore, our residuals are skewed (see below) and the difference in RMSEs between our test and train sets is very high (> 8.2 MM). 

![alt text](https://raw.githubusercontent.com/miriamsemmar/dsc-mod-2-project-v2-1-onl01-dtsc-pt-070620/master/Baseline%20Model%20residuals.png)

## Final Model

To arrive at our final model, I performed log transofrmations on price, sqft_living, sqft_lot and home_age to normalize the resdiuals. Furthermore, I dropped columns with high p-values in our subsequent models. Ultimately, I limited our model to 50 features. 

![alt text](https://github.com/miriamsemmar/dsc-mod-2-project-v2-1-onl01-dtsc-pt-070620/blob/master/price_before_transformation.png distribution of price before log transformation)
*Distribution of price before log transformation*

![alt text](https://github.com/miriamsemmar/dsc-mod-2-project-v2-1-onl01-dtsc-pt-070620/blob/master/price_after_transformation.png)
*Distribution of price after log transformation (more normal)*

The final R^2 of our model 0.736. While R^2 did decrease from our baseline model, the residuals are more normally distributed (see below). This model also have a smaller RMSE difference of 0.001, further supporting the strength of this model.

![alt text](https://github.com/miriamsemmar/dsc-mod-2-project-v2-1-onl01-dtsc-pt-070620/blob/master/final_model_OLS.png)

![alt text](https://github.com/miriamsemmar/dsc-mod-2-project-v2-1-onl01-dtsc-pt-070620/blob/master/final_model.png)
*Q-Q Plot of final model residuals*

![alt text](https://github.com/miriamsemmar/dsc-mod-2-project-v2-1-onl01-dtsc-pt-070620/blob/master/final_model_homosce.png)
*Homoscedasticity of final model*

## Conclusions

### Which features of a home have the greatest impact on home price?

As outlined below, the zipcode a home is located in, the grade of a home (referring to the construction quality) and the liveable sqft have the biggest impact on the price of a home.

For example, a home located in zipcode 98004 will increase the log price of a home by 0.69. 

Every additional square foot will increase home price by 0.433 the log of price

Having a home with a grade of 4-6 will decrease your home value by a minimum of 0.50 the log of price.

### Which areas of King County should we consider building in?

Homes in Bellevue (98004) and Seattle (98112,98109) are generally more expensive.

### How can we improve the potential sale price of a home?

We don't only have to build homes on empty lots. We can also consider conducting remodels and focus on using higher grade materials as well as building extensions to increase the squarefootage of a home. 



