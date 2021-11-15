---
title: "CodeBook"
author: "Aleksandra Cvetanovska"
date: "11/14/2021"
output: 
  html_document: 
    keep_md: yes
---



## Getting & Cleaning Data Final Project CodeBook

This codebook describes the `run_analysis.R` script, which is used to clean the `Human Activity Recognition Using Smartphones Data Set` provided by UCI Machine Learning Repository.

The data is downloaded from https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip, and unzipped, thus creating the "UCI HAR Dataset" folder.

The script goes through 6 steps:

1. Load all files, and store them in appropriately-named variables 
  - activity_labels.txt (6 x 2) - Contains mapping of activities names, to an ID, stored in labels
  - features.txt (561 x 2) - Contains a list of all of the features measured, stored in features
  - subject_test.txt (2947 x 1) - Contains a list of IDs of 9/30 volunteers, stored in subject_test
  - X_test.txt (2947 x 561) - Contains test data of values of the features measured, stored in x_test
  - y_test.txt (2947 x 561) - Contains test data of activities' IDs, stored in y_test
  - subject_test.txt (7352 x 1) - Contains a list of IDs of 21/30 volunteers, stored in subject_train
  - X_test.txt (7352 x 561) - Contains train data of values of the features measured, stored in x_train
  - y_test.txt (7352 x 1) - Contains train data of activities' IDs, stored in y_train
  
2. Combine all train datasets with their corresponding test dataset
  - Create x_combined by row-wise combining x_test with x_train 
  - Create y_combined by row-wise combining y_test with y_train
  - Create subject_combined by row-wise combining subject_test with subject_train

3. Combine all of the different datasets together
  - Create full_data_combined by column-wise combining x_combined, y_combined, and subject_combined
  
4. Grab only mean & std measurements, along with subject & number columns
  - Create mean_std_data (10299 X 81) by removing all columns that don't include 'mean' or 'std' in their name, in addition to the columns subject, and number

5. Use descriptive names for the activities, instead of a number
  - Update the second column of mean_std_data to contain the activity's name instead of it's ID
  
6. Update column names to be more descriptive
  - Update 'subject' col name to 'Subject'
  - Update 'number' col name to 'Activity Performed'
  - Update all columns containing . (dot), to have a ' ' (space) instead
  - Update all columns containing 'bodybody', to have 'Body' instead
  - Update all columns containing 'tbody', to have 'Time Body' instead
  - Update all columns containing 'fbody', to have 'Frequency Body' instead
  - Update all columns containing 'std', to have 'Standard Deviation' instead
  - Update all columns containing 'mean', to have 'Mean' instead
  - Update all columns containing 'acc', to have 'Accelerometer' instead
  - Update all columns containing 'gyro', to have 'Gyroscope' instead
  - Update all columns containing 'mag', to have 'Magnitude' instead
  - Update all columns containing 'gravity', to have 'Gravity' instead
  - Update all columns containing 'angle', to have 'Angle' instead
  - Update all columns containing 'jerk', to have 'Jerk' instead
  - Update all columns containing 't ', to have 'Time' instead

7. Store clean dataset, with with the average of each variable for each activity and each subject in a file
  - Create clean_data, by using dyplr library to calculate the mean of all variables
  - Export `CleanData.txt` file, containing the final, clean dataset
