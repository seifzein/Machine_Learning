Machine learning algorithm 
========================================================

### We start with Data Slicing:
We first attempt to divid our training data set into 75% for training and 25% for testing

```r
library(caret)
```

```
## Loading required package: lattice
## Loading required package: ggplot2
```

```r
rawdata <- read.csv("pml-training.csv", na.strings = c("NA", ""))  ## reading data from csv file
## Removing NAs
NAs <- apply(rawdata, 2, function(x) {
    sum(is.na(x))
})
data <- rawdata[, which(NAs == 0)]
inTrain <- createDataPartition(y = data$classe, p = 0.35, list = FALSE)  ## try 0.25 next time
training <- data[inTrain, ]
testing <- data[-inTrain, ]
dim(training)
```

```
## [1] 6869   60
```

```r
# discards unuseful predictors
removeIndex <- grep("timestamp|X|user_name|new_window", names(training))
training <- training[, -removeIndex]
```

#### Exporing the data 

```r
plot(mldata$classe)
```

```
## Error: object 'mldata' not found
```

We will start pre-processing by the PCA


Then I will create a model for the prediction 



After creating the model for prediction, we want to test it with our validation dataset kept aside from the beginning when we sliced our training data.



Then we want to test our testing dataset 


