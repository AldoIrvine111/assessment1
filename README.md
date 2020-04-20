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
In the first steps, we will set a PRIVATE repository in GitHub, where we will work on our project. Project is set to private to prevent unauthorized people to see or alter the project. We will make a branch for each feature or testing added that we will build. There will be a master code and several branches, and each team member can work on different branches at once(which is effective) and not work on the master. Once feature has passed the testing, we will merge it with our master code. 

![repo images](https://github.com/AldoIrvine111/assessment1/blob/master/pic/create_repo.PNG)

## Test to be added for Continuous Integration Build

### 1. Unit testing 
Unit testing is a level of software testing where indentify simple bug. To ensure to catch this bug, unit testing will breakdown big chunks of code into smaller bits and tested it. In this project, we will cooperate unit testing using Circle CI. We need to make sure unit testing stages to pass before deploying it to public. I will use Mocha for our unit testing.
![unit images](https://github.com/AldoIrvine111/assessment1/blob/master/pic/unit-testing-succesfull.PNG)

### 2. Static Code Analysis / Lint
Next, we are going to implement another test. This is linting test, it is an automated checking of source code for programmatic and stylistic errors. To answer why we should lint test, linting is implemented to reduce error and improve overall quality of code. In this case, we will use EsLint to stasically analyzes our code to find problem.
![lint images](https://github.com/AldoIrvine111/assessment1/blob/master/pic/lint-unit-coverage%20artifacts.PNG)

### 3. Code coverage Report
Code coverage is a metric that can help you understand how much of your source is tested. It's a very useful metric that can help you assess the quality of your test suite, and we will see here how you can get started with your projects. The reports will include percentages of statement, functions, line coverage and branches. To generate, we will nyc for mocha for our code coverage and --reporter flag for text report.
![code images](https://github.com/AldoIrvine111/assessment1/blob/master/pic/lint-unit-coverage%20artifacts.PNG)

### 4. Generating artifact
After all the test we done, we will store files or directory as an artifact into Circle CI's artifact section with store_artifacts Artifacts persist data after a job is completed and may be used for storage of the outputs of your build process.Artifacts are stored on Amazon S3 and are protected with your CircleCI account for private projects. Artifacts will only be generated on MASTER branch hence why later on our workflow will have a require command for master branch only.
![artifact images](https://github.com/AldoIrvine111/assessment1/blob/master/pic/lint-unit-coverage%20artifacts.PNG)
![repo images](https://github.com/AldoIrvine111/assessment1/blob/master/pic/masteronly.PNG)

### 5. Integration Testing
After unit testing, the next level of software testing is Integration Testing. This test will only run after unit testing pass, because this testing is where individual units are combined and tested as a group. We will once again used Mocha for integration testing. Apart from the docker image, we will now use another images to launch instances on PostgresSQL. This interaction between integrated units is tested here.
![integration images](https://github.com/AldoIrvine111/assessment1/blob/master/pic/lint-unit-coverage%20artifacts.PNG)

### 6. End to End test
Last but not least, we will implement the end to end testing or usually known as E2E. What this test does, is to test the flow of project from the start until the end. This test will behave like a real user under certain scenarios. QaWolf will help us in performing this E2E test. 
![e2e images](https://github.com/AldoIrvine111/assessment1/blob/master/pic/e2e%20succesfull.PNG)
![e2e images](https://github.com/AldoIrvine111/assessment1/blob/master/pic/e2e%20succesfull%20artifact.PNG)

### Multiple Fail Scenario

![e2e images](https://github.com/AldoIrvine111/assessment1/blob/master/pic/integration_failed1.PNG)
![e2e images](https://github.com/AldoIrvine111/assessment1/blob/master/pic/integration_failed2.PNG)

![e2e images](https://github.com/AldoIrvine111/assessment1/blob/master/pic/lint_failed1.PNG)
![e2e images](https://github.com/AldoIrvine111/assessment1/blob/master/pic/lint_failed2.PNG)

![e2e images](https://github.com/AldoIrvine111/assessment1/blob/master/pic/unit-testing_failed1.PNG)
![e2e images](https://github.com/AldoIrvine111/assessment1/blob/master/pic/lint_failed2.PNG)


### Multiple branches and pipeline
![multiple images](https://github.com/AldoIrvine111/assessment1/blob/master/pic/multiple_branches_pipelin%20e.PNG)
![multiople images](https://github.com/AldoIrvine111/assessment1/blob/master/pic/multiple_branches.PNG)

