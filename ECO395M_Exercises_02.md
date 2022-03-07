## 1) Visualization

![](ECO395M_Exercises_02_files/figure-markdown_github/unnamed-chunk-1-1.png)

The hour of peak boarding times seem to stay constant day to day, month
to month.

During Mondays in September, average boarding looks lower compared to
other days and months. One possible reason for this is that weather in
September 2018 was more pleasant than the colder October and November
months. This may have incentivized people to go out more on Sundays
rendering it difficult to get up on Monday mornings to go to work.

Wednesday, Thursday, Friday look lower in November because the week of
Thanksgiving break (November 21-23 in 2018) may have lowered the
averages down for the rest of the month because a lot of students and
others would be going back to home.

![](ECO395M_Exercises_02_files/figure-markdown_github/unnamed-chunk-2-1.png)

Temperature seems to not have a noticeable effect on ridership among UT
students when holding hour of day and weekend status constant.

## 2) Saratoga house prices

    ##         V1 lm_new_err         V3 
    ## 67140.8771 66759.3901  -381.4869

    ## 
    ## Call:
    ## lm(formula = price ~ . + (livingArea:rooms) + (rooms:bedrooms) + 
    ##     (bedrooms:bathrooms) - pctCollege - sewer - waterfront - 
    ##     landValue - newConstruction, data = saratoga_train)
    ## 
    ## Coefficients:
    ##            (Intercept)                 lotSize                     age  
    ##              32910.320                6851.146                  62.146  
    ##             livingArea                bedrooms              fireplaces  
    ##                 22.599               24488.450                4203.200  
    ##              bathrooms                   rooms  heatinghot water/steam  
    ##              23568.464                5013.722               -8348.707  
    ##        heatingelectric            fuelelectric                 fueloil  
    ##              -4187.640               -9614.104               -8497.324  
    ##           centralAirNo        livingArea:rooms          bedrooms:rooms  
    ##             -16755.637                   8.109               -5100.596  
    ##     bedrooms:bathrooms  
    ##                 47.415

The linear model produces the lowest RMSE. Using this model allows for
more control over variables and features as well as interactions between
them. In the linear model, I interacted living area with number of
rooms,number of rooms with number of bedrooms, and bedrooms and
bathrooms.

The optimal K for the RMSE model is `r`optimal_k$err\[1\]\`

### Appendix

    ##      Linear_Model KNN_Model
    ## RSME     66759.39  62726.14

    ## 
    ## Call:
    ## lm(formula = price ~ . + (livingArea:rooms) + (rooms:bedrooms) + 
    ##     (bedrooms:bathrooms) - pctCollege - sewer - waterfront - 
    ##     landValue - newConstruction, data = saratoga_train)
    ## 
    ## Coefficients:
    ##            (Intercept)                 lotSize                     age  
    ##              32910.320                6851.146                  62.146  
    ##             livingArea                bedrooms              fireplaces  
    ##                 22.599               24488.450                4203.200  
    ##              bathrooms                   rooms  heatinghot water/steam  
    ##              23568.464                5013.722               -8348.707  
    ##        heatingelectric            fuelelectric                 fueloil  
    ##              -4187.640               -9614.104               -8497.324  
    ##           centralAirNo        livingArea:rooms          bedrooms:rooms  
    ##             -16755.637                   8.109               -5100.596  
    ##     bedrooms:bathrooms  
    ##                 47.415

## 3) Classification and retrospective sampling

![](ECO395M_Exercises_02_files/figure-markdown_github/unnamed-chunk-5-1.png)

    ##    yhat
    ## y     0   1
    ##   0 133   8
    ##   1  47  12

    ## 
    ## Call:  glm(formula = Default ~ duration + amount + installment + age + 
    ##     history + purpose + foreign, family = "binomial", data = credit_train)
    ## 
    ## Coefficients:
    ##         (Intercept)             duration               amount  
    ##          -8.583e-01            3.002e-02            8.587e-05  
    ##         installment                  age          historypoor  
    ##           2.255e-01           -1.691e-02           -1.054e+00  
    ##     historyterrible           purposeedu  purposegoods/repair  
    ##          -1.817e+00            5.426e-01            2.520e-02  
    ##       purposenewcar       purposeusedcar        foreigngerman  
    ##           6.783e-01           -1.082e+00           -1.060e+00  
    ## 
    ## Degrees of Freedom: 799 Total (i.e. Null);  788 Residual
    ## Null Deviance:       979.1 
    ## Residual Deviance: 856.6     AIC: 880.6

The bar plot along with the regression implies that the historypoor and
historyterrible variables are negatively correlated with default
probability which doesn’t make a lot of sense. Given that a big majority
of the sample are “poor” or “terrible” credit scores, history isn’t a
good variable to use in this dataset to predict “high” or “low”
probability of default. And since the bank looked for similar types of
loans that caused defaults this dataset would be looking for probability
of defaulting among loans that are already biased towards defaulting in
the first place. So, they should sample a random or bigger variety of
loan types.

## 4) Children and hotel reservations

### Model building

    ##    yhat
    ## y      0
    ##   0 8263
    ##   1  737

    ##    yhat
    ## y      0    1
    ##   0 8147  116
    ##   1  481  256

    ##    yhat
    ## y      0    1
    ##   0 8155  108
    ##   1  480  257

    ##                    baseline_1 baseline_2  my_model
    ## Out_of_sample_prob  0.9181111  0.9336667 0.9346667

Using the confusion matrices to tabulate predicted vs actual class, I’m
able to to measure out-of-sample accuracy for each model.

### Model validation: step 1

![](ECO395M_Exercises_02_files/figure-markdown_github/unnamed-chunk-8-1.png)

### Model validation: step 2
