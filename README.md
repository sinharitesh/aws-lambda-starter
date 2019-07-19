# aws-lambda-starter

Note: Following set up is tested on Windows environment. The steps may not work on other environment.

Prerequisites:
Requires AWS CLI to be present and configured beforhand.
aws configure list
aws configure will help in doing so.

Requires AWS SAM to be present in your environment.

Download the zip file aws-lambda-starter zip in your local environment and unzip, say in folder C:\Temp
On Windows explorer, go to C:\Temp\aws-lambda-starter directory and delete packaged.yml
Open the command prompt and traverse to the C:\Temp\aws-lambda-starter directory.

Issue this command on command prompt: sam package --output-template-file packaged.yaml --s3-bucket <bucket-name>
NEXT : sam deploy --template-file packaged.yaml --stack-name pytorch-sam-app   --capabilities CAPABILITY_IAM --parameter-overrides BucketName=<bucket-name> ObjectKey=<modelfile>.tar.gz

Above steps should deploy the model and create the AWS Lambda functions.

For testing the code:
Issue the following on Command Prompt.
curl -d "{\"url\":\"<YOUR_TEST_IMAGE_URL>\"}" -H "Content-Type: application/json" -X POST <YOUR_PROD_URL>

Alternatively, you can upload your own public image on S3 and pass that URL in above command in place of <YOUR_TEST_IMAGE_URL>.

