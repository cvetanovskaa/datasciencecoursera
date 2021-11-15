# Getting & Cleaning Data Final Project

This proejct uses the `Human Activity Recognition Using Smartphones Data Set` from UCI Machine Learning Repository. The data contains information on 6 types of activities, that a group of 30 volunteers had performed. Using smartphones' accelerometers and gyroscopes, the volunteers' 3-axial linear acceleration and 3-axial angular velocity had been measures.

The `run_analysis.R` script performs a number of steps on the dataset provided by UCI ML Repo, to combine the split up dataset, to clean up the column names, and associate the correct acitvity with the each measurement.
The script requires the dyplr package is installed, and that the correct data set is in the same folder as the script. It also expects that the dataset has been unziped. 

For more detailed explanation of what each variable does, look at the Codebook
