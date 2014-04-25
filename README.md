# How to run

## Prerequisities

```
$ gem install ebfly
```

## Create application and docker environment

### Setup env

```
$ export AWS_ACCESS_KEY=[your access key]
$ export AWS_SECRET_ACCESS_KEY=[your secret key]
$ export AWS_REGION=us-east-1
```

### Create application and empty docker envrionment

```
$ ebfly app create docker
$ ebfly env create web -s docker0.9 -a docker
```
