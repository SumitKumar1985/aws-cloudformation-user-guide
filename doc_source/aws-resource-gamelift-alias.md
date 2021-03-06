# AWS::GameLift::Alias<a name="aws-resource-gamelift-alias"></a>

The `AWS::GameLift::Alias` resource creates an alias for an Amazon GameLift \(GameLift\) fleet, which you can use to anonymize your fleet\. You can reference the alias instead of a specific fleet when you create game sessions\. For more information, see the [CreateAlias](http://docs.aws.amazon.com/gamelift/latest/apireference/API_CreateAlias.html) action in the *Amazon GameLift API Reference*\.


+ [Syntax](#aws-resource-gamelift-alias-syntax)
+ [Properties](#w3ab2c21c10d642b9)
+ [Return Value](#w3ab2c21c10d642c11)
+ [Example](#w3ab2c21c10d642c13)

## Syntax<a name="aws-resource-gamelift-alias-syntax"></a>

To declare this entity in your AWS CloudFormation template, use the following syntax:

### JSON<a name="aws-resource-gamelift-alias-syntax.json"></a>

```
{
  "Type" : "AWS::GameLift::Alias",
  "Properties" : {
    "[[ERROR] BAD/MISSING LINK TEXT](#cfn-gamelift-alias-name)" : String,
    "[[ERROR] BAD/MISSING LINK TEXT](#cfn-gamelift-alias-description)" : String,
    "[[ERROR] BAD/MISSING LINK TEXT](#cfn-gamelift-alias-routingstrategy)" : RoutingStrategy
  }
}
```

### YAML<a name="aws-resource-gamelift-alias-syntax.yaml"></a>

```
Type: "AWS::GameLift::Alias"
Properties: 
  [[ERROR] BAD/MISSING LINK TEXT](#cfn-gamelift-alias-name): String
  [[ERROR] BAD/MISSING LINK TEXT](#cfn-gamelift-alias-description): String
  [[ERROR] BAD/MISSING LINK TEXT](#cfn-gamelift-alias-routingstrategy):
    RoutingStrategy
```

## Properties<a name="w3ab2c21c10d642b9"></a>

`Description`  
Information that helps you identify the purpose of this alias\.  
*Required: *No  
*Type*: String  
*Update requires*: No interruption

`Name`  
An identifier to associate with this alias\. Alias names don't need to be unique\.  
*Required: *Yes  
*Type*: String  
*Update requires*: No interruption

`RoutingStrategy`  
A routing configuration that specifies where traffic is directed for this alias, such as to a fleet or to a message\.  
*Required: *Yes  
*Type*: [Amazon GameLift Alias RoutingStrategy](aws-properties-gamelift-alias-routingstrategy.md)  
*Update requires*: No interruption

## Return Value<a name="w3ab2c21c10d642c11"></a>

### Ref<a name="w3ab2c21c10d642c11b2"></a>

When the logical ID of this resource is provided to the `Ref` intrinsic function, `Ref` returns the alias ID, such as `myalias-a01234b56-7890-1de2-f345-g67h8i901j2k`\.

For more information about using the `Ref` function, see Ref\.

## Example<a name="w3ab2c21c10d642c13"></a>

The following example creates a terminal alias named `TerminalAlias` with a generic terminal message\.

### JSON<a name="aws-resource-gamelift-alias-example.json"></a>

```
"AliasResource": {
  "Type": "AWS::GameLift::Alias",
  "Properties": {
    "Name": "TerminalAlias",
    "Description": "A terminal alias",
    "RoutingStrategy": {
      "Type": "TERMINAL",
      "Message": "Terminal routing strategy message"
    }
  }
}
```

### YAML<a name="aws-resource-gamelift-alias-example.yaml"></a>

```
AliasResource: 
  Type: "AWS::GameLift::Alias"
  Properties: 
    Name: "TerminalAlias"
    Description: "A terminal alias"
    RoutingStrategy: 
      Type: "TERMINAL"
      Message: "Terminal routing strategy message"
```