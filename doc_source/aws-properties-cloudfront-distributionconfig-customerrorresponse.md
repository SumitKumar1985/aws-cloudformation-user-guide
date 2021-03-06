# CloudFront DistributionConfig CustomErrorResponse<a name="aws-properties-cloudfront-distributionconfig-customerrorresponse"></a>

`CustomErrorResponse` is a property of the [CloudFront DistributionConfig](aws-properties-cloudfront-distributionconfig.md) resource that defines custom error messages for certain HTTP status codes\.

## Syntax<a name="w3ab2c21c14d181b5"></a>

### JSON<a name="aws-properties-cloudfront-distributionconfig-customerrorresponse-syntax.json"></a>

```
{
  "[[ERROR] BAD/MISSING LINK TEXT](#cfn-cloudfront-distributionconfig-customerrorresponse-errorcachingminttl)" : Integer,
  "[[ERROR] BAD/MISSING LINK TEXT](#cfn-cloudfront-distributionconfig-customerrorresponse-errorcode)" : Integer,
  "[[ERROR] BAD/MISSING LINK TEXT](#cfn-cloudfront-distributionconfig-customerrorresponse-responsecode)" : Integer,
  "[[ERROR] BAD/MISSING LINK TEXT](#cfn-cloudfront-distributionconfig-customerrorresponse-responsepagepath)" : String
}
```

### YAML<a name="aws-properties-cloudfront-distributionconfig-customerrorresponse-syntax.yaml"></a>

```
[[ERROR] BAD/MISSING LINK TEXT](#cfn-cloudfront-distributionconfig-customerrorresponse-errorcachingminttl): Integer
[[ERROR] BAD/MISSING LINK TEXT](#cfn-cloudfront-distributionconfig-customerrorresponse-errorcode): Integer
[[ERROR] BAD/MISSING LINK TEXT](#cfn-cloudfront-distributionconfig-customerrorresponse-responsecode): Integer
[[ERROR] BAD/MISSING LINK TEXT](#cfn-cloudfront-distributionconfig-customerrorresponse-responsepagepath): String
```

## Properties<a name="w3ab2c21c14d181b7"></a>

**Note**  
For more information about the constraints and valid values of each property, see the [CustomErrorResponse](http://docs.aws.amazon.com/cloudfront/latest/APIReference/API_CustomErrorResponse.html) data type in the *Amazon CloudFront API Reference*\.

`ErrorCachingMinTTL`  
The minimum amount of time, in seconds, that Amazon CloudFront caches the HTTP status code that you specified in the `ErrorCode` property\. The default value is `300`\.  
*Required: *No  
*Type*: Integer

`ErrorCode`  
An HTTP status code for which you want to specify a custom error page\. You can specify `400`, `403`, `404`, `405`, `414`, `500`, `501`, `502`, `503`, or `504`\.  
*Required: *Yes  
*Type*: Integer

`ResponseCode`  
The HTTP status code that CloudFront returns to viewer along with the custom error page\. You can specify `200`, `400`, `403`, `404`, `405`, `414`, `500`, `501`, `502`, `503`, or `504`\.  
*Required: *Conditional\. Required if you specified the `ResponsePagePath` property\.  
*Type*: Integer

`ResponsePagePath`  
The path to the custom error page that CloudFront returns to a viewer when your origin returns the HTTP status code that you specified in the `ErrorCode` property\. For example, you can specify `/404-errors/403-forbidden.html`\.  
*Required: *Conditional\. Required if you specified the `ResponseCode` property\.  
*Type*: String