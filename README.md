# Lambda function that can tweet text or the results of an http request

[![License](https://img.shields.io/badge/license-MIT-lightgray.svg)](https://github.com/andrewmacheret/twitter-bot-lambda/blob/master/LICENSE.md)

## Dependencies

Installation requires a UNIX environment with:

- Bash
- Node.js
- An Amazon Web Services account
- A Twitter account

## Setup and installation

[Create a new app on your twitter account](https://apps.twitter.com/app/new) to obtain the following:
  * accessToken
  * accessSecret
  * consumerKey
  * consumerSecret

Then create a file in src/lambda/twitter.json with the following content:
  ```json
  {
    "accessToken": "...",
    "accessSecret": "...",
    "consumerKey": "...",
    "consumerSecret": "..."
  }
  ```

Run aws-setup.sh to install AWS command line tools and create an AWS Lambda Function. (*It will run `aws configure`, so have an key id and access key ready*)

Run aws-update-lambda.sh after further changes to source code to update the AWS Lambda Functon with the new source code.

You may also want to:
1. Create an API gateway with AWS API Gateway, and connect it to the AWS Lambda Function
2. Create a new certificate with AWS Certificate Manager for use with AWS API Gateway (for HTTPS)
3. Create a new custom domain in AWS API Gateway (for HTTPS, and/or to put on your domain)
4. Create a CNAME record with your domain name provider (for HTTPS, and/or to put on your domain)

## Running

Pass an event of the following json format to the lamdba function:

  ```json
  {
    "twitter": {
      "accessToken": "...",
      "accessSecret": "...",
      "consumerKey": "...",
      "consumerSecret": "..."
    },
    "text": "Here's a status I'd like to tweet"
  }
  ```

or:

  ```json
  {
    "twitter": {
      "accessToken": "...",
      "accessSecret": "...",
      "consumerKey": "...",
      "consumerSecret": "..."
    },
    "request": {
      "uri": "https://pun.andrewmacheret.com",
      "headers": { "Accept": "text/plain" }
    }
  }
  ```

Then check your twitter account!
