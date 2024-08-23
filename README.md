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

