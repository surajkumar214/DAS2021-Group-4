Group\_04
================
Suraj Kumar
17/07/2021

# Introduction

The Philippine government conducts surveys on household income and
expenditure every three years to understand the living conditions of
residents. In some past studies, we found that some factors may affect
the number of family members. This research studied 2122 families in
Soccsksargen district and collected the data of total household income,
total food expenditure, household head sex, household head age, type of
household, total number of family members, house floor area, house age,
number of bedrooms and electricity, the purpose is to find the
relationship between the number of family members and other variables.
This report focuses on a different analysis level through summaries,
boxplots, and general linear model. Section consists of an exploratory
data analysis of number of family members and explores the potential
relationship between member numbers and other variables. Section
contains the results from fitting a generalized linear model to the
data, as well as the assessment of the model assumptions. Concluding
remarks are given in Section .

# Exploratory Data Analysis

            
             Extended Family Single Family Two or More Nonrelated Persons/Members
      Female             151           210                                      1
      Male               434          1321                                      5

       
        Extended Family Single Family Two or More Nonrelated Persons/Members
      0              47           124                                      0
      1             124           553                                      3
      2             233           645                                      3
      3             129           149                                      0
      4              42            48                                      0
      5               7            10                                      0
      6               3             1                                      0
      7               0             1                                      0

       
        Extended Family Single Family Two or More Nonrelated Persons/Members
      0              67           295                                      1
      1             518          1236                                      5

       
          0   1   2   3   4   5   6   7
      0  53 196 102  12   0   0   0   0
      1 118 484 779 266  90  17   4   1

            
                0    1
      Female   58  304
      Male    305 1455

# Formal Data Analysis

we fit a poisson model as our response is a count variable. We have
excluded Region as a covariate because there was only one factor. We
will start with a model that considers all the initial impressions that
we get from the exploratory analysis. The model takes into account the
interaction between Household.Head.Age and Type.of.Household,
log(Total.Food.Expenditure ) and Type.of.Household,
log(Total.Household.Income) and Electricity, and Type.of.Household and
Electricity. We have scaled down Total.Food.Expenditure,
Total.Household.Income, and House.Floor.Area by taking log
transformation to address the scalability issue in the design matrix.
Here is the following model:-

$$log(E(Total.Number.of.Family.members)) = + 1Household.Head.Sex
+2Household.Head.Age + 3log(Total.Food.Expenditure ) +

\_i, \~\~\~\~ \_i N(0, ^2),$$

![](group_04_files/figure-gfm/model1-1.png)<!-- -->

    332 
    332 

    212 
    212 

![](group_04_files/figure-gfm/unnamed-chunk-1-1.png)<!-- -->

    332 
    332 

    212 
    212 

![](group_04_files/figure-gfm/unnamed-chunk-1-2.png)<!-- -->![](group_04_files/figure-gfm/unnamed-chunk-1-3.png)<!-- -->

