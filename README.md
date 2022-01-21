# devops-docker
 Docker build files for services managed by devops 

## Authenticate docker to Amazon ECR 
`aws ecr get-login-password --region us-east-1 [--profile prod|dev] | docker login --username AWS --password-stdin {$aws_account_id}.dkr.ecr.us-east-1.amazonaws.com` 


## Use
To make use of this image, include the following in the task definition, changing the config-file-value as needed for your application

```
"firelensConfiguration": {
    "type": "fluentbit",
    "options": {
    "config-file-type": "file",
    "config-file-value": "/elastic.conf"
    }
},
```

### Configs

* base.conf: configures baseline options
* elastic.conf: ships logs to a cloudwatch log stream and elastic cloud endpoint with env vars to config host, username, password and index.