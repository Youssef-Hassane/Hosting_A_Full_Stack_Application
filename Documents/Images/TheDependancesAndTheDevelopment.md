# BackEnd (udagram-api):

## The requirements:

- node.js 14.15.0
- The AWS Elastic Beanstalk (AWS EB)
- Express "^4.16.4"

## How to can deploy the application (BackEnd) to the Amazon Elastic Beanstalk):

- Firstly, you need to download the Elastic Beanstalk Command Line Interface (EB CLI) and add it to the PATH from https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb-cli3-install-advanced.html

- Secondly, you need to to go to the correct directory cd ~/udagram/udagram-api

- Thirdly, you need to download the Dependencies/DevDependencies and build the BackEnd, which mean you need to run the following script:

```
cd ~/udagram/udagram-api
npm install
npm run build
npm run deploy:sh
OR you can use the following command (it will do everything):
npm run deploy
```

# FrontEnd (udagram-frontend):

## The requirements:

- node.js 14.15.0
- The Amazon Simple Storage Service (Amazon S3)
- Angular
- ionic

## How to can deploy the application to the Amazon Simple Storage Service (Amazon S3):

- Firstly, you need to download the AWS Command Line Interface (AWS CLI) and add it to the PATH from https://aws.amazon.com/cli/

- Secondly, you need to to go to the correct directory cd ~/udagram/udagram-frontend

- Thirdly, you need to download the Dependencies/DevDependencies and build the FrontEnd, which mean you need to run the following script:

```
cd ~/udagram/udagram-frontend
npm install
npm run build
```

- Fourthly, you need to run following the S3 command in order to deploy the application:

```
aws s3 cp --recursive --acl public-read ./www s3://my-bucket-0612/
```
