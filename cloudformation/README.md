# CloudFormation Stack(s) Installation

#### Install the project as a static website on a S3 bucket:
```sh
aws cloudformation deploy \
    --stack-name aws-js-s3-explorer \
    --template-file explorer.yml \
    --no-fail-on-empty-changeset

aws s3 sync ../static s3://aws-js-s3-explorer --delete
```

#### (Optional) Install a sample properly configured S3 bucket to test the S3 explorer:
```sh
aws cloudformation deploy \
    --stack-name aws-js-s3-explorer-sample-bucket \
    --template-file bucket.yml \
    --no-fail-on-empty-changeset

aws s3 sync ../test/content s3://aws-js-s3-explorer-sample-bucket --delete
```

#### (Optional) Install a sample CloudFormation distribution to test the S3 explorer:
```sh
aws cloudformation deploy \
    --stack-name aws-js-s3-explorer-sample-cloudfront \
    --template-file cloudfront.yml \
    --no-fail-on-empty-changeset \
    --parameter-overrides \
        OriginBucketName=aws-js-s3-explorer-sample-bucket
```
