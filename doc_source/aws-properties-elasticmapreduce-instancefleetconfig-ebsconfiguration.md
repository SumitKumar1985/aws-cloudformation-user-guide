# Amazon EMR InstanceFleetConfig EbsConfiguration<a name="aws-properties-elasticmapreduce-instancefleetconfig-ebsconfiguration"></a>

Use the `EbsConfiguration` property to specify the Amazon EBS configuration of an Amazon EMR fleet instance\. `EbsConfiguration` is a subproperty of the [Amazon EMR InstanceFleetConfig InstanceTypeConfig](aws-properties-elasticmapreduce-instancefleetconfig-instancetypeconfig.md) property\.

**Note**  
The instance fleet configuration is available only in Amazon EMR versions 4\.8\.0 and later, excluding 5\.0\.x versions\.

## Syntax<a name="aws-properties-elasticmapreduce-instancefleetconfig-ebsconfiguration-syntax"></a>

To declare this entity in your AWS CloudFormation template, use the following syntax:

### JSON<a name="aws-properties-elasticmapreduce-instancefleetconfig-ebsconfiguration-syntax.json"></a>

```
{
  "[[ERROR] BAD/MISSING LINK TEXT](#cfn-elasticmapreduce-instancefleetconfig-ebsconfiguration-ebsblockdeviceconfigs)" : [ EbsBlockDeviceConfig, ...],
  "[[ERROR] BAD/MISSING LINK TEXT](#cfn-elasticmapreduce-instancefleetconfig-ebsconfiguration-ebsoptimized)" : Boolean
}
```

### YAML<a name="aws-properties-elasticmapreduce-instancefleetconfig-ebsconfiguration-syntax.yaml"></a>

```
[[ERROR] BAD/MISSING LINK TEXT](#cfn-elasticmapreduce-instancefleetconfig-ebsconfiguration-ebsblockdeviceconfigs): 
  - EbsBlockDeviceConfig
[[ERROR] BAD/MISSING LINK TEXT](#cfn-elasticmapreduce-instancefleetconfig-ebsconfiguration-ebsoptimized): Boolean
```

## Properties<a name="aws-properties-elasticmapreduce-instancefleetconfig-ebsconfiguration-properties"></a>

`EbsBlockDeviceConfigs`  
A list of Amazon EBS volume specifications that are attached to an instance\. Duplicates not allowed\.  
*Required: *No  
*Type*: List of [Amazon EMR InstanceFleetConfig EbsBlockDeviceConfig](aws-properties-elasticmapreduce-instancefleetconfig-ebsblockdeviceconfig.md)  
*Update requires*: Replacement

`EbsOptimized`  
Indicates whether an Amazon EBS volume is EBS\-optimized\.  
*Required: *No  
*Type*: Boolean  
*Update requires*: Replacement