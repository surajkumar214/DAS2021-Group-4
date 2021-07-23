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

# Formal Data Analysis

We fit a Poisson model as our response is a count variable. We have
excluded Region as a covariate because there was only one factor. We
will start with a model that considers all the initial impressions from
the exploratory analysis. The model takes into account the interaction
between log(Household.Head.Age) and Type.of.Household,
log(Total.Food.Expenditure ) and Type.of.Household, and
log(Total.Household.Income) and Electricity. We have scaled
Total.Food.Expenditure, Total.Household.Income, Household.Head.Age, and
House.Floor.Area by taking log transformation to address the scalability
issue in the design matrix. Here is the summary of the described model:-

<table class="table table-striped table-hover table-condensed table-responsive" style="width: auto !important; margin-left: auto; margin-right: auto;">
<tbody>
<tr>
<td style="text-align:left;font-weight: bold;">
Observations
</td>
<td style="text-align:right;">
2122
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
Dependent variable
</td>
<td style="text-align:right;">
Total.Number.of.Family.members
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
Type
</td>
<td style="text-align:right;">
Generalized linear model
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
Family
</td>
<td style="text-align:right;">
poisson
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
Link
</td>
<td style="text-align:right;">
log
</td>
</tr>
</tbody>
</table>
<table class="table table-striped table-hover table-condensed table-responsive" style="width: auto !important; margin-left: auto; margin-right: auto;">
<tbody>
<tr>
<td style="text-align:left;font-weight: bold;">
𝛘²(17)
</td>
<td style="text-align:right;">
927.82
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
Pseudo-R² (Cragg-Uhler)
</td>
<td style="text-align:right;">
0.36
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
Pseudo-R² (McFadden)
</td>
<td style="text-align:right;">
0.10
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
AIC
</td>
<td style="text-align:right;">
8264.07
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
BIC
</td>
<td style="text-align:right;">
8365.95
</td>
</tr>
</tbody>
</table>
<table class="table table-striped table-hover table-condensed table-responsive" style="width: auto !important; margin-left: auto; margin-right: auto;border-bottom: 0;">
<thead>
<tr>
<th style="text-align:left;">
</th>
<th style="text-align:right;">
Est.
</th>
<th style="text-align:right;">
S.E.
</th>
<th style="text-align:right;">
z val.
</th>
<th style="text-align:right;">
p
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;font-weight: bold;">
(Intercept)
</td>
<td style="text-align:right;">
-4.14
</td>
<td style="text-align:right;">
0.71
</td>
<td style="text-align:right;">
-5.84
</td>
<td style="text-align:right;">
0.00
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
Household.Head.SexMale
</td>
<td style="text-align:right;">
0.21
</td>
<td style="text-align:right;">
0.03
</td>
<td style="text-align:right;">
6.74
</td>
<td style="text-align:right;">
0.00
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
log(Household.Head.Age)
</td>
<td style="text-align:right;">
-0.02
</td>
<td style="text-align:right;">
0.07
</td>
<td style="text-align:right;">
-0.33
</td>
<td style="text-align:right;">
0.74
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
Type.of.HouseholdSingle Family
</td>
<td style="text-align:right;">
-0.51
</td>
<td style="text-align:right;">
0.56
</td>
<td style="text-align:right;">
-0.91
</td>
<td style="text-align:right;">
0.36
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
Type.of.HouseholdTwo or More Nonrelated Persons/Members
</td>
<td style="text-align:right;">
-3.83
</td>
<td style="text-align:right;">
8.33
</td>
<td style="text-align:right;">
-0.46
</td>
<td style="text-align:right;">
0.65
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
log(Total.Food.Expenditure)
</td>
<td style="text-align:right;">
0.54
</td>
<td style="text-align:right;">
0.06
</td>
<td style="text-align:right;">
9.85
</td>
<td style="text-align:right;">
0.00
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
log(Total.Household.Income)
</td>
<td style="text-align:right;">
0.01
</td>
<td style="text-align:right;">
0.06
</td>
<td style="text-align:right;">
0.18
</td>
<td style="text-align:right;">
0.85
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
Electricity1
</td>
<td style="text-align:right;">
1.65
</td>
<td style="text-align:right;">
0.57
</td>
<td style="text-align:right;">
2.91
</td>
<td style="text-align:right;">
0.00
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
log(House.Floor.Area)
</td>
<td style="text-align:right;">
-0.05
</td>
<td style="text-align:right;">
0.02
</td>
<td style="text-align:right;">
-2.87
</td>
<td style="text-align:right;">
0.00
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
Number.of.bedrooms
</td>
<td style="text-align:right;">
0.03
</td>
<td style="text-align:right;">
0.01
</td>
<td style="text-align:right;">
2.43
</td>
<td style="text-align:right;">
0.02
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
House.Age
</td>
<td style="text-align:right;">
-0.00
</td>
<td style="text-align:right;">
0.00
</td>
<td style="text-align:right;">
-4.02
</td>
<td style="text-align:right;">
0.00
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
log(Household.Head.Age):Type.of.HouseholdSingle Family
</td>
<td style="text-align:right;">
-0.08
</td>
<td style="text-align:right;">
0.08
</td>
<td style="text-align:right;">
-1.02
</td>
<td style="text-align:right;">
0.31
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
log(Household.Head.Age):Type.of.HouseholdTwo or More Nonrelated
Persons/Members
</td>
<td style="text-align:right;">
0.57
</td>
<td style="text-align:right;">
0.74
</td>
<td style="text-align:right;">
0.76
</td>
<td style="text-align:right;">
0.44
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
Type.of.HouseholdSingle Family:log(Total.Food.Expenditure)
</td>
<td style="text-align:right;">
0.04
</td>
<td style="text-align:right;">
0.06
</td>
<td style="text-align:right;">
0.67
</td>
<td style="text-align:right;">
0.50
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
Type.of.HouseholdTwo or More Nonrelated
Persons/Members:log(Total.Food.Expenditure)
</td>
<td style="text-align:right;">
0.40
</td>
<td style="text-align:right;">
1.20
</td>
<td style="text-align:right;">
0.33
</td>
<td style="text-align:right;">
0.74
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
Type.of.HouseholdSingle Family:log(Total.Household.Income)
</td>
<td style="text-align:right;">
0.01
</td>
<td style="text-align:right;">
0.04
</td>
<td style="text-align:right;">
0.11
</td>
<td style="text-align:right;">
0.91
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
Type.of.HouseholdTwo or More Nonrelated
Persons/Members:log(Total.Household.Income)
</td>
<td style="text-align:right;">
-0.23
</td>
<td style="text-align:right;">
0.75
</td>
<td style="text-align:right;">
-0.31
</td>
<td style="text-align:right;">
0.75
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
log(Total.Household.Income):Electricity1
</td>
<td style="text-align:right;">
-0.16
</td>
<td style="text-align:right;">
0.05
</td>
<td style="text-align:right;">
-3.19
</td>
<td style="text-align:right;">
0.00
</td>
</tr>
</tbody>
<tfoot>
<tr>
<td style="padding: 0; " colspan="100%">
<sup></sup> Standard errors: MLE
</td>
</tr>
</tfoot>
</table>

