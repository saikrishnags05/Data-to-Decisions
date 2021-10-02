

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

Lets us take a limited data frame for the table like age,program name and program description
#  1. One bar chart, properly labeled

```{r }
library(ggplot2)
ggplot(df_HFS, aes(x=age))+ geom_bar(width=0.75, fill="steelblue")+theme_minimal()+facet_wrap(state~program_name)+labs(title = "Bar plot based on Age based on program description") +ylab('Program Description')+ylab('Age')
```


# 2. One scatter plot of two variables, properly labeled, with a trend line added in
```{r }
p <- ggplot(data = df_HFS, aes(x =age , y =program_unit_description , color=program_name)) 
p + geom_point(size = 3) + geom_smooth(method = "lm")+ labs(title = "Scatter plot based on Age &
Program Descriptionwith a trend line") +ylab('Program Description')+ylab('Age')
```
# 3. One faceted plot of two variables, properly labeled

```{r  out.height= '100%' }
p <- ggplot(data = df_HFS, aes(x =age , y =program_unit_description , color=program_name)) 
p + geom_point(size = 3) +facet_wrap(state~program_type)+labs(title = "Scatter plot based on  Age and Program Description")+
  ylab('Age')+ylab('Program Description')
```


