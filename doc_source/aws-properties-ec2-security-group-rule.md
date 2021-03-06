# EC2 Security Group Rule Property Type<a name="aws-properties-ec2-security-group-rule"></a>

The EC2 Security Group Rule is an embedded property of the AWS::EC2::SecurityGroup type\.

## Syntax SecurityGroupIngress<a name="w3ab2c21c14d605b5"></a>

### JSON<a name="aws-properties-ec2-securitygroup-rule-securitygroupingress-syntax.json"></a>

```
{
  "CidrIp" : String,
  "CidrIpv6" : String,
  "Description" : String,
  "FromPort" : Integer,
  "IpProtocol" : String,
  "SourceSecurityGroupId" : String,
  "SourceSecurityGroupName" : String,
  "SourceSecurityGroupOwnerId" : String,
  "ToPort" : Integer
}
```

### YAML<a name="aws-properties-ec2-securitygroup-rule-securitygroupingress-syntax.yaml"></a>

```
CidrIp: String
CidrIpv6: String
Description: String
FromPort: Integer
IpProtocol: String
SourceSecurityGroupId: String
SourceSecurityGroupName: String
SourceSecurityGroupOwnerId: String
ToPort: Integer
```

## Syntax SecurityGroupEgress<a name="w3ab2c21c14d605b7"></a>

### JSON<a name="aws-properties-ec2-securitygroup-rule-securitygroupegress-syntax.json"></a>

```
{
  "CidrIp" : String,
  "CidrIpv6" : String,
  "Description" : String,
  "DestinationPrefixListId" : String,
  "DestinationSecurityGroupId" : String,
  "FromPort" : Integer,
  "IpProtocol" : String,
  "ToPort" : Integer
}
```

### YAML<a name="aws-properties-ec2-securitygroup-rule-securitygroupegress-syntax.yaml"></a>

```
CidrIp: String
CidrIpv6: String
Description: String
DestinationPrefixListId: String
DestinationSecurityGroupId: String
FromPort: Integer
IpProtocol: String
ToPort: Integer
```

## Properties<a name="w3ab2c21c14d605b9"></a>

`CidrIp`  
Specifies an IPv4 CIDR range\.  
*Required: *Conditional\. You must specify only one of the following properties: `CidrIp`, `CidrIpv6`, `DestinationPrefixListId`, `DestinationSecurityGroupId`, or `SourceSecurityGroupId`\.  
*Type*: String

`CidrIpv6`  
Specifies an IPv6 CIDR range\.  
*Required: *Conditional\. You must specify only one of the following properties: `CidrIp`, `CidrIpv6`, `DestinationPrefixListId`, `DestinationSecurityGroupId`, or `SourceSecurityGroupId`\.  
*Type*: String

`Description`  
Description of the security group rule\.  
*Type*: String

`DestinationPrefixListId` \(SecurityGroupEgress only\)  
The AWS service prefix of an Amazon VPC endpoint\. For more information, see [VPC Endpoints](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/vpc-endpoints.html) in the *Amazon VPC User Guide*\.  
*Required: *Conditional\. You must specify only one of the following properties: `CidrIp`, `CidrIpv6`, `DestinationPrefixListId`, `DestinationSecurityGroupId`, or `SourceSecurityGroupId`\.  
*Type*: String

`DestinationSecurityGroupId` \(SecurityGroupEgress only\)  
Specifies the GroupId of the destination Amazon VPC security group\.  
*Required: *Conditional\. You must specify only one of the following properties: `CidrIp`, `CidrIpv6`, `DestinationPrefixListId`, `DestinationSecurityGroupId`, or `SourceSecurityGroupId`\.  
*Type*: String

`FromPort`  
The start of port range for the TCP and UDP protocols, or an ICMP type number\. An ICMP type number of \-1 indicates a wildcard \(i\.e\., any ICMP type number\)\.  
*Required: *No  
*Type*: Integer

