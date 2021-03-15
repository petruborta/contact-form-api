# CONTACT FORM API

Serverless service for sending emails from a contact form.

## Table of contents

* [Technologies](#technologies)
* [Setup](#setup)
* [Status](#status)
* [Inspiration](#inspiration)
* [Contact](#contact)

## Technologies

* [Serverless](https://www.serverless.com/)
* [AWS SES](https://aws.amazon.com/ses/)
* [AWS Lambda](https://aws.amazon.com/lambda/)
* [AWS CloudFormation](https://aws.amazon.com/cloudformation/)

## Setup

* Install serverless framework (run command as `sudo` if you're using Linux)

  `$ npm i -g serverless`

* [Create an AWS IAM user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html) or use credentials of an existing one

* Set credentials so that Serverless knows what account to connect to when you run any terminal command

```shell
$ serverless config credentials \
    --provider aws \
    --key YOUR_ACCESS_KEY_ID \
    --secret YOUR_SECRET_ACCESS_KEY
```

* Create a service

  `$ serverless create --template aws-nodejs --path /path/to/your/contact-form-api`

* Clone this repository to your local machine and replace the files

  `$ git clone https://github.com/petruborta/contact-form-api.git`

* In `serverless.yml`, replace the value of `region` (line 11) with your own region

* Create `secrets.json` and use two of your emails for `MAIN_EMAIL` and `SECONDARY_EMAIL` or a single one for both

  NOTICE: The emails must be verified with AWS SES

  You can change `NODE_ENV`'s value to _production_ and `DOMAIN`'s value to your actual domain, once it's ready for production

```json
{
  "NODE_ENV": "dev",
  "MAIN_EMAIL": "YOUR_MAIN_EMAIL",
  "SECONDARY_EMAIL": "YOUR_SECONDARY_EMAIL",
  "DOMAIN": "*"
}
```

* Deploy the API to AWS Lambda

  `$ serverless deploy`

  The endpoint will be logged to the console once it's deployed

* Test the API

```shell
$ curl --header "Content-Type: application/json" \
    --request POST \
    --data '{"email":"john.doe@email.com","name":"John Doe","subject":"Test email","message":"Hello!"}' \
    https://{id}.execute-api.{region}.amazonaws.com/{stage}/email/send
```

## Status

Project is: _finished_

## Inspiration

Followed [this](https://dev.to/adnanrahic/building-a-serverless-contact-form-with-aws-lambda-and-aws-ses-4jm0) tutorial to implement a serverless contact form

## Contact

Created by [@petruborta](https://petruborta.com/) - feel free to contact me!
