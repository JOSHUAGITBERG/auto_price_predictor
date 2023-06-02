Overview:

The following is an analysis of a dataset of ~400k car purchases, which can be found in the data directory of this repository. Once the data was cleansed of nulls and incomplete entries, we generated several predictive models, which estimated price based on available feature information.  We determined which model was most accurate by running a subset of the actual data through the model, and comparing model generated price predictions to actual prices.  Recommendations focus on the features identified by our supervised learning model.

Summary Analysis:

The primary drivers of price, in order of priority, are mileage and year, followed by body style and manufacturer:

![alt text](https://github.com/JOSHUAGITBERG/auto_price_predictor/blob/main/images/Relative_Feature_Weights.png)

Year/Vintage

Note that prices drop roughly $2k for each year from 2020 to roughly 2005. Cars lose roughly $2k in value each year, plateauing to a floor after 15 years. Price starts to climb modestly each year after they are 30 years old, and jumps again by roughly 50% once they are 50 years old.

Interestingly, the chart also shows a price drop in 2021, likely triggered by Covid and macroeconomic conditions.

![alt text](https://github.com/JOSHUAGITBERG/auto_price_predictor/blob/main/images/Price_By_Year.png)


The following graph further illustrates the impact of model year on price.  Note that prices clearly trend lower as cars move from new or low mileage towards higher mileage.  In this graph, "moderate" mileage represents 50-100k miles, and extremely high represents over 200k miles.

![alt text](https://github.com/JOSHUAGITBERG/auto_price_predictor/blob/main/images/price_by_mileage.png)

Body Type:

Other than specialty vehicles, coupes and pickups are the highest price vehicles.  Minivans are the least expensive.

![alt text](https://github.com/JOSHUAGITBERG/auto_price_predictor/blob/main/images/Median_Price_By_Type.png)

Condition

Note the wide density of low prices for cars in fair condition. Either avoid fair condition vehicles, or improve their condition before selling.

![alt text](https://github.com/JOSHUAGITBERG/auto_price_predictor/blob/main/images/price_by_condition.png)


Condition  Effects on Highly Valued Vehicles:

The following charts show the relative distribution of prices for cohorts of trucks, coupes and antique cars, sorted by condition.

The data shows the following tends:

Condition affects most cohorts similarly- with the following exceptions:

“Like new” trucks do not retain value as well as coupes and antiques (this requires further analysis)
Trucks in "fair" and "good"  condition retain their value better than coupes or antiques
Antiques in "new" condition have a relativelt high and narrow interquartile range


![alt text](https://github.com/JOSHUAGITBERG/auto_price_predictor/blob/main/images/Cohort_Price_By_Conditions.png)


Methodology:

     We started with a dataset of 420k sales, which we widdled down to ~200k by the time we removed incomplete and irrelevant data.
We measured feature correlation in two independent ways. First, we simply ran correlation against the original, unscrubbed dataset, which produced the following feature weights:

![alt text](https://github.com/JOSHUAGITBERG/auto_price_predictor/blob/main/images/Initial_Feature_Weight.png)

Then, once we identified the most accurate regression model, random forest,  we scrubbed the data and measured feature correlation again.
The optimized data and regression analysis emphasized body style and manufacturer slightly more than vintage, relative to the unscrubbed data.

![alt text](https://github.com/JOSHUAGITBERG/auto_price_predictor/blob/main/images/Relative_Feature_Weights.png)

Modeling:

We standardized the data and ran Ridge, Lasso, Linear and Random Forest Regressors.  Random Forest Regressor had the lowest mean absolute error (~$3k), and generated predictions with 75%+ accuracy.
Our model generated the relative feature weights.  We can use the model to provide a price generator in the future upon request.

![alt text](https://github.com/JOSHUAGITBERG/auto_price_predictor/blob/main/images/Relative_Feature_Weights.png)

Other Assumptions:
Sales with incomplete data were removed from the dataset.
There were many sales with very low sales prices, including sales of new cars for $0 or $1. We assume these are either in-family sales or donations which don't reflet market sales. We arbitrarily selected a $500 floor
which removed such outliers.  Ideally this should allow us to focus on profitable sales.
There were several multi-million dollar sales records.  We removed the highest .1% of sales to eliminate these high priced outliers.
All cars were assumed to be front wheel drive unless otherwise noted
Paint Color and engine cylinder information was too sparse to use
Cars will be sold in the state or region they are acquired