`IpProtocol`  
An IP protocol name or number\. For valid values, go to the IpProtocol parameter in [AuthorizeSecurityGroupIngress](http://docs.aws.amazon.com/AWSEC2/latest/APIReference/ApiReference-query-AuthorizeSecurityGroupIngress.html)  
*Required: *Yes  
*Type*: String

`SourceSecurityGroupId` \(SecurityGroupIngress only\)  
*For VPC security groups only*\. Specifies the ID of the Amazon EC2 Security Group to allow access\. You can use the `Ref` intrinsic function to refer to the logical ID of a security group defined in the same template\.  
*Required: *Conditional\. You must specify only one of the following properties: `CidrIp`, `CidrIpv6`, `DestinationPrefixListId`, `DestinationSecurityGroupId`, or `SourceSecurityGroupId`\.  
*Type*: String

`SourceSecurityGroupName` \(SecurityGroupIngress only\)  
*For non\-VPC security groups only*\. Specifies the name of the Amazon EC2 Security Group to use for access\. You can use the `Ref` intrinsic function to refer to the logical name of a security group that is defined in the same template\.  
*Required: *Conditional\. If you specify `CidrIp`, do not specify `SourceSecurityGroupName`\.  
*Type*: String

`SourceSecurityGroupOwnerId` \(SecurityGroupIngress only\)  
Specifies the AWS Account ID of the owner of the Amazon EC2 Security Group that is specified in the `SourceSecurityGroupName` property\.  
*Required: *Conditional\. If you specify `SourceSecurityGroupName` and that security group is owned by a different account than the account creating the stack, you must specify the `SourceSecurityGroupOwnerId`; otherwise, this property is optional\.  
*Type*: String

`ToPort`  
The end of port range for the TCP and UDP protocols, or an ICMP code\. An ICMP code of \-1 indicates a wildcard \(i\.e\., any ICMP code\)\.  
*Required: *No  
*Type*: Integer

## Examples<a name="w3ab2c21c14d605c11"></a>

### Security Group with CidrIp<a name="w3ab2c21c14d605c11b2"></a>

#### JSON<a name="aws-properties-ec2-securitygroup-rule-securitygroupingress-example.json"></a>

```
"InstanceSecurityGroup" : {
   "Type" : "AWS::EC2::SecurityGroup",
   "Properties" : {
      "GroupDescription" : "Enable SSH access via port 22",
      "SecurityGroupIngress" : [ {
         "IpProtocol" : "tcp",
         "FromPort" : "22",
         "ToPort" : "22",
         "CidrIp" : "0.0.0.0/0"
      } ]
   }
}
```

#### YAML<a name="aws-properties-ec2-securitygroup-rule-securitygroupingress-example.yaml"></a>

```
InstanceSecurityGroup: 
  Type: "AWS::EC2::SecurityGroup"
  Properties: 
    GroupDescription: "Enable SSH access via port 22"
    SecurityGroupIngress: 
      - 
        IpProtocol: "tcp"
        FromPort: "22"
        ToPort: "22"
        CidrIp: "0.0.0.0/0"
```

### Security Group with Security Group Id<a name="w3ab2c21c14d605c11b4"></a>

#### JSON<a name="aws-properties-ec2-securitygroup-rule-securitygroupingress-example2.json"></a>

```
"InstanceSecurityGroup" : {
   "Type" : "AWS::EC2::SecurityGroup",
   "Properties" : {
      "GroupDescription" : "Enable HTTP access on the configured port",
      "VpcId" : { "Ref" : "VpcId" },
      "SecurityGroupIngress" : [ {
         "IpProtocol" : "tcp",
         "FromPort" : { "Ref" : "WebServerPort" },
         "ToPort" : { "Ref" : "WebServerPort" },
         "SourceSecurityGroupId" : { "Ref" : "LoadBalancerSecurityGroup" }
      } ]
   }
}
```

#### YAML<a name="aws-properties-ec2-securitygroup-rule-securitygroupingress-example2.yaml"></a>

```
InstanceSecurityGroup: 
  Type: "AWS::EC2::SecurityGroup"
  Properties: 
    GroupDescription: "Enable HTTP access on the configured port"
    VpcId: 
      Ref: "VpcId"
    SecurityGroupIngress: 
      - 
        IpProtocol: "tcp"
        FromPort: 
          Ref: "WebServerPort"
        ToPort: 
          Ref: "WebServerPort"
        SourceSecurityGroupId: 
          Ref: "LoadBalancerSecurityGroup"
```

### Security Group with Multiple Ingress Rules<a name="w3ab2c21c14d605c11b6"></a>

This snippet grants SSH access with CidrIp, and HTTP access with `SourceSecurityGroupName`\. `Fn::GetAtt` is used to derive the values for `SourceSecurityGroupName` and `SourceSecurityGroupOwnerId` from the elastic load balancer\.

#### JSON<a name="aws-properties-ec2-securitygroup-rule-securitygroupingress-example3.json"></a>

```
"ElasticLoadBalancer" : {
   "Type" : "AWS::ElasticLoadBalancing::LoadBalancer",
   "Properties" : {
      "AvailabilityZones" : { "Fn::GetAZs" : "" },
      "Listeners" : [ {
         "LoadBalancerPort" : "80",
         "InstancePort" : { "Ref" : "WebServerPort" },
         "Protocol" : "HTTP"
      } ],
      "HealthCheck" : {
         "Target" : { "Fn::Join" : [ "", ["HTTP:", { "Ref" : "WebServerPort" }, "/"]]},
         "HealthyThreshold" : "3",
         "UnhealthyThreshold" : "5",
         "Interval" : "30",
         "Timeout" : "5"
      }
   }
},

"InstanceSecurityGroup" : {
   "Type" : "AWS::EC2::SecurityGroup",
   "Properties" : {
      "GroupDescription" : "Enable SSH access and HTTP from the load balancer only",
      "SecurityGroupIngress" : [ {
         "IpProtocol" : "tcp",
         "FromPort" : "22",
         "ToPort" : "22",
         "CidrIp" : "0.0.0.0/0"
      }, {
         "IpProtocol" : "tcp",
         "FromPort" : { "Ref" : "WebServerPort" },
         "ToPort" : { "Ref" : "WebServerPort" },
         "SourceSecurityGroupOwnerId" : {"Fn::GetAtt" : ["ElasticLoadBalancer", "SourceSecurityGroup.OwnerAlias"]},
         "SourceSecurityGroupName" : {"Fn::GetAtt" : ["ElasticLoadBalancer", "SourceSecurityGroup.GroupName"]}
      } ]
   }
}
```

#### YAML<a name="aws-properties-ec2-securitygroup-rule-securitygroupingress-example3.yaml"></a>

```
ElasticLoadBalancer: 
  Type: "AWS::ElasticLoadBalancing::LoadBalancer"
  Properties: 
    AvailabilityZones: 
      Fn::GetAZs: ""
    Listeners: 
      - 
        LoadBalancerPort: "80"
        InstancePort: 
          Ref: "WebServerPort"
        Protocol: "HTTP"
    HealthCheck: 
      Target: 
        Fn::Join: 
          - ""
          - 
            - "HTTP:"
            - 
              Ref: "WebServerPort"
            - "/"
      HealthyThreshold: "3"
      UnhealthyThreshold: "5"
      Interval: "30"
      Timeout: "5"
InstanceSecurityGroup: 
  Type: "AWS::EC2::SecurityGroup"
  Properties: 
    GroupDescription: "Enable SSH access and HTTP from the load balancer only"
    SecurityGroupIngress: 
      - 
        IpProtocol: "tcp"
        FromPort: "22"
        ToPort: "22"
        CidrIp: "0.0.0.0/0"
      - 
        IpProtocol: "tcp"
        FromPort: 
          Ref: "WebServerPort"
        ToPort: 
          Ref: "WebServerPort"
        SourceSecurityGroupOwnerId: 
          Fn::GetAtt: 
            - "ElasticLoadBalancer"
            - "SourceSecurityGroup.OwnerAlias"
        SourceSecurityGroupName: 
          Fn::GetAtt: 
            - "ElasticLoadBalancer"
            - "SourceSecurityGroup.GroupName"
```

## See Also<a name="w3ab2c21c14d605c13"></a>

+ [Amazon EC2 Security Groups](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html) in the *Amazon EC2 User Guide*