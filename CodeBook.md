The run_analysis.R script performs the data preparation and then followed by the 5 steps required as described in the course project’s definition.

Download the data
Dataset is downloaded and unzipped under the folder called UCI HAR Dataset

Assign each data to variables
features <- features.txt
The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ.
activities <- activity_labels.txt 
List of activities performed when the corresponding measurements were taken and its codes (labels)
subject_test <- test/subject_test.txt
contains test data of 9/30 volunteer test subjects being observed
x_test <- test/X_test.txt
contains recorded features test data
y_test <- test/y_test.txt
contains test data of activities’code labels
subject_train <- test/subject_train.txt
contains train data of 21/30 volunteer subjects being observed
x_train <- test/X_train.txt
contains recorded features train data
y_train <- test/y_train.txt
contains train data of activities’code labels

Step 1: Merges the training and the test sets to create one data set
"X" is created by merging x_train and x_test using rbind() function
"Y" is created by merging y_train and y_test using rbind() function
"Subject" is created by merging subject_train and subject_test using rbind() function
'Merged_Data" is created by merging Subject, Y and X using cbind() function

Step 2: Extracts only the measurements on the mean and standard deviation for each measurement
TidyData is created by subsetting Merged_Data, selecting only columns: subject, code and the measurements on the mean and standard deviation (std) for each measurement

Step 3: Uses descriptive activity names to name the activities in the data set
Entire numbers in code column of the TidyData are replaced with corresponding activity taken from second column of the activities variable

Step 4: Appropriately labels the data set with descriptive variable names
TidyData renamed into activities
Acc renamed into Accelerometer
Gyro renamed into Gyroscope
BodyBody renamed into Body
Mag renamed into Magnitude
^f renamed into Frequency
^t renamed into Time

Step 5: From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject
TData is created by sumarizing TidyData taking the means of each variable for each activity and subject, after groupped by subject and activity.
Export TData into tidydata.txt file.
