The purpose of this file is to explain the process for cleaning the data sets, all the variables used and all transformation work done to 
the data

## Download of data from the internet

The datasets were downloaded from the internet using the download.file commands. The files were stored in the local drive
as text files. These steps are detailed in Step 1 of the code.

## Initital reading of the data ( Steps 2,3 & 4 in the run.analysis.R code)

All the data sets were read into R using the read.table command. All the text files were converted to table format using
this command. The important files which are relevant for this exercise are the following

1. features - This table list down the variable names for all the observations. There are 561 variables under this table.
2. Labels - This tale lists down the activities in their numerical order. For eg. 1. denotes the activity "Walking", 2. "Walking_upstairs" and so on
3. subject_train - This table denotes the order of the subjects who performs various activities. There are 21 unique subjects who carry out the training realted activities. There are in total 7352 observations for these 21 subjects in the 
    subjects_train table.
4. X_train - This is the actual data set for the training related which is being analysed in this exercise. There are 7352 observations in this table and 561 variables. The number of observations corresponds to the number of observations in the subject_train table and the number of variables corresponds to the number of variables in the features table.
5. y_train - This table also have 7352 rows ( observations) and these rows denotes the activity which corresponds to each row in the X_train table.
6. subject_test - This table denotes the order of the subjects who performs various activities. There are 9 unique         subjects who carry out the training realted activities. There are in total 2947 observations for these 9 subjects in     the subjects_test table.
7. X_test - This is the actual data set for the training related which is being analysed in this exercise. There are 2947 observations in this table and 561 variables. The number of observations corresponds to the number of observations in the subject_test table and the number of variables corresponds to the number of variables in the features table.
8. y_test - This table also have 2947 rows ( observations) and these rows denotes the activity which corresponds to each row in the X_test table.

The other list of tables which have been read by the code like (bodyacc_x_test etc ) are not relevant for this exercise and therefore are not explained in this code book

## Transformation to the data set ( steps 5 & 6 in the run.analysis.R code)
    
    The y_train(test) data sets are in reality the activities perfomed against each observation row in the X-train(test) data sets. However since no description existed for the labels of activities, the corresponding description had to be added to the data set. The method used for adding the description was to replace the numerical observations ( numbers 1 to 6) with the activity labels corresponding to each number. i.e 1 for walking, 2 for Walking_upstairs etc. A for loop was constructed as per the number of observations ( 7352 or 2947) and the activity labels were pasted in place of the numerals.
        
The second tranformation done to the X_train(test) data set was to add the description labels to the 561 variables. The description of the variables were added by pasting the features table on the column names of the X_train(test) data set.

The third transformation done to the data set was to combine the X_train(test) data sets with their corresonding activity and subject data sets to form a comprehensive data set.

## Combining the training and test data sets ( Step 7)

Once the above mentioned transformation was completed, the training and test data sets were combined with the rbind command to form a single data set.

## Subsetting of the data set to take only the varibles which corresponds to mean and SD ( Step 8)

The next step done was to subset the combined data set which had a total of 561 variables to around 66 variables by selecting the variables related to mean or standard deviation.

Column numbers (1,2,3,4,5,6,7,8,43,44,45,46,47,48,83,84,85,86,87,88,123,124,125,126,127,128,163,164,165,166,167,168,203,204,229,230,242,243,255,256,268,269,270,271,272,273,347,348,349,350,351,352,426,427,428,429,430,431,505,506,518,519,531,532,544,545) were those columns corresponding to either mean or standard deviation and therefore these columns were selected to subset to a more compact dataset.

Once the relevant variables were selected, proper naming was given using the make.names command

## Calculating the average of each variable ( Step 9)
The next important step which was done with the combined data set was to calculate the average of each variable. The average was calculated, activity wise and subject wise. So in effect each subject will have 6 sets of averages which corresponds to each activity the subject performs . This was done with the aggregate command and the total number of records of the data set was reduced to 180.

## Creating a text file for the tidy data set ( Step 10)
This was the last step which was done with the script.

