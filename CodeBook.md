# Codebook for human movement smartphone data#

This codebook describes the tidy dataset produced by 'run_analysis.r'. The tidy data set is derived from the original data found on the [UCI Machine Learning Repository](http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones)

##Summary choices and changes from the original data set##

The tidy data set is a summary of the original data. It contains 180 observations and 68 variables.

The original data collects human movement data from 30 subjects completed 6 different activities

1. WALKING
- WALKING_UPSTAIRS
- WALKING_DOWNSTAIRS
- SITTING
- STANDING
- LAYING

Each subject performs these activities numerous times, and there are a number of observations for each subject completing each activity (usually between 40-100 observations for each activity for each individual in the original data set).

The observations (rows) in the original data are composed of a feature vector that contains variables (columns) related to time and frequency signals obtained from the accelerometer and gyroscope on the smartphones the human subjects carried while performing the activities. Many statistics are reported for each measurement signal including things such as the mean and standard deviation of the signal, the min and max measurements, mad, sma, energy, igr, entropy, ar coefficient, correlation between X, Y, and Z dimension, and others.

The variable values in the original data set had already been summarized in the following way: Each variable was scaled between -1 and 1.

For more information about the original dataset contact: activityrecognition@smartlab.ws

The original data set was summarized in two ways for the tidy data set: 'SubjectMeans.txt'

1. Only a subset of the original variables was selected. The variables selected correspond to the mean and standard deviations of each of the measurement features. 
- Only the means for each activity for each individual are reported for the variables selected

Some variables with the word 'mean' in the variable name were excluded from the tidy data set because they did not include a corresponding standard deviation variable. These additional 'mean' variables were taken as derived quantities that were not needed for this exercise since a mean and standard deviation were already reported for each of the measurement signals.

Additional to the means of the feature means and standard deviations, the 'SubjectMeans.txt' data set includes a subject ID variable is included to identify the subject and an Activity Index variable is included to identify the activity.

In summary, the tidy data set is derived from the original data set by the following steps, which are given in more detail in the 'README.md' file.

1. An R script called run_analysis.R was created 
- The script file merges the training and the test sets to create one data set
- The script file extracts only the measurements on the mean and standard deviation for each measurement. 
- The script file applies the variables names from the original data set to the new data set with special characters removed
- The script file creates a factor variable that labels each activity such as 'walking', 'sitting', etc.
- The script file exports a csv file (with a .txt extension for easy upload to Coursera) containing the tidy data set with the mean of each variable (both means and standard deviations) for each activity for each subject. 

##Study design##

The following information describes how the original data was collected. It is take from the README.txt file from the original data set  [original data set](http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones)

Citation: Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz. Human Activity Recognition on Smartphones using a Multiclass Hardware-Friendly Support Vector Machine. International Workshop of Ambient Assisted Living (IWAAL 2012). Vitoria-Gasteiz, Spain. Dec 2012

###Human Activity Recognition Using Smartphones Dataset Version 1.0###

Jorge L. Reyes-Ortiz, Davide Anguita, Alessandro Ghio, Luca Oneto.
Smartlab - Non Linear Complex Systems Laboratory
DITEN - Universit? degli Studi di Genova.
Via Opera Pia 11A, I-16145, Genoa, Italy.
activityrecognition@smartlab.ws
www.smartlab.ws

The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data. 

The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain. See 'features_info.txt' for more details. 

####For each record it is provided:####

* Triaxial acceleration from the accelerometer (total acceleration) and the estimated body acceleration.
- Triaxial Angular velocity from the gyroscope. 
- A 561-feature vector with time and frequency domain variables. 
- Its activity label. 
- An identifier of the subject who carried out the experiment.

####The dataset includes the following files: ####

* 'README.txt'
- 'features_info.txt': Shows information about the variables used on the feature vector.
- 'features.txt': List of all features.
- 'activity_labels.txt': Links the class labels with their activity name.
- 'train/X_train.txt': Training set.
- 'train/y_train.txt': Training labels.
- 'test/X_test.txt': Test set.
- 'test/y_test.txt': Test labels.

The following files are available for the train and test data. Their descriptions are equivalent. 

* 'train/subject_train.txt': Each row identifies the subject who performed the activity for each window sample. Its range is from 1 to 30. 
- 'train/Inertial Signals/total_acc_x_train.txt': The acceleration signal from the smartphone accelerometer X axis in standard gravity units 'g'. Every row shows a 128 element vector. The same description applies for the 'total_acc_x_train.txt' and 'total_acc_z_train.txt' files for the Y and Z axis. 
- 'train/Inertial Signals/body_acc_x_train.txt': The body acceleration signal obtained by subtracting the gravity from the total acceleration. 
- 'train/Inertial Signals/body_gyro_x_train.txt': The angular velocity vector measured by the gyroscope for each window sample. The units are radians/second. 

####Notes: ####
* Features are normalized and bounded within [-1,1].
- Each feature vector is a row on the text file.

For more information about this dataset contact: activityrecognition@smartlab.ws

#### License: ####

Use of this dataset in publications must be acknowledged by referencing the following publication [1] 

[1] Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz. Human Activity Recognition on Smartphones using a Multiclass Hardware-Friendly Support Vector Machine. International Workshop of Ambient Assisted Living (IWAAL 2012). Vitoria-Gasteiz, Spain. Dec 2012

This dataset is distributed AS-IS and no responsibility implied or explicit can be addressed to the authors or their institutions for its use or misuse. Any commercial use is prohibited.

Jorge L. Reyes-Ortiz, Alessandro Ghio, Luca Oneto, Davide Anguita. November 2012.


##Codebook - Variables##

**Variable Number 	Variable Name 		Variable Type		Description**

1.	SubjectID	Categorical	Index from 1-30 identifying the human subjects in the experiment
2.	ActivityIndex	Categorical	The movement activity corresponding to the observation
			1 WALKING
			2 WALKING_UPSTAIRS
			3 WALKING_DOWNSTAIRS
			4 SITTING
			5 STANDING
			6 LAYING
3.	tBodyAccmeanX	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
4.	tBodyAccmeanY	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
5.	tBodyAccmeanZ	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
6.	tBodyAccstdX	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
7.	tBodyAccstdY	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
8.	tBodyAccstdZ	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
9.	tGravityAccmeanX	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
10.	tGravityAccmeanY	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
11.	tGravityAccmeanZ	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
12.	tGravityAccstdX	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
13.	tGravityAccstdY	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
14.	tGravityAccstdZ	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
15.	tBodyAccJerkmeanX	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
16.	tBodyAccJerkmeanY	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
17.	tBodyAccJerkmeanZ	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
18.	tBodyAccJerkstdX	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
19.	tBodyAccJerkstdY	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
20.	tBodyAccJerkstdZ	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
21.	tBodyGyromeanX	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
22.	tBodyGyromeanY	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
23.	tBodyGyromeanZ	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
24.	tBodyGyrostdX	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
25.	tBodyGyrostdY	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
26.	tBodyGyrostdZ	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
27.	tBodyGyroJerkmeanX	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
28.	tBodyGyroJerkmeanY	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
29.	tBodyGyroJerkmeanZ	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
30.	tBodyGyroJerkstdX	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
31.	tBodyGyroJerkstdY	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
32.	tBodyGyroJerkstdZ	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
33.	tBodyAccMagmean	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
34.	tBodyAccMagstd	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
35.	tGravityAccMagmean	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
36.	tGravityAccMagstd	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
37.	tBodyAccJerkMagmean	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
38.	tBodyAccJerkMagstd	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
39.	tBodyGyroMagmean	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
40.	tBodyGyroMagstd	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
41.	tBodyGyroJerkMagmean	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
42.	tBodyGyroJerkMagstd	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
43.	fBodyAccmeanX	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
44.	fBodyAccmeanY	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
45.	fBodyAccmeanZ	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
46.	fBodyAccstdX	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
47.	fBodyAccstdY	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
48.	fBodyAccstdZ	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
49.	fBodyAccJerkmeanX	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
50.	fBodyAccJerkmeanY	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
51.	fBodyAccJerkmeanZ	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
52.	fBodyAccJerkstdX	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
53.	fBodyAccJerkstdY	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
54.	fBodyAccJerkstdZ	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
55.	fBodyGyromeanX	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
56.	fBodyGyromeanY	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
57.	fBodyGyromeanZ	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
58.	fBodyGyrostdX	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
59.	fBodyGyrostdY	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
60.	fBodyGyrostdZ	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
61.	fBodyAccMagmean	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
62.	fBodyAccMagstd	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
63.	fBodyBodyAccJerkMagmean	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
64.	fBodyBodyAccJerkMagstd	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
65.	fBodyBodyGyroMagmean	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
66.	fBodyBodyGyroMagstd	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
67.	fBodyBodyGyroJerkMagmean	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity
68.	fBodyBodyGyroJerkMagstd	Continuous	Mean of a normalized variable [-1, 1] corresponding to all observations for a given subject for a specific human movement activity

