HFS Data Exploration
================
Sai Krishna Gaduputi Subbammagari

Let us read the HFS Service Data.csv file into R-studio

``` r
library(ggplot2)
df_HFS<-read.csv("HFS Service Data.csv")
str(df_HFS)
```

    ## 'data.frame':    8745 obs. of  51 variables:
    ##  $ gender                  : chr  "Male" "Female" "Female" "Female" ...
    ##  $ program_name            : chr  "Mental Health" "Mental Health" "Mental Health" "Mental Health" ...
    ##  $ program_type            : chr  "Counseling and Prevention" "Counseling and Prevention" "Counseling and Prevention" "Counseling and Prevention" ...
    ##  $ facility                : chr  "Heartland Family Service - Logan" "Center Mall Office" "Center Mall Office" "Center Mall Office" ...
    ##  $ job_title               : chr  "Clinical Supervisor" "THERAPIST II" "THERAPIST II" "THERAPIST II" ...
    ##  $ staff_name              : chr  "Poore, Lindsay" "Carlson, Kaitlin" "Carlson, Kaitlin" "Carlson, Kaitlin" ...
    ##  $ actual_date             : int  961 857 682 710 696 772 794 864 661 737 ...
    ##  $ duration                : chr  "0:00" "0:02" "0:51" "0:00" ...
    ##  $ event_name              : chr  "Daily Living Assessment DLA 20" "Collateral Note" "Individual Therapy" "Individual Therapy" ...
    ##  $ activity_type           : chr  "" "Phone" "" "" ...
    ##  $ encounter_with          : chr  "" "Client" "" "" ...
    ##  $ is_client_involved      : logi  TRUE TRUE TRUE TRUE TRUE TRUE ...
    ##  $ is_noshow               : logi  FALSE FALSE FALSE TRUE FALSE FALSE ...
    ##  $ is_locked               : logi  FALSE TRUE TRUE TRUE TRUE TRUE ...
    ##  $ is_billed               : logi  FALSE FALSE TRUE FALSE TRUE FALSE ...
    ##  $ is_paid                 : logi  FALSE FALSE FALSE FALSE FALSE FALSE ...
    ##  $ date_entered            : int  961 857 683 710 696 773 795 864 661 739 ...
    ##  $ user_entered_name       : chr  "Poore, Lindsay" "Carlson, Kaitlin V." "Carlson, Kaitlin V." "Carlson, Kaitlin V." ...
    ##  $ approved_date           : int  NA 857 689 714 697 773 795 864 662 739 ...
    ##  $ approved_staff_name     : chr  "" "Carlson, Kaitlin V." "Stanek, Sean" "Stanek, Sean" ...
    ##  $ submitted               : chr  "" "Approved" "Approved" "Approved" ...
    ##  $ is_approved             : int  0 1 1 1 1 1 1 1 1 1 ...
    ##  $ is_notapproved          : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ is_notapproved_subm     : int  1 0 0 0 0 0 0 0 0 0 ...
    ##  $ program_unit_description: chr  "Behavioral Health IA -  Mental Health" "Behavioral Health NE - Mental Health" "Behavioral Health NE - Mental Health" "Behavioral Health NE - Mental Health" ...
    ##  $ sc_code                 : chr  "1311-16" "1311-05" "1311-05" "1311-05" ...
    ##  $ duration_num            : int  0 2 51 0 50 80 4 2 52 115 ...
    ##  $ do_not_bill             : logi  FALSE FALSE FALSE FALSE FALSE FALSE ...
    ##  $ do_not_pay              : logi  FALSE FALSE FALSE FALSE FALSE FALSE ...
    ##  $ general_location        : chr  "" "Homeless Shelter" "Home" "Telehealth - Phone" ...
    ##  $ program_modifier        : chr  "No Modifier - IA" "Heartland Housing Navigation" "Heartland Housing Navigation" "Heartland Housing Navigation" ...
    ##  $ program_modifier_code   : chr  "NMODI" "HHN" "HHN" "HHN" ...
    ##  $ NormalWorkHours         : chr  "Yes" "Yes" "Yes" "Yes" ...
    ##  $ duration_other_num      : int  0 0 10 0 10 10 0 0 10 10 ...
    ##  $ duration_other          : chr  "0:00" "0:00" "0:10" "0:00" ...
    ##  $ travel_time_num         : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ travel_time             : chr  "0:00" "0:00" "0:00" "0:00" ...
    ##  $ planning_time_num       : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ planning_time           : chr  "0:00" "0:00" "0:00" "0:00" ...
    ##  $ total_duration_num      : int  0 2 61 0 60 90 4 2 62 125 ...
    ##  $ total_duration          : chr  "0:00" "0:02" "1:01" "0:00" ...
    ##  $ reason_for_no_show      : chr  "" "" "" "Client No Show - No Call" ...
    ##  $ is_billable             : logi  FALSE FALSE FALSE FALSE FALSE FALSE ...
    ##  $ zip                     : int  0 681 681 681 681 681 681 681 681 681 ...
    ##  $ state                   : chr  "IA" "NE" "NE" "NE" ...
    ##  $ age                     : int  12 26 25 25 25 25 25 26 25 25 ...
    ##  $ recordID                : int  298 338 338 338 338 338 338 338 338 338 ...
    ##  $ simple_race             : int  8 16 16 16 16 16 16 16 16 16 ...
    ##  $ ethnic_identity         : chr  "Not Spanish/Hispanic/Latino" "Not Spanish/Hispanic/Latino" "Not Spanish/Hispanic/Latino" "Not Spanish/Hispanic/Latino" ...
    ##  $ gender_identity         : chr  "Not Obtained" NA NA NA ...
    ##  $ sexual_orientation      : chr  "Not Obtained" NA NA NA ...

