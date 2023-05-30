Overview:  

The following is a data analysis of ~400k car purchases.  Our goal is to test several predictive models to understand the relative factors of car prices.  While is it intuitive that low mileage, mint condition vehicles will demand higher prices, it becomes more complex when we compare used cars of varying condition, milage, manufacturer and body style.  


Summary Analysis:

If you want maximize your profits:
Focus on trucks and pickups
Aim for low mileage vehicles
Either avoid fair condition vehicles, or improve their condition before selling
Avoid minivans
Why?
Low mileage is by far the strongest price driver, followed by body style and vintage.  For example, a brand new pickup truck would consistently demand a high sale price.
Coupes are the highest value among smaller cars
Minivans have the lowest resale price


Methodology:

     We started with a dataset of 420k sales, which we widdled down to ~200k by the time we removed incomplete and irrelevant data data.  We measured feature correlation in two independent ways. First, we simply ran correlation against the original, unscrubbed dataset.  Then, once we identified a regression model, we scrubbed the data and measured feature correlation again.  The optimized data and regression analysis emphasized body style and manufacturer slightly more than vintage, relative to the unscrubbed data.  

Modeling:

We ran Ridge, Lasso, Linear Regression and Random Forest Regressors.  Random Forest Regressor had the lowest mean absolute error (~$3k).  We used our model to generate the following chart of feature weights.  We can provide the model upon request if you need a price generator in the future. 


Assumptions:
 Cars with a sales price of < $2 were removed from the dataset.  We assume these are either in-family sales or donations, which don’t reflect the active used car sales market.
Ferrari data was removed because the high prices throw off the scale of the charts.  A dedicated Ferrari price predictor and analysis can be made available using the available models on demand.
All cars were assumed to be front wheel drive unless otherwise noted
Paint Color and engine cylinder information was too spares to use
Cars will be sold in the state or region they are acquired in

