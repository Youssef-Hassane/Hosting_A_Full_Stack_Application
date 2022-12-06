# Hosting a Full-Stack Application

## How I have created the Database:

---

## How I have created the Elastic Beanstalk:

```
cd Desktop/Hosting_A_Full_Stack_Application/udagram/udagram-api/
eb init udagram-api
eb create udagram-api-dev
```

### deployment

- Firstly, I have created folder called bin
- Secondly, I have created file called deploy.sh
- Thirdly, I added the following in the deploy.sh file

```
eb list
eb use udagram-api-dev
eb deploy udagram-api-dev
eb setenv POSTGRES_HOST=$POSTGRES_HOST POSTGRES_USERNAME=$POSTGRES_USERNAME POSTGRES_DB=$POSTGRES_DB POSTGRES_PASSWORD=$POSTGRES_PASSWORD DATABASE_PORT=$DATABASE_PORT PORT=$PORT URL=$URL JWT_SECRET=$JWT_SECRET AWS_REGION=$AWS_REGION AWS_PROFILE=$AWS_PROFILE AWS_BUCKET=$AWS_BUCKET AWS_ACCESS_KEY_ID=$AWS_ACCESS_KEY_ID AWS_SECRET_ACCESS_KEY=$AWS_SECRET_ACCESS_KEY AWS_DEFAULT_REGION=$AWS_DEFAULT_REGION
```

- Fourthly, I have added new script called "deploy:sh" and modified the "start" and the "deploy" script of the package.json that is located in the “udagram-api” folder.

---

## How I have created the Amazon Simple Storage Service (Amazon S3)::

```
cd Desktop/Hosting_A_Full_Stack_Application/udagram/udagram-frontend
aws s3api create-bucket --bucket my-bucket-0612 --region us-east-1
aws s3 cp --recursive --acl public-read ./www s3://my-bucket-0612/
aws s3 website s3://my-bucket-0612/ --index-document index.html --error-document index.html
```

After that I went to the console to add the bucket policy:

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::my-bucket-0612/*"
        }
    ]
}
```

---

## Infrastructure

![Screenshot1](https://github.com/Youssef-Hassane/Screenshot-3/blob/main/ScreenShot_2.png)

---

## Continuous Integration And Continuous Deployment (CI/CD) Pipeline

![Screenshot2](https://github.com/Youssef-Hassane/Screenshot-3/blob/main/ScreenShot_1.png)

---

Environment Variables In The CircleCI:

```
POSTGRES_HOST=$POSTGRES_HOST
POSTGRES_USERNAME=$POSTGRES_USERNAME
POSTGRES_DB=$POSTGRES_DB
POSTGRES_PASSWORD=$POSTGRES_PASSWORD
DATABASE_PORT=$DATABASE_PORT
PORT=$PORT
URL=$URL
JWT_SECRET=$JWT_SECRET
AWS_REGION=$AWS_REGION
AWS_PROFILE=$AWS_PROFILE
AWS_BUCKET=$AWS_BUCKET
AWS_ACCESS_KEY_ID=$AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY=$AWS_SECRET_ACCESS_KEY
AWS_DEFAULT_REGION=$AWS_DEFAULT_REGION
```

---

In this project you will learn how to take a newly developed Full-Stack application built for a retailer and deploy it to a cloud service provider so that it is available to customers. You will use the aws console to start and configure the services the application needs such as a database to store product information and a web server allowing the site to be discovered by potential customers. You will modify your package.json scripts and replace hard coded secrets with environment variables in your code.

After the initial setup, you will learn to interact with the services you started on aws and will deploy manually the application a first time to it. As you get more familiar with the services and interact with them through a CLI, you will gradually understand all the moving parts.

You will then register for a free account on CircleCi and connect your Github account to it. Based on the manual steps used to deploy the app, you will write a config.yml file that will make the process reproducible in CircleCi. You will set up the process to be executed automatically based when code is pushed on the main Github branch.

The project will also include writing documentation and runbooks covering the operations of the deployment process. Those runbooks will serve as a way to communicate with future developers and anybody involved in diagnosing outages of the Full-Stack application.

# Udagram

This application is provided to you as an alternative starter project if you do not wish to host your own code done in the previous courses of this nanodegree. The udagram application is a fairly simple application that includes all the major components of a Full-Stack web application.

### Dependencies

```
- Node v14.15.1 (LTS) or more recent. While older versions can work it is advisable to keep node to latest LTS version

- npm 6.14.8 (LTS) or more recent, Yarn can work but was not tested for this project

- AWS CLI v2, v1 can work but was not tested for this project

- A RDS database running Postgres.

- A S3 bucket for hosting uploaded pictures.

```

### Installation

Provision the necessary AWS services needed for running the application:

1. In AWS, provision a publicly available RDS database running Postgres. <Place holder for link to classroom article>
1. In AWS, provision a s3 bucket for hosting the uploaded files. <Place holder for tlink to classroom article>
1. Export the ENV variables needed or use a package like [dotnev](https://www.npmjs.com/package/dotenv)/.
1. From the root of the repo, navigate udagram-api folder `cd starter/udagram-api` to install the node_modules `npm install`. After installation is done start the api in dev mode with `npm run dev`.
1. Without closing the terminal in step 1, navigate to the udagram-frontend `cd starter/udagram-frontend` to intall the node_modules `npm install`. After installation is done start the api in dev mode with `npm run start`.

## Testing

This project contains two different test suite: unit tests and End-To-End tests(e2e). Follow these steps to run the tests.

1. `cd starter/udagram-frontend`
1. `npm run test`
1. `npm run e2e`

There are no Unit test on the back-end

### Unit Tests:

Unit tests are using the Jasmine Framework.

### End to End Tests:

The e2e tests are using Protractor and Jasmine.

## Built With

- [Angular](https://angular.io/) - Single Page Application Framework
- [Node](https://nodejs.org) - Javascript Runtime
- [Express](https://expressjs.com/) - Javascript API Framework

## License

[License](LICENSE.txt)
