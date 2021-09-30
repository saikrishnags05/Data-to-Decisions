
## 1) Code for reading in the dataset and/or processing the data

```r

dataFile<-"auto-mpg.csv.csv"

data<-read.table(dataFile, header=TRUE, sep=",", stringsAsFactors=FALSE, dec=".")
head(data)

```
