# Lambda Template
## Usage
This project can be forked for the creation of Spring Boot based Lambda functions.

The function with the `@Bean` annotation in `LambdaApplication` is the function that will be executed by the lambda. 

## Testing
### Requirements 
* Docker Dektop installed
* AWS CLI installed
* AWS SAM CLI installed

### Configure template.yaml
* **AWSTemplateFormatVersion** - Don't change, use default from file below
* **Transform** - Don't change, use default from file below
* **Description** - The description of the AMI
* **Resources** - This is the list of functions
* **ReverseStringFunction** - Function name, can be changed to whatever you like
* **Type** - Don't change, use default from file below
* **Properties** - AMI properties
* **CodeUri** - The path to the jar to execute
* **Handler** - The full class name of the `RequestHandler` 
* **Runtime** - The runtime environment, eg `Java8`
* **Timeout** - Execution timeout.

#### Example
```yaml
AWSTemplateFormatVersion : '2010-09-09'
Transform: AWS::Serverless-2016-10-31
Description: AWS Lambda Template Project
Resources:
  ReverseStringFunction:
    Type: AWS::Serverless::Function
    Properties:
      CodeUri: target/lambda-template-1.0-SNAPSHOT-aws.jar
      Handler: com.univeris.lambda.MyStringHandlers
      Runtime: java8
      Timeout: 10
```

### Run 
* execute with `sam local invoke -e data.json`