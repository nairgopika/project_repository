Static website hosting using S3 bucket

Step 1: Design Your Website
    Downloaded a free CSS framework

Step 2: Set Up Amazon S3 Bucket
    Go to the AWS Management Console and open the Amazon S3 console.
    Click "Create bucket" and enter a unique name for your bucket.
    Enable public access.
    In the "Properties" section, enable "Static website hosting."
    Upload your website files to the bucket.
    In the "Permissions" section update the policy
Bucket policy:
              {
                    "Version": "2012-10-17",
                          "Statement": [
                      {
                          "Sid": "Statement1",
                           "Effect": "Allow",
                           "Principal": "*",
                           "Action": "s3:*",
                           "Resource": "arn:aws:s3:::<bucket-name>/*"
                         }
                          ]
              }
          
    Set the bucket permissions to allow public access.

Step 3:Bucket hosting
	Bucket website endpoint
	When you configure your bucket as a static website, the website is available at the AWS Region-specific website endpoint of the bucket.
	In this project (http://testpublicbucketmay.s3-website-us-east-1.amazonaws.com) was the endpoint.
