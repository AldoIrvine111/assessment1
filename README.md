# Assignment 1 DevOps
Name : Aldo Irvine
Student Number : s3692192


## ACME Corps

ACME corp faces several problem, such as:
1. Using only their leader's laptop to deliver project. (Inefficient and this approach is not recommanded)
2. Issues with lots of bug after delivering project. (impacted their revenue and teams' morale) 

Me as an expert in DevOps field, I suggest them to :
1. Create a version control system system (.git) and push their code to online repository.
2. Add automated testing to reduce the number of defects that is missed during testing.

## Step by Step
So, the following text will explain on how we will implement our solutions.

### Set up a private repository in GitHub and commit the application there to be built, tested, and packaged using CircleCI.
In the first steps, we will set a PRIVATE repository in GitHub, where we will work on our project. Project is set to private to prevent unauthorized people to see or alter the project.

![repo images](https://github.com/AldoIrvine111/assessment1/blob/master/pic/create_repo.PNG)



### Unit tests

 - Unit testing breaks codes into smaller bits that can be easily and effectively tested. Unit testing helps to identify a simple bug that might have been passed undetected. 

 - In this case, we are using Mocha for our unit test implementation. Tests from test/unit directory are being executed in Circle CI to check for test output. We have to make sure that all the tests passed. 

### Linting

 - Linting helps to identify the common error, including syntax error and structural problem, and to help improve overall code quality. 

 - Here we are using EsLint as our lint tools. EsLint will go through everything in the directory by specifying "eslint ./" or just a specific file with "eslint /filename". There is no output in our case as eslintrc.json has "ignorePatterns" included. 

### Code coverage

 - Code coverage provides percentages of codes that are executed when automated tests are run. Common coverage summary includes the percentages of statements, branches, functions, and lines coverage.

 - We are using nyc for mocha to generate our code coverage, and --reporter flag to generate the default text report.

### Generating artefact

 - Store artifacts will upload a file or directory as an artifact. After it is successfully generated, it can be accessed from the artifacts tab in circleci. 

 - To pack up the application, node environment has to be set to production mode, which will install only the required dependencies. We can then do a zipping and store it as an artifact. 

### Multiple Fail Scenario 

![fail-scenario-1](https://github.com/gladysganda/s3679389-A1/blob/master/images/fail(1).JPG)
 - This error might be occurred to some situation, but in this case is caused by config.yml file and package.json not being in the same directory.

![fail-scenario-2](https://github.com/gladysganda/s3679389-A1/blob/master/images/fail(2).JPG)
 - The most common error that might happen on yaml file is indentation error. Run "circleci config validate" to check if you have a valid indentation

![fail-scenario-3](https://github.com/gladysganda/s3679389-A1/blob/master/images/fail(3).JPG)
 - The working directory is not set correctly in this case. Error is caused by config file not being able to find package.json

![fail-scenario-4](https://github.com/gladysganda/s3679389-A1/blob/master/images/fail(4).JPG)
 - The error occurs because of the wrong format when using npm <command>. Instead of doing npm test-unit, the right format should be npm run test-unit

![fail-scenario-5](https://github.com/gladysganda/s3679389-A1/blob/master/images/fail(5).JPG)
 - The file or directory could not be found. This case is usually caused by the wrong directory path specified, or it has not been created. 


### Integration tests

 - Integration testing is where individual units combined to be tested as a group. Integration testing is implemented after unit testing has been passed. 

 - Mocha is again used for integration testing. Other than docker images, postgres image is also implemented in this case as we are launching an instance on PostgreSQL to run the integration testing. 

### End to end test

 - End to end testing is used to test whether the flow of application from the beginning to the end is behaving as expected. E2E test will simulate real user scenarios and validate the system under integration with external interfaces.

 - E2E tests are implemented using QaWolf. "npx qawolf init" is used to set up config of the project. Here we are using circleci/node:lts-browsers which will make testing easier as it configures the application to run in a containerized environment.

Fail Scenario
![e2e-fail-1](https://github.com/gladysganda/s3679389-A1/blob/master/images/e2e-fail(1).JPG)
 - A wrong docker image has been used. In this scenario, docker images must support the browser to be able to run e2e browser testing.
![e2e-fail-2](https://github.com/gladysganda/s3679389-A1/blob/master/images/e2e-fail(2).JPG)
 - Prompted Database error is caused by DB Username, Name and Password not being declared.


### CircleCI Log 

Unit Test

![tess-pass](https://github.com/gladysganda/s3679389-A1/blob/master/images/unit-test-success.JPG)
![tess-pass](https://github.com/gladysganda/s3679389-A1/blob/master/images/test-pass.JPG)

Lint 

![lint-success](https://github.com/gladysganda/s3679389-A1/blob/master/images/lint-success.JPG)

Code Coverage

![Code Coverage](https://github.com/gladysganda/s3679389-A1/blob/master/images/code-coverage-success.JPG)
![Code Coverage](https://github.com/gladysganda/s3679389-A1/blob/master/images/artifacts.JPG)

Generate Artefact

![Code Coverage](https://github.com/gladysganda/s3679389-A1/blob/master/images/generate-artefact-success.JPG)

The artifact should be generated on the master branch only 

![Master-1](https://github.com/gladysganda/s3679389-A1/blob/master/images/master-only.JPG)
![Master-2](https://github.com/gladysganda/s3679389-A1/blob/master/images/master-only(2).JPG)

Integration Testing

![Integration Testing](https://github.com/gladysganda/s3679389-A1/blob/master/images/int-test-success.JPG)


E2E Testing

![E2E](https://github.com/gladysganda/s3679389-A1/blob/master/images/e2e-test-success.JPG)


### CircleCI Pipelines

Generate Artefact
![Pipeline-1](https://github.com/gladysganda/s3679389-A1/blob/master/images/pipeline(1).JPG)
![Pipeline-2](https://github.com/gladysganda/s3679389-A1/blob/master/images/pipeline(2).JPG)
![Pipeline-3](https://github.com/gladysganda/s3679389-A1/blob/master/images/pipeline(3).JPG)
![Pipeline-4](https://github.com/gladysganda/s3679389-A1/blob/master/images/pipeline(4).JPG)
![Pipeline-5](https://github.com/gladysganda/s3679389-A1/blob/master/images/pipeline(5).JPG)
![Pipeline-6](https://github.com/gladysganda/s3679389-A1/blob/master/images/pipeline(6).JPG)
![Pipeline-7](https://github.com/gladysganda/s3679389-A1/blob/master/images/pipeline(7).JPG)
![Pipeline-8](https://github.com/gladysganda/s3679389-A1/blob/master/images/pipeline(8).JPG)
![Pipeline-9](https://github.com/gladysganda/s3679389-A1/blob/master/images/pipeline(9).JPG)
![Pipeline-10](https://github.com/gladysganda/s3679389-A1/blob/master/images/pipeline(10).JPG)