We can observe a lot of insignificant variables in our initial model.
However, before proceeding to the wald test to check the significance of
each variable, we, firstly, looked for any potential outliers and
checked whether assumptions are holding. We can notice that the deviance
of the model(1290.01) is much less than chi-square(2211.83). There could
be a case of underdispersion wherein the estimated variance is less than
the expected mean. We can interpret the coefficients in such a situation
but can’t rely on standard error as they are deflated.

<div class="figure" style="text-align: center">

<img src="group_04_files/figure-gfm/plot-1.png" alt="\label{fig:out} Outlier check" width="68%" />
<p class="caption">
Outlier check
</p>

</div>

We have plotted Normal\_qq\_plot for Pearson and deviance residuals. The
purpose of such plots is to identify any point that doesn’t follow the
straight line. We have also plotted deviance residuals vs. the fitted
value to check the independence and identify any pattern in the
residuals. From above Figure , we can notice one potential outlier at
the top of the qq\_plot, and presence of heavy tails. So, our next step
is to identify and remove the point and again fit the model. Let’s run
an Outlier test:-

    No Studentized residuals with Bonferroni p < 0.05
    Largest |rstudent|:
         rstudent unadjusted p-value Bonferroni p
    2033 4.044985         5.2326e-05      0.11104

We have identified the outlier point having id 2033. However, addressing
outlier is totally subjective. We try to fit the model again removing
this outlier and check for the assumptions.

