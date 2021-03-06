# Route 53 HealthCheckConfig<a name="aws-properties-route53-healthcheck-healthcheckconfig"></a>

The `HealthCheckConfig` property is part of the [AWS::Route53::HealthCheck](aws-resource-route53-healthcheck.md) resource that describes a health check that Amazon Route 53 uses before responding to a DNS query\.

## Syntax<a name="w3ab2c21c14e1445b5"></a>

### JSON<a name="aws-properties-route53-healthcheck-healthcheckconfig-syntax.json"></a>

```
{
  "[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-alarmidentifier)" : AlarmIdentifier,
  "[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-childhealthchecks)" : [ String, ... ],
  "[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-enablesni)" : Boolean,
  "[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-failurethreshold)" : Integer,
  "[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-fullyqualifieddomainname)" : String,
  "[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-healththreshold)" : Integer,
  "[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-insufficientdatahealthstatus)" : String,
  "[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-inverted)" : Boolean,
  "[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-ipaddress)" : String,
  "[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-measurelatency)" : Boolean,
  "[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-port)" : Integer,
  "[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-requestinterval)" : Integer,
  "[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-resourcepath)" : String,
  "[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-searchstring)" : String,
  "[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-type)" : String
}
```

### YAML<a name="aws-properties-route53-healthcheck-healthcheckconfig-syntax.yaml"></a>

```
[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-alarmidentifier):  AlarmIdentifier
[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-childhealthchecks): 
   - String
[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-enablesni): Boolean
[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-failurethreshold): Integer
[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-fullyqualifieddomainname): String
[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-healththreshold): Integer
[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-insufficientdatahealthstatus): String
[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-inverted): Boolean
[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-ipaddress): String
[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-measurelatency): Boolean
[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-port): Integer
[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-requestinterval): Integer
[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-resourcepath): String
[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-searchstring): String
[[ERROR] BAD/MISSING LINK TEXT](#cfn-route53-healthcheck-healthcheckconfig-type): String
```

## Properties<a name="w3ab2c21c14e1445b7"></a>

`AlarmIdentifier`  
Identifies the CloudWatch alarm that you want Route 53 health checkers to use to determine whether this health check is healthy\.  
*Type*: [Amazon Route 53 AlarmIdentifier](aws-properties-route53-healthcheck-healthcheckconfig-alarmidentifier.md)  
*Required: *No

`ChildHealthChecks`  
\(CALCULATED Health Checks Only\) A complex type that contains one `ChildHealthCheck` element for each health check that you want to associate with a `CALCULATED` health check\.  
*Required: *No  
*Type*: List of String values

`EnableSNI`  
Specifies whether you want Route 53 to send the value of `FullyQualifiedDomainName` to the endpoint in the `client_hello` message during TLS negotiation\. This allows the endpoint to respond to `HTTPS` health check requests with the applicable SSL/TLS certificate\. For more information, see [http://docs.aws.amazon.com/Route53/latest/APIReference/API_HealthCheckConfig.html](http://docs.aws.amazon.com/Route53/latest/APIReference/API_HealthCheckConfig.html)\.  
*Required: *No  
*Type*: Boolean

`FailureThreshold`  
The number of consecutive health checks that an endpoint must pass or fail for Route 53 to change the current status of the endpoint from unhealthy to healthy or healthy to unhealthy\. For more information, see [How Amazon Route 53 Determines Whether an Endpoint Is Healthy](http://docs.aws.amazon.com/Route53/latest/DeveloperGuide/dns-failover-determining-health-of-endpoints.html) in the *Amazon Route 53 Developer Guide*\.   
*Required: *No  
*Type*: Integer

`FullyQualifiedDomainName`  
If you specified the `IPAddress` property, the value that you want Route 53 to pass in the host header in all health checks except for TCP health checks\. If you don't specify an IP address, the domain that Route 53 sends a DNS request to\. Route 53 uses the IP address that the DNS returns to check the health of the endpoint\.  
*Required: *Conditional  
*Type*: String

`HealthThreshold`  
The number of child health checks that are associated with a `CALCULATED` health that Route 53 must consider healthy for the `CALCULATED` health check to be considered healthy\.  
*Required: *No  
*Type*: Integer

`InsufficientDataHealthStatus`  
When Amazon CloudWatch has insufficient data about the metric to determine the alarm state, the status that you want Route 53 to assign to the health check \(`Healthy`, `Unhealthy`, or `LastKnownStatus`\)\.  
*Required: *No  
*Type*: String

`Inverted`  
Specifies whether you want Route 53 to invert the status of a health check, for example, to consider a health check unhealthy when it otherwise would be considered healthy\.  
*Required: *No  
*Type*: Boolean

`IPAddress`  
The IPv4 IP address of the endpoint on which you want Route 53 to perform health checks\. If you don't specify an IP address, Route 53 sends a DNS request to resolve the domain name that you specify in the `FullyQualifiedDomainName` property\.  
*Required: *No  
*Type*: String

`MeasureLatency`  
Specifies whether you want Route 53 to measure the latency between health checkers in multiple AWS regions and your endpoint and display CloudWatch latency graphs on the **Health Checks** page in the Route 53 console\.  
*Required: *No  
*Type*: Boolean  
*Update requires*: Replacement

`Port`  
The port on the endpoint on which you want Route 53 to perform health checks\.  
*Required: *Conditional\. Required when you specify `TCP` for the `Type` property\.   
*Type*: Integer

`RequestInterval`  
The number of seconds between the time that Route 53 gets a response from your endpoint and the time that it sends the next health check request\. Each Route 53 health checker makes requests at this interval\. For valid values, see the [RequestInterval element](http://docs.aws.amazon.com/Route53/latest/APIReference/API_GetHealthCheck.html) in the *Amazon Route 53 API Reference*\.  
*Required: *No  
*Type*: Integer  
*Update requires*: Replacement

`ResourcePath`  
The path that you want Route 53 to request when performing health checks\. The path can be any value for which your endpoint returns an HTTP status code of `2xx` or `3xx` when the endpoint is healthy, such as `/docs/route53-health-check.html`\.   
*Required: *No  
*Type*: String

`SearchString`  
If the value of the `Type` property is `HTTP_STR_MATCH` or `HTTPS_STR_MATCH`, the string that you want Route 53 to search for in the response body from the specified resource\. If the string appears in the response body, Route 53 considers the resource healthy\.  
*Required: *No  
*Type*: String

`Type`  
The type of health check that you want to create\. This indicates how Route 53 determines whether an endpoint is healthy\. You can specify `HTTP`, `HTTPS`, `HTTP_STR_MATCH`, `HTTPS_STR_MATCH`, or `TCP`\. For information about the different types, see the [http://docs.aws.amazon.com/Route53/latest/APIReference/API_CreateHealthCheck.html](http://docs.aws.amazon.com/Route53/latest/APIReference/API_CreateHealthCheck.html) element in the *Amazon Route 53 API Reference*\.  
*Required: *Yes  
*Type*: String  
*Update requires*: Replacement