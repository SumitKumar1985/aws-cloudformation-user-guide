# AWS::Logs::Destination<a name="aws-resource-logs-destination"></a>

The `AWS::Logs::Destination` resource creates an Amazon CloudWatch Logs \(CloudWatch Logs\) destination, which enables you to specify a physical resource \(such as an Kinesis stream\) that subscribes to CloudWatch Logs log events from another AWS account\. For more information, see [Cross\-Account Log Data Sharing with Subscriptions](http://docs.aws.amazon.com/AmazonCloudWatch/latest/DeveloperGuide/CrossAccountSubscriptions.html) in the *Amazon CloudWatch User Guide*\.


+ [Syntax](#aws-resource-logs-destination-syntax)
+ [Properties](#w3ab2c21c10d818b9)
+ [Return Values](#w3ab2c21c10d818c11)
+ [Example](#w3ab2c21c10d818c13)

## Syntax<a name="aws-resource-logs-destination-syntax"></a>

To declare this entity in your AWS CloudFormation template, use the following syntax:

### JSON<a name="aws-resource-logs-destination-syntax.json"></a>

```
{
  "Type" : "AWS::Logs::Destination",
  "Properties" : {
    "[[ERROR] BAD/MISSING LINK TEXT](#cfn-logs-destination-destinationname)" : String,
    "[[ERROR] BAD/MISSING LINK TEXT](#cfn-logs-destination-destinationpolicy)" : String,
    "[[ERROR] BAD/MISSING LINK TEXT](#cfn-logs-destination-rolearn)" : String,
    "[[ERROR] BAD/MISSING LINK TEXT](#cfn-logs-destination-targetarn)" : String
  }
}
```

### YAML<a name="aws-resource-logs-destination-syntax.yaml"></a>

```
Type: "AWS::Logs::Destination"
Properties: 
  [[ERROR] BAD/MISSING LINK TEXT](#cfn-logs-destination-destinationname): String
  [[ERROR] BAD/MISSING LINK TEXT](#cfn-logs-destination-destinationpolicy): String
  [[ERROR] BAD/MISSING LINK TEXT](#cfn-logs-destination-rolearn): String
  [[ERROR] BAD/MISSING LINK TEXT](#cfn-logs-destination-targetarn): String
```

## Properties<a name="w3ab2c21c10d818b9"></a>

`DestinationName`  
The name of the CloudWatch Logs destination\.  
*Required: *Yes  
*Type*: String  
*Update requires*: Replacement

`DestinationPolicy`  
An AWS Identity and Access Management \(IAM\) policy that specifies who can write to your destination\.  
*Required: *Yes  
*Type*: String  
*Update requires*: No interruption

`RoleArn`  
The Amazon Resource Name \(ARN\) of an IAM role that permits CloudWatch Logs to send data to the specified AWS resource \(`TargetArn`\)\.  
*Required: *Yes  
*Type*: String  
*Update requires*: No interruption

`TargetArn`  
The ARN of the AWS resource that receives log events\. Currently, you can specify only an Kinesis stream\.  
*Required: *Yes  
*Type*: String  
*Update requires*: No interruption

## Return Values<a name="w3ab2c21c10d818c11"></a>

### Ref<a name="w3ab2c21c10d818c11b2"></a>

When the logical ID of this resource is provided to the `Ref` intrinsic function, `Ref` returns the resource name, such as `TestDestination`\.

For more information about using the `Ref` function, see Ref\.

### Fn::GetAtt<a name="aws-resource-logs-destination-getatt"></a>

`Fn::GetAtt` returns a value for a specified attribute of this type\. The following are the available attributes and sample return values\.

`Arn`  
The ARN of the CloudWatch Logs destination, such as `arn:aws:logs:us-east-2:123456789012:destination:MyDestination`\.

For more information about using `Fn::GetAtt`, see Fn::GetAtt\.

## Example<a name="w3ab2c21c10d818c13"></a>

In the following example, the target stream \(`TestStream`\) can receive log events from the `logger` IAM user that is in the `234567890123` AWS account\. The user can call only the `PutSubscriptionFilter` action against the `TestDestination` destination\.

### JSON<a name="aws-resource-logs-destination-example.json"></a>

```
"DestinationWithName" : {
  "Type" : "AWS::Logs::Destination",
  "Properties" : {
    "DestinationName": "TestDestination",
    "RoleArn": "arn:aws:iam::123456789012:role/LogKinesisRole",
    "TargetArn": "arn:aws:kinesis:us-east-1:123456789012:stream/TestStream",
    "DestinationPolicy": "{\"Version\" : \"2012-10-17\",\"Statement\" : [{\"Effect\" : \"Allow\", \"Principal\" : {\"AWS\" : \"arn:aws:iam::234567890123:user/logger\"},
\"Action\" : \"logs:PutSubscriptionFilter\", \"Resource\" : \"arn:aws:logs:us-east-1:123456789012:destination:TestDestination\"}]}"
  }
}
```

### YAML<a name="aws-resource-logs-destination-example.yaml"></a>

```
DestinationWithName: 
  Type: "AWS::Logs::Destination"
  Properties: 
    DestinationName: "TestDestination"
    RoleArn: "arn:aws:iam::123456789012:role/LogKinesisRole"
    TargetArn: "arn:aws:kinesis:us-east-1:123456789012:stream/TestStream"
    DestinationPolicy: >
      {"Version" : "2012-10-17","Statement" : [{"Effect" : "Allow", "Principal" : {"AWS" : "arn:aws:iam::234567890123:user/logger"},"Action" : "logs:PutSubscriptionFilter", "Resource" : "arn:aws:logs:us-east-1:123456789012:destination:TestDestination"}]}
```