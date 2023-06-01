Overview:  

The following is an analysis of a dataset of ~400k car purchases, which can be found in the data directory of this repository. Once the data was cleansed of nulls and incomplete entries, we generated several predictive models, which estimated price based on available feature information.  We determined which model was most accurate by running a subset of the actual data through the model, and comparing model generated price predictions to actual prices.  The following analysis is based on features identified by our supervised learning model.

Summary Analysis:

The primary drivers of price, in order of priority, are mileage and year, followed by body style and manufacturer:

![alt text](https://github.com/JOSHUAGITBERG/auto_price_predictor/blob/main/images/Relative_Feature_Weights.png)

Other than specialty vehicles, coupes and pickups are the highest price vehicles.  Minivans are the least expensive.

![alt text](https://github.com/JOSHUAGITBERG/auto_price_predictor/blob/main/images/PricebyBodyType.png))

Either avoid fair condition vehicles, or improve their condition before selling

![alt text](https://github.com/JOSHUAGITBERG/auto_price_predictor/blob/main/images/price_by_condition.png)

![alt text](https://github.com/JOSHUAGITBERG/auto_price_predictor/blob/main/images/price_by_mileage.png)

Other Trends:

Vintage Analysis:

Note that prices drop after a car is ten years old, and start to rise again at around 50 years old.  
Prices started dropping in 2021, probably due to Covid and the stock market crash

![alt text](https://github.com/JOSHUAGITBERG/auto_price_predictor/blob/main/images/Price_By_Year.png)

Condition  Effects on Highly Valued Vehicles:

The following charts show condition affecting trucks, coupes and antiques similarly
“Like new” trucks do not retain value relative to “new”

![alt text](https://github.com/JOSHUAGITBERG/auto_price_predictor/blob/main/images/Price_By_Year.png)




Methodology:

     We started with a dataset of 420k sales, which we widdled down to ~200k by the time we removed incomplete and irrelevant data.  We measured feature correlation in two independent ways. First, we simply ran correlation against the original, unscrubbed dataset, which produced the following feature weights:  

![alt text](https://github.com/JOSHUAGITBERG/auto_price_predictor/blob/main/images/Relative_Feature_Weights_Raw.png)

Then, once we identified a regression model, we scrubbed the data and measured feature correlation again.  The optimized data and regression analysis emphasized body style and manufacturer slightly more than vintage, relative to the unscrubbed data.  

![alt text](https://github.com/JOSHUAGITBERG/auto_price_predictor/blob/main/images/Relative_Feature_Weights_Scrubbed.png)

Modeling:

We ran Ridge, Lasso, Linear Regression and Random Forest Regressors.  Random Forest Regressor had the lowest mean absolute error (~$3k), and generated predictions with above 75% accuracy.  We used our model to generate the following chart of feature weights.  We can provide the model upon request if you need a price generator in the future. 

![alt text](https://github.com/JOSHUAGITBERG/auto_price_predictor/blob/main/images/Relative_Feature_Weights.png)

Other Assumptions:
 Cars with a sales price of < $500 were removed from the dataset.  There were many cars in good condition listed as low as $0 or $1.  We assume these are either in-family sales or donations, which don’t reflect the active used car sales market.  We arbitrarily used a $500 floor to remove outliers and focus on profitable sales. 
Ferrari data was removed from the manufacturer chart because the high prices throw off the scale.
All cars were assumed to be front wheel drive unless otherwise noted
Paint Color and engine cylinder information was too spares to use
Cars will be sold in the state or region they are acquired in

