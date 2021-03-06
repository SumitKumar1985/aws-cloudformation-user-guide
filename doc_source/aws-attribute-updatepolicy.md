# UpdatePolicy Attribute<a name="aws-attribute-updatepolicy"></a>

Use the `UpdatePolicy` attribute to specify how AWS CloudFormation handles updates to the [http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-as-group.html](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-as-group.html) or [http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-lambda-alias.html](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-lambda-alias.html) resource\.

For `AWS::AutoScaling::AutoScalingGroup` resources, AWS CloudFormation invokes one of three update policies depending on the type of change you make or whether a scheduled action is associated with the Auto Scaling group\.

+ The `AutoScalingReplacingUpdate` and `AutoScalingRollingUpdate` policies apply *only* when you do one or more of the following:

  + Change the Auto Scaling group's `[AWS::AutoScaling::LaunchConfiguration](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-as-launchconfig.html)`\.

  + Change the Auto Scaling group's `VPCZoneIdentifier` property

  + Update an Auto Scaling group that contains instances that don't match the current `LaunchConfiguration`\.

  If both the `AutoScalingReplacingUpdate` and `AutoScalingRollingUpdate` policies are specified, setting the `WillReplace` property to `true` gives `AutoScalingReplacingUpdate` precedence\.

+ The `AutoScalingScheduledAction` policy applies when you update a stack that includes an Auto Scaling group with an associated scheduled action\.

For `AWS::Lambda::Alias` resources, AWS CloudFormation performs an AWS CodeDeploy deployment when the version changes on the alias\. For more information, see \.

## AutoScalingReplacingUpdate Policy<a name="cfn-attributes-updatepolicy-replacingupdate"></a>

To specify how AWS CloudFormation handles replacement updates for an Auto Scaling group, use the `AutoScalingReplacingUpdate` policy\. This policy enables you to specify whether AWS CloudFormation replaces an Auto Scaling group with a new one or replaces only the instances in the Auto Scaling group\.

**Important**  
Before attempting an update, ensure that you have sufficient Amazon EC2 capacity for both your old and new Auto Scaling groups\.

### Syntax<a name="w3ab2c21c23c23c11b6"></a>

#### JSON<a name="aws-attribute-updatepolicy-replacingupdate-syntax.json"></a>

```
"UpdatePolicy" : {
  "AutoScalingReplacingUpdate" : {
    "[[ERROR] BAD/MISSING LINK TEXT](#cfn-attributes-updatepolicy-replacingupdate-willreplace)" : Boolean
  }
}
```

#### YAML<a name="aws-attribute-updatepolicy-replacingupdate-syntax.yaml"></a>

```
UpdatePolicy:
  AutoScalingReplacingUpdate:
    [[ERROR] BAD/MISSING LINK TEXT](#cfn-attributes-updatepolicy-replacingupdate-willreplace): Boolean
```

### Properties<a name="w3ab2c21c23c23c11b8"></a>

`WillReplace`  
Specifies whether an Auto Scaling group and the instances it contains are replaced during an update\. During replacement, AWS CloudFormation retains the old group until it finishes creating the new one\. If the update fails, AWS CloudFormation can roll back to the old Auto Scaling group and delete the new Auto Scaling group\.  
While AWS CloudFormation creates the new group, it doesn't detach or attach any instances\. After successfully creating the new Auto Scaling group, AWS CloudFormation deletes the old Auto Scaling group during the cleanup process\.  
When you set the `WillReplace` parameter, remember to specify a matching `[CreationPolicy](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-attribute-creationpolicy.html)`\. If the minimum number of instances \(specified by the `MinSuccessfulInstancesPercent` property\) don't signal success within the `Timeout` period \(specified in the `CreationPolicy` policy\), the replacement update fails and AWS CloudFormation rolls back to the old Auto Scaling group\.  
*Type*: Boolean  
*Required: *No

## AutoScalingRollingUpdate Policy<a name="cfn-attributes-updatepolicy-rollingupdate"></a>