str() function gives use the structure of the whole variables in csv
files.

Let us see the summery of the CSV file.

``` r
summary(df_HFS)
```

    ##     gender          program_name       program_type         facility        
    ##  Length:8745        Length:8745        Length:8745        Length:8745       
    ##  Class :character   Class :character   Class :character   Class :character  
    ##  Mode  :character   Mode  :character   Mode  :character   Mode  :character  
    ##                                                                             
    ##                                                                             
    ##                                                                             
    ##                                                                             
    ##   job_title          staff_name         actual_date       duration        
    ##  Length:8745        Length:8745        Min.   : -31.0   Length:8745       
    ##  Class :character   Class :character   1st Qu.: 102.0   Class :character  
    ##  Mode  :character   Mode  :character   Median : 373.0   Mode  :character  
    ##                                        Mean   : 595.8                     
    ##                                        3rd Qu.: 930.0                     
    ##                                        Max.   :3267.0                     
    ##                                        NA's   :4                          
    ##   event_name        activity_type      encounter_with     is_client_involved
    ##  Length:8745        Length:8745        Length:8745        Mode :logical     
    ##  Class :character   Class :character   Class :character   FALSE:547         
    ##  Mode  :character   Mode  :character   Mode  :character   TRUE :8198        
    ##                                                                             
    ##                                                                             
    ##                                                                             
    ##                                                                             
    ##  is_noshow       is_locked       is_billed        is_paid       
    ##  Mode :logical   Mode :logical   Mode :logical   Mode :logical  
    ##  FALSE:7660      FALSE:409       FALSE:4661      FALSE:8745     
    ##  TRUE :1085      TRUE :8336      TRUE :4084                     
    ##                                                                 
    ##                                                                 
    ##                                                                 
    ##                                                                 
    ##   date_entered    user_entered_name  approved_date  approved_staff_name
    ##  Min.   : -29.0   Length:8745        Min.   :  -7   Length:8745        
    ##  1st Qu.: 103.0   Class :character   1st Qu.: 110   Class :character   
    ##  Median : 376.0   Mode  :character   Median : 385   Mode  :character   
    ##  Mean   : 597.5                      Mean   : 605                      
    ##  3rd Qu.: 930.0                      3rd Qu.: 944                      
    ##  Max.   :3268.0                      Max.   :3271                      
    ##  NA's   :4                           NA's   :587                       
    ##   submitted          is_approved     is_notapproved    is_notapproved_subm
    ##  Length:8745        Min.   :0.0000   Min.   :0.00000   Min.   :0.00000    
    ##  Class :character   1st Qu.:1.0000   1st Qu.:0.00000   1st Qu.:0.00000    
    ##  Mode  :character   Median :1.0000   Median :0.00000   Median :0.00000    
    ##                     Mean   :0.9332   Mean   :0.02001   Mean   :0.04677    
    ##                     3rd Qu.:1.0000   3rd Qu.:0.00000   3rd Qu.:0.00000    
    ##                     Max.   :1.0000   Max.   :1.00000   Max.   :1.00000    
    ##                                                                           
    ##  program_unit_description   sc_code           duration_num    do_not_bill    
    ##  Length:8745              Length:8745        Min.   :  0.00   Mode :logical  
    ##  Class :character         Class :character   1st Qu.:  0.00   FALSE:8539     
    ##  Mode  :character         Mode  :character   Median : 45.00   TRUE :206      
    ##                                              Mean   : 35.69                  
    ##                                              3rd Qu.: 50.00                  
    ##                                              Max.   :720.00                  
    ##                                                                              
    ##  do_not_pay      general_location   program_modifier   program_modifier_code
    ##  Mode :logical   Length:8745        Length:8745        Length:8745          
    ##  FALSE:8745      Class :character   Class :character   Class :character     
    ##                  Mode  :character   Mode  :character   Mode  :character     
    ##                                                                             
    ##                                                                             
    ##                                                                             
    ##                                                                             
    ##  NormalWorkHours    duration_other_num duration_other     travel_time_num
    ##  Length:8745        Min.   :  0.00     Length:8745        Min.   :0      
    ##  Class :character   1st Qu.:  0.00     Class :character   1st Qu.:0      
    ##  Mode  :character   Median :  8.00     Mode  :character   Median :0      
    ##                     Mean   : 12.95                        Mean   :0      
    ##                     3rd Qu.: 22.00                        3rd Qu.:0      
    ##                     Max.   :135.00                        Max.   :0      
    ##                                                                          
    ##  travel_time        planning_time_num planning_time      total_duration_num
    ##  Length:8745        Min.   :0         Length:8745        Min.   :  0.00    
    ##  Class :character   1st Qu.:0         Class :character   1st Qu.:  0.00    
    ##  Mode  :character   Median :0         Mode  :character   Median : 50.00    
    ##                     Mean   :0                            Mean   : 48.64    
    ##                     3rd Qu.:0                            3rd Qu.: 60.00    
    ##                     Max.   :0                            Max.   :825.00    
    ##                                                                            
    ##  total_duration     reason_for_no_show is_billable          zip       
    ##  Length:8745        Length:8745        Mode :logical   Min.   :  0.0  
    ##  Class :character   Class :character   FALSE:8745      1st Qu.:  0.0  
    ##  Mode  :character   Mode  :character                   Median :  0.0  
    ##                                                        Mean   :287.5  
    ##                                                        3rd Qu.:681.0  
    ##                                                        Max.   :809.0  
    ##                                                                       
    ##     state                age           recordID      simple_race     
    ##  Length:8745        Min.   : 1.00   Min.   :  1.0   Min.   :  0.000  
    ##  Class :character   1st Qu.:14.00   1st Qu.:131.0   1st Qu.:  1.000  
    ##  Mode  :character   Median :28.00   Median :270.0   Median :  1.000  
    ##                     Mean   :28.91   Mean   :259.5   Mean   :  5.346  
    ##                     3rd Qu.:40.00   3rd Qu.:391.0   3rd Qu.:  1.000  
    ##                     Max.   :72.00   Max.   :490.0   Max.   :128.000  
    ##                                                                      
    ##  ethnic_identity    gender_identity    sexual_orientation
    ##  Length:8745        Length:8745        Length:8745       
    ##  Class :character   Class :character   Class :character  
    ##  Mode  :character   Mode  :character   Mode  :character  
    ##                                                          
    ##                                                          
    ##                                                          
    ## 

Lets us take a limited data frame for the table like age,program name
and program description # 1. One bar chart, properly labeled

``` r
library(ggplot2)
ggplot(df_HFS, aes(x=age))+ geom_bar(width=0.75, fill="steelblue")+theme_minimal()+facet_wrap(state~program_name)+labs(title = "Bar plot based on Age based on program description") +ylab('count of Age W.R.T to location')+xlab('Age')
```

![Bar Plot](https://github.com/saikrishnags05/Data-to-Decisions/blob/main/Data%20Exploration/plots/barplot_1.PNG)<!-- -->

### According to the Bar plot we can tell that most of the people from IA and NE taken part in Mental Health in all age groups.

-   In **IA** most of the people are in between **0-20** age group who
    attended the **Mental Health** event.
-   People between age group 20-40 have attended **Substance Use** in
    **IA** .
-   In **NE** most of the people are in between **20-40** age group who
    attended the **Mental Health** event.

# 2. One scatter plot of two variables, properly labeled, with a trend line added in

``` r
p <- ggplot(data = df_HFS, aes(x =age , y =program_unit_description , color=program_name)) 
p + geom_point(size = 3) + geom_smooth(method = "lm")+ labs(title = "Scatter plot based on Age &
Program Descriptionwith a trend line") +ylab('Program Description')+xlab('Age')
```

    ## `geom_smooth()` using formula 'y ~ x'

![Scattor Plot](https://github.com/saikrishnags05/Data-to-Decisions/blob/main/Data%20Exploration/plots/Q2.PNG)<!-- -->

The above image is a scatter plot with two variables `X axes` is about
the age group and `Y axis` is about the program description with trend
line. \* most of the people took part in Mental Health event for their
behavioral health is all the 5 areas.

    * Nebraska

    * Iowa

    * South Carolina

    * North Carolina

    * Colorado

-   second people in IA,NE have attended to Substance Use events.

-   Events on Gambling is mostly taken place in Iowa.

## Note

-   But according to the program name and program description we need to
    check if name of the program is `Substance Use` or `Substance Abuse`

# 3. One faceted plot of two variables, properly labeled

``` r
p <- ggplot(data = df_HFS, aes(x =state , y =program_name , color= is_client_involved)) 
p + geom_point(size = 3) +facet_wrap(~ethnic_identity)+
labs(title = "Scatter plot based on  Age and Program faceted with ethnic identity W.R.T to client involvement") +ylab('Name of the Program ')+xlab('Age')
```
![Faceted Plot](https://github.com/saikrishnags05/Data-to-Decisions/blob/main/Data%20Exploration/plots/Q3.PNG)

The above graph explains us about the events that took place in the
different places and involvement of clients invloved W.R.T to ethnic
identity

-   Clients did not involved in gambling event.

# Note:

There are some ethnic Identity that are missing.

-   some are not collected and unknown

**According to ht above 3 plots we came under a consideration that there
are few missing values, short formas for the states**

Verify if we have any missing values or not. with command `any(is.na())`
if we get TRUE then there are some missing values if False then we have
NA values.

``` r
sapply(df_HFS, function(x) sum(is.na(x)))
```

    ##                   gender             program_name             program_type 
    ##                        0                        0                        0 
    ##                 facility                job_title               staff_name 
    ##                        0                        0                        0 
    ##              actual_date                 duration               event_name 
    ##                        4                        0                        0 
    ##            activity_type           encounter_with       is_client_involved 
    ##                        0                        0                        0 
    ##                is_noshow                is_locked                is_billed 
    ##                        0                        0                        0 
    ##                  is_paid             date_entered        user_entered_name 
    ##                        0                        4                        0 
    ##            approved_date      approved_staff_name                submitted 
    ##                      587                        0                        0 
    ##              is_approved           is_notapproved      is_notapproved_subm 
    ##                        0                        0                        0 
    ## program_unit_description                  sc_code             duration_num 
    ##                        0                        0                        0 
    ##              do_not_bill               do_not_pay         general_location 
    ##                        0                        0                        0 
    ##         program_modifier    program_modifier_code          NormalWorkHours 
    ##                        0                        0                        0 
    ##       duration_other_num           duration_other          travel_time_num 
    ##                        0                        0                        0 
    ##              travel_time        planning_time_num            planning_time 
    ##                        0                        0                        0 
    ##       total_duration_num           total_duration       reason_for_no_show 
    ##                        0                        0                        0 
    ##              is_billable                      zip                    state 
    ##                        0                        0                        0 
    ##                      age                 recordID              simple_race 
    ##                        0                        0                        0 
    ##          ethnic_identity          gender_identity       sexual_orientation 
    ##                        0                      499                     1069

There are some missing values. We have short forms in `df_HFS$state` for
state names now we rewrite the state name normaly names

``` r
s<-c(unique(df_HFS$state))
s
```

    ## [1] "IA" "NE" "CO" "NC" "SC"

now change it according ot the short forms.

``` r
df_HFS$state<- as.character(df_HFS$state)
df_HFS$state[df_HFS$state == "NE"] <- "nebrska"
df_HFS$state[df_HFS$state == "IA"] <- "iowa"
df_HFS$state[df_HFS$state == "SC"] <- "south carolina"
df_HFS$state[df_HFS$state == "NC"] <- "north carolina"
df_HFS$state[df_HFS$state == "CO"] <- "colorado"
c(unique(df_HFS$state))
```

    ## [1] "iowa"           "nebrska"        "colorado"       "north carolina"
    ## [5] "south carolina"

# future work according to the plot

``` r
df_NE<- subset(df_HFS, state=='NE')
```

``` r
p <- ggplot(data = df_HFS, aes(x =age , y =program_name , color= ethnic_identity)) 
p + geom_point(size = 3) +facet_wrap(~is_client_involved)+
  labs(title = "Scatter plot based on  Age and Program faceted with ethnic identity W.R.T to client involvement") +ylab('Name of the Program ')+xlab('Age')
```

<img src="GIT_data_exploration_files/figure-gfm/unnamed-chunk-10-1.png" height="100%" />
