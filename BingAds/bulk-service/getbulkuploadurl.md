﻿---
title: GetBulkUploadUrl Service Operation
ms.service: bing-ads-bulk-service
ms.topic: article
author: eric-urban
ms.author: eur
description: Submits a request for a URL where a bulk upload file may be posted.
---
# GetBulkUploadUrl Service Operation
Submits a request for a URL where a bulk upload file may be posted.

## <a name="request"></a>Request Elements
The *GetBulkUploadUrlRequest* object defines the [body](#request-body) and [header](#request-header) elements of the service operation request. The elements must be in the same order as shown in the [Request SOAP](#request-soap). 

### <a name="request-body"></a>Request Body Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="responsemode"></a>ResponseMode|Specify whether to return errors and their corresponding data, or only the errors in the results file. The default is *ErrorsOnly*.|[ResponseMode](responsemode.md)|
|<a name="accountid"></a>AccountId|The account identifier corresponding to the data that will be uploaded.|**long**|

### <a name="request-header"></a>Request Header Elements
[!INCLUDE[request-header](./includes/request-header.md)]

## <a name="response"></a>Response Elements
The *GetBulkUploadUrlResponse* object defines the [body](#response-body) and [header](#response-header) elements of the service operation response. The elements are returned in the same order as shown in the [Response SOAP](#response-soap).

### <a name="response-body"></a>Response Body Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="requestid"></a>RequestId|The identifier of the upload request.<br /><br />The identifier is valid for a maximum of two days. If you have not successfully uploaded the file within this period, you will need to get a new request identifier and upload URL. .|**string**|
|<a name="uploadurl"></a>UploadUrl|The URL where you may submit your bulk upload file with  HTTP POST.<br /><br />The upload URL is valid for a maximum of two days. If you have not successfully uploaded the file within this period, you will need to get a new request identifier and upload URL.|**string**|

### <a name="response-header"></a>Response Header Elements
[!INCLUDE[response-header](./includes/response-header.md)]

## <a name="request-soap"></a>Request SOAP
The following template shows the order of the [body](#request-body) and [header](#request-header) elements for the SOAP request.

```xml
<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
    <Action mustUnderstand="1">GetBulkUploadUrl</Action>
    <ApplicationToken i:nil="false">ValueHere</ApplicationToken>
    <AuthenticationToken i:nil="false">ValueHere</AuthenticationToken>
    <CustomerAccountId i:nil="false">ValueHere</CustomerAccountId>
    <CustomerId i:nil="false">ValueHere</CustomerId>
    <DeveloperToken i:nil="false">ValueHere</DeveloperToken>
    <Password i:nil="false">ValueHere</Password>
    <UserName i:nil="false">ValueHere</UserName>
  </s:Header>
  <s:Body>
    <GetBulkUploadUrlRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <ResponseMode>ValueHere</ResponseMode>
      <AccountId>ValueHere</AccountId>
    </GetBulkUploadUrlRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response-soap"></a>Response SOAP
The following template shows the order of the [body](#response-body) and [header](#response-header) elements for the SOAP response.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
    <TrackingId d3p1:nil="false" xmlns:d3p1="http://www.w3.org/2001/XMLSchema-instance">ValueHere</TrackingId>
  </s:Header>
  <s:Body>
    <GetBulkUploadUrlResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <RequestId d4p1:nil="false" xmlns:d4p1="http://www.w3.org/2001/XMLSchema-instance">ValueHere</RequestId>
      <UploadUrl d4p1:nil="false" xmlns:d4p1="http://www.w3.org/2001/XMLSchema-instance">ValueHere</UploadUrl>
    </GetBulkUploadUrlResponse>
  </s:Body>
</s:Envelope>
```

## <a name="example"></a>Code Syntax
The example syntax can be used with [Bing Ads SDKs](~/guides/client-libraries.md). See [Bing Ads Code Examples](~/guides/code-examples.md) for more examples.
```csharp
public async Task<GetBulkUploadUrlResponse> GetBulkUploadUrlAsync(
	ResponseMode responseMode,
	long accountId)
{
	var request = new GetBulkUploadUrlRequest
	{
		ResponseMode = responseMode,
		AccountId = accountId
	};

	return (await Bulk.CallAsync((s, r) => s.GetBulkUploadUrlAsync(r), request));
}
```
```java
static GetBulkUploadUrlResponse getBulkUploadUrl(
	ResponseMode responseMode,
	java.lang.Long accountId) throws RemoteException, Exception
{
	GetBulkUploadUrlRequest request = new GetBulkUploadUrlRequest();

	request.setResponseMode(responseMode);
	request.setAccountId(accountId);

	return Bulk.getService().getBulkUploadUrl(request);
}
```
```php
static function GetBulkUploadUrl(
	$responseMode,
	$accountId)

	$getBulkUploadUrlRequest = new GetBulkUploadUrlRequest();

	$request->ResponseMode = $responseMode;
	$request->AccountId = $accountId;

	return $BulkProxy->GetService()->GetBulkUploadUrl($request);
}
```
```python
response=bulk.GetBulkUploadUrl(
	ResponseMode=ResponseModeHere,
	AccountId=AccountIdHere
)
```

## Requirements
Service: [BulkService.svc v11](https://bulk.api.bingads.microsoft.com/Api/Advertiser/CampaignManagement/v11/BulkService.svc)  
Namespace: https://bingads.microsoft.com/CampaignManagement/v11  