To specify how AWS CloudFormation handles rolling updates for an Auto Scaling group, use the `AutoScalingRollingUpdate` policy\. Rolling updates enable you to specify whether AWS CloudFormation updates instances that are in an Auto Scaling group in batches or all at once\.

**Important**  
During a rolling update, some Auto Scaling processes might make changes to the Auto Scaling group before AWS CloudFormation completes the rolling update\. These changes might cause the rolling update to fail\. To prevent Auto Scaling from running processes during a rolling update, use the `SuspendProcesses` property\. For more information, see [What are some recommended best practices for performing Auto Scaling group rolling updates?](https://aws.amazon.com/premiumsupport/knowledge-center/auto-scaling-group-rolling-updates/)

### Syntax<a name="w3ab2c21c23c23c13b6"></a>

#### JSON<a name="aws-attribute-updatepolicy-rollingupdate-syntax.json"></a>

```
"UpdatePolicy" : {
  "AutoScalingRollingUpdate" : {
    "[[ERROR] BAD/MISSING LINK TEXT](#cfn-attributes-updatepolicy-rollingupdate-maxbatchsize)" : Integer,
    "[[ERROR] BAD/MISSING LINK TEXT](#cfn-attributes-updatepolicy-rollingupdate-mininstancesinservice)" : Integer,
    "[[ERROR] BAD/MISSING LINK TEXT](#cfn-attributes-updatepolicy-rollingupdate-minsuccessfulinstancespercent)" : Integer
    "[[ERROR] BAD/MISSING LINK TEXT](#cfn-attributes-updatepolicy-rollingupdate-pausetime)" : String,
    "[[ERROR] BAD/MISSING LINK TEXT](#cfn-attributes-updatepolicy-rollingupdate-suspendprocesses)" : [ List of processes ],
    "[[ERROR] BAD/MISSING LINK TEXT](#cfn-attributes-updatepolicy-rollingupdate-waitonresourcesignals)" : Boolean
  }
}
```

#### YAML<a name="aws-attribute-updatepolicy-rollingupdate-syntax.yaml"></a>

```
UpdatePolicy:
  AutoScalingRollingUpdate:
    [[ERROR] BAD/MISSING LINK TEXT](#cfn-attributes-updatepolicy-rollingupdate-maxbatchsize): Integer
    [[ERROR] BAD/MISSING LINK TEXT](#cfn-attributes-updatepolicy-rollingupdate-mininstancesinservice): Integer
    [[ERROR] BAD/MISSING LINK TEXT](#cfn-attributes-updatepolicy-rollingupdate-minsuccessfulinstancespercent): Integer
    [[ERROR] BAD/MISSING LINK TEXT](#cfn-attributes-updatepolicy-rollingupdate-pausetime): String
    [[ERROR] BAD/MISSING LINK TEXT](#cfn-attributes-updatepolicy-rollingupdate-suspendprocesses):
      - List of processes
    [[ERROR] BAD/MISSING LINK TEXT](#cfn-attributes-updatepolicy-rollingupdate-waitonresourcesignals): Boolean
```

### Properties<a name="w3ab2c21c23c23c13b8"></a>

`MaxBatchSize`  
Specifies the maximum number of instances that AWS CloudFormation updates\.  
*Default*: `1`  
*Type*: Integer  
*Required: *No

`MinInstancesInService`  
Specifies the minimum number of instances that must be in service within the Auto Scaling group while AWS CloudFormation updates old instances\.  
*Default*: `0`  
*Type*: Integer  
*Required: *No

`MinSuccessfulInstancesPercent`  
Specifies the percentage of instances in an Auto Scaling rolling update that must signal success for an update to succeed\. You can specify a value from `0` to `100`\. AWS CloudFormation rounds to the nearest tenth of a percent\. For example, if you update five instances with a minimum successful percentage of `50`, three instances must signal success\.  
If an instance doesn't send a signal within the time specified in the `PauseTime` property, AWS CloudFormation assumes that the instance wasn't updated\.  
If you specify this property, you must also enable the `WaitOnResourceSignals` and `PauseTime` properties\.  
*Default*: `100`  
*Type*: Integer  
*Required: *No

`PauseTime`  
The amount of time that AWS CloudFormation pauses after making a change to a batch of instances to give those instances time to start software applications\. For example, you might need to specify `PauseTime` when scaling up the number of instances in an Auto Scaling group\.   
If you enable the `WaitOnResourceSignals` property, `PauseTime` is the amount of time that AWS CloudFormation should wait for the Auto Scaling group to receive the required number of valid signals from added or replaced instances\. If the `PauseTime` is exceeded before the Auto Scaling group receives the required number of signals, the update fails\. For best results, specify a time period that gives your applications sufficient time to get started\. If the update needs to be rolled back, a short `PauseTime` can cause the rollback to fail\.  
Specify `PauseTime` in the [ISO8601 duration format](http://en.wikipedia.org/wiki/ISO_8601#Durations) \(in the format `PT#H#M#S`, where each *\#* is the number of hours, minutes, and seconds, respectively\)\. The maximum `PauseTime` is one hour \(`PT1H`\)\.  
*Default*: `PT0S` \(zero seconds\)\. If the `WaitOnResourceSignals` property is set to `true`, the default is `PT5M`\.  
*Type*: String  
*Required: *No

`SuspendProcesses`  
Specifies the Auto Scaling processes to suspend during a stack update\. Suspending processes prevents Auto Scaling from interfering with a stack update\. For example, you can suspend alarming so that Auto Scaling doesn't execute scaling policies associated with an alarm\. For valid values, see the `ScalingProcesses.member.N` parameter for the [SuspendProcesses](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_SuspendProcesses.html) action in the *Auto Scaling API Reference*\.  
*Default*: Not specified  
*Type*: List of Auto Scaling processes  
*Required: *No

`WaitOnResourceSignals`  
Specifies whether the Auto Scaling group waits on signals from new instances during an update\. Use this property to ensure that instances have completed installing and configuring applications before the Auto Scaling group update proceeds\. AWS CloudFormation suspends the update of an Auto Scaling group after new EC2 instances are launched into the group\. AWS CloudFormation must receive a signal from each new instance within the specified `PauseTime` before continuing the update\. To signal the Auto Scaling group, use the [cfn\-signal](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-signal.html) helper script or [http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_SignalResource.html](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_SignalResource.html) API\.  
To have instances wait for an Elastic Load Balancing health check before they signal success, add a health\-check verification by using the [cfn\-init](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-init.html) helper script\. For an example, see the `verify_instance_health` command in the [Auto Scaling rolling updates](https://github.com/awslabs/aws-cloudformation-templates/blob/master/aws/services/AutoScaling/AutoScalingRollingUpdates.yaml) sample template\.  
*Default*: `false`  
*Type*: Boolean  
*Required: *Conditional\. If you specify the `MinSuccessfulInstancesPercent` property, you must also enable the `WaitOnResourceSignals` and `PauseTime` properties\.

## AutoScalingScheduledAction Policy<a name="cfn-attributes-updatepolicy-scheduledactions"></a>

To specify how AWS CloudFormation handles updates for the `MinSize`, `MaxSize`, and `DesiredCapacity` properties when the `AWS::AutoScaling::AutoScalingGroup` resource has an associated scheduled action, use the `AutoScalingScheduledAction` policy\.

With scheduled actions, the group size properties of an Auto Scaling group can change at any time\. When you update a stack with an Auto Scaling group and scheduled action, AWS CloudFormation always sets the group size property values of your Auto Scaling group to the values that are defined in the `AWS::AutoScaling::AutoScalingGroup` resource of your template, even if a scheduled action is in effect\. 

If you do not want AWS CloudFormation to change any of the group size property values when you have a scheduled action in effect, use the `AutoScalingScheduledAction` update policy to prevent AWS CloudFormation from changing the `MinSize`, `MaxSize`, or `DesiredCapacity` properties unless you have modified these values in your template\.

### Syntax<a name="w3ab2c21c23c23c15b8"></a>

#### JSON<a name="aws-attribute-updatepolicy-scheduledactions-syntax.json"></a>

```
"UpdatePolicy" : {
  "AutoScalingScheduledAction" : {
    "[[ERROR] BAD/MISSING LINK TEXT](#cfn-attributes-updatepolicy-scheduledactions-ignoreunmodifiedgroupsizeproperties)" : Boolean
  }
}
```

#### YAML<a name="aws-attribute-updatepolicy-scheduledactions-syntax.yaml"></a>

```
UpdatePolicy:
  AutoScalingScheduledAction:
    [[ERROR] BAD/MISSING LINK TEXT](#cfn-attributes-updatepolicy-scheduledactions-ignoreunmodifiedgroupsizeproperties): Boolean
```

### Properties<a name="w3ab2c21c23c23c15c10"></a>

`IgnoreUnmodifiedGroupSizeProperties`  
Specifies whether AWS CloudFormation ignores differences in group size properties between your current Auto Scaling group and the Auto Scaling group described in the `AWS::AutoScaling::AutoScalingGroup` resource of your template during a stack update\. If you modify any of the group size property values in your template, AWS CloudFormation uses the modified values and updates your Auto Scaling group\.  
*Default*: `false`  
*Type*: Boolean  
*Required: *No

## CodeDeployLambdaAliasUpdate Policy<a name="cfn-attributes-updatepolicy-codedeploylambdaaliasupdate"></a>

To perform an AWS CodeDeploy deployment when the version changes on an `AWS::Lambda::Alias` resource, use the `CodeDeployLambdaAliasUpdate` update policy\.

### Syntax<a name="w3ab2c21c23c23c17b5"></a>

#### JSON<a name="aws-attribute-updatepolicy-codedeploylambdaaliasupdate-syntax.json"></a>

```
"UpdatePolicy" : {
  "CodeDeployLambdaAliasUpdate" : {
    "[[ERROR] BAD/MISSING LINK TEXT](#cfn-attributes-updatepolicy-codedeploylambdaaliasupdate-afterallowtraffichook)" : String,
    "[[ERROR] BAD/MISSING LINK TEXT](#cfn-attributes-updatepolicy-codedeploylambdaaliasupdate-applicationname)" : String,
    "[[ERROR] BAD/MISSING LINK TEXT](#cfn-attributes-updatepolicy-codedeploylambdaaliasupdate-beforeallowtraffichook)" : String,
    "[[ERROR] BAD/MISSING LINK TEXT](#cfn-attributes-updatepolicy-codedeploylambdaaliasupdate-deploymentgroupname)" : String
  }
}
```

#### YAML<a name="aws-attribute-updatepolicy-codedeploylambdaaliasupdate-syntax.yaml"></a>

```
UpdatePolicy:
  CodeDeployLambdaAliasUpdate:
    [[ERROR] BAD/MISSING LINK TEXT](#cfn-attributes-updatepolicy-codedeploylambdaaliasupdate-afterallowtraffichook): String
    [[ERROR] BAD/MISSING LINK TEXT](#cfn-attributes-updatepolicy-codedeploylambdaaliasupdate-applicationname): String
    [[ERROR] BAD/MISSING LINK TEXT](#cfn-attributes-updatepolicy-codedeploylambdaaliasupdate-beforeallowtraffichook): String
    [[ERROR] BAD/MISSING LINK TEXT](#cfn-attributes-updatepolicy-codedeploylambdaaliasupdate-deploymentgroupname): String
```

### Properties<a name="aws-attribute-updatepolicy-codedeploylambdaaliasupdate-properties"></a>

`AfterAllowTrafficHook`  
The name of the Lambda function to run after traffic routing completes\.  
*Required: *No  
*Type: *String

`ApplicationName`  
The name of the AWS CodeDeploy application\.  
*Required: *Yes  
*Type: *String

`BeforeAllowTrafficHook`  
The name of the Lambda function to run before traffic routing starts\.  
*Required: *No  
*Type: *String

`DeploymentGroupName`  
The name of the AWS CodeDeploy deployment group\. This is where the traffic\-shifting policy is set\.  
*Required: *Yes  
*Type: *String

For an example that specifies the `UpdatePolicy` attribute for an `AWS::Lambda::Alias` resource, see \.

## Examples<a name="aws-attribute-updatepolicy-examples"></a>

The following examples show how to add an update policy to an Auto Scaling group and how to maintain availability when updating metadata\.

### Add an UpdatePolicy to an Auto Scaling Group<a name="w3ab2c21c23c23c19b4"></a>

The following example shows how to add an update policy\. During an update, the Auto Scaling group updates instances in batches of two and keeps a minimum of one instance in service\. Because the `WaitOnResourceSignals` flag is set, the Auto Scaling group waits for new instances that are added to the group\. The new instances must signal the Auto Scaling group before it updates the next batch of instances\.

#### JSON<a name="attribute-updatepolicy-example-1.json"></a>

```
"ASG" : {
   "Type" : "AWS::AutoScaling::AutoScalingGroup",
   "Properties" : {
      "AvailabilityZones" : [
         "us-east-1a",
         "us-east-1b"
      ],
      "DesiredCapacity" : "1",
      "LaunchConfigurationName" : {
         "Ref" : "LaunchConfig"
      },
      "MaxSize" : "4",
      "MinSize" : "1"
   },
   "UpdatePolicy" : {
      "AutoScalingScheduledAction" : {
         "IgnoreUnmodifiedGroupSizeProperties" : "true"
      },
      "AutoScalingRollingUpdate" : {
         "MinInstancesInService" : "1",
         "MaxBatchSize" : "2",
         "WaitOnResourceSignals" : "true",
         "PauseTime" : "PT10M"
      }
   }
 },
"ScheduledAction" : {
   "Type" : "AWS::AutoScaling::ScheduledAction",
   "Properties" : {
      "AutoScalingGroupName" : {
         "Ref" : "ASG"
      },
      "DesiredCapacity" : "2",
      "StartTime" : "2017-06-02T20 : 00 : 00Z"
   }
}
```

#### YAML<a name="attribute-updatepolicy-example-1.yaml"></a>

```
ASG:
  Type: 'AWS::AutoScaling::AutoScalingGroup'
  Properties:
    AvailabilityZones:
    - us-east-1a
    - us-east-1b
    DesiredCapacity: '1'
    LaunchConfigurationName:
      Ref: LaunchConfig
    MaxSize: '4'
    MinSize: '1'
  UpdatePolicy:
    AutoScalingScheduledAction:
      IgnoreUnmodifiedGroupSizeProperties: 'true'
    AutoScalingRollingUpdate:
      MinInstancesInService: '1'
      MaxBatchSize: '2'
      WaitOnResourceSignals: 'true'
      PauseTime: PT10M
ScheduledAction:
  Type: 'AWS::AutoScaling::ScheduledAction'
  Properties:
    AutoScalingGroupName:
      Ref: ASG
    DesiredCapacity: '2'
    StartTime: '2017-06-02T20 : 00 : 00Z'
```

### AutoScalingReplacingUpdate Policy<a name="w3ab2c21c23c23c19b6"></a>

The following example declares a policy that forces an associated Auto Scaling group to be replaced during an update\. For the update to succeed, a percentage of instances \(specified by the `MinSuccessfulPercentParameter` parameter\) must signal success within the `Timeout` period\.

#### JSON<a name="attribute-updatepolicy-example-2.json"></a>

```
"UpdatePolicy" : {
  "AutoScalingReplacingUpdate" : {
    "WillReplace" : "true"
  }
},
"CreationPolicy" : {
  "ResourceSignal" : {
    "Count" : { "Ref" : "ResourceSignalsOnCreate"},
    "Timeout" : "PT10M"
  },
  "AutoScalingCreationPolicy" : {
    "MinSuccessfulInstancesPercent" : { "Ref" : "MinSuccessfulPercentParameter" }
  }
}
```

#### YAML<a name="attribute-updatepolicy-example-2.yaml"></a>

```
UpdatePolicy:
  AutoScalingReplacingUpdate:
    WillReplace: 'true'
CreationPolicy:
  ResourceSignal:
    Count: !Ref 'ResourceSignalsOnCreate'
    Timeout: PT10M
  AutoScalingCreationPolicy:
    MinSuccessfulInstancesPercent: !Ref 'MinSuccessfulPercentParameter'
```

### Maintain Availability When Updating the Metadata for the cfn\-init Helper Script<a name="w3ab2c21c23c23c19b8"></a>

When you install software applications on your instances, you might use the [http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-init.html](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-init.html) metadata key and the [http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-init.html](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-init.html) helper script to bootstrap the instances in your Auto Scaling group\. AWS CloudFormation installs the packages, runs the commands, and performs other bootstrapping actions described in the metadata\.

When you update only the metadata \(for example, when updating a package to another version\), you can use the `[cfn\-hup](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-hup.html)` helper daemon to detect and apply the updates\. However, the `cfn-hup` daemon runs independently on each instance\. If the daemon happens to runs at the same time on all instances, your application or service might be unavailable during the update\. To guarantee availability, you can force a rolling update so that AWS CloudFormation updates your instances one batch at a time\.

**Important**  
Forcing a rolling update requires AWS CloudFormation to create a new instance and then delete the old one\. Any information stored on the old instance is lost\.

To force a rolling update, change the logical ID of the launch configuration resource, and then update the stack and any references pointing to the original logic ID \(such as the associated Auto Scaling group\)\. AWS CloudFormation triggers a rolling update on the Auto Scaling group, replacing all instances\.

### Original Template<a name="w3ab2c21c23c23c19c10"></a>

```
"LaunchConfig": {
  "Type" : "AWS::AutoScaling::LaunchConfiguration",
  "Metadata" : {
    "Comment" : "Install a simple PHP application",
    "AWS::CloudFormation::Init" : {
    ...
    }
  }
}
```

### Updated Logical ID<a name="w3ab2c21c23c23c19c12"></a>

```
"LaunchConfigUpdateRubygemsPkg": {
  "Type" : "AWS::AutoScaling::LaunchConfiguration",
  "Metadata" : {
    "Comment" : "Install a simple PHP application",
    "AWS::CloudFormation::Init" : {
    ...
    }
  }
}
```

### Lambda Alias Update Policy<a name="aws-resource-lambda-alias-example"></a>

The following example specifies the `UpdatePolicy` attribute for an `AWS::Lambda::Alias` resource\. All the details for the deployment are defined by the application and deployment group that are passed into the policy\.

#### JSON<a name="aws-attribute-updatepolicy-codedeploylambda.json"></a>

```
"Alias": {
  "Type": "AWS::Lambda::Alias",
  "Properties": {
    "FunctionName": {
      "Ref": "LambdaFunction"
    },
    "FunctionVersion": {
      "Fn::GetAtt": [
        "FunctionVersionTwo",
        "Version"
      ]
    },
    "Name": "MyAlias"
  },
  "UpdatePolicy": {
    "CodeDeployLambdaAliasUpdate": {
      "ApplicationName": {
        "Ref": "CodeDeployApplication"
      },
      "DeploymentGroupName": {
        "Ref": "CodeDeployDeploymentGroup"
      },
      "BeforeAllowTrafficHook": {
        "Ref": "PreHookLambdaFunction"
      },
      "AfterAllowTrafficHook": {
        "Ref": "PreHookLambdaFunction"
      }
    }
  }
}
```

#### YAML<a name="aws-attribute-updatepolicy-codedeploylambda-example.yaml"></a>

```
Alias:
  Type: 'AWS::Lambda::Alias'
  Properties:
    FunctionName: !Ref LambdaFunction
    FunctionVersion: !GetAtt FunctionVersionTwo.Version
    Name: MyAlias
  UpdatePolicy:
    CodeDeployLambdaAliasUpdate:
      ApplicationName: !Ref CodeDeployApplication
      DeploymentGroupName: !Ref CodeDeployDeploymentGroup
      BeforeAllowTrafficHook: !Ref PreHookLambdaFunction
      AfterAllowTrafficHook: !Ref PreHookLambdaFunction
```