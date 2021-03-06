# CreateStreamProcessor<a name="API_CreateStreamProcessor"></a>

Creates an Amazon Rekognition stream processor that you can use to detect and recognize faces in a streaming video\.

Rekognition Video is a consumer of live video from Amazon Kinesis Video Streams\. Rekognition Video sends analysis results to Amazon Kinesis Data Streams\.

You provide as input a Kinesis video stream \(`Input`\) and a Kinesis data stream \(`Output`\) stream\. You also specify the face recognition criteria in `Settings`\. For example, the collection containing faces that you want to recognize\. Use `Name` to assign an identifier for the stream processor\. You use `Name` to manage the stream processor\. For example, you can start processing the source video by calling [StartStreamProcessor](API_StartStreamProcessor.md) with the `Name` field\. 

After you have finished analyzing a streaming video, use [StopStreamProcessor](API_StopStreamProcessor.md) to stop processing\. You can delete the stream processor by calling [DeleteStreamProcessor](API_DeleteStreamProcessor.md)\.

## Request Syntax<a name="API_CreateStreamProcessor_RequestSyntax"></a>

```
{
   "Input": { 
      "KinesisVideoStream": { 
         "Arn": "string"
      }
   },
   "Name": "string",
   "Output": { 
      "KinesisDataStream": { 
         "Arn": "string"
      }
   },
   "RoleArn": "string",
   "Settings": { 
      "FaceSearch": { 
         "CollectionId": "string",
         "FaceMatchThreshold": number
      }
   }
}
```

## Request Parameters<a name="API_CreateStreamProcessor_RequestParameters"></a>

The request accepts the following data in JSON format\.

 ** Input **   
Kinesis video stream stream that provides the source streaming video\. If you are using the AWS CLI, the parameter name is `StreamProcessorInput`\.  
Type: [StreamProcessorInput](API_StreamProcessorInput.md) object  
Required: Yes

 ** Name **   
An identifier you assign to the stream processor\. You can use `Name` to manage the stream processor\. For example, you can get the current status of the stream processor by calling [DescribeStreamProcessor](API_DescribeStreamProcessor.md)\. `Name` is idempotent\.   
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 128\.  
Pattern: `[a-zA-Z0-9_.\-]+`   
Required: Yes

 ** Output **   
Kinesis data stream stream to which Rekognition Video puts the analysis results\. If you are using the AWS CLI, the parameter name is `StreamProcessorOutput`\.  
Type: [StreamProcessorOutput](API_StreamProcessorOutput.md) object  
Required: Yes

 ** RoleArn **   
ARN of the IAM role that allows access to the stream processor\.  
Type: String  
Pattern: `arn:aws:iam::\d{12}:role/?[a-zA-Z_0-9+=,.@\-_/]+`   
Required: Yes

 ** Settings **   
Face recognition input parameters to be used by the stream processor\. Includes the collection to use for face recognition and the face attributes to detect\.  
Type: [StreamProcessorSettings](API_StreamProcessorSettings.md) object  
Required: Yes

## Response Syntax<a name="API_CreateStreamProcessor_ResponseSyntax"></a>

```
{
   "StreamProcessorArn": "string"
}
```

## Response Elements<a name="API_CreateStreamProcessor_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** StreamProcessorArn **   
ARN for the newly create stream processor\.  
Type: String  
Pattern: `(^arn:[a-z\d-]+:rekognition:[a-z\d-]+:\d{12}:streamprocessor\/.+$)` 

## Errors<a name="API_CreateStreamProcessor_Errors"></a>

 **AccessDeniedException**   
You are not authorized to perform the action\.  
HTTP Status Code: 400

 **InternalServerError**   
Amazon Rekognition experienced a service issue\. Try your call again\.  
HTTP Status Code: 500

 **InvalidParameterException**   
Input parameter violated a constraint\. Validate your parameter before calling the API operation again\.  
HTTP Status Code: 400

 **LimitExceededException**   
  
HTTP Status Code: 400

 **ProvisionedThroughputExceededException**   
The number of requests exceeded your throughput limit\. If you want to increase this limit, contact Amazon Rekognition\.  
HTTP Status Code: 400

 **ResourceInUseException**   
  
HTTP Status Code: 400

 **ThrottlingException**   
Amazon Rekognition is temporarily unable to process the request\. Try your call again\.  
HTTP Status Code: 500

## See Also<a name="API_CreateStreamProcessor_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:

+  [AWS Command Line Interface](http://docs.aws.amazon.com/goto/aws-cli/rekognition-2016-06-27/CreateStreamProcessor) 

+  [AWS SDK for \.NET](http://docs.aws.amazon.com/goto/DotNetSDKV3/rekognition-2016-06-27/CreateStreamProcessor) 

+  [AWS SDK for C\+\+](http://docs.aws.amazon.com/goto/SdkForCpp/rekognition-2016-06-27/CreateStreamProcessor) 

+  [AWS SDK for Go](http://docs.aws.amazon.com/goto/SdkForGoV1/rekognition-2016-06-27/CreateStreamProcessor) 

+  [AWS SDK for Java](http://docs.aws.amazon.com/goto/SdkForJava/rekognition-2016-06-27/CreateStreamProcessor) 

+  [AWS SDK for JavaScript](http://docs.aws.amazon.com/goto/AWSJavaScriptSDK/rekognition-2016-06-27/CreateStreamProcessor) 

+  [AWS SDK for PHP V3](http://docs.aws.amazon.com/goto/SdkForPHPV3/rekognition-2016-06-27/CreateStreamProcessor) 

+  [AWS SDK for Python](http://docs.aws.amazon.com/goto/boto3/rekognition-2016-06-27/CreateStreamProcessor) 

+  [AWS SDK for Ruby V2](http://docs.aws.amazon.com/goto/SdkForRubyV2/rekognition-2016-06-27/CreateStreamProcessor) 