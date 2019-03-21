# CloudFormation Stack(s) Installation

```sh
# Install the project as a static website on a S3 bucket:
aws cloudformation deploy \
    --stack-name aws-js-s3-explorer \
    --template-file explorer.yml \
    --no-fail-on-empty-changeset

# Upload the web application to the bucket:
aws s3 sync ../static s3://aws-js-s3-explorer --delete

# Get the URL to the S3 static website:
aws cloudformation describe-stacks \
    --stack-name aws-js-s3-explorer

# (Optional) Install a sample S3 bucket to test the S3 explorer:
aws cloudformation deploy \
    --stack-name aws-js-s3-explorer-sample-bucket \
    --template-file bucket.yml \
    --no-fail-on-empty-changeset

# (Optional) Upload some test content to the S3 bucket:
aws s3 sync ../test/content s3://aws-js-s3-explorer-sample-bucket --delete

# (Optional) Install a sample CloudFormation distribution to test the S3 explorer:
aws cloudformation deploy \
    --stack-name aws-js-s3-explorer-sample-cloudfront \
    --template-file cloudfront.yml \
    --no-fail-on-empty-changeset \
    --parameter-overrides \
        OriginBucketName=aws-js-s3-explorer-sample-bucket

# (Optional) Get the URL of the CloudFormation distribution:
aws cloudformation describe-stacks \
    --stack-name aws-js-s3-explorer-sample-cloudfront
  
```

Note: if you install the sample S3 bucket and CloudFront distribution using the above aws-cli commands, use the same AWS Access Key as your aws-cli when configuring the S3 explorer.
