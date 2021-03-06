# AWS::Glue::Classifier<a name="aws-resource-glue-classifier"></a>

The `AWS::Glue::Classifier` resource creates an AWS Glue classifier that categorizes data sources and specifies schemas\. For more information, see [Adding Classifiers to a Crawler](http://docs.aws.amazon.com/glue/latest/dg/add-classifier.html) and [Classifier Structure](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-classifiers.html#aws-glue-api-crawler-classifiers-Classifier) in the *AWS Glue Developer Guide*\. 


+ [Syntax](#aws-resource-glue-classifier-syntax)
+ [Properties](#aws-resource-glue-classifier-properties)
+ [Return Values](#aws-resource-glue-classifier-returnvalues)

## Syntax<a name="aws-resource-glue-classifier-syntax"></a>

To declare this entity in your AWS CloudFormation template, use the following syntax:

### JSON<a name="aws-resource-glue-classifier-syntax.json"></a>

```
{
  "Type" : "AWS::Glue::Classifier",
  "Properties" : {
    "[[ERROR] BAD/MISSING LINK TEXT](#cfn-glue-classifier-grokclassifier)" : GrokClassifier
  }
}
```

### YAML<a name="aws-resource-glue-classifier-syntax.yaml"></a>

```
Type: "AWS::Glue::Classifier"
Properties:
  [[ERROR] BAD/MISSING LINK TEXT](#cfn-glue-classifier-grokclassifier): 
    GrokClassifier
```

## Properties<a name="aws-resource-glue-classifier-properties"></a>

`GrokClassifier`  
A classifier that uses `grok`\.  
 *Required*: No  
 *Type*:   
 *Update requires*: No interruption 

## Return Values<a name="aws-resource-glue-classifier-returnvalues"></a>

### Ref<a name="w3ab2c21c10d654c10b3"></a>

When the logical ID of this resource is provided to the `Ref` intrinsic function, `Ref` returns the resource name\.

For more information about using the `Ref` function, see Ref\. 