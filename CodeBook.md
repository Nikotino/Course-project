RUN ANALYSIS
##1. Variables

Subjects
- The number of each participants in the measurement
integer 1:30

Activities

6 types of activities during which the measurements were made
- 1 WALKING 
- 2 WALKING_UPSTAIRS  
- 3 WALKING_DOWNSTAIRS 
- 4 SITTING
- 5 STANDING 
- 6 LAYING

Measurements

Mean value and Standard deviation of signal measurements collected from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ.  '-XYZ' is used to denote 3-axial signals in the X, Y and Z directions.
-	tBodyAcc-XYZ: body acceleration 
-	tGravityAcc-XYZ: gravity acceleration 
-	tBodyAccJerk-XYZ: body acceleration Jerk signal
-	tBodyGyro-XYZ: body angular velocity
-	tBodyGyroJerk-XYZ: body angular velocity Jerk signal
-	tBodyAccMag: magnitude of body acceleration calculated using the Euclidean norm
-	tGravityAccMag: magnitude of gravity acceleration calculated using the Euclidean norm
-	tBodyAccJerkMag: magnitude of body acceleration Jerk signal calculated using the Euclidean norm
-	tBodyGyroMag: magnitude of gravity acceleration calculated using the Euclidean norm
-	tBodyGyroJerkMag: magnitude of gravity acceleration Jerk signal calculated using the Euclidean norm
-	fBodyAcc-XYZ: Fast Fourier Transform applied to body acceleration signal
-	fBodyAccJerk-XYZ: Fast Fourier Transform applied to body acceleration Jerk signal
-	fBodyGyro-XYZ: Fast Fourier Transform applied to gravity acceleration signal
-	fBodyAccMag: Fast Fourier Transform applied to body acceleration magnitude
-	fBodyAccJerkMag: Fast Fourier Transform applied to body acceleration Jerk signal magnitude
-	fBodyGyroMag: Fast Fourier Transform applied to gravity acceleration signal
-	fBodyGyroJerkMag: Fast Fourier Transform applied to gravity acceleration Jerk signal


##2. Data source
The initial data source is obtained from Human Activity Recognition database and included the following files:
 - features_info.txt': list of variables used on the feature vector.
- 'features.txt': List with the names of measurements
- 'activity_labels.txt': List of activity names 
- 'train/X_train.txt': measurement data from training set
- 'train/y_train.txt': participant’s number performed for each measurement in the training set
- 'test/X_test.txt': measurement data from test set
- 'test/y_test.txt': type of activity performed for each measurement in the test set
- 'train/subject_train.txt': information on subject who performed the activity for each window sample in the training set
- 'test/subject_test.txt': information on subject who performed the activity for each window sample in the test.set
The “Inertial Signals” folders for training set and test set contained in the data source were not used for the purpose of the project 

##3. Operations performed with the data sources
1.	Merging the blocks of information obtained from different files:
-	Information from X_train.txt and X_test.txt files was merged to create one dataframe X with measurement data
-	Table from features.txt was transformed (to convert the rows into columns) and merged with X dataframe to label X columns for the names of the measurements
-	Y_train.txt and Y_test.txt were merged into one vector “activity” for the list of activities of all measurements
-	subject_train.txt and subject_test.txt data were merged into one vector “subject” for the list of subjects for all measurements
2.	Extracting only the measurements on the mean and standard deviation for each measurement
From the resulting X dataframe only columns with mean and standard deviation measurements have been chosen. The choice has been made based on analysis of columns names extracted from features.txt file
This resulted into reduction of the dataframe from 563 to 68 columns
3.	Labeling activity dataset with the names of activity
Numeric information on activity types in the “activity” column has been replaced with labels extracted from “'activity_labels.txt'” file
4.	Creating a second, independent tidy data set with the average of each variable for each activity and each subject. 
New dataset has been created melting and casting the X_selected dataframe with reshape2 package.  The new dataset is names “means” and saved as txt.file
