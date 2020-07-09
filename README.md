### AWS LAMBDA GIT INTEGRATOR
Integrate [AWS LAMBDA Function](https://aws.amazon.com/lambda/) to a [GIT](https://git-scm.com/) repository. The AWS Lambda Git integrator will help to integrate GIT Repository to your AWS Lambda Function. This software will do GIT pull with AWS Lambda Function code download and AWS Lambda Function code upload with GIT push parallely(See [here](https://github.com/justin-john/aws-lambda-git-integrator#usage-and-how-it-works)). So you can manage to have Version Control System integrated with AWS Lambda function for the project.

### PREREQUISITES
AWS2 CLI need to configured in your system. This needs active AWS account to configure.
You should set couple of local git configs one for setting up your lambda function name and other setting git hook path. Please make sure set only local git config that applies to your current git repository.

#### SETTING GIT LOCAL CONFIGS
```
git config --local lambda.functionName <YourLambdaFunctionName>
git config --local core.hooksPath githooks/
```
You can add `pre-push`(located inside "githooks/pre-push") hook inside the default GIT hooks folder `.git/hooks` and setting local GIT hook path(`git config --local core.hooksPath githooks/`) can be avoided.

#### SOFTWARES REQUIRED
* aws2/aws
* jq
* zip   (This might be preinstalled as starter kit of OS)

#### GET STARTED 
* Create an AWS Lambda Function or Should have an existing AWS Lambda function that needs git integration.
* Copy `lambda` and `githooks` of this repository in a folder with same name as your AWS Lambda Function name.
* Initialize an new git repository and set up all local git configs and create a remote GIT repository.
* Do a `./lambda pullsync` and follows a git commit and push to remote GIT server.

### USAGE AND HOW IT WORKS

##### CODE PULL
GIT PULL + AWS LAMBDA FUNCTION CODE DOWNLOAD - Recommended.

It'll first do a GIT pull and then follows code download from AWS Lambda function.
```
./lambda pullsync
```
###### Additional code pull options, but not recommended as both operations are done by above single command.
* AWS LAMBDA FUNCTION CODE DOWNLOAD - The code will be download from aws lambda function to your current folder. `./lambda synconly`.
* GIT PULL - Normal git pull. The following both commands do the same operation.`./lambda pullonly`  or `git pull origin <branchName>`

##### CODE COMMIT
This is normal git commit. After commit, you can do `./lambda pullsync` to know someone directly updated code in aws lambda function or any update in git repo.

##### CODE PUSH
This is normal git push. A pre-push commit hook is attached, so when you do git push, the pre-push git hook will upload code to AWS Lambda Function and follows git push to repo.

NB: Please make sure lambda and pre-push are executable files.

#### OS Supported
* Linux
* Mac OS (Not Tested, Should Work. If anybody of you like to contribute in this project by testing in Mac OS, please test and let me know your report by creating an issue/pull request. Don't have MAC machine to test. :disappointed:)

## License

The MIT License (MIT)

Copyright (c) 2020 Justin John Mathews <justinjohnmathews@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
