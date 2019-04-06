Milestone2
================
Simon Chiu, Sabrina Tse, Sylvia Lee, Hayley Boyce
2019-04-03

Introduction
------------

#### Survey

Survey link: https://ubc.ca1.qualtrics.com/jfe/form/SV_agz0I9HiBEeZqBL


The survey was conducted online anonymously during the lab session on April 3rd, 2019. We expected that most of the responders were UBC MDS students in the 2018-2019 cohort since the survey content focused on gathering MDS students' study behaviour and location preference. In total, we received 65 responses.


#### Exploratory Data Analysis

**Language**
For this milestone exploratory data analysis was required. Due to the statistical nature of the lab and an overall consensus, we agreed on programming in R.

``` r
# reading the data into Python or R and creating a summary table

data <- read_csv("../DSCI554_SSSHteam_Survey.csv")
```

    ## Parsed with column specification:
    ## cols(
    ##   .default = col_character()
    ## )

    ## See spec(...) for full column specifications.

``` r
data <- data %>% filter( Status == "IP Address", Q0 == "I agree to participate" ) %>% select(Q15, Q2, Q2_1_TEXT, Q3, Q4,Q16, Q11, Q5, Q18)
data <- data %>%  mutate(Q2 = ifelse(Q2 == "No", 0,  Q2_1_TEXT)) %>% select(-Q2_1_TEXT)
data <- data %>%  mutate(Q15 = ifelse(Q15 == "Academic environment (school libraries, lounges, classrooms)", "Academic",  Q15))
# adjusting the category types
data <- data %>% mutate(Q15 = as.factor(Q15), Q2 = as.numeric(Q2), Q3 = as.integer(Q3),  Q4 = as.numeric(Q4),  Q16 = as.numeric(Q16),  Q11 = as.numeric(Q11), Q5 = as.numeric(Q5), Q18= as.numeric(Q18) )

data <- data %>% rename(Location = Q15, OptionalQ = Q2, ProcrastLV = Q3,  Household_Hr = Q4,  Commute_Hm_Sch_Min = Q16,  Commute_Stu_Loc_Min = Q11, Time_On_Lab_Hr = Q5, Spare_Time_Min= Q18 )
```

``` r
kable(head(data))
```

| Location |  OptionalQ|  ProcrastLV|  Household\_Hr|  Commute\_Hm\_Sch\_Min|  Commute\_Stu\_Loc\_Min|  Time\_On\_Lab\_Hr|  Spare\_Time\_Min|
|:---------|----------:|-----------:|--------------:|----------------------:|-----------------------:|------------------:|-----------------:|
| Academic |        0.0|           7|            3.0|                     20|                      10|                 12|                10|
| Home     |        0.0|           6|            2.5|                     35|                       0|                 11|               120|
| Academic |        0.0|           1|            2.5|                     20|                      10|                 24|               180|
| Academic |        4.0|           6|            2.5|                     25|                      20|                 20|               180|
| Home     |        0.5|           3|            1.5|                     40|                      60|                 20|              1440|
| Home     |        0.0|           5|            2.0|                     30|                      10|                 15|              2880|


``` r
# added a clean data csv to private repo
write.csv(data, file = "cleaned_data.csv")
```

### Variable Discription

A discription of the variables are as followed:

-   `Location (fctr)`: Categorical variable, a person's usual study location.
-   `OptionalQ (dbl)`: Continuous variable, how long a person spends doing bonus questions.
-   `ProcrastLV (int)`: Discrete variable, the level of procrastination of which a person identifies. This is an ordinal scale from 1-7, 1 being not a procrastinator and 7 being the highest form of procrastination.
-   `Household_Hr (dbl)`: Continuous variable, the amount of daily household responsibilities in hours a person assumes.
-   `Commute_Hm_Sch_Min (dbl)`: Continuous variable, the amount of time it takes to commute from their home to school (one way) in minutes.
-   `Commute_Stu_Loc_Min (dbl)`: Continuous variable, the amount of time it takes to move to their usual study location in minutes.
-   `Time_On_Lab_Hr (dbl)`: Continuous variable, the amount of time taken to complete all four labs in hours.
-   `Spare_Time_Min (dbl)`: Continuous variable, the amount of spare time a person has left before the submission time.


**Summary**

![](summary.png)


### Procrastination

To Start our EDA we wanted to confirm our hypothesis that the pracratination distribution among students is approximately normal.

``` r
plot_Q1 <- ggplot(data, aes(x = ProcrastLV)) + geom_histogram(bins = 7, colour='white', fill = "#51B1D9") +theme_bw() + labs(x= "Level of Procrastination", y = "Frequency", title = "Distribution of Procrastination levels Among MDS Students") + scale_x_continuous(breaks = seq(1, 7, len = 7) )
plot_Q1
```

![](Milestone2_files/figure-markdown_github/unnamed-chunk-5-1.png)

### Study Location

Exactly what does the Ratio of students to study location look like?

``` r
plot_Q1 <- data %>% ggplot() + geom_bar(aes(x=Location), colour='white', fill = "#082042") +theme_bw() + labs(x= "Location", y = "Quantity of MDS Students", title = "Amount of MDS Students usual Study Location")
plot_Q1
```

![](Milestone2_files/figure-markdown_github/unnamed-chunk-6-1.png)

This seems to show that most student usually study at home however, the quantity of students who use school resources is still very high. Very few people use other locations to do there school work.

### Household Responsibilties vs Study Location

Proceeding further, we wanted to see if people who had more household responsibilities tend to study more from home.

``` r
plot_Q3 <- data %>% filter( Household_Hr < 45) %>% ggplot() + geom_point(aes(x = log(Household_Hr), y= log(Time_On_Lab_Hr), colour = Location), size = 2)  +theme_bw() + labs(x= "Household Responsibilities (log(hours))", y = "Time Spent on the Labs (log(hours))", title = "Relationship Between Time Spent on Labs versus Household Responsibilities ") + scale_color_manual(values  = c("#51B1D9", "#082042", "#BFA057"))
plot_Q3
```

![](Milestone2_files/figure-markdown_github/unnamed-chunk-7-1.png)

To give a more clear relationship we took the log scale of both axis, which did not seem to show anything substantial. This was unexpected as we anticipated people with more responsibilities to study more at home.

``` r
boxplot(Spare_Time_Min~ProcrastLV,
data=data,
main="Procrast. Level vs. Spare Time after Git Push",
xlab="Levels",
ylab="Spare Time",
col="white",
border="black"
)
```

![](Milestone2_files/figure-markdown_github/unnamed-chunk-8-1.png)
