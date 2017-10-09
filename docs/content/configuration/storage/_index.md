+++
title = "Storage"
date =  2017-10-09T12:35:00-07:00
weight = 3
+++

## Storage
The storage section controls safe storage for pick.

Currently supported storage types include `file` and `s3`.

#### File
File storage uses the local file system to store the Pick safe.

```toml
[storage]
type = "file"

[storage.settings]
# Path to store the safe.
# $HOME is replaced with the path to your home directory
path = "$HOME/.pick/pick.safe"

[storage.backup]
# Whether to auto-create backups before the safe is modified.
auto = true
# The number of backups to keep.
# Specify -1 to allow unlimited backups, 0 to not create backups at all.
max = -1
```

#### S3
S3 storage uses the AWS S3 to store the Pick safe.

> NOTE: An Internet is required for this backend

```toml
[storage]
type = "s3"

[storage.settings]
# Name of AWS S3 bucket
bucket = "your-bucket"
# Key for safe in bucket
key = "public/default.safe"
# AWS Region
region = "us-west-2"
# AWS Profile in ~/.aws/credentials. If none is provided, "default" will be used.
profile = ""

[storage.backup]
# Whether to auto-create backups before the safe is modified.
auto = true
# The number of backups to keep.
# Specify -1 to allow unlimited backups, 0 to not create backups at all.
max = -1
```
