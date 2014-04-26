# Create tidy data set from human movement smartphone data #

The run_analysis.r script creates a tidy data set containing the means of each variable in each activity for each subject from the human movement smartphone data from the [UCI Machine Learning Repository](http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones)

This document describes the steps that run_analysis.r file executes in order to prepare the final data set

#The repository includes the following files:#

1. 'README.md'
* 'CodeBook.md''
* 'run_analysis.r'

# Steps in the 'run_analysis.r' script #

# load plyr package for later use to summarize data
	library(plyr)

## Load training and test data sets ##
### features list ###
	featureList<-read.table("./UCI HAR Dataset/features.txt",sep=" ")

### test data ###
	subject_test<-read.table("./UCI HAR Dataset/test/subject_test.txt",sep=" ")
	y_test<-read.table("./UCI HAR Dataset/test/y_test.txt",sep=" ")
	X_test<-read.table("./UCI HAR Dataset/test/X_test.txt",sep=" ")

### training data ###
	subject_train<-read.table("./UCI HAR Dataset/train/subject_train.txt",sep=" ")
	y_train<-read.table("./UCI HAR Dataset/train/y_train.txt",sep=" ")
	X_train<-read.table("./UCI HAR Dataset/train/X_train.txt",sep=" ")


## Combine the training and the test sets to create a single data set ##
## original data from [here](https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip)  ##
## from the UCI Machine Learning Repository [here](http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones) ##
	test_data<-cbind(subject_test,y_test, X_test) #combine test data
	train_data<-cbind(subject_train,y_train, X_train) #combine training data

	All_data<-rbind(train_data,test_data) #combine test and training data

## Label variables with descriptive names ##
	namesList<-featureList[,2] #get the raw variable names
	newNamesList<-vector("character",length(namesList)) #initialize a vector for new 
                                                    #variable names where the 
                                                    #punctuation characters are 
                                                    #removed
	#remove punctation from variable names
	for (i in 1:length(namesList)){
        		newNamesList[i]<-gsub("[[:punct:]]", "", namesList[i])
	}
	newNamesList<-c("SubjectID","ActivityIndex",newNamesList)
	names(All_data)<-newNamesList #apply names


## Extracts the mean and standard deviation measures for each measurement ##
	VarSel<-c(1:2,c(1:6,41:46,81:86,121:126,161:166,201:202,214:215,227:228,240:241,
          253:254,266:271,345:350,424:429,503:504,
          516:517,529:530,542:543)+2) #identify the columns

	All_data_MeansStd<-All_data[,VarSel] #extract the relevant columns

	#sort the data according to respondent ID and Activity 
	All_data_MeansStd<-All_data_MeansStd[order(All_data_MeansStd$SubjectID, All_data_MeansStd$ActivityIndex),] 
        
## Define names for the activities in the data set as labels for the ActivityIndex factor ##
	All_data_MeansStd$ActivityIndex <- factor(All_data_MeansStd$ActivityIndex,
                                        levels = c(1,2,3,4,5,6),
                                        labels = c("WALKING", "WALKING_UPSTAIRS", 
                                        "WALKING_DOWNSTAIRS", "SITTING", 
                                        "STANDING", "LAYING"))

## Create a new data set that contains the average for each variable, for each activity and each subject ##
	SubjectMeans<-ddply(All_data_MeansStd, .(SubjectID, ActivityIndex), numcolwise(mean))

## Export the tidy data set to csv text file ##
	write.table(SubjectMeans,"./SubjectMeans.txt",sep=",")