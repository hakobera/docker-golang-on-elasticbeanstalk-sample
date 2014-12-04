# How to run

## Prerequisities

```
$ gem install ebfly
```

## Create application and docker environment

### Clone this repository

```
$ git clone https://github.com/hakobera/docker-golang-on-elasticbeanstalk-sample.git
```

### Setup env

```
$ export AWS_ACCESS_KEY_ID=[your access key]
$ export AWS_SECRET_ACCESS_KEY=[your secret key]
$ export AWS_REGION=us-east-1
```

### Create application and empty docker envrionment

```
$ ebfly app create docker
$ ebfly env create web -s docker0.9 -a docker
```

Wait about 5 minutes until environment is ready.
You can check environment status using `ebfly env info` command.
When `status` change to `Ready`, it's time to deploy app.

```
$ ebfly env info web -a docker
ebfly env info web -a docker

=== environment info ===
application name: docker
environment id:
environment name: docker-web
description:
status:     Ready
health:     Green
tier:     WebServer Standard 1.0
solution stack name:  64bit Amazon Linux 2014.03 v1.0.2 running Docker 0.9.0
endpoint url:   awseb-e-w-AWSEBLoa-956NXWFC8619-1360484152.us-west-1.elb.amazonaws.com
cname:
updated at:   2014-04-25 01:57:49 UTC
```

### Deploy application

```
$ ebfly env push web master -a docker
```

Wait until environment is ready.
It takes time about 10-20 minutes, because of many apt-get install.

### Open app

Your app URL is see in `ebfly env info web -a docker`.
Open `cname` on your browser.

```
$ ebfly env info web -a docker

=== environment info ===
...
cname: docker-web-1234556677.elasticbeanstalk.com
...
```

You can use `ebfly env open` if you use Mac OS X.

```
$ ebfly env open web -a docker
```
