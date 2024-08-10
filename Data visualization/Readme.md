  Visualize Data using Amazon QuickSight
 
Created visualizations from a large dataset using Amazon S3 and Amazon Quicksight. Working with a dataset of 50,000 best-selling products on Amazon.com.

#Step 1: Download the Dataset
 Download the "Amazon Bestseller Dataset" CSV file and the "manifest.json" file from bright data for data source.
Click on "raw" and Control+S to save both files onto your computer.

#Step 2: Store the Dataset in Amazon S3
 Open the Amazon S3 console and click "Create Bucket."
 Name the bucket and keep the settings as default.
 Upload the CSV file and the "manifest.json" file into the bucket.
 Replace the URL in the "manifest.json" file with the S3 URL of your dataset.

#Step 3: Connect S3 Bucket with Amazon Quicksight
 Open the AWS management console and navigate to Amazon Quicksight.
 Sign up
 Select Amazon S3 and tick the box for the S3 bucket you created and click on new dataset.
 Enter the S3 URL to your "manifest.json" file and connect to Quicksight.
 Select "interactive sheet" to start creating visualizations.

#Step 4: Create Visualizations
 Drag fields into the graph to create visualizations (e.g., Most popular brands).
 Sort, filter, and customize the graphs on desired parameters(for e.g.: price,brands,etc)
 Experiment with different types of graphs like bar charts, pie charts, line graphs, etc.