<div class="figure" style="text-align: center">

<img src="group_04_files/figure-gfm/plot1-1.png" alt="\label{fig:assum} Assumptions checking" width="68%" />
<p class="caption">
Assumptions checking
</p>

</div>

From Figure , we can see some patterns in the residuals. It would be
better to fit some quadratic terms in the explanatory variables.
Residuals seem to be normally distributed with some heavy tails. Now, we
proceed with the dispersion test as there has been some evidence of
underdispersion.

<div class="figure" style="text-align: center">

<img src="group_04_files/figure-gfm/plot2-1.png" alt="\label{fig:disp} Assumptions checking" width="68%" />
<p class="caption">
Assumptions checking
</p>

</div>


        Underdispersion test

    data:  .
    z = -17.657, p-value < 2.2e-16
    alternative hypothesis: true alpha is less than 0
    sample estimates:
         alpha 
    -0.3806268 

The negative value of aplha (-0.38) is significant because the p\_value
for the hypothesis test is (0). Figure displays the underdispersed
variance. Therefore, we can’t rely on Wald’s test for inference in the
above model. Rather, we perform analysis with quasi-poisson model that
adjusts variance for both overdispersion and underdispersion. We resort
to F test and do step by step variable removal to choose the best
fitting model.

<table class="table" style="margin-left: auto; margin-right: auto;">
<caption>
Performing F test on the inital model
</caption>
<thead>
<tr>
<th style="text-align:left;">
</th>
<th style="text-align:right;">
Df
</th>
<th style="text-align:right;">
Deviance
</th>
<th style="text-align:right;">
AIC
</th>
<th style="text-align:right;">
F value
</th>
<th style="text-align:right;">
Pr(&gt;F)
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
&lt;none&gt;
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:right;">
1273.652
</td>
<td style="text-align:right;">
8242.915
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:right;">
NA
</td>
</tr>
<tr>
<td style="text-align:left;">
Household.Head.Sex
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
1325.520
</td>
<td style="text-align:right;">
8292.783
</td>
<td style="text-align:right;">
85.6430129
</td>
<td style="text-align:right;">
0.0000000
</td>
</tr>
<tr>
<td style="text-align:left;">
log(House.Floor.Area)
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
1282.125
</td>
<td style="text-align:right;">
8249.388
</td>
<td style="text-align:right;">
13.9910642
</td>
<td style="text-align:right;">
0.0001886
</td>
</tr>
<tr>
<td style="text-align:left;">
Number.of.bedrooms
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
1278.592
</td>
<td style="text-align:right;">
8245.855
</td>
<td style="text-align:right;">
8.1568031
</td>
<td style="text-align:right;">
0.0043321
</td>
</tr>
<tr>
<td style="text-align:left;">
House.Age
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
1288.128
</td>
<td style="text-align:right;">
8255.391
</td>
<td style="text-align:right;">
23.9032567
</td>
<td style="text-align:right;">
0.0000011
</td>
</tr>
<tr>
<td style="text-align:left;">
log(Household.Head.Age):Type.of.Household
</td>
<td style="text-align:right;">
2
</td>
<td style="text-align:right;">
1275.626
</td>
<td style="text-align:right;">
8240.889
</td>
<td style="text-align:right;">
1.6300660
</td>
<td style="text-align:right;">
0.1961641
</td>
</tr>
<tr>
<td style="text-align:left;">
Type.of.Household:log(Total.Food.Expenditure)
</td>
<td style="text-align:right;">
2
</td>
<td style="text-align:right;">
1274.361
</td>
<td style="text-align:right;">
8239.623
</td>
<td style="text-align:right;">
0.5852555
</td>
<td style="text-align:right;">
0.5570542
</td>
</tr>
<tr>
<td style="text-align:left;">
Type.of.Household:log(Total.Household.Income)
</td>
<td style="text-align:right;">
2
</td>
<td style="text-align:right;">
1273.757
</td>
<td style="text-align:right;">
8239.019
</td>
<td style="text-align:right;">
0.0865810
</td>
<td style="text-align:right;">
0.9170645
</td>
</tr>
<tr>
<td style="text-align:left;">
log(Total.Household.Income):Electricity
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
1283.776
</td>
<td style="text-align:right;">
8251.039
</td>
<td style="text-align:right;">
16.7164971
</td>
<td style="text-align:right;">
0.0000450
</td>
</tr>
</tbody>
</table>

In the table ,log(Household.Head.Age):Type.of.Household,
Type.of.Household:log(Total.Food.Expenditure) and
Type.of.Household:log(Total.Household.Income) can be eliminated without
significantly hurting the model’s Deviance. So, we firstly eliminate
variable Type.of.Household:log(Total.Household.Income) and check for F
test again:-

<table class="table" style="margin-left: auto; margin-right: auto;">
<caption>
Performing F test on the inital model
</caption>
<thead>
<tr>
<th style="text-align:left;">
</th>
<th style="text-align:right;">
Df
</th>
<th style="text-align:right;">
Deviance
</th>
<th style="text-align:right;">
AIC
</th>
<th style="text-align:right;">
F value
</th>
<th style="text-align:right;">
Pr(&gt;F)
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
&lt;none&gt;
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:right;">
1273.757
</td>
<td style="text-align:right;">
8239.019
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:right;">
NA
</td>
</tr>
<tr>
<td style="text-align:left;">
Household.Head.Sex
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
1325.950
</td>
<td style="text-align:right;">
8289.213
</td>
<td style="text-align:right;">
86.254403
</td>
<td style="text-align:right;">
0.0000000
</td>
</tr>
<tr>
<td style="text-align:left;">
log(House.Floor.Area)
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
1282.239
</td>
<td style="text-align:right;">
8245.502
</td>
<td style="text-align:right;">
14.018291
</td>
<td style="text-align:right;">
0.0001859
</td>
</tr>
<tr>
<td style="text-align:left;">
House.Age
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
1288.193
</td>
<td style="text-align:right;">
8251.455
</td>
<td style="text-align:right;">
23.856783
</td>
<td style="text-align:right;">
0.0000011
</td>
</tr>
<tr>
<td style="text-align:left;">
Number.of.bedrooms
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
1278.713
</td>
<td style="text-align:right;">
8241.976
</td>
<td style="text-align:right;">
8.190448
</td>
<td style="text-align:right;">
0.0042528
</td>
</tr>
<tr>
<td style="text-align:left;">
log(Household.Head.Age):Type.of.Household
</td>
<td style="text-align:right;">
2
</td>
<td style="text-align:right;">
1275.698
</td>
<td style="text-align:right;">
8236.961
</td>
<td style="text-align:right;">
1.604133
</td>
<td style="text-align:right;">
0.2013095
</td>
</tr>
<tr>
<td style="text-align:left;">
Type.of.Household:log(Total.Food.Expenditure)
</td>
<td style="text-align:right;">
2
</td>
<td style="text-align:right;">
1275.549
</td>
<td style="text-align:right;">
8236.812
</td>
<td style="text-align:right;">
1.481077
</td>
<td style="text-align:right;">
0.2276296
</td>
</tr>
<tr>
<td style="text-align:left;">
log(Total.Household.Income):Electricity
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
1284.083
</td>
<td style="text-align:right;">
8247.345
</td>
<td style="text-align:right;">
17.064527
</td>
<td style="text-align:right;">
0.0000375
</td>
</tr>
</tbody>
</table>

The F test says that we can remove
log(Household.Head.Age):Type.of.Household and
Type.of.Household:log(Total.Food.Expenditure). So, repeat the same
process until we reach all terms are significant.

<table class="table" style="margin-left: auto; margin-right: auto;">
<caption>
Performing F test on the inital model
</caption>
<thead>
<tr>
<th style="text-align:left;">
</th>
<th style="text-align:right;">
Df
</th>
<th style="text-align:right;">
Deviance
</th>
<th style="text-align:right;">
AIC
</th>
<th style="text-align:right;">
F value
</th>
<th style="text-align:right;">
Pr(&gt;F)
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
&lt;none&gt;
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:right;">
1420.634
</td>
<td style="text-align:right;">
8373.897
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:right;">
NA
</td>
</tr>
<tr>
<td style="text-align:left;">
Household.Head.Sex
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
1453.645
</td>
<td style="text-align:right;">
8404.908
</td>
<td style="text-align:right;">
49.0529897
</td>
<td style="text-align:right;">
0.0000000
</td>
</tr>
<tr>
<td style="text-align:left;">
log(Household.Head.Age)
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
1420.848
</td>
<td style="text-align:right;">
8372.111
</td>
<td style="text-align:right;">
0.3185475
</td>
<td style="text-align:right;">
0.5725418
</td>
</tr>
<tr>
<td style="text-align:left;">
log(Total.Food.Expenditure)
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
1871.125
</td>
<td style="text-align:right;">
8822.388
</td>
<td style="text-align:right;">
669.4095760
</td>
<td style="text-align:right;">
0.0000000
</td>
</tr>
<tr>
<td style="text-align:left;">
log(House.Floor.Area)
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
1429.989
</td>
<td style="text-align:right;">
8381.251
</td>
<td style="text-align:right;">
13.9005724
</td>
<td style="text-align:right;">
0.0001978
</td>
</tr>
<tr>
<td style="text-align:left;">
House.Age
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
1431.574
</td>
<td style="text-align:right;">
8382.837
</td>
<td style="text-align:right;">
16.2559534
</td>
<td style="text-align:right;">
0.0000573
</td>
</tr>
<tr>
<td style="text-align:left;">
Number.of.bedrooms
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
1427.393
</td>
<td style="text-align:right;">
8378.656
</td>
<td style="text-align:right;">
10.0442410
</td>
<td style="text-align:right;">
0.0015501
</td>
</tr>
<tr>
<td style="text-align:left;">
log(Total.Household.Income):Electricity
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
1432.657
</td>
<td style="text-align:right;">
8383.920
</td>
<td style="text-align:right;">
17.8655919
</td>
<td style="text-align:right;">
0.0000247
</td>
</tr>
</tbody>
</table>
<table class="table" style="margin-left: auto; margin-right: auto;">
<caption>
Performing F test on the inital model
</caption>
<thead>
<tr>
<th style="text-align:left;">
</th>
<th style="text-align:right;">
Df
</th>
<th style="text-align:right;">
Deviance
</th>
<th style="text-align:right;">
AIC
</th>
<th style="text-align:right;">
F value
</th>
<th style="text-align:right;">
Pr(&gt;F)
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
&lt;none&gt;
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:right;">
1420.848
</td>
<td style="text-align:right;">
8372.111
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:right;">
NA
</td>
</tr>
<tr>
<td style="text-align:left;">
Household.Head.Sex
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
1453.886
</td>
<td style="text-align:right;">
8403.149
</td>
<td style="text-align:right;">
49.10858
</td>
<td style="text-align:right;">
0.0000000
</td>
</tr>
<tr>
<td style="text-align:left;">
log(Total.Food.Expenditure)
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
1871.234
</td>
<td style="text-align:right;">
8820.497
</td>
<td style="text-align:right;">
669.46960
</td>
<td style="text-align:right;">
0.0000000
</td>
</tr>
<tr>
<td style="text-align:left;">
log(House.Floor.Area)
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
1430.102
</td>
<td style="text-align:right;">
8379.365
</td>
<td style="text-align:right;">
13.75527
</td>
<td style="text-align:right;">
0.0002136
</td>
</tr>
<tr>
<td style="text-align:left;">
House.Age
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
1431.712
</td>
<td style="text-align:right;">
8380.975
</td>
<td style="text-align:right;">
16.14837
</td>
<td style="text-align:right;">
0.0000606
</td>
</tr>
<tr>
<td style="text-align:left;">
Number.of.bedrooms
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
1427.755
</td>
<td style="text-align:right;">
8377.018
</td>
<td style="text-align:right;">
10.26619
</td>
<td style="text-align:right;">
0.0013751
</td>
</tr>
<tr>
<td style="text-align:left;">
log(Total.Household.Income):Electricity
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
1432.862
</td>
<td style="text-align:right;">
8382.125
</td>
<td style="text-align:right;">
17.85789
</td>
<td style="text-align:right;">
0.0000248
</td>
</tr>
</tbody>
</table>

Eventually, we reached to our final model that considers interactions
between log(Total.Household.Income) and Electricity as significant. Now,
we adjust the standard error using dispersion parameter, which is
equivalent of fitting a quasipoission model.

    [1] 0.6880479

