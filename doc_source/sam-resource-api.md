# AWS::Serverless::Api<a name="sam-resource-api"></a>

Creates a collection of Amazon API Gateway resources and methods that can be invoked through HTTPS endpoints\.

An [AWS::Serverless::Api](#sam-resource-api) resource need not be explicitly added to a AWS Serverless Application Definition template\. A resource of this type is implicitly created from the union of Api events defined on [AWS::Serverless::Function](sam-resource-function.md) resources defined in the template that do not refer to an [AWS::Serverless::Api](#sam-resource-api) resource\.

An [AWS::Serverless::Api](#sam-resource-api) resource should be used to define and document the API using OpenApi, which provides more ability to configure the underlying Amazon API Gateway resources\.

We recommend that you use AWS CloudFormation hooks or IAM policies to verify that API Gateway resources have authorizers attached to them to control access to them\.

For more information about using AWS CloudFormation hooks, see [Registering hooks](https://docs.aws.amazon.com/cloudformation-cli/latest/userguide/registering-hook-python.html) in the *AWS CloudFormation CLI user guide* and the [apigw\-enforce\-authorizer](https://github.com/aws-cloudformation/aws-cloudformation-samples/tree/main/hooks/python-hooks/apigw-enforce-authorizer/) GitHub repository\.

For more information about using IAM policies, see [Require that API routes have authorization](https://docs.aws.amazon.com/apigateway/latest/developerguide/security_iam_id-based-policy-examples.html#security_iam_id-based-policy-examples-require-authorization) in the *API Gateway Developer Guide*\.

**Note**  
When you deploy to AWS CloudFormation, AWS SAM transforms your AWS SAM resources into AWS CloudFormation resources\. For more information, see [Generated AWS CloudFormation resources](sam-specification-generated-resources.md)\.

## Syntax<a name="sam-resource-api-syntax"></a>

To declare this entity in your AWS Serverless Application Model \(AWS SAM\) template, use the following syntax\.

### YAML<a name="sam-resource-api-syntax.yaml"></a>

```
Type: AWS::Serverless::Api
Properties:
  [AccessLogSetting](#sam-api-accesslogsetting): [AccessLogSetting](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-stage.html#cfn-apigateway-stage-accesslogsetting)
  AlwaysDeploy: Boolean
  [ApiKeySourceType](#sam-api-apikeysourcetype): String
  [Auth](#sam-api-auth): ApiAuth
  [BinaryMediaTypes](#sam-api-binarymediatypes): List
  [CacheClusterEnabled](#sam-api-cacheclusterenabled): Boolean
  [CacheClusterSize](#sam-api-cacheclustersize): String
  [CanarySetting](#sam-api-canarysetting): [CanarySetting](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-stage.html#cfn-apigateway-stage-canarysetting)
  [Cors](#sam-api-cors): String | CorsConfiguration
  [DefinitionBody](#sam-api-definitionbody): JSON
  [DefinitionUri](#sam-api-definitionuri): String | ApiDefinition
  [Description](#sam-api-description): String
  [DisableExecuteApiEndpoint](#sam-api-disableexecuteapiendpoint): Boolean
  [Domain](#sam-api-domain): DomainConfiguration
  [EndpointConfiguration](#sam-api-endpointconfiguration): EndpointConfiguration
  [FailOnWarnings](#sam-api-failonwarnings): Boolean
  [GatewayResponses](#sam-api-gatewayresponses): Map
  MergeDefinitions: Boolean
  [MethodSettings](#sam-api-methodsettings): MethodSettings
  [MinimumCompressionSize](#sam-api-minimumcompressionsize): Integer
  [Mode](#sam-api-mode): String
  [Models](#sam-api-models): Map
  [Name](#sam-api-name): String
  [OpenApiVersion](#sam-api-openapiversion): String
  [StageName](#sam-api-stagename): String
  [Tags](#sam-api-tags): Map
  [TracingEnabled](#sam-api-tracingenabled): Boolean
  [Variables](#sam-api-variables): Map
```

## Properties<a name="sam-resource-api-properties"></a>

 `AccessLogSetting`   <a name="sam-api-accesslogsetting"></a>
Configures Access Log Setting for a stage\.  
*Type*: [AccessLogSetting](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-stage.html#cfn-apigateway-stage-accesslogsetting)  
*Required*: No  
*AWS CloudFormation compatibility*: This property is passed directly to the `[AccessLogSetting](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-stage.html#cfn-apigateway-stage-accesslogsetting)` property of an `AWS::ApiGateway::Stage` resource\.

 `AlwaysDeploy`   <a name="sam-api-alwaysdeploy"></a>
Always deploys the API, even when no changes to the API have been detected\.  
*Type*: Boolean  
*Required*: No  
*AWS CloudFormation compatibility*: This property is unique to AWS SAM and doesn't have an AWS CloudFormation equivalent\.

 `ApiKeySourceType`   <a name="sam-api-apikeysourcetype"></a>
The source of the API key for metering requests according to a usage plan\. Valid values are `HEADER` and `AUTHORIZER`\.  
*Type*: String  
*Required*: No  
*AWS CloudFormation compatibility*: This property is passed directly to the `[ApiKeySourceType](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-restapi.html#cfn-apigateway-restapi-apikeysourcetype)` property of an `AWS::ApiGateway::RestApi` resource\.

 `Auth`   <a name="sam-api-auth"></a>
Configure authorization to control access to your API Gateway API\.  
For more information about configuring access using AWS SAM see [Controlling access to API Gateway APIs](serverless-controlling-access-to-apis.md)\.  
*Type*: [ApiAuth](sam-property-api-apiauth.md)  
*Required*: No  
*AWS CloudFormation compatibility*: This property is unique to AWS SAM and doesn't have an AWS CloudFormation equivalent\.

 `BinaryMediaTypes`   <a name="sam-api-binarymediatypes"></a>
List of MIME types that your API could return\. Use this to enable binary support for APIs\. Use \~1 instead of / in the mime types\.  
*Type*: List  
*Required*: No  
*AWS CloudFormation compatibility*: This property is similar to the `[BinaryMediaTypes](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-restapi.html#cfn-apigateway-restapi-binarymediatypes)` property of an `AWS::ApiGateway::RestApi` resource\. The list of BinaryMediaTypes is added to both the AWS CloudFormation resource and the OpenAPI document\.

 `CacheClusterEnabled`   <a name="sam-api-cacheclusterenabled"></a>
Indicates whether caching is enabled for the stage\. To cache responses, you must also set `CachingEnabled` to `true` under `MethodSettings`\.  
*Type*: Boolean  
*Required*: No  
*AWS CloudFormation compatibility*: This property is passed directly to the `[CacheClusterEnabled](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-stage.html#cfn-apigateway-stage-cacheclusterenabled)` property of an `AWS::ApiGateway::Stage` resource\.

 `CacheClusterSize`   <a name="sam-api-cacheclustersize"></a>
The stage's cache cluster size\.  
*Type*: String  
*Required*: No  
*AWS CloudFormation compatibility*: This property is passed directly to the `[CacheClusterSize](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-stage.html#cfn-apigateway-stage-cacheclustersize)` property of an `AWS::ApiGateway::Stage` resource\.

 `CanarySetting`   <a name="sam-api-canarysetting"></a>
Configure a canary setting to a stage of a regular deployment\.  
*Type*: [CanarySetting](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-stage.html#cfn-apigateway-stage-canarysetting)  
*Required*: No  
*AWS CloudFormation compatibility*: This property is passed directly to the `[CanarySetting](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-stage.html#cfn-apigateway-stage-canarysetting)` property of an `AWS::ApiGateway::Stage` resource\.

 `Cors`   <a name="sam-api-cors"></a>
Manage Cross\-origin resource sharing \(CORS\) for all your API Gateway APIs\. Specify the domain to allow as a string or specify a dictionary with additional Cors configuration\. NOTE: CORS requires AWS SAM to modify your OpenAPI definition\. So, it works only if inline OpenApi is defined with DefinitionBody\.  
For more information about CORS, see [Enable CORS for an API Gateway REST API Resource](https://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-cors.html) in the *API Gateway Developer Guide*\.  
*Type*: String \| [CorsConfiguration](sam-property-api-corsconfiguration.md)  
*Required*: No  
*AWS CloudFormation compatibility*: This property is unique to AWS SAM and doesn't have an AWS CloudFormation equivalent\.

 `DefinitionBody`   <a name="sam-api-definitionbody"></a>
OpenAPI specification that describes your API\. If neither `DefinitionUri` nor `DefinitionBody` are specified, SAM will generate a `DefinitionBody` for you based on your template configuration\.  
*Type*: JSON  
*Required*: No  
*AWS CloudFormation compatibility*: This property is similar to the `[Body](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-restapi.html#cfn-apigateway-restapi-body)` property of an `AWS::ApiGateway::RestApi` resource\. If certain properties are provided, content may be inserted or modified into the DefinitionBody before being passed to CloudFormation\. Properties include `Auth`, `BinaryMediaTypes`, `Cors`, `GatewayResponses`, `Models`, and an `EventSource` of type Api for a corresponding `AWS::Serverless::Function`\.

 `DefinitionUri`   <a name="sam-api-definitionuri"></a>
Amazon S3 Uri, local file path, or location object of the the OpenAPI document defining the API\. The Amazon S3 object this property references must be a valid OpenAPI file\. If neither `DefinitionUri` nor `DefinitionBody` are specified, SAM will generate a `DefinitionBody` for you based on your template configuration\.  
If a local file path is provided, the template must go through the workflow that includes the `sam deploy` or `sam package` command, in order for the definition to be transformed properly\.  
Intrinsic functions are not supported in external OpenApi files referenced by `DefinitionUri`\. Use instead the `DefinitionBody` property with the [Include Transform](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/create-reusable-transform-function-snippets-and-add-to-your-template-with-aws-include-transform.html) to import an OpenApi definition into the template\.  
*Type*: String \| [ApiDefinition](sam-property-api-apidefinition.md)  
*Required*: No  
*AWS CloudFormation compatibility*: This property is similar to the `[BodyS3Location](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-restapi.html#cfn-apigateway-restapi-bodys3location)` property of an `AWS::ApiGateway::RestApi` resource\. The nested Amazon S3 properties are named differently\.

 `Description`   <a name="sam-api-description"></a>
A description of the Api resource\.  
*Type*: String  
*Required*: No  
*AWS CloudFormation compatibility*: This property is passed directly to the `[Description](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-restapi.html#cfn-apigateway-restapi-description)` property of an `AWS::ApiGateway::RestApi` resource\.

 `DisableExecuteApiEndpoint`   <a name="sam-api-disableexecuteapiendpoint"></a>
Specifies whether clients can invoke your API by using the default `execute-api` endpoint\. By default, clients can invoke your API with the default `https://{api_id}.execute-api.{region}.amazonaws.com`\. To require that clients use a custom domain name to invoke your API, specify `True`\.  
*Type*: Boolean  
*Required*: No  
*AWS CloudFormation compatibility*: This property is similar to the `[DisableExecuteApiEndpoint](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-restapi.html#cfn-apigateway-restapi-disableexecuteapiendpoint)` property of an `AWS::ApiGateway::RestApi` resource\. It is passed directly to the [https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-swagger-extensions-endpoint-configuration.html](https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-swagger-extensions-endpoint-configuration.html) property of an `x-amazon-apigateway-endpoint-configuration` extension, which gets added to the `[Body](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-restapi.html#cfn-apigateway-restapi-body)` property of an `AWS::ApiGateway::RestApi` resource\. 

 `Domain`   <a name="sam-api-domain"></a>
Configures a custom domain for this API Gateway API\.  
*Type*: [DomainConfiguration](sam-property-api-domainconfiguration.md)  
*Required*: No  
*AWS CloudFormation compatibility*: This property is unique to AWS SAM and doesn't have an AWS CloudFormation equivalent\.

 `EndpointConfiguration`   <a name="sam-api-endpointconfiguration"></a>
The endpoint type of a REST API\.  
*Type*: [EndpointConfiguration](sam-property-api-endpointconfiguration.md)  
*Required*: No  
*AWS CloudFormation compatibility*: This property is similar to the `[EndpointConfiguration](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-restapi.html#cfn-apigateway-restapi-endpointconfiguration)` property of an `AWS::ApiGateway::RestApi` resource\. The nested configuration properties are named differently\.

 `FailOnWarnings`   <a name="sam-api-failonwarnings"></a>
Specifies whether to roll back the API creation \(`true`\) or not \(`false`\) when a warning is encountered\. The default value is `false`\.  
*Type*: Boolean  
*Required*: No  
*AWS CloudFormation compatibility*: This property is passed directly to the `[FailOnWarnings](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-restapi.html#cfn-apigateway-restapi-failonwarnings)` property of an `AWS::ApiGateway::RestApi` resource\.

 `GatewayResponses`   <a name="sam-api-gatewayresponses"></a>
Configures Gateway Responses for an API\. Gateway Responses are responses returned by API Gateway, either directly or through the use of Lambda Authorizers\. For more information, see the documentation for the [Api Gateway OpenApi extension for Gateway Responses](https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-swagger-extensions-gateway-responses.html)\.  
*Type*: Map  
*Required*: No  
*AWS CloudFormation compatibility*: This property is unique to AWS SAM and doesn't have an AWS CloudFormation equivalent\.

 `MergeDefinitions`   <a name="sam-api-mergedefinitions"></a>
AWS SAM generates an OpenAPI specification from your API event source\. Specify `true` to have AWS SAM merge this into the inline OpenAPI specification defined in your `AWS::Serverless::Api` resource\. Specify `false` to not merge\.  
`MergeDefinitions` requires the `DefinitionBody` property for `AWS::Serverless::Api` to be defined\. `MergeDefinitions` is not compatible with the `DefinitionUri` property for `AWS::Serverless::Api`\.  
*Default value*: `false`  
*Type*: Boolean  
*Required*: No  
*AWS CloudFormation compatibility*: This property is unique to AWS SAM and doesn't have an AWS CloudFormation equivalent\.

 `MethodSettings`   <a name="sam-api-methodsettings"></a>
Configures all settings for API stage including Logging, Metrics, CacheTTL, Throttling\.  
*Type*: List of [ MethodSetting](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-apigateway-stage-methodsetting.html)  
*Required*: No  
*AWS CloudFormation compatibility*: This property is passed directly to the `[MethodSettings](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-stage.html#cfn-apigateway-stage-methodsettings)` property of an `AWS::ApiGateway::Stage` resource\.

 `MinimumCompressionSize`   <a name="sam-api-minimumcompressionsize"></a>
Allow compression of response bodies based on client's Accept\-Encoding header\. Compression is triggered when response body size is greater than or equal to your configured threshold\. The maximum body size threshold is 10 MB \(10,485,760 Bytes\)\. \- The following compression types are supported: gzip, deflate, and identity\.  
*Type*: Integer  
*Required*: No  
*AWS CloudFormation compatibility*: This property is passed directly to the `[MinimumCompressionSize](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-restapi.html#cfn-apigateway-restapi-minimumcompressionsize)` property of an `AWS::ApiGateway::RestApi` resource\.

 `Mode`   <a name="sam-api-mode"></a>
This property applies only when you use OpenAPI to define your REST API\. The `Mode` determines how API Gateway handles resource updates\. For more information, see [Mode](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-restapi.html#cfn-apigateway-restapi-mode) property of the [https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-restapi.html](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-restapi.html) resource type\.  
*Valid values*: `overwrite` or `merge`  
*Type*: String  
*Required*: No  
*AWS CloudFormation compatibility*: This property is passed directly to the `[Mode](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-restapi.html#cfn-apigateway-restapi-mode)` property of an `AWS::ApiGateway::RestApi` resource\.

 `Models`   <a name="sam-api-models"></a>
The schemas to be used by your API methods\. These schemas can be described using JSON or YAML\. See the Examples section at the bottom of this page for example models\.  
*Type*: Map  
*Required*: No  
*AWS CloudFormation compatibility*: This property is unique to AWS SAM and doesn't have an AWS CloudFormation equivalent\.

 `Name`   <a name="sam-api-name"></a>
A name for the API Gateway RestApi resource  
*Type*: String  
*Required*: No  
*AWS CloudFormation compatibility*: This property is passed directly to the `[Name](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-restapi.html#cfn-apigateway-restapi-name)` property of an `AWS::ApiGateway::RestApi` resource\.

 `OpenApiVersion`   <a name="sam-api-openapiversion"></a>
Version of OpenApi to use\. This can either be `2.0` for the Swagger specification, or one of the OpenApi 3\.0 versions, like `3.0.1`\. For more information about OpenAPI, see the [OpenAPI Specification](https://swagger.io/specification/)\.  
 AWS SAM creates a stage called `Stage` by default\. Setting this property to any valid value will prevent the creation of the stage `Stage`\. 
*Type*: String  
*Required*: No  
*AWS CloudFormation compatibility*: This property is unique to AWS SAM and doesn't have an AWS CloudFormation equivalent\.

 `StageName`   <a name="sam-api-stagename"></a>
The name of the stage, which API Gateway uses as the first path segment in the invoke Uniform Resource Identifier \(URI\)\.  
To reference the stage resource, use `<api-logical-id>.Stage`\. For more information about referencing resources generated when an [AWS::Serverless::Api](#sam-resource-api) resource is specified, see [AWS CloudFormation resources generated when AWS::Serverless::Api is specified](sam-specification-generated-resources-api.md)\. For general information about generated AWS CloudFormation resources, see [Generated AWS CloudFormation resources](sam-specification-generated-resources.md)\.  
*Type*: String  
*Required*: Yes  
*AWS CloudFormation compatibility*: This property is similar to the `[StageName](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-stage.html#cfn-apigateway-stage-stagename)` property of an `AWS::ApiGateway::Stage` resource\. It is required in SAM, but not required in API Gateway  
*Additional notes*: The Implicit API has a stage name of "Prod"\.

 `Tags`   <a name="sam-api-tags"></a>
A map \(string to string\) that specifies the tags to be added to this API Gateway stage\. For details about valid keys and values for tags, see [Resource tag](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-resource-tags.html) in the *AWS CloudFormation User Guide*\.  
*Type*: Map  
*Required*: No  
*AWS CloudFormation compatibility*: This property is similar to the `[Tags](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-stage.html#cfn-apigateway-stage-tags)` property of an `AWS::ApiGateway::Stage` resource\. The Tags property in SAM consists of Key:Value pairs; in CloudFormation it consists of a list of Tag objects\.

 `TracingEnabled`   <a name="sam-api-tracingenabled"></a>
Indicates whether active tracing with X\-Ray is enabled for the stage\. For more information about X\-Ray, see [Tracing user requests to REST APIs using X\-Ray](https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-xray.html) in the *API Gateway Developer Guide*\.  
*Type*: Boolean  
*Required*: No  
*AWS CloudFormation compatibility*: This property is passed directly to the `[TracingEnabled](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-stage.html#cfn-apigateway-stage-tracingenabled)` property of an `AWS::ApiGateway::Stage` resource\.

 `Variables`   <a name="sam-api-variables"></a>
A map \(string to string\) that defines the stage variables, where the variable name is the key and the variable value is the value\. Variable names are limited to alphanumeric characters\. Values must match the following regular expression: `[A-Za-z0-9._~:/?#&=,-]+`\.  
*Type*: Map  
*Required*: No  
*AWS CloudFormation compatibility*: This property is passed directly to the `[Variables](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-stage.html#cfn-apigateway-stage-variables)` property of an `AWS::ApiGateway::Stage` resource\.

## Return Values<a name="sam-resource-api-return-values"></a>

### Ref<a name="sam-resource-api-return-values-ref"></a>

When the logical ID of this resource is provided to the `Ref` intrinsic function, it returns the ID of the underlying API Gateway API\.

For more information about using the `Ref` function, see [https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-ref.html](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-ref.html) in the *AWS CloudFormation User Guide*\. 

### Fn::GetAtt<a name="sam-resource-api-return-values-fn--getatt"></a>

`Fn::GetAtt` returns a value for a specified attribute of this type\. The following are the available attributes and sample return values\. 

For more information about using `Fn::GetAtt`, see [https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-getatt.html](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-getatt.html) in the *AWS CloudFormation User Guide*\. 

`RootResourceId`  <a name="RootResourceId-fn::getatt"></a>
The root resource ID for a `RestApi` resource, such as `a0bc123d4e`\.

## Examples<a name="sam-resource-api--examples"></a>

### SimpleApiExample<a name="sam-resource-api--examples--simpleapiexample"></a>

A Hello World AWS SAM template file that contains a Lambda Function with an API endpoint\. This is a full AWS SAM template file for a working serverless application\.

#### YAML<a name="sam-resource-api--examples--simpleapiexample--yaml"></a>

```
AWSTemplateFormatVersion: '2010-09-09'
Transform: AWS::Serverless-2016-10-31
Description: AWS SAM template with a simple API definition
Resources:
  ApiGatewayApi:
    Type: AWS::Serverless::Api
    Properties:
      StageName: prod
  ApiFunction: # Adds a GET api endpoint at "/" to the ApiGatewayApi via an Api event
    Type: AWS::Serverless::Function
    Properties:
      Events:
        ApiEvent:
          Type: Api
          Properties:
            Path: /
            Method: get
            RestApiId:
              Ref: ApiGatewayApi
      Runtime: python3.7
      Handler: index.handler
      InlineCode: |
        def handler(event, context):
            return {'body': 'Hello World!', 'statusCode': 200}
```

### ApiCorsExample<a name="sam-resource-api--examples--apicorsexample"></a>

An AWS SAM template snippet with an API defined in an external Swagger file along with Lambda integrations and CORS configurations\. This is just a portion of an AWS SAM template file showing an [AWS::Serverless::Api](#sam-resource-api) definition\.

#### YAML<a name="sam-resource-api--examples--apicorsexample--yaml"></a>

```
Resources:
  ApiGatewayApi:
    Type: AWS::Serverless::Api
    Properties:
      StageName: Prod
      # Allows www.example.com to call these APIs
      # SAM will automatically add AllowMethods with a list of methods for this API
      Cors: "'www.example.com'"
      DefinitionBody: # Pull in an OpenApi definition from S3
        'Fn::Transform':
          Name: 'AWS::Include'
          # Replace "bucket" with your bucket name
          Parameters:
            Location: s3://bucket/swagger.yaml
```

### ApiCognitoAuthExample<a name="sam-resource-api--examples--apicognitoauthexample"></a>

An AWS SAM template snippet with an API that uses Amazon Cognito to authorize requests against the API\. This is just a portion of an AWS SAM template file showing an [AWS::Serverless::Api](#sam-resource-api) definition\.

#### YAML<a name="sam-resource-api--examples--apicognitoauthexample--yaml"></a>

```
Resources:
  ApiGatewayApi:
    Type: AWS::Serverless::Api
    Properties:
      StageName: Prod
      Cors: "'*'"
      Auth:
        DefaultAuthorizer: MyCognitoAuthorizer
        Authorizers:
          MyCognitoAuthorizer:
            UserPoolArn:
              Fn::GetAtt: [MyCognitoUserPool, Arn]
```

### ApiModelsExample<a name="sam-resource-api--examples--apimodelsexample"></a>

An AWS SAM template snippet with an API that includes a Models schema\. This is just a portion of an AWS SAM template file, showing an [AWS::Serverless::Api](#sam-resource-api) definition with two model schemas\.

#### YAML<a name="sam-resource-api--examples--apimodelsexample--yaml"></a>

```
Resources:
  ApiGatewayApi:
    Type: AWS::Serverless::Api
    Properties:
      StageName: Prod
      Models:
        User:
          type: object
          required:
            - username
            - employee_id
          properties:
            username:
              type: string
            employee_id:
              type: integer
            department:
              type: string
        Item:
          type: object
          properties:
            count:
              type: integer
            category:
              type: string
            price:
              type: integer
```

### Caching example<a name="sam-resource-api--examples--caching-example"></a>

A Hello World AWS SAM template file that contains a Lambda Function with an API endpoint\. The API has caching enabled for one resource and method\. For more information about caching, see [Enabling API caching to enhance responsiveness](https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-caching.html) in the *API Gateway Developer Guide*\.

#### YAML<a name="sam-resource-api--examples--caching-example--yaml"></a>

```
AWSTemplateFormatVersion: '2010-09-09'
Transform: AWS::Serverless-2016-10-31
Description: AWS SAM template with a simple API definition
Resources:
  ApiGatewayApi:
    Type: AWS::Serverless::Api
    Properties:
      StageName: prod
      CacheClusterEnabled: true
      CacheClusterSize: '0.5'
      MethodSettings:
        - ResourcePath: /
          HttpMethod: GET
          CachingEnabled: true
          CacheTtlInSeconds: 300

  ApiFunction: # Adds a GET api endpoint at "/" to the ApiGatewayApi via an Api event
    Type: AWS::Serverless::Function
    Properties:
      Events:
        ApiEvent:
          Type: Api
          Properties:
            Path: /
            Method: get
            RestApiId:
              Ref: ApiGatewayApi
      Runtime: python3.7
      Handler: index.handler
      InlineCode: |
        def handler(event, context):
            return {'body': 'Hello World!', 'statusCode': 200}
```