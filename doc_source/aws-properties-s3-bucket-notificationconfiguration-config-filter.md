# Amazon S3 Bucket NotificationFilter<a name="aws-properties-s3-bucket-notificationconfiguration-config-filter"></a>

`Filter` is a property of the `LambdaConfigurations`, `QueueConfigurations`, and `TopicConfigurations` properties that describes the filtering rules that determine the Amazon Simple Storage Service \(Amazon S3\) objects for which to send notifications\.

## Syntax<a name="w3ab2c21c14e1514b5"></a>

### JSON<a name="aws-properties-s3-bucket-notificationconfiguration-config-filter-syntax.json"></a>

```
{
  "[[ERROR] BAD/MISSING LINK TEXT](#cfn-s3-bucket-notificationconfiguraiton-config-filter-s3key)" : S3 Key
}
```

### YAML<a name="aws-properties-s3-bucket-notificationconfiguration-config-filter-syntax.yaml"></a>

```
[[ERROR] BAD/MISSING LINK TEXT](#cfn-s3-bucket-notificationconfiguraiton-config-filter-s3key):
  S3 Key
```

## Properties<a name="w3ab2c21c14e1514b7"></a>

`S3Key`  
Amazon S3 filtering rules that describe for which object key names to send notifications\.  
*Required: *Yes  
*Type*: [Amazon S3 Bucket S3KeyFilter](aws-properties-s3-bucket-notificationconfiguration-config-filter-s3key.md)