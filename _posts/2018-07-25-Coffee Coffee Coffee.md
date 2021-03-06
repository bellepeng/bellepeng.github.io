---
layout: post
title: Coffee Coffee Coffee
---

For 99% of my conscious life, coffee has been a daily routine. In my quest to better understand this magical drink, I booked a trip to Colombia to visit a coffee farm, where some of the world's finest coffees are grown. This is what a coffee plant looks like for those of you unfamiliar.

![Highest Coffee Producing Countries](/images/coffee3.png)

I hand picked my own beans, tasted one. The farmer told me "Colombian coffee is the sweetest in world because Colombians are sweet!"

The [Coffee Institute](http://www.coffeeinstitute.org) tastes the coffee from farms all over the world, gives them an overall quality score, and issues a certificate of quality so the farmers can sell their produce worldwide. However, this process can be painfully slow, and perhaps it's not worth the farmer's time, money, and effort to send their beans so far away and wait months if they already know their coffee isn't going to perform well. This got me thinking...

__What if I can predict the quality of the coffee without having to taste it?__

I used webscraping techniques to gather the data from the Coffee Institute on all 1350 farms that submitted their beans for the quality certification from 2015 - 2018. With information on the country of origin, coffee variety, altitude of the farm, moisture,  chemical acidity, sweetness, processing methods, bean color, and number of defects, can I predict the total quality score? 

__Here is some background fun facts about coffee production__

Accoridng to the [Interantional Coffee Organization](http://www.ico.org/new_historical.asp), the largest producing countries of coffee beans are 

![Highest Coffee Producing Countries](/images/coffee4-production ranking.png)

__So is Colombian coffee really sweeter?__

Colombian coffees average close to 10/10 on the sweetness scale, but so do many other countries! So I would say it's inconclusive.

![Highest Coffee Producing Countries](/images/coffee5-sweetness.png)

__But we do know Colombian coffee is pretty darn good!__

For being one of the top producing countries, even with the top quantity Colombia still maintains top position! 

![Highest Coffee Producing Countries](/images/coffee6-coffee quality.png)


### Modelling

For the purpose of predicting the total quality score, I primarily used Ordinary Least Square Methods. 

| Model                                                        | Cross Validation Mean Squared Error | Optimized Hyperparameter Value |
| ------------------------------------------------------------ | :---------------------------------: | :----------------------------: |
| Model 1: OLS, no transformation                              |                1.533                |              None              |
| Model 2: OLS, log transformation on some features            |                1.535                |              None              |
| Model 3: OLS, logged features, LASSO regularization          |                1.509                |          alpha = 0.01          |
| Model 4: OLS, logged and polynomial features, LASSO regularization |                1.526                |          alpha = 0.05          |
| Model 5: OLS, logged and polynomial features, Ridge regularization |                6.405                |          alpha = 1.0           |

After numerous iterations of modeling, I chose model 3 for the best cross validation mean squared error. This model achieved about 60% prediction rate (adjusted $R^2$\) on test data, and averaging about 1.2 points off on a 100 point scale. The respectable prediciton rate of my model indicates that there is linear structure in the features, so what can we tell about the coffee quality? 

### Results: The good - The Bad - No Ugly

These "Good" features are ones that contribute to a higher quality score. These "Bad" features are ones that contribute to a lower quality score. 

![Highest Coffee Producing Countries](/images/coffee8-good bad.png)

__If I had more time__
I would incorporate more data, such as the export data to figure out the market share of each coffee farm within their respective countries. I would explore more modelling methods to see if I can improve the prediction rate. 

![Highest Coffee Producing Countries](/images/coffee7-drinkmore.png)