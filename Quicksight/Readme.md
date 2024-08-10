Netflix Titles Visualization with Amazon QuickSight

This project demonstrates how to visualize a dataset of TV shows and movies available on Netflix using Amazon QuickSight. The dataset is stored in an Amazon S3 bucket and includes a CSV file and a manifest.json file for connecting with QuickSight.

Prerequisites

An AWS account with access to Amazon S3 and Amazon QuickSight.
The dataset files (Netflix_titles.csv and manifest.json) downloaded from Bright Data.

Step-by-Step Instructions

Step 1: Download the Dataset
Download the Netflix_titles.csv file.
Download the manifest.json file from Bright Data, which serves as the data source.

Step 2: Store the Dataset in Amazon S3
Open the Amazon S3 console.
Click on "Create Bucket" to create a new S3 bucket.
Name the bucket as desired and leave the settings as default.
Upload the Netflix_titles.csv and manifest.json files into the newly created bucket.
Open the manifest.json file and replace the existing URL with the S3 URL of your Netflix_titles.csv file.

Step 3: Connect the S3 Bucket with Amazon QuickSight
Open the AWS Management Console and navigate to Amazon QuickSight.
If you haven't already signed up, complete the signup process.
Once inside QuickSight, select "Manage Data" and then click "New Dataset."
Choose Amazon S3 as the data source.
Tick the box for the S3 bucket you created in Step 2.
Enter the S3 URL to your manifest.json file and click "Connect."
Choose "Interactive Sheet" to start creating visualizations.

Step 4: Create Visualizations
Drag and drop fields from the dataset into the graph area to create visualizations.
Use sorting and filtering options to customize the data displayed on the graphs.
Experiment with different types of visualizations, such as bar charts, pie charts, and line graphs.
Example parameters to visualize: Movie titles, release years, content types, etc.
Save your visualizations to share insights or create reports.

Conclusion

By following these steps, you have successfully created visualizations of Netflix's dataset using Amazon QuickSight. These visualizations provide valuable insights into the variety and distribution of content available on Netflix.
