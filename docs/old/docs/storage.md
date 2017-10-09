+++
date = "2015-06-20T14:02:37+02:00"
title = "Storage"
weight = 3
+++


## Types
By default the Safe is stored on the local disk using the `file` backend. 
Additionally, there is built in support for remote storage on AWS S3. 

### File
The default storage for Pick is a file on the local disk.

```toml
[storage]
type = "file"

  [storage.settings]
  path = "$HOME/.pick/pick.safe"
```

### S3
The S3 backend provides support for storing safes in AWS S3. To use this you'll
need to provision an S3 Bucket and enable read/write access in IAM.

1. Configure pick to use the S3 storage type in `~/.pick/config.toml`
  ```toml
  [storage]
    type = "s3"
  
    [storage.settings]
      bucket  = "my-bucket"
      key     = "safes/pick.safe"
      region  = "us-west-2"
      profile = "default"
  ```
  
2. Make sure you have an `~/.aws/credentials` file
  ```toml
  [default]
  aws_access_key_id     = "xxx"
  aws_secret_access_key = "xxxx"
  ```
  
3. Create an S3 bucket
  ```
  aws s3api create-bucket --bucket my-bucket --region us-west-2
  ```
  
4. Upload your safe to the S3 bucket
   ```
   aws s3 cp ~/.pick/pick.safe s3://my-bucket/safes/pick.safe
   ```
   
5. Ensure your AWS Profile has read/write access to the bucket. Below is an
   example IAM Policy.
  ```json
  {
      "Version": "2012-10-17",
      "Statement": [
          {
              "Sid": "Stmt1501718731000",
              "Effect": "Allow",
              "Action": [
                  "s3:GetObject",
                  "s3:PutObject"
              ],
              "Resource": [
                  "arn:aws:s3:::my-bucket/safes/pick.safe"
              ]
          }
      ]
  }
  ```

## Backups
Backups are configurable for all storage types.

```toml
[storage]
  [storage.backup]
  # Create a backup before the safe is modified
  auto = true

  # The number of backups to keep.
  # Specify -1 to allow unlimited backups, 0 to not create backups at all.
  max = 100
```