<table class="table table-striped table-hover table-condensed table-responsive" style="width: auto !important; margin-left: auto; margin-right: auto;">
<tbody>
<tr>
<td style="text-align:left;font-weight: bold;">
Observations
</td>
<td style="text-align:right;">
2121
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
Dependent variable
</td>
<td style="text-align:right;">
Total.Number.of.Family.members
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
Type
</td>
<td style="text-align:right;">
Generalized linear model
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
Family
</td>
<td style="text-align:right;">
poisson
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
Link
</td>
<td style="text-align:right;">
log
</td>
</tr>
</tbody>
</table>
<table class="table table-striped table-hover table-condensed table-responsive" style="width: auto !important; margin-left: auto; margin-right: auto;">
<tbody>
<tr>
<td style="text-align:left;font-weight: bold;">
𝛘²(8)
</td>
<td style="text-align:right;">
771.44
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
Pseudo-R² (Cragg-Uhler)
</td>
<td style="text-align:right;">
0.31
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
Pseudo-R² (McFadden)
</td>
<td style="text-align:right;">
0.08
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
AIC
</td>
<td style="text-align:right;">
8372.11
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
BIC
</td>
<td style="text-align:right;">
8423.05
</td>
</tr>
</tbody>
</table>
<table class="table table-striped table-hover table-condensed table-responsive" style="width: auto !important; margin-left: auto; margin-right: auto;border-bottom: 0;">
<thead>
<tr>
<th style="text-align:left;">
</th>
<th style="text-align:right;">
Est.
</th>
<th style="text-align:right;">
S.E.
</th>
<th style="text-align:right;">
z val.
</th>
<th style="text-align:right;">
p
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;font-weight: bold;">
(Intercept)
</td>
<td style="text-align:right;">
-5.44
</td>
<td style="text-align:right;">
0.53
</td>
<td style="text-align:right;">
-10.18
</td>
<td style="text-align:right;">
0.00
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
Household.Head.SexMale
</td>
<td style="text-align:right;">
0.17
</td>
<td style="text-align:right;">
0.03
</td>
<td style="text-align:right;">
5.64
</td>
<td style="text-align:right;">
0.00
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
log(Total.Food.Expenditure)
</td>
<td style="text-align:right;">
0.62
</td>
<td style="text-align:right;">
0.03
</td>
<td style="text-align:right;">
21.93
</td>
<td style="text-align:right;">
0.00
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
log(Total.Household.Income)
</td>
<td style="text-align:right;">
0.02
</td>
<td style="text-align:right;">
0.05
</td>
<td style="text-align:right;">
0.47
</td>
<td style="text-align:right;">
0.63
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
Electricity1
</td>
<td style="text-align:right;">
1.78
</td>
<td style="text-align:right;">
0.56
</td>
<td style="text-align:right;">
3.19
</td>
<td style="text-align:right;">
0.00
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
log(House.Floor.Area)
</td>
<td style="text-align:right;">
-0.05
</td>
<td style="text-align:right;">
0.02
</td>
<td style="text-align:right;">
-3.03
</td>
<td style="text-align:right;">
0.00
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
House.Age
</td>
<td style="text-align:right;">
-0.00
</td>
<td style="text-align:right;">
0.00
</td>
<td style="text-align:right;">
-3.27
</td>
<td style="text-align:right;">
0.00
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
Number.of.bedrooms
</td>
<td style="text-align:right;">
0.03
</td>
<td style="text-align:right;">
0.01
</td>
<td style="text-align:right;">
2.63
</td>
<td style="text-align:right;">
0.01
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;">
log(Total.Household.Income):Electricity1
</td>
<td style="text-align:right;">
-0.17
</td>
<td style="text-align:right;">
0.05
</td>
<td style="text-align:right;">
-3.47
</td>
<td style="text-align:right;">
0.00
</td>
</tr>
</tbody>
<tfoot>
<tr>
<td style="padding: 0; " colspan="100%">
<sup></sup> Standard errors: MLE
</td>
</tr>
</tfoot>
</table>

We can see that standard error slight rises up after adjusting with the
dispersion parameter, while the intercept term remains the same. Still ,
the wald test is not very reliable to draw inferences and may conflict
with the F test.

# Conclusions

# Extention

We will consider more appropirate models like Generalized poisson model,
or Conway-Maxwell Poisson (COM-Poisson) Regression, which have less
expected residual variance than the mean. We wil also attempt to apply
quadratic model that address the slight curve in the deviance against
fitted plot.
