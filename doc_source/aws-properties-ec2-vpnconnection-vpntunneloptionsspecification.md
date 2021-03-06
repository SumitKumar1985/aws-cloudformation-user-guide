# Amazon EC2 VPNConnection VpnTunnelOptionsSpecification<a name="aws-properties-ec2-vpnconnection-vpntunneloptionsspecification"></a>

<a name="aws-properties-ec2-vpnconnection-vpntunneloptionsspecification-description"></a>The `VpnTunnelOptionsSpecification` property type configures tunnel options for an EC2 VPN connection\.

<a name="aws-properties-ec2-vpnconnection-vpntunneloptionsspecification-inheritance"></a> `VpnTunnelOptionsSpecification` is a property of the [AWS::EC2::VPNConnection](aws-resource-ec2-vpn-connection.md) resource\.

## Syntax<a name="aws-properties-ec2-vpnconnection-vpntunneloptionsspecification-syntax"></a>

To declare this entity in your AWS CloudFormation template, use the following syntax:

### JSON<a name="aws-properties-ec2-vpnconnection-vpntunneloptionsspecification-syntax.json"></a>

```
{
  "[[ERROR] BAD/MISSING LINK TEXT](#cfn-ec2-vpnconnection-vpntunneloptionsspecification-presharedkey)" : String,
  "[[ERROR] BAD/MISSING LINK TEXT](#cfn-ec2-vpnconnection-vpntunneloptionsspecification-tunnelinsidecidr)" : String
}
```

### YAML<a name="aws-properties-ec2-vpnconnection-vpntunneloptionsspecification-syntax.yaml"></a>

```
[[ERROR] BAD/MISSING LINK TEXT](#cfn-ec2-vpnconnection-vpntunneloptionsspecification-presharedkey): String
[[ERROR] BAD/MISSING LINK TEXT](#cfn-ec2-vpnconnection-vpntunneloptionsspecification-tunnelinsidecidr): String
```

## Properties<a name="aws-properties-ec2-vpnconnection-vpntunneloptionsspecification-properties"></a>

`PreSharedKey`  
The pre\-shared key \(PSK\) to establish initial authentication between the virtual private gateway and customer gateway\.  
 *Constraints*: Allowed characters are alphanumeric characters and \.\_\. Must be between 8 and 64 characters in length and cannot start with zero \(0\)\.  
 *Required*: No  
 *Type*: String  
 *Update requires*: Replacement 

`TunnelInsideCidr`  
The range of inside IP addresses for the tunnel\. Any specified CIDR blocks must be unique across all VPN connections that use the same virtual private gateway\.  
 *Constraints*: A size /30 CIDR block from the `169.254.0.0/16` range\. The following CIDR blocks are reserved and cannot be used:  

+ `169.254.0.0/30`

+ `169.254.1.0/30`

+ `169.254.2.0/30`

+ `169.254.3.0/30`

+ `169.254.4.0/30`

+ `169.254.5.0/30`

+ `169.254.169.252/30`
 *Required*: No  
 *Type*: String  
 *Update requires*: Replacement 

## See Also<a name="aws-properties-ec2-vpnconnection-vpntunneloptionsspecification-seealso"></a>

+  [VpnTunnelOptionsSpecification](http://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_VpnTunnelOptionsSpecification.html) in the *Amazon EC2 API Reference*