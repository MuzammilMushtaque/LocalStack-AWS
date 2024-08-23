# Operate S3 Bucket of AWS Using LocalStack


The goal is to work with file storage and retrieval in a local AWS-like environment, sticking with S3 is best option. We can simulate S3 behavior entirely using Localstack which can cover many use cases like:

1) Uploading and downloading files

2) Listing objects in a bucket

3) Managing object versions and metadata

### 1. Start LocalStack with Docker

```bash
docker pull request localstack/localstack
docker run --rm -p 4566:4566 localstack/localstack
```
### 2. Install AWS-CLI is local machine

```bash
pip install awscli
```

### 3. Configure AWS

```bash
aws configure
```
Enter any dummy values for `AWS Access Key ID`, `AWS Secret Access Key`, and `Default region name`. Set the `Default output format` to json.

### 4. Create an S3 Bucket using Localstack

```bash
aws --endpoint-url=http://localhost:4566 s3api create-bucket --bucket my-bucket
```

### 5. Uplaod a File to S3
```bash
echo "This is a test file." > test.txt
aws --endpoint-url=http://localhost:4566 s3 cp test.txt s3://my-bucket/test.txt
```

### 6. List Files in the Bucket
To see the files in your bucket:

```bash
aws --endpoint-url=http://localhost:4566 s3 ls s3://my-bucket/
```

### 7. Download a File from S3
To download a file from S3:

```bash
aws --endpoint-url=http://localhost:4566 s3 cp s3://my-bucket/test.txt test_downloaded.txt
```
### 8. Delete a File
To delete a file from S3:

```bash
aws --endpoint-url=http://localhost:4566 s3 rm s3://my-bucket/test.txt
```

## Simplified Architecture
By focusing only on S3, the architecture simplifies to:

a) LocalStack Docker Container: Running S3 service locally.

b) AWS CLI: Interacting with LocalStack’s S3 service for file operations.