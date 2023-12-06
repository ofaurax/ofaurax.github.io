# TIL: Today I Learned

Inspired by https://github.com/jbranchaud/til


## AWS S3 without authentication

When using `aws s3`, it will complain if you have no credentials,
and ask for `aws configure`.

To bypass, use `--no-sign-request` (for example for accessing public
s3 storages)

Source:
https://dev.to/aws-builders/access-s3-public-data-without-credentials-4f06

