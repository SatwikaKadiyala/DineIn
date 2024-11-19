# DineIn

Services Used:

•AWS S3: For frontend hosting

•AWS API Gateway: To route API requests

•AWS Lambda: For backend processing

•AWS CloudFront: To enable global content delivery

•GitHub: To store and manage source code

Follow the below steps:

Step 1: Set Up the Backend with AWS Lambda and API Gateway
1. Create a Lambda Function

•	Go to the AWS Lambda console and click Create Function. Choose an Author from Scratch.
•	Upload your backend code (index.js) as a .zip file.
•	Set the runtime to Node.js and configure the necessary permissions.


2.Test Lambda Locally

•Add a sample test payload in the AWS Lambda console and test your function to make sure it works as expected.

3. Set Up API Gateway

•Open the API Gateway service and create a new REST API.
•Define methods like /menu, /order, and /order, and link them to your Lambda function.

4. Deploy the API

•Deploy the API to a new stage (e.g., "prod"). Note down the base URL provided by API Gateway, as you’ll need it for the front end.


Step 2: Set Up the Frontend with AWS S3
1.	Build the React Project
Run the command:

npm run build
This creates a build/ directory containing optimized files for deployment.

2.	Create an S3 Bucket
   
•	In the AWS S3 console, click Create Bucket.
•	Enable the option for static website hosting.

4.	Upload Files
   
•	Upload the contents of the build/ directory to your S3 bucket.


6.	Set a Public Access Policy

•	To make the website accessible, apply this bucket policy (replace <BUCKET_NAME> with your bucket name):
 Link the Frontend to the Backend
•	Update the API URLs in your React project (App.js) to point to the API Gateway URL from Step 1.

Step 3: Optimize Delivery with AWS CloudFront
1.	Set Up CloudFront
•	Create a CloudFront distribution and set your S3 bucket as the origin.
•	Enable caching to improve performance for static content delivery.
2.	(Optional) Use a Custom Domain
•	If you have a domain, configure its DNS settings to point to the CloudFront distribution.


Step 4: Push Code to GitHub
1.	Initialize a Git Repository
•	Run the following commands in your project directory:
git init
git add.
git commit -m "Initial commit"
git branch -M main
git remote add origin <GITHUB_REPO_URL>
git push -u origin main
2.	Set Up CI/CD (Optional)
•	Use GitHub Actions or AWS CodePipeline to automate deployments whenever new code is pushed to GitHub.


Step 5: Test and Verify
1.	Verify the Backend
•	Test your APIs using the base URL from API Gateway. Ensure all endpoints (/menu, /order, etc.) work as expected.
2.	Verify the Frontend
•	Access your static website using the S3 URL or CloudFront distribution URL. Ensure that it connects properly to the backend APIs.
3.	Check GitHub Integration
•	Verify that all your project files are visible in your GitHub repository and accessible for future updates.

