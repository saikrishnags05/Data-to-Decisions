

# "HFS Data Exploration"
# author: "Sai Krishna Gaduputi Subbammagari"



Let us read the HFS Service Data.csv file into R-studio

```{r}
library(ggplot2)
df_HFS<-read.csv("HFS Service Data.csv")
str(df_HFS)
```
str() function gives use the structure of the whole variables in csv files.

Let us see the summery of the CSV file.
```{r}
summary(df_HFS)
```


Lets us take a limited data frame for the table like age,program name and program description
#  1. One bar chart, properly labeled

```{r }
library(ggplot2)
ggplot(df_HFS, aes(x=age))+ geom_bar(width=0.75, fill="steelblue")+theme_minimal()+facet_wrap(state~program_name)+labs(title = "Bar plot based on Age based on program description") +ylab('Program Description')+ylab('Age')
```
![Bar Plot](https://github.com/saikrishnags05/Data-to-Decisions/blob/main/Data%20Exploration/plots/barplot_1.PNG)

### According to the Bar plot we can tell that most of the people from IA and NE taken part in Mental Health in all age groups.
* In **IA** most of the people are in between **0-20** age group who attended the **Mental Health** event.
* People between age group 20-40 have attended **Substance Use** in **IA** .
* In **NE** most of the people are in between **20-40** age group who attended the **Mental Health** event.



# 2. One scatter plot of two variables, properly labeled, with a trend line added in
```{r }
p <- ggplot(data = df_HFS, aes(x =age , y =program_unit_description , color=program_name)) 
p + geom_point(size = 3) + geom_smooth(method = "lm")+ labs(title = "Scatter plot based on Age &
Program Descriptionwith a trend line") +ylab('Program Description')+xlab('Age')
```
![Scattor Plot](https://github.com/saikrishnags05/Data-to-Decisions/blob/main/Data%20Exploration/plots/Q2.PNG)
The above image is a scatter plot with two variables `X axes` is about the age group and `Y axis` is about the program description
with trend line.
* most of the people took part in Mental Health event for their behavioral health is all the 5 areas.
	* nebrska 
	* iowa
	* south carolina
	* north carolina
	* colorado
* second people in IA,NE have attended to Substance Use events.
* Events on Gambline is mostly taken place in Iowa.
## Note
* But according to the program name and program description we need to check if name of the program is `Substance Use` or `Substance Abuse`

# 3. One faceted plot of two variables, properly labeled

```{r  out.height= '100%' }
p <- ggplot(data = df_HFS, aes(x =state , y =program_name , color= is_client_involved)) 
p + geom_point(size = 3) +facet_wrap(~ethnic_identity)+
labs(title = "Scatter plot based on  Age and Program faceted with ethnic identity W.R.T to client involvement") +ylab('Name of the Program ')+xlab('Age')
```

![Faceted Plot](https://github.com/saikrishnags05/Data-to-Decisions/blob/main/Data%20Exploration/plots/Q3.PNG)


The above graph explains us about the events that took place in the different places and involment of clients  invloved W.R.T to 
ethnic identity
* Clients did not involved in gambling event. 
Note: 
There are some ethnic Identity that are missing.
* some are  not collected and unknown


**According to ht above 3 plots we came under a consideration that there are few missing values, short formas for the states**

Verify if we have any missing values or not.
with command `any(is.na())` if we get TRUE then there are some missing values if 
False then we have NA values.

```{r}
sapply(df_HFS, function(x) sum(is.na(x)))
```
There are some missing values.
We have  short forms in `df_HFS$state` for state names now we rewrite the state name normaly
names
```{r}
s<-c(unique(df_HFS$state))
s
```
now change it according ot the short forms.

```{r}
df_HFS$state<- as.character(df_HFS$state)
df_HFS$state[df_HFS$state == "NE"] <- "nebrska"
df_HFS$state[df_HFS$state == "IA"] <- "iowa"
df_HFS$state[df_HFS$state == "SC"] <- "south carolina"
df_HFS$state[df_HFS$state == "NC"] <- "north carolina"
df_HFS$state[df_HFS$state == "CO"] <- "colorado"
c(unique(df_HFS$state))
```