![](group_04_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->![](group_04_files/figure-gfm/unnamed-chunk-2-2.png)<!-- -->


        Underdispersion test

    data:  model1
    z = -18.596, p-value < 2.2e-16
    alternative hypothesis: true alpha is less than 0
    sample estimates:
         alpha 
    -0.3920074 

    Single term deletions

    Model:
    Total.Number.of.Family.members ~ Household.Head.Sex + Household.Head.Age * 
        Type.of.Household + log(Total.Food.Expenditure) * Type.of.Household + 
        log(Total.Household.Income) * Type.of.Household + log(Total.Household.Income) * 
        Electricity + Type.of.Household * Electricity + log(House.Floor.Area) + 
        Number.of.bedrooms + House.Age
                                                  Df Deviance    AIC F value
    <none>                                             1250.0 8235.3        
    Household.Head.Sex                             1   1298.7 8282.0 81.5312
    log(House.Floor.Area)                          1   1258.0 8241.3 13.4105
    Number.of.bedrooms                             7   1260.3 8231.6  2.4570
    House.Age                                      1   1261.3 8244.6 18.9318
    Household.Head.Age:Type.of.Household           2   1254.1 8235.3  3.3867
    Type.of.Household:log(Total.Food.Expenditure)  2   1250.8 8232.0  0.6198
    Type.of.Household:log(Total.Household.Income)  2   1251.0 8232.3  0.8445
    log(Total.Household.Income):Electricity        1   1263.0 8246.2 21.6628
    Type.of.Household:Electricity                  2   1260.1 8241.3  8.3970
                                                     Pr(>F)    
    <none>                                                     
    Household.Head.Sex                            < 2.2e-16 ***
    log(House.Floor.Area)                         0.0002564 ***
    Number.of.bedrooms                            0.0164574 *  
    House.Age                                     1.420e-05 ***
    Household.Head.Age:Type.of.Household          0.0340044 *  
    Type.of.Household:log(Total.Food.Expenditure) 0.5381329    
    Type.of.Household:log(Total.Household.Income) 0.4299288    
    log(Total.Household.Income):Electricity       3.454e-06 ***
    Type.of.Household:Electricity                 0.0002332 ***
    ---
    Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

    Single term deletions

    Model:
    Total.Number.of.Family.members ~ Household.Head.Sex + Household.Head.Age * 
        Type.of.Household + log(Total.Food.Expenditure) * Type.of.Household + 
        log(Total.Household.Income) * Electricity + Type.of.Household * 
        Electricity + log(House.Floor.Area) + House.Age + Number.of.bedrooms
                                                  Df Deviance    AIC F value
    <none>                                             1251.0 8232.3        
    Household.Head.Sex                             1   1300.0 8279.3 82.1117
    log(House.Floor.Area)                          1   1258.8 8238.1 12.9858
    House.Age                                      1   1262.3 8241.6 18.9148
    Number.of.bedrooms                             7   1261.0 8228.3  2.3842
    Household.Head.Age:Type.of.Household           2   1254.8 8232.1  3.1814
    Type.of.Household:log(Total.Food.Expenditure)  2   1255.4 8232.6  3.6216
    log(Total.Household.Income):Electricity        1   1264.7 8243.9 22.8539
    Type.of.Household:Electricity                  2   1260.3 8237.5  7.7283
                                                     Pr(>F)    
    <none>                                                     
    Household.Head.Sex                            < 2.2e-16 ***
    log(House.Floor.Area)                         0.0003212 ***
    House.Age                                     1.432e-05 ***
    Number.of.bedrooms                            0.0198478 *  
    Household.Head.Age:Type.of.Household          0.0417261 *  
    Type.of.Household:log(Total.Food.Expenditure) 0.0269082 *  
    log(Total.Household.Income):Electricity       1.869e-06 ***
    Type.of.Household:Electricity                 0.0004528 ***
    ---
    Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

    Single term deletions

    Model:
    Total.Number.of.Family.members ~ Household.Head.Sex + Household.Head.Age + 
        log(Total.Food.Expenditure) * Type.of.Household + log(Total.Household.Income) * 
        Electricity + Type.of.Household * Electricity + log(House.Floor.Area) + 
        House.Age + Number.of.bedrooms
                                                  Df Deviance    AIC F value
    <none>                                             1254.8 8232.1        
    Household.Head.Sex                             1   1303.3 8278.6 81.0680
    Household.Head.Age                             1   1263.1 8238.4 13.8483
    log(House.Floor.Area)                          1   1262.7 8238.0 13.2018
    House.Age                                      1   1266.2 8241.5 19.0069
    Number.of.bedrooms                             7   1265.3 8228.5  2.4919
    log(Total.Food.Expenditure):Type.of.Household  2   1259.2 8232.5  3.6370
    log(Total.Household.Income):Electricity        1   1268.5 8243.8 22.8206
    Type.of.Household:Electricity                  2   1263.9 8237.2  7.5742
                                                     Pr(>F)    
    <none>                                                     
    Household.Head.Sex                            < 2.2e-16 ***
    Household.Head.Age                            0.0002034 ***
    log(House.Floor.Area)                         0.0002864 ***
    House.Age                                     1.365e-05 ***
    Number.of.bedrooms                            0.0150380 *  
    log(Total.Food.Expenditure):Type.of.Household 0.0264976 *  
    log(Total.Household.Income):Electricity       1.902e-06 ***
    Type.of.Household:Electricity                 0.0005277 ***
    ---
    Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

    No Studentized residuals with Bonferroni p < 0.05
    Largest |rstudent|:
          rstudent unadjusted p-value Bonferroni p
    1521 -3.463215         0.00053376           NA

![](group_04_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

    [1] 0.6113809


    Call:
    glm(formula = Total.Number.of.Family.members ~ Household.Head.Sex + 
        Household.Head.Age + log(Total.Food.Expenditure) * Type.of.Household + 
        log(Total.Household.Income) * Electricity + Type.of.Household * 
        Electricity + log(House.Floor.Area) + House.Age + Number.of.bedrooms, 
        family = "poisson", data = dataset4)

    Deviance Residuals: 
        Min       1Q   Median       3Q      Max  
    -3.1996  -0.5387  -0.1097   0.4183   2.9405  

    Coefficients:
                                                                                          Estimate
    (Intercept)                                                                         -4.2823533
    Household.Head.SexMale                                                               0.2110798
    Household.Head.Age                                                                  -0.0023816
    log(Total.Food.Expenditure)                                                          0.5032097
    Type.of.HouseholdSingle Family                                                      -1.0943810
    Type.of.HouseholdTwo or More Nonrelated Persons/Members                             -7.9639107
    log(Total.Household.Income)                                                          0.0498296
    Electricity1                                                                         2.1165998
    log(House.Floor.Area)                                                               -0.0502534
    House.Age                                                                           -0.0034594
    Number.of.bedrooms1                                                                  0.1005389
    Number.of.bedrooms2                                                                  0.1088343
    Number.of.bedrooms3                                                                  0.0973565
    Number.of.bedrooms4                                                                  0.1486297
    Number.of.bedrooms5                                                                  0.2385225
    Number.of.bedrooms6                                                                  0.3587403
    Number.of.bedrooms7                                                                  0.4554365
    log(Total.Food.Expenditure):Type.of.HouseholdSingle Family                           0.0863010
    log(Total.Food.Expenditure):Type.of.HouseholdTwo or More Nonrelated Persons/Members  0.7765212
    log(Total.Household.Income):Electricity1                                            -0.1890513
    Type.of.HouseholdSingle Family:Electricity1                                         -0.1939749
    Type.of.HouseholdTwo or More Nonrelated Persons/Members:Electricity1                -0.7087339
                                                                                        Std. Error
    (Intercept)                                                                          0.5217257
    Household.Head.SexMale                                                               0.0242358
    Household.Head.Age                                                                   0.0006479
    log(Total.Food.Expenditure)                                                          0.0332601
    Type.of.HouseholdSingle Family                                                       0.3776642
    Type.of.HouseholdTwo or More Nonrelated Persons/Members                              8.7869257
    log(Total.Household.Income)                                                          0.0406058
    Electricity1                                                                         0.4582030
    log(House.Floor.Area)                                                                0.0140311
    House.Age                                                                            0.0008083
    Number.of.bedrooms1                                                                  0.0339014
    Number.of.bedrooms2                                                                  0.0345628
    Number.of.bedrooms3                                                                  0.0411376
    Number.of.bedrooms4                                                                  0.0526165
    Number.of.bedrooms5                                                                  0.0923139
    Number.of.bedrooms6                                                                  0.1455098
    Number.of.bedrooms7                                                                  0.3547158
    log(Total.Food.Expenditure):Type.of.HouseholdSingle Family                           0.0342686
    log(Total.Food.Expenditure):Type.of.HouseholdTwo or More Nonrelated Persons/Members  0.8365459
    log(Total.Household.Income):Electricity1                                             0.0399125
    Type.of.HouseholdSingle Family:Electricity1                                          0.0526321
    Type.of.HouseholdTwo or More Nonrelated Persons/Members:Electricity1                 0.5769559
                                                                                        z value
    (Intercept)                                                                          -8.208
    Household.Head.SexMale                                                                8.709
    Household.Head.Age                                                                   -3.676
    log(Total.Food.Expenditure)                                                          15.130
    Type.of.HouseholdSingle Family                                                       -2.898
    Type.of.HouseholdTwo or More Nonrelated Persons/Members                              -0.906
    log(Total.Household.Income)                                                           1.227
    Electricity1                                                                          4.619
    log(House.Floor.Area)                                                                -3.582
    House.Age                                                                            -4.280
    Number.of.bedrooms1                                                                   2.966
    Number.of.bedrooms2                                                                   3.149
    Number.of.bedrooms3                                                                   2.367
    Number.of.bedrooms4                                                                   2.825
    Number.of.bedrooms5                                                                   2.584
    Number.of.bedrooms6                                                                   2.465
    Number.of.bedrooms7                                                                   1.284
    log(Total.Food.Expenditure):Type.of.HouseholdSingle Family                            2.518
    log(Total.Food.Expenditure):Type.of.HouseholdTwo or More Nonrelated Persons/Members   0.928
    log(Total.Household.Income):Electricity1                                             -4.737
    Type.of.HouseholdSingle Family:Electricity1                                          -3.685
    Type.of.HouseholdTwo or More Nonrelated Persons/Members:Electricity1                 -1.228
                                                                                        Pr(>|z|)
    (Intercept)                                                                         2.25e-16
    Household.Head.SexMale                                                               < 2e-16
    Household.Head.Age                                                                  0.000237
    log(Total.Food.Expenditure)                                                          < 2e-16
    Type.of.HouseholdSingle Family                                                      0.003758
    Type.of.HouseholdTwo or More Nonrelated Persons/Members                             0.364758
    log(Total.Household.Income)                                                         0.219764
    Electricity1                                                                        3.85e-06
    log(House.Floor.Area)                                                               0.000342
    House.Age                                                                           1.87e-05
    Number.of.bedrooms1                                                                 0.003021
    Number.of.bedrooms2                                                                 0.001639
    Number.of.bedrooms3                                                                 0.017952
    Number.of.bedrooms4                                                                 0.004731
    Number.of.bedrooms5                                                                 0.009771
    Number.of.bedrooms6                                                                 0.013686
    Number.of.bedrooms7                                                                 0.199160
    log(Total.Food.Expenditure):Type.of.HouseholdSingle Family                          0.011790
    log(Total.Food.Expenditure):Type.of.HouseholdTwo or More Nonrelated Persons/Members 0.353279
    log(Total.Household.Income):Electricity1                                            2.17e-06
    Type.of.HouseholdSingle Family:Electricity1                                         0.000228
    Type.of.HouseholdTwo or More Nonrelated Persons/Members:Electricity1                0.219296
                                                                                           
    (Intercept)                                                                         ***
    Household.Head.SexMale                                                              ***
    Household.Head.Age                                                                  ***
    log(Total.Food.Expenditure)                                                         ***
    Type.of.HouseholdSingle Family                                                      ** 
    Type.of.HouseholdTwo or More Nonrelated Persons/Members                                
    log(Total.Household.Income)                                                            
    Electricity1                                                                        ***
    log(House.Floor.Area)                                                               ***
    House.Age                                                                           ***
    Number.of.bedrooms1                                                                 ** 
    Number.of.bedrooms2                                                                 ** 
    Number.of.bedrooms3                                                                 *  
    Number.of.bedrooms4                                                                 ** 
    Number.of.bedrooms5                                                                 ** 
    Number.of.bedrooms6                                                                 *  
    Number.of.bedrooms7                                                                    
    log(Total.Food.Expenditure):Type.of.HouseholdSingle Family                          *  
    log(Total.Food.Expenditure):Type.of.HouseholdTwo or More Nonrelated Persons/Members    
    log(Total.Household.Income):Electricity1                                            ***
    Type.of.HouseholdSingle Family:Electricity1                                         ***
    Type.of.HouseholdTwo or More Nonrelated Persons/Members:Electricity1                   
    ---
    Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

    (Dispersion parameter for poisson family taken to be 0.6113809)

        Null deviance: 2192.3  on 2120  degrees of freedom
    Residual deviance: 1254.8  on 2099  degrees of freedom
    AIC: 8232.1

    Number of Fisher Scoring iterations: 4

# Conclusions

# Extention
