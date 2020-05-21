1. Downloads the dataset into R
2. Assigning of data to variables
	a. features stores features.txt : 561 rows, 2 columns
		The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ.
	b. activities store activity_labels.txt : 6 rows, 2 columns
		List of activities performed when the corresponding measurements and their codes were taken
	c. subject_test stores subject_test.txt : 2947 rows, 1 column
		contains test data of 9/30 volunteer test subjects being observed
	d. x_test stores X_test.txt : 2947 rows, 561 columns
		contains recorded features test data
	e. y_test stores y_test.txt : 2947 rows, 561 columns
		contains test data of activities’code labels
	f. subject_train stores subject_train.txt : 7352 rows, 1 column
		contains train data of 21/30 volunteer subjects being observed
	g. x_train stores X_train.txt : 7352 rows, 561 columns
		contains recorded features train data
	h. y_train stores y_train.txt : 7352 rows, 1 columns
		contains train data of activities’code labels
3. Merges the training and the test sets to create one data set.
	a. X : 10299 rows, 561 columns
		created by merging x_train and x_test using rbind() function
	b. Y : 10299 rows, 561 columns
		created by merging y_train and y_test using rbind() function
	c. Subject : 10299 rows, 1 column
		created by merging subject_train and subject_test using rbind() function
	d. Merged_Data : 10299 rows, 563 column
		created by merging Subject, Y and X using cbind() function
4. Extracts only the measurements on the mean and standard deviation for each measurement.
	a. TidyData (10299 rows, 88 columns) 
		created by subsetting Merged_Data, selecting only columns: subject, code and the measurements on the mean and standard deviation (std) for each measurement
5. Uses descriptive activity names to name the activities in the data set
	a. Entire numbers in code column of the TidyData replaced with corresponding activity taken from second column of the activities variable
6. Appropriately labels the data set with descriptive variable names
	a. code column in TidyData renamed into activities
	b. All Acc in column’s name replaced by Accelerometer
	c. All Gyro in column’s name replaced by Gyroscope
	d. All BodyBody in column’s name replaced by Body
	e. All Mag in column’s name replaced by Magnitude
	f. All start with character f in column’s name replaced by Frequency
	g. All start with character t in column’s name replaced by Time
7. From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject
	a. Final Data : 180 rows, 88 columns	
		Created by summarizing TidyData taking mean for each activity after grouping by subject and activity.
	b. Export FinalData into FinalData.txt