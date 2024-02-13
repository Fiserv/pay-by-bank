# Extra Information from SDK. Not sure if needed. 
This was information from section 4.2
## Sample JSON Response for SDK
```json
{
"componentDelta": "responseDataEncryptedUsingAESKey" 
"componentFallBack": "{string}"
}
```

## Response Data Elements Specification for SDK

|Data Element|Description|Requires Encryption| Required?| Rules|Data Type| Minimum Length| Maximum Length|#Occur|
|------------|-----------|-------------------|----------|------|---------|---------------|---------------|------|
|componentDelta|Encrypted Response Payload|Y|O||||||
|componentFallBack|This would only be populated if decryption failed on ConnectPayAPI because SDK sent details which resulted in decryption exception. This would be clear error response payload which signifies decryption error.|N|O||||||

## Decrypted Component Delta JSON format for SDK
```json
{
"transactionStatus": "{string}", 
"transactionStatusCode": "{string}", 
"referenceTransactionID": "{string}", 
"transactionStatusDescription": "{string}", 
"responseVerbiage": "{string}",
"nonce": "{string}",
"errorDetails": [
{
"errorCode": "{string}",
"errorField": "{string}",
"errorReason": "{string}"
}
],
"account": [
{
"userDetails": {
"firstName": "{string}",
"lastName": "{string}",
"email": "{string}"
},
"userAddressDetails": {
"street": "{string}",
"street2": "{string}",
"state": "{string}",
"city": "{string}",
"postalCode": "{string}"
},
"userIdentificationDetails": { 
"routingNumber": "{string}", 
"accountNumber": "{string}", 
"onlineBankTransactionId": "{string}"
},
"userPhone": [
{
"number": "{string}"
}
]
}
],
" teleCheckDetails ": { 
"transactionId": "{string}", 
"tckResponseCode": "{string}", 
"approvalCode": "{string}", 
"denialRecordNumber": "{string}", 
"displayText": "{string}", 
"sequenceId": "{string}", 
"ecaOfferCode": "{string}", 
"achTransactionStatus": "{string}", 
"amount": "{string}",
"currency": "{string}", 
"responseMessageMisc": "{string}", 
"dateTime": "{string}", 
"returnCheckFee": "{string}", 
"returnCheckNote": "{string}",
"key": "{string}",
"accessId": "{string}",
"merchantId": "{string}", 
"description": "{string}", 
"merchantReference": "{string}", 
"paymentType": "{string}",
"returnUrl": "{string}",
"cancelUrl": "{string}", 
"requestSignature": "{string}", 
"onlineBankTransactionId": "{string}" },
"partner": {
"subscriberID": "{string}" },
"customer": {
"fdCustomerID": "{string}", 
"externalID": "{string}"
},
"security": {
"tokenID": "{string}", 
"issuedOn": "{timestamp}", 
"expiresInSeconds": "{number}", 
"publicKey": "{string}", 
"alogorithm": "{string}",
"status": "{string}"
}
}
```

## Create Session Token
>Note: This is a re-write from SDK guide. I do not think this is needed if we can just call the API. 
<p>
The Create Session Token API call is used to create a session token and to retrieve the public encryption key generated for this session. This information will be used to initialize the ConnectPay SDK for every use case. This API is secured as it requires the Authorization header that can only be derived using the API Secret stored in the Merchant’s web server. Below are the details of the API end point.
</p>

## Connectivity
|Attribute|Value|
|---------|-----|
|Cert  API Endpoint | https://cat.api.firstdata.com/gateway/v2/connectpay/security/createsessiontoken|
|Production  API Endpoint | https://prod.api.firstdata.com/gateway/v2/connectpay/security/createsessiontoken|

## Header Description
|Headers|Description|
|-------|-----------|
|Content-Type|application/json|
|Api-Key|Merchant’s ConnectPay FirstAPI key|
|Timestamp|Request initiation timestamp, expecting Epoch time. The value has to generate out of UTC timestamp and it is in milliseconds. Sample value format is 1499961987232|
|Authorization|HMAC for Authenticating Merchant with ConnectPay on FirstAPI, and Authorizing to process business functionality Value for this header should be the word HMAC, followed by a space, followed by values for computed HMAC. Example : HMAC G9FqRSvZGMuJbjgLovkdlYz9ppBGh0++/5d/BIwoUuE= |

### Request Body
<p>
This is the only request where payload is not encrypted, since this call is requesting the Public Encryption Key to encrypt subsequent calls.
</p>
<p>
Sample request body for CreateConsumerProfile, ConsumerEnrollment, AccountValidations, GetConsumerAccountDetails, GetConsumerAccountList, ACH Transaction calls:
</p>

```json
{
    "security": {
      "publicKeyRequired": "true" 
    }
}
```
Sample request body for MicroDepositValidation, ConsumerUpdates and ACH account closure:
```json
{
    "account": [
      {
        "fdAccountID": "CP1GWQ1571349549912484x2r1yf", 
        "type": "ACH"
      }
      ], 
      "security": {
        "publicKeyRequired": "true" 
    }
}
```
|Data Element|Description|Requires Encryption|Required?|Rules|Data Type|Minimum Length|Maximum Length|# Occur|
|------------|-----------|-------------------|---------|-----|---------|--------------|--------------|-------|
|fdAccountID|fdAccountID is required for MicroDepositValidation , ConsumerUpdates and ACH account closure calls|N|C||A,N|1|50|<=1|
|type|Defines the account type for this request.Should always be **ACH**. This element should be present if account section is present|N|C||A|3|3|1|
|publicKeyRequired|Specifies if a public key is required in response.Allowable values for this field are either **true** or **false**|N|Y||A|4|5|1|



### Response Body
<p>Create session token response would contain the response in unencrypted / clear / readable format.</p>
<p>RSA public key from the response of this call would be used to encrypt the AES key and IV for the subsequent calls.</p>
<p>Until the end of this call we would not have all the necessary pieces of information for doing a full payload encryption / decryption</p>
<p>Sample response body for CreateSessionToken call</p>

```json
{
"transactionStatus": "APPROVED",
"transactionStatusCode": 0,
"referenceTransactionID": "ee5870a4-b5a4-3cc8-89da-e67f30c6628c", "transactionStatusDescription": "OK",
"security": {
"tokenID": "0zdH0UyzmQN9m2zbYsFmm0MS4jgd", "issuedOn": "1571430030138",
"expiresInSeconds": "599",
"publicKey":
"MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAs+OzWu916RvgPWkqXN79onLlMlSwIp0P WylPshXhybp/127cvPNblbzq3dIOysGHZK8ZNVjYA5qETmE98wLqM/msBepdslnjj9Z6DNiDruQo4K6L6 EV7K8Nz258ZE6OgBoixy5ZQDFgIgzlpGfEmgQrfG0CiFe7oeC8BXRyWlZNJjvf0ya7Wn/UN5cM8qpf1lR0 ySJTWcxsQz1qSMRB5KEtQjz/Yyj9f9YyvvNCn/aCg45ydKcrGSCpfeLQtsCknviukcsudmBFbJtsTKUjPQ deuUCy4ToD2lKdwQmE+cZQG/FvAVM1MFvK65q6N5TaTx1a6RGfxP5WyKDcHQZDS3QIDAQAB",
"algorithm": "RSA/None/PKCS1Padding",
"status": "ACTIVE" }
}
```
<p>The Create Session Token API call is used to create a session token and to retrieve the RSA public key. This API is secured as it requires the Authorization header that can only be derived using the API Secret stored in the Merchant’s server. Below is more information on the API specification as well as example request and response payloads. </p>

Try it below to also see acceptable error and acceptance codes: 
[![](/assets/images/button.png '')](https://qa-developer.fiserv.com/product/ConnectPay/api/?type=post&path=/security/createsessiontoken&branch=develop&version=1.0.0)


!-- Already in the request section of guide
<p>
Headers|Description|
|---------|-----|
|Content-Type|application/json|
|Api-Key|Merchant’s ConnectPay FirstAPI key|
|Timestamp|Request initiation timestamp, expecting Epoch time. The value has to generate out of UTC timestamp and it is in milliseconds. Sample value format is 1499961987232|
|Authorization|HMAC for Authenticating Merchant with ConnectPay on FirstAPI, and Authorizing to process business functionality.
Value for this header should be the word HMAC, followed by a space, followed by values for computed HMAC. Example : HMAC G9FqRSvZGMuJbjgLovkdlYz9ppBGh0++/5d/BIwoUuE= |
|Client-Token |Session Token received from CreateSessionToken call. Value for this header should be Bearer, followed by a space, followed by values for tokened. Example: Bearer b361Nhsd97hsujuiUSuiua99iq9921kkjsuuahjsa | 
</p>
<br>

<p>Request Body: (Sample request body before payload encryption) </p>
<!-- Already in API Explorer>
```json
{
"customer": {
"externalID": "Merchant01Consumer65746635" }
}
```
<!-- Need to move this requirements information to API explorer. This table is not needed. 

|Data Element|Description|Requires Encryption|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|-----------|-------------------|---------------|---------|--------------|--------------|-------|
|externalID|This is the user’s unique identifier in the merchant system.|N|R||A,N|1|50|<=1|
-->


<p>Sample request body after payload encryption and before transmission</p>
<!-- added to examples>
```json
{
"componentX":
"L0WLCiqw0TT0tqaRH3Ksz4wdQFf2YAnIeiCScd+hrAWO2Hlv7lDsNnQpd+ORxkIjOHmwJuC58Q0tsc WnOI2Gh5DJ75wk5xnp/0RWQoB2+pTMGo6On+O+vFxkhVQRKlRgJu0G/RNZV4EFa1iBdDTY6UZL0I WtqDT1zwUiu+2NWAOdPDIbAIsekhJrhRAIFNsHeiYhUxBCsF+gxybJupB0XjGIWhAkPjO7AKPR1fXWU/ ZRifzsdu1/X43DSTz4d4/bYAD6iAaSBJUewSVwUG9OodeU84LYgdba4vRNa2G3BpzfomdvK6H1C8pj HjnVjUGP2F3IO6tMDnpAFZfrxvytlg==",
"componentY": "K5BTgBGzhIux2ZnodU4MWRUVhUFbU4P376TLTHZa02nU2jVb2pAWK3gMfpEHsE7WeoLlNrzAJwR 1FJ679z4Oo/yWp7k39zamQNlMHvm6EYBBbxIemexBHIIqqNRFdHhq6S3pA6L/9ItyscEl5/zZIKxcx44hv CCPZOZUhnOTSc4ehPnYJhdJQFgIDhY5UPRRZntM8hP2hOPZTVz5D4re17bSYVOEEK7bmpGIWpf9p ERUj4MlUpyRpafNd2mQsZpXPvW3XZfHDbslO7o3LourFHRSqAfBHOfx+pwH+YcMwglnay/Ay2SYWyZ hKkD+UcHSkyBdk/AMdcKt1K9uCIPm/Q==",
"componentDelta": "KKRKg/jPcb+r/3TZmhLP/KxrMEajXKvBYQd5jeGFm2OzznUvNHuyEhWyJc4RlXFRoLhwcj9eEuSOz0a bTAeU+Xw8hSMJ6kYhHokJ3ev8tgQ="
}
```
-->

<!-- Already in API explorer
<p>In either case, the decrypted/unencrypted version of this payload has three high level transactionStatus , namely, APPROVED/DECLINED/ERROR.</p>

**APPROVED** as the name suggests represents a successful outcome.
<br>

**DECLINED** status signifies that ConnectPayAPI rejected the request either due to format validation or business validation.
<br>

**ERROR** status signifies a system error or equivalent.
<br>
-->

### Request Body after payload encryption and before transmission
For a sample request body **AFTER** payload encryption and before transmission: 
```json
{
    "componentX": "ju5PPi7k4K2jtI0z47qKcHnQGRrIymN+dK+PVlWjKyufoaUHJqjqOAbjsQZ0q3sLciBkEVWm5jGbWQoGf2e9Us+yfYu8ua2hz3wOIRSymHdx8qKuoexQiKhLWnp/GAL0+TIdzb/CvNijuJkOe1XSzEoFdFjYgRNMV8LJM3G/izn48kZm9gexM/iJenJyzwFoqXJc7EcWrC3C0RlkBF5jTgZzTGCvBpxDq4pw3CjFDsGvFy5Gg26B1KRcRDctrFpLV697QAW//hWyS91NYB68S3TIo/B6/LfUjj9bOY3fM+i+5BY2oV7zbLLyvA+CKfLFRBoXtevfBJyndrUDFD0EBA==",
    "componentY": "CqTTfUbNR66rGRhAKGqnEYJBGona07l2lvV7s7sEG97b0eohkWCqcw/XhCSy2+A6rYxhhuvvQ+orjfmCzssIl4Uz+4gu3GE3lfMGeykjRuhipyV+fjnjOBcw/VDOg3IXffr4Oe/isRYTZ5gp0uht89Rpu9VXfWktKH5uEJiZdNyD9TY+xZ2Ekwc6trDjTSFPbxVNaITJGqMBFsuWXGcHvaqoo6bC7Q9r/pVsUHq5KDdoi0zuW+xBilMxk/hZE8fBifXkUZ+KGGibyHlseh/uH9U32UHgvyVSsiUjI1j44WNulRnvfN7Mi5HozJTiYbX2iGrL5QQLKkQIWQPWV37VgQ==",
    "componentDelta": "OEIyAAUL1Py3/oKewtNXswtkYOw+krJP0EFhucFWFXSug0TCV7kqL67Mk5PTzVqNWTAyPl0lK6ac2EBK3kxskC6WpzpJI4qSv7/9JSfQ7zAYUiKAKPobIXpHAJ7BuHSMlMkv/6UTJvdIRsgDaqfAbD5pqG5KDbRzXpzmLIpVJnGyPCkwwm+F36wGbe1ccuvzDHNL77e6XSmm2LpzO/NAGJRjMGXdLQ9XKFvjr/gK0ruO2gdqglomlvy3MG8BSvLCAYkOL1CAB4wF8ovsfpOAAV92KRdqxeMISntCc0/Fxg7fs9JILmn4ZkgiSgha1CsN"
}
```
Response Body may contain either componentDelta or componentFallBack elements.
<ol>
    <li>componentDelta: is encrypted ConnectPayAPI response</li>
    <li>componentFallBack : is unencrypted response and is only triggered in cases of ,Sessiontimeout(responsefromApigee) and Encryption decryptionlogicfailsonConnectPayAPI(inthiscaseencryption/decryption failed so not able to give back encrypted response).</li>
</ol>

### Make The Request
Using the correct endpoint, headers, and encrypted payload, we can then make the call. The ConnectPay backend will decrypt the payload and process the request. It will then return the response encrypted with the AES key and IV provided by componentX and componentY. An example of the output is shown below:
```json
{
"componentDelta": "cRD5xVaJab13iRQ7l6No6ot9YPTFT3bi/qapHYGgsNmxQ8nT2mtIz7uLLHz5kdp5JEmDjiP1dXMNPg8jP5rIZQf/5dtMfFLq7YL7FQY/boTsd7BoJg7reDeeAk6l9+76gaSAZMIRJGYS4fhy1bgClx2jIeWo4fLlfildeHnghCU1ElR8XhFi3oyd8hU+YEpDENP5IJJMVxjnYChuFX8paVy/SAYFMESBXSTIgPi6Y/kJc/bswlxaa9Yei4GnD+Ny1laVs4HqJp32JJ+NHJIYdZr5117AY0JJxJ9oudnkK6J8oPnnXhLCBGxNCRDJG3AVLRxDnQcds/cSiwAVREHr4nn848IEsUb27wJR7SiDxVaELxme9CNZ1dB0tPYQ1wux3ymWtnUgLfVRFsHH3EeucbHv8uIc8dxcwxZReROzVS8="
}
```



|Content-Type| application/json|
|Api-Key|Merchant’s ConnectPay FirstAPI key|
|Timestamp|Request initiation timestamp, expecting Epoch time. The value has to generate out of UTC timestamp and it is in milliseconds. Sample value format is 1499961987232|
|Authorization|HMAC for Authenticating Merchant with ConnectPay on FirstAPI, and Authorizing to process business functionality. Value for this header should be the word HMAC, followed by a space, followed by values for computed HMAC. Example : HMAC G9FqRSvZGMuJbjgLovkdlYz9ppBGh0++/5d/BIwoUuE=|
|Client-Token|Session Token received from CreateSessionToken call. Value for this header should be Bearer, followed by a space, followed by values for tokened. Example: Bearer b361Nhsd97hsujuiUSuiua99iq9921kkjsuuahjsa|
</p>
Request Body:
<br>
Sample request body before payload encryption:

```json
{
    "customer": {
        "fdCustomerID": "CP87rx15814147322210000442tJpajq",
        "externalID": " Merchant01Consumer65746635" 
    }
}
```
Data Element|Description|Requires Encryption|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|-----------|-------------------|---------------|---------|--------------|--------------|-------|
|fdCustomerID|Consumer’s fdCustomerID associated with this request.|N|O||A,N|1|50|<=1|
|externalID|This is the user’s unique identifier in the merchant system.|N|O||A,N|1|50|<=1|
>Anyone is required in request to retrieve the consumer profile
<br>
<p>Sample request body after payload encryption and before transmission:

```json
{
"componentX":
"L0WLCiqw0TT0tqaRH3Ksz4wdQFf2YAnIeiCScd+hrAWO2Hlv7lDsNnQpd+ORxkIjOHmwJuC58Q0tsc WnOI2Gh5DJ75wk5xnp/0RWQoB2+pTMGo6On+O+vFxkhVQRKlRgJu0G/RNZV4EFa1iBdDTY6UZL0I WtqDT1zwUiu+2NWAOdPDIbAIsekhJrhRAIFNsHeiYhUxBCsF+gxybJupB0XjGIWhAkPjO7AKPR1fXWU/ ZRifzsdu1/X43DSTz4d4/bYAD6iAaSBJUewSVwUG9OodeU84LYgdba4vRNa2G3BpzfomdvK6H1C8pj HjnVjUGP2F3IO6tMDnpAFZfrxvytlg==",
"componentY": "K5BTgBGzhIux2ZnodU4MWRUVhUFbU4P376TLTHZa02nU2jVb2pAWK3gMfpEHsE7WeoLlNrzAJwR 1FJ679z4Oo/yWp7k39zamQNlMHvm6EYBBbxIemexBHIIqqNRFdHhq6S3pA6L/9ItyscEl5/zZIKxcx44hv CCPZOZUhnOTSc4ehPnYJhdJQFgIDhY5UPRRZntM8hP2hOPZTVz5D4re17bSYVOEEK7bmpGIWpf9p ERUj4MlUpyRpafNd2mQsZpXPvW3XZfHDbslO7o3LourFHRSqAfBHOfx+pwH+YcMwglnay/Ay2SYWyZ hKkD+UcHSkyBdk/AMdcKt1K9uCIPm/Q==",
"componentDelta": "KKRKg/jPcb+r/3TZmhLP/KxrMEajXKvBYQd5jeGFm2OzznUvNHuyEhWyJc4RlXFRoLhwcj9eEuSOz0a bTAeU+Xw8hSMJ6kYhHokJ3ev8tgQ="
}
```
</p>
<br>
Data Element|Description|Requires Encryption|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|-----------|-------------------|---------------|---------|--------------|--------------|-------|
|componentX|Secret for AES encryption, encrypted using public key from create session|Y|R||A,N|32|32|<=1|
|componentY|IV for Data Encryption and Decryption|Y|R|A,N|16|16|<=1|
|componentDelta|Encrypted Payload|Y|R||A,N|1||<=1|
<p>
Response Body:
<br>
Response may contain either componentDelta or componentFallBack elements.
<br>
> - • componentDelta: is encrypted ConnectPayAPI response.
> - • componentFallBack : is unencrypted response and is only triggered in cases of
> - - o Session timeout(response from Apigee)
> - - o Encryption/decryption logic fails on ConnectPayAPI(in this case encryption/decryption failed so not able to give back encrypted response).
<br>
In either case, the decrypted/unencrypted version of this payload has three high level transactionStatus , namely, APPROVED/DECLINED/ERROR.
</p>
<p>
**APPROVED** as the name suggests represents a successful outcome.
**DECLINED** status signifies that ConnectPayAPI rejected the request either due to format validation or business validation.
**ERROR** status signifies a system error or equivalent.
</p>

Sample response body after it is received with payload encryption:

```json
{
"componentDelta":
"cRD5xVaJab13iRQ7l6No6ot9YPTFT3bi/qapHYGgsNmxQ8nT2mtIz7uLLHz5kdp5JEmDjiP1dXMNPg8j P5rIZQf/5dtMfFLq7YL7FQY/boTsd7BoJg7reDeeAk6l9+76gaSAZMIRJGYS4fhy1bgClx2jIeWo4fLlfildeH nghCU1ElR8XhFi3oyd8hU+YEpDENP5IJJMVxjnYChuFX8paVy/SAYFMESBXSTIgPi6Y/kJc/bswlxaa9Yei 4GnD+Ny1laVs4HqJp32JJ+NHJIYdZr5117AY0JJxJ9oudnkK6J8oPnnXhLCBGxNCRDJG3AVLRxDnQc ds/cSiwAVREHr4nn848IEsUb27wJR7SiDxVaELxme9CNZ1dB0tPYQ1wux3ymWtnUgLfVRFsHH3Eeuc bHv8uIc8dxcwxZReROzVS8="
}
```
<br>
Data Element|Description|Requires Encryption|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|-----------|-------------------|---------------|---------|--------------|--------------|-------|
|componentDelta|Encrypted Payload|Y|R||A,N|1||<=1|
<br>
JSON sample data for **APPROVED** response body after payload decryption
<br>

```json
{
"transactionStatus" : "APPROVED",
"transactionStatusCode" : 0,
"referenceTransactionID" : "b9034a46-5e84-b305-233d-f5424756a85f", 
"transactionStatusDescription" : "OK",
"customer" : {
"fdCustomerID": "CP87rx15814147322210000442tJpajq",
"externalID": " Merchant01Consumer65746635" }
}
```
<br>
JSON datatype definition for APPROVED response body after payload decryption
<br>

Data Element|Description|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|----------|---------|-----|---------|--------------|--------------|-------|
|transactionStatus|Overall status of the call|R|Allowable Values: APPROVED DECLINED ERROR||A|5|11|=1|
|transactionStatusCode|Unique code signifying detailed transaction status|R||N|1|3|=1|
|referenceTransactionID|Unique ID for each Transaction which could be used to trace a transaction.
**It is highly recommended that merchants should store the ID on their side. This can be used for researching the transactions in case issue arises**|O||A,N,s0,S1,S2|1|100|<=1|
|transactionStatusDescription|Short description of statusCode|O||A,S0,S1,S2|1|30|<=1|
|fdCustomerID|Consumer’s fdCustomerID associated with this request.|O||A,N|1|50|<=1|
|ExternalID|This is the user’s unique identifier in the merchant system.|O||A,N|1|50|<=1|
<br>
JSON sample data for **DECLINED** response body after payload decryption

```json
{
"transactionStatus": "DECLINED", 
"transactionStatusCode": 450, 
"referenceTransactionID": " Partner Not Found ", 
"transactionStatusDescription": "Conflict",
"responseVerbiage": "",
"errorDetails": [
  {
   "errorCode": 4500,
   "errorField": " PartnerID ", 
   "errorReason": "" Partner Not Found "
  } 
 ]
}
```
<br>
JSON datatype definition for DECLINED response body after payload decryption
<br>

Data Element|Description|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|----------|---------|-----|---------|--------------|--------------|-------|
|transactionStatus|Overall status of the call|R|Allowable Values: APPROVED DECLINED ERROR||A|5|11|=1|
|transactionStatusCode|Unique code signifying detailed transaction status|R||N|1|3|=1|
|referenceTransactionID|Unique ID for each Transaction which could be used to trace a transaction.
**It is highly recommended that merchants should store the ID on their side. This can be used for researching the transactions in case issue arises**|O||A,N,s0,S1,S2|1|100|<=1|
|transactionStatusDescription|Short description of statusCode|O||A,S0,S1,S2|1|30|<=1|
|responseVerbiage|Detailed description of transactionStatus|O||A,N,S0,S1,S2|1|1000|<=1|
|errorCode|Code signifying what kind of error occurred|O||N|1|4|<=1|
|errorField|Signifies which input field that caused the error|O||A|1|30|<=1|
|errorReason|Short description of the error|O||A,S1|1|100|<=1|
<br>

JSON sample data for ERROR response body after payload decryption
```json
{
"transactionStatus" : "ERROR",
"transactionStatusCode" : 100,
"referenceTransactionID" : "1a3f6b65-9104-00eb-a2a9-ae7daf952a31", 
"transactionStatusDescription" : "Input is invalid ",
"errorDetails" : [ {
 "errorCode" : 1010,
 "errorField" : "externalID/fdCustomerID", 
 "errorReason" : "Field did not have a valid format"
}] 
}
```
<br>
JSON datatype definition for ERROR response body after payload decryption
<br>

Data Element|Description|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|----------|---------|-----|---------|--------------|--------------|-------|
|transactionStatus|Overall status of the call|R|Allowable Values: APPROVED DECLINED ERROR||A|5|11|=1|
|transactionStatusCode|Unique code signifying detailed transaction status|R||N|1|3|=1|
|referenceTransactionID|Unique ID for each Transaction which could be used to trace a transaction.
**It is highly recommended that merchants should store the ID on their side. This can be used for researching the transactions in case issue arises**|O||A,N,s0,S1,S2|1|100|<=1|
|transactionStatusDescription|Short description of statusCode|O||A,S0,S1,S2|1|30|<=1|
|responseVerbiage|Detailed description of transactionStatus|O||A,N,S0,S1,S2|1|1000|<=1|
|errorCode|Code signifying what kind of error occurred|O||N|1|4|<=1|
|errorField|Signifies which input field that caused the error|O||A|1|30|<=1|
|errorReason|Short description of the error|O||A,S1|1|100|<=1|

<br>
JSON sample data without payload encryption (componentFallBack)
<br>

```json
{
"componentFallBack": "{\r\n \"transactionStatus\" : \"DECLINED\",\r\n \"transactionStatusCode\ " : 420,\r\n \"referenceTransactionID\" : \"APIGEE-a-90f-4946-ff14-
36aa4b9a6325\",\r\n \"transactionStatusDescription\" : \"Unauthorized\",\r\n \"responseVerbia ge\" : \"Unauthorized\",\r\n \"errorDetails\" : [ {\r\n \"errorCode\" : 4250,\r\n \"errorField\" :
\"Client-Token\",\r\n \"errorReason\" : \"Session time out\"\r\n } ]\r\n}" }
```
<br>
Datatype definition without payload encryption (componentFallBack)
<br>

Data Element|Description|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|----------|---------|-----|---------|--------------|--------------|-------|
|transactionStatus|Overall status of the call|R|Allowable Values: APPROVED DECLINED ERROR||A|5|11|=1|
|transactionStatusCode|Unique code signifying detailed transaction status|R||N|1|3|=1|
|referenceTransactionID|Unique ID for each Transaction which could be used to trace a transaction.
**It is highly recommended that merchants should store the ID on their side. This can be used for researching the transactions in case issue arises**|O||A,N,s0,S1,S2|1|100|<=1|
|transactionStatusDescription|Short description of statusCode|O||A,S0,S1,S2|1|30|<=1|
|responseVerbiage|Detailed description of transactionStatus|O||A,N,S0,S1,S2|1|1000|<=1|
|errorCode|Code signifying what kind of error occurred|O||N|1|4|<=1|
|errorField|Signifies which input field that caused the error|O||A|1|30|<=1|
|errorReason|Short description of the error|O||A,S1|1|100|<=1|

<br>





> Please Note: Merchants who will be using Fiserv's Connected Commerce (uCom) gateway should use "Create Customer Profile API" from their Implementation Guide
> 
[uCom Implementation Guide](https://developer.fiserv.com/product/ConnectedCommerce/api/?type=post&path=/v1/customers&branch=main&version=1.0.0)

|Attribute|Value|
|---------|-----|
|Certification End Point|https://cat.api.firstdata.com/gateway/v2/connectpay/consumerprofile/deenroll|
|Production API End Point|https://prod.api.firstdata.com/gateway/v2/connectpay/consumerprofile/deenroll|
|HTTP Method|POST|
</p>
<p>
|Headers|Description|
|-------|-----------|
|Content-Type| application/json|
|Api-Key|Merchant’s ConnectPay FirstAPI key|
|Timestamp|Request initiation timestamp, expecting Epoch time. The value has to generate out of UTC timestamp and it is in milliseconds. Sample value format is 1499961987232|
|Authorization|HMAC for Authenticating Merchant with ConnectPay on FirstAPI, and Authorizing to process business functionality. Value for this header should be the word HMAC, followed by a space, followed by values for computed HMAC. Example : HMAC G9FqRSvZGMuJbjgLovkdlYz9ppBGh0++/5d/BIwoUuE=|
|Client-Token|Session Token received from CreateSessionToken call. Value for this header should be Bearer, followed by a space, followed by values for tokened. Example: Bearer b361Nhsd97hsujuiUSuiua99iq9921kkjsuuahjsa|
</p>
<br>
Request Body:

```json
{
 "customer" : {
  "fdCustomerID" : "cddae0a7285b45ebbd34b42c01eb752f" 
  }
}
```
<br>
Data Element|Description|Requires Encryption|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|-----------|-------------------|---------------|---------|--------------|--------------|-------|
|fdCustomerID|Consumer’s fdCustomerID associated with this request.|N|R||A,N|1|50|<=1|

<br>
Sample request body after payload encryption and before transmission:

```json
{
"componentX": "L0WLCiqw0TT0tqaRH3Ksz4wdQFf2YAnIeiCScd+hrAWO2Hlv7lDsNnQpd+ORxkIjOHmwJuC58Q0tsc WnOI2Gh5DJ75wk5xnp/0RWQoB2+pTMGo6On+O+vFxkhVQRKlRgJu0G/RNZV4EFa1iBdDTY6UZL0I WtqDT1zwUiu+2NWAOdPDIbAIsekhJrhRAIFNsHeiYhUxBCsF+gxybJupB0XjGIWhAkPjO7AKPR1fXWU/ ZRifzsdu1/X43DSTz4d4/bYAD6iAaSBJUewSVwUG9OodeU84LYgdba4vRNa2G3BpzfomdvK6H1C8pj HjnVjUGP2F3IO6tMDnpAFZfrxvytlg==",
"componentY": "K5BTgBGzhIux2ZnodU4MWRUVhUFbU4P376TLTHZa02nU2jVb2pAWK3gMfpEHsE7WeoLlNrzAJwR 1FJ679z4Oo/yWp7k39zamQNlMHvm6EYBBbxIemexBHIIqqNRFdHhq6S3pA6L/9ItyscEl5/zZIKxcx44hv CCPZOZUhnOTSc4ehPnYJhdJQFgIDhY5UPRRZntM8hP2hOPZTVz5D4re17bSYVOEEK7bmpGIWpf9p ERUj4MlUpyRpafNd2mQsZpXPvW3XZfHDbslO7o3LourFHRSqAfBHOfx+pwH+YcMwglnay/Ay2SYWyZ hKkD+UcHSkyBdk/AMdcKt1K9uCIPm/Q==",
"componentDelta": "KKRKg/jPcb+r/3TZmhLP/KxrMEajXKvBYQd5jeGFm2OzznUvNHuyEhWyJc4RlXFRoLhwcj9eEuSOz0a bTAeU+Xw8hSMJ6kYhHokJ3ev8tgQ="
}
```
<br>
Data Element|Description|Requires Encryption|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|-----------|-------------------|---------------|---------|--------------|--------------|-------|
|componentX|Secret for AES encryption, encrypted using public key from create session|Y|R||A,N|32|32|<=1|
|componentY|IV for Data Encryption and Decryption|Y|R|A,N|16|16|<=1|
|componentDelta|Encrypted Payload|Y|R||A,N|1||<=1|
<br>
<p>
Response Body:
<br>
Response may contain either componentDelta or componentFallBack elements.
<br>
> - • componentDelta: is encrypted ConnectPayAPI response.
> - • componentFallBack : unencrypted response and is only triggered in cases of
> - - o Session timeout(response from Apigee)
> - - o Encryption/decryption logic fails on ConnectPayAPI(in this case encryption/decryption failed so not able to give back encrypted response).
<br>
In either case, the decrypted/unencrypted version of this payload has three high level transactionStatus , namely, APPROVED/DECLINED/ERROR.
</p>
<p>
**APPROVED** as the name suggests represents a successful outcome.
**DECLINED** status signifies that ConnectPayAPI rejected the request either due to format validation or business validation.
**ERROR** status signifies a system error or equivalent.
</p>

Sample response body after it is received with payload encryption:

```json
{
"componentDelta":
"cRD5xVaJab13iRQ7l6No6ot9YPTFT3bi/qapHYGgsNmxQ8nT2mtIz7uLLHz5kdp5JEmDjiP1dXMNPg8j P5rIZQf/5dtMfFLq7YL7FQY/boTsd7BoJg7reDeeAk6l9+76gaSAZMIRJGYS4fhy1bgClx2jIeWo4fLlfildeH nghCU1ElR8XhFi3oyd8hU+YEpDENP5IJJMVxjnYChuFX8paVy/SAYFMESBXSTIgPi6Y/kJc/bswlxaa9Yei 4GnD+Ny1laVs4HqJp32JJ+NHJIYdZr5117AY0JJxJ9oudnkK6J8oPnnXhLCBGxNCRDJG3AVLRxDnQc ds/cSiwAVREHr4nn848IEsUb27wJR7SiDxVaELxme9CNZ1dB0tPYQ1wux3ymWtnUgLfVRFsHH3Eeuc bHv8uIc8dxcwxZReROzVS8="
}
```
<br>
Data Element|Description|Requires Encryption|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|-----------|-------------------|---------------|---------|--------------|--------------|-------|
|componentDelta|Encrypted Payload|Y|R||A,N|1||<=1|
<br>
JSON sample data for **APPROVED** response body after payload decryption
<br>

```json
{
  "transactionStatus": "APPROVED",
  "transactionStatusCode": 0,
  "referenceTransactionID": "5cdd1d99-5367-ed98-56fd-3f52ab008ac8", 
  "transactionStatusDescription": "Created"
}
```
<br>
JSON datatype definition for APPROVED response body after payload decryption
<br>

Data Element|Description|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|----------|---------|-----|---------|--------------|--------------|-------|
|transactionStatus|Overall status of the call|R|Allowable Values: APPROVED DECLINED ERROR||A|5|11|=1|
|transactionStatusCode|Unique code signifying detailed transaction status|R||N|1|3|=1|
|referenceTransactionID|Unique ID for each Transaction which could be used to trace a transaction.
**It is highly recommended that merchants should store the ID on their side. This can be used for researching the transactions in case issue arises**|O||A,N,s0,S1,S2|1|100|<=1|
|transactionStatusDescription|Short description of statusCode|O||A,N,S0,S1,S2|1|30|<=1|

<br>
JSON sample data for **DECLINED** response body after payload decryption

```json
{
"transactionStatus": "DECLINED", 
"transactionStatusCode": 450, 
"referenceTransactionID": " Partner Not Found ", 
"transactionStatusDescription": "Conflict",
"responseVerbiage": "",
"errorDetails": [
  {
   "errorCode": 4500,
   "errorField": " PartnerID ", 
   "errorReason": "" Partner Not Found "
  } 
 ]
}
```
<br>
JSON datatype definition for DECLINED response body after payload decryption
<br>

Data Element|Description|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|----------|---------|-----|---------|--------------|--------------|-------|
|transactionStatus|Overall status of the call|R|Allowable Values: APPROVED DECLINED ERROR||A|5|11|=1|
|transactionStatusCode|Unique code signifying detailed transaction status|R||N|1|3|=1|
|referenceTransactionID|Unique ID for each Transaction which could be used to trace a transaction.
**It is highly recommended that merchants should store the ID on their side. This can be used for researching the transactions in case issue arises**|O||A,N,s0,S1,S2|1|100|<=1|
|transactionStatusDescription|Short description of statusCode|O||A,S0,S1,S2|1|30|<=1|
|responseVerbiage|Detailed description of transactionStatus|O||A,N,S0,S1,S2|1|1000|<=1|
|errorCode|Code signifying what kind of error occurred|O||N|1|4|<=1|
|errorField|Signifies which input field that caused the error|O||A|1|30|<=1|
|errorReason|Short description of the error|O||A,S1|1|100|<=1|

<br>

```json
{
  "transactionStatus": "ERROR",
  "transactionStatusCode": 140,
  "referenceTransactionID": "593c1364-2ea6-4edc-842c-319fd2880c3a", 
  "transactionStatusDescription": "Customer profile not found", 
  "responseVerbiage": "Customer profile not found",
  "errorDetails": [
    {
     "errorCode": 2220,
     "errorField": "fdCustomerID", 
     "errorReason": "Customer profile not found"
    } 
  ]
}
```
<br>
JSON datatype definition for ERROR response body after payload decryption
<br>

Data Element|Description|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|----------|---------|-----|---------|--------------|--------------|-------|
|transactionStatus|Overall status of the call|R|Allowable Values: APPROVED DECLINED ERROR||A|5|11|=1|
|transactionStatusCode|Unique code signifying detailed transaction status|R||N|1|3|=1|
|referenceTransactionID|Unique ID for each Transaction which could be used to trace a transaction.
**It is highly recommended that merchants should store the ID on their side. This can be used for researching the transactions in case issue arises**|O||A,N,S0,S1,S2|1|100|<=1|
|transactionStatusDescription|Short description of statusCode|O||A,S0,S1,S2|1|30|<=1|
|responseVerbiage|Detailed description of transactionStatus|O||A,N,S0,S1,S2|1|1000|<=1|
|errorCode|Code signifying what kind of error occurred|O||N|1|4|<=1|
|errorField|Signifies which input field that caused the error|O||A|1|30|<=1|
|errorReason|Short description of the error|O||A,S1|1|100|<=1|

<br>
JSON sample data without payload encryption (componentFallBack)

```json
{
"componentFallBack": "{\r\n \"transactionStatus\" : \"DECLINED\",\r\n \"transactionStatusCode\ " : 420,\r\n \"referenceTransactionID\" : \"APIGEE-a-90f-4946-ff14-
36aa4b9a6325\",\r\n \"transactionStatusDescription\" : \"Unauthorized\",\r\n \"responseVerbia ge\" : \"Unauthorized\",\r\n \"errorDetails\" : [ {\r\n \"errorCode\" : 4250,\r\n \"errorField\" :
\"Client-Token\",\r\n \"errorReason\" : \"Session time out\"\r\n } ]\r\n}" }
```

<br>
Datatype definition without payload encryption (componentFallBack)
Data Element|Description|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|----------|---------|-----|---------|--------------|--------------|-------|
|transactionStatus|Overall status of the call|R|Allowable Values: APPROVED DECLINED ERROR||A|5|11|=1|
|transactionStatusCode|Unique code signifying detailed transaction status|R||N|1|3|=1|
|referenceTransactionID|Unique ID for each Transaction which could be used to trace a transaction.
**It is highly recommended that merchants should store the ID on their side. This can be used for researching the transactions in case issue arises**|O||A,N,S0,S1,S2|1|100|<=1|
|transactionStatusDescription|Short description of statusCode|O||A,S0,S1,S2|1|30|<=1|
|responseVerbiage|Detailed description of transactionStatus|O||A,N,S0,S1,S2|1|1000|<=1|
|errorCode|Code signifying what kind of error occurred|O||N|1|4|<=1|
|errorField|Signifies which input field that caused the error|O||A|1|30|<=1|
|errorReason|Short description of the error|O||A|1|100|<=1|
<br>

Response Code List [Response Codes](https://github.com/Fiserv/connect-pay/blob/develop/documentation/statuscodes.md)
<br>

[![](/assets/images/button.png '')](https://qa-developer.fiserv.com/product/ConnectPay/api/?type=post&path=/consumerprofile/enrollment&branch=develop&version=1.0.0)

<p>
|Headers|Description|
|-------|-----------|
|Content-Type| application/json|
|Api-Key|Merchant’s ConnectPay FirstAPI key|
|Timestamp|Request initiation timestamp, expecting Epoch time. The value has to generate out of UTC timestamp and it is in milliseconds. Sample value format is 1499961987232|
|Authorization|HMAC for Authenticating Merchant with ConnectPay on FirstAPI, and Authorizing to process business functionality. Value for this header should be the word HMAC, followed by a space, followed by values for computed HMAC. Example : HMAC G9FqRSvZGMuJbjgLovkdlYz9ppBGh0++/5d/BIwoUuE=|
|Client-Token|Session Token received from CreateSessionToken call. Value for this header should be Bearer, followed by a space, followed by values for tokened. Example: Bearer b361Nhsd97hsujuiUSuiua99iq9921kkjsuuahjsa|
</p>
<br>

br>
Data Element|Description|Requires Encryption|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|-----------|-------------------|---------------|---------|--------------|--------------|-------|
|componentDelta|Encrypted Payload|Y|R||A,N|1||<=1|
|componentX|Secret for AES encryption|Y|R||A,N|32|32|<=1|
|componentY|IV for Data Encryption and Decryption|Y|R|A,N|16|16|<=1|
<br>

#### Get Data Response Specification (Need subtitle)
<p>
Sample response body received with payload encryption:

```json 
{
"componentDelta":
"n689JQiDumqRxIMP5HPDNW7BArz3BhvZU5DpA1j14MzZI8KM4JjQh9ahBeJG3SVJAF428zQj7TjaVFrSkBVV Quhz6p0WD+vze4Skm9EOV6j3P1X7CCPEG9a43AInKrczxpVWzBfqyRhV3yutGVDAbOGWEuqYe8+VIqEvi2gY TeQg6J/Z/Whgcd1Xz0l8JffNsWkv4qFVny1ehHi9zBOQMo27HY/ipaHMbGjqHkd3Cf+HlJ47HjcZh597h7740yjkD olLGHx4DW8hdZh5vEqZu9zBJy+rXXRhMxLcGD0IidUT6FHQWpNV7KQKYHDFNIX42dVrXqGI7hZzZB4AfiHb+/ pxFTONeM0+cKA/u2DbAFNjsPlPwLtD77yVfsCT2X6IpnXtKc8TgdtyxujooQH7npK2IpsSUAHfxwuioYy/QoL2rgP UkLZmO0Pi7pkPb8Zo4ll+5tXpUfxj9KrCXjHeQBGhUg7VVidrjmcR7Cz3XMS+2m96Vbo8GAWxNhKrO+OAMH6k 1RxnMcgUg4s5AOcne2IwoLz/b71oNJGi8SVdLhVmaWsBrL2MrKq1YXR/pLyW"
}
```
<br>
Data Element|Description|Requires Encryption|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|-----------|-------------------|---------------|---------|--------------|--------------|-------|
|componentDelta|Encrypted GetData response|N|R||A,N|1||<=1|
<br>
Sample response body after payload is decrypted:

```json
{
   "transactionStatus": "APPROVED",
   "transactionStatusCode": 0,
   "referenceTransactionID": "2cad9e56-0837-fd3b-ca8b-cdeb38529814", 
   "transactionStatusDescription": "OK",
   "customer": {
      "fdCustomerID": "0bf52d6bac534a96a9c300d143f0689a" 
    },
    "account": [ 
        {
           "fdAccountID": "8a7f42087ee46e0c017ee7e92a6d013e", 
           "type": "ACH",
           "accountStatus": "70",
           "accountStatusDesc": "PENDING_VALIDATIONS", 
           "accountValidationDetails": [
             {
                "validationCode": "10",
                "validationCodeDesc": "Bank Validation Status", 
                "validationCodeStatus": "PENDING"
             },
             { 
                "validationCode": "50", 
                "validationCodeDesc": "Pin Update Status", 
                "validationCodeStatus": "COMPLETE"
            }, 
            {
                "validationCode": "70",
                "validationCodeDesc": "Email Validation Status", 
                "validationCodeStatus": "COMPLETE"
            }, 
            {
                "validationCode": "80",
                "validationCodeDesc": "Phone Validation Status", 
                "validationCodeStatus": "COMPLETE"
            } 
        ],
        "userDetails": {
            "firstName": "Joe",
            "lastName": "Smith",
            "email": "Joe.Smith@fiserv.com", 
            "gender": "M",
            "dob": "19871115", 
            "memberSince": "20150226",
            "agreedTncVersion": "v1"
        }, 
        "userAddressDetails": {
            "street": "112 Freeway", 
            "street2": "APT 999", 
            "state": "TX",
            "city": "Houston", 
            "country": "840", 
            "postalCode": "77478"
        }, 
        "userIdentificationDetails": {
            "ssn": "986525482",
            "routingNumber": "311080311",
            "accountNumber": "8262192877",
            "bankName": "SUN CU",
            "connectPayPaymentNumber": "4341120000000019108", 
            "corporateAccountFlag": "personal_check", 
            "driverLicenseNumber": "86090280",
            "driverLicenseState": "TX"
        }, 
        "userPhone": [
            {
                "type": "MOBILE", 
                "number": "8652547895", 
                "primary": "Y"
            }, 
            {
                "type": "HOME", 
                "number": "8652547895", 
                "primary": "N"  
            }, 
            {
                "type": "BUSINESS", 
                "number": "8652545789", 
                "primary": "N"
            },
            {
                "type": "OTHERS", 
                "number": "6525434789", 
                "primary": "N"
            } 
        ],
        "sqnA": [ 
            {
                "securityQuestionId": "1",
                "securityQuestion": "ABC" 
            },
            {
                "securityQuestionId": "2", 
                "securityQuestion": "GHI"
            }, 
                        {
                "securityQuestionId": "3", 
                "securityQuestion": "GHI"
            }, 
            {
                "securityQuestionId": "4", 
                "securityQuestion": "GHI"
            },
                        {
                "securityQuestionId": "5", 
                "securityQuestion": "GHI"
            } 
        ], 
        "reportingFields": {
            "reportingField1": "123", 
            "reportingField2": "1234", 
            "reportingField3": "12345"
        }, 
        "genericCodes": {
            "genericCode1": "1", 
            "genericCode2": "2", 
            "genericCode3": "3"
        }, 
        "genericFlags": {
            "genericFlag1": "Y", 
            "genericFlag2": "Y", 
            "genericFlag3": "Y"
        } 
    }
  ] 
}




Sample request body after payload encryption and before transmission:

```json
{
"componentX": "L0WLCiqw0TT0tqaRH3Ksz4wdQFf2YAnIeiCScd+hrAWO2Hlv7lDsNnQpd+ORxkIjOHmwJuC58Q0tsc WnOI2Gh5DJ75wk5xnp/0RWQoB2+pTMGo6On+O+vFxkhVQRKlRgJu0G/RNZV4EFa1iBdDTY6UZL0I WtqDT1zwUiu+2NWAOdPDIbAIsekhJrhRAIFNsHeiYhUxBCsF+gxybJupB0XjGIWhAkPjO7AKPR1fXWU/ ZRifzsdu1/X43DSTz4d4/bYAD6iAaSBJUewSVwUG9OodeU84LYgdba4vRNa2G3BpzfomdvK6H1C8pj HjnVjUGP2F3IO6tMDnpAFZfrxvytlg==",
"componentY": "K5BTgBGzhIux2ZnodU4MWRUVhUFbU4P376TLTHZa02nU2jVb2pAWK3gMfpEHsE7WeoLlNrzAJwR 1FJ679z4Oo/yWp7k39zamQNlMHvm6EYBBbxIemexBHIIqqNRFdHhq6S3pA6L/9ItyscEl5/zZIKxcx44hv CCPZOZUhnOTSc4ehPnYJhdJQFgIDhY5UPRRZntM8hP2hOPZTVz5D4re17bSYVOEEK7bmpGIWpf9p ERUj4MlUpyRpafNd2mQsZpXPvW3XZfHDbslO7o3LourFHRSqAfBHOfx+pwH+YcMwglnay/Ay2SYWyZ hKkD+UcHSkyBdk/AMdcKt1K9uCIPm/Q==",
"componentDelta": "KKRKg/jPcb+r/3TZmhLP/KxrMEajXKvBYQd5jeGFm2OzznUvNHuyEhWyJc4RlXFRoLhwcj9eEuSOz0a bTAeU+Xw8hSMJ6kYhHokJ3ev8tgQ="
}
```
<br>
JSON datatype definition for APPROVED response body after payload decryption
<br>

Data Element|Description|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|----------|---------|-----|---------|--------------|--------------|-------|
|transactionStatus|Overall status of the call|R|Allowable Values: APPROVED DECLINED ERROR||A|5|11|=1|
|transactionStatusCode|Unique code signifying detailed transaction status|R||N|1|3|=1|
|referenceTransactionID|Unique ID for each Transaction which could be used to trace a transaction.
**It is highly recommended that merchants should store the ID on their side. This can be used for researching the transactions in case issue arises**|O||A,N,S0,S1,S2|1|100|<=1|
|transactionStatusDescription|Short description of statusCode|O||A,S0,S1,S2|1|30|<=1|
|fdCustomerID|Unique consumer identifier in Fiserv Telecheck|O||A,N|1|50|<=1|
|fdAccountID|fdAccountID for Request|O||A,N|1|50|<=1|
|account.type|Always "ACH"|O||A|3|3|<=1|
|account Status|Numeric value which defines the status of ACH account|O||N|1|3|<=1|
|accountStatusDesc|Short description which describes the accountStatus|O||A|1|20|<=1|

<br>
JSON sample data for ERROR response body after payload decryption

```json
{
 "transactionStatus": "ERROR",
 "transactionStatusCode": 100,
 "referenceTransactionID": "49eac2d3-b0be-3c39-c791-ef2e5a91ab36", 
 "transactionStatusDescription": "Input is invalid",
"responseVerbiage": "Input is invalid",
"errorDetails": [
 {
  "errorCode": 1070,
  "errorField": "NONCE",
  "errorReason": "The URI Param is Missing or Invalid"
  } 
 ]
}

```
<br>
JSON datatype definition for ERROR response body after payload decryption
<br>

Data Element|Description|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|----------|---------|-----|---------|--------------|--------------|-------|
|transactionStatus|Overall status of the call|R|Allowable Values: APPROVED DECLINED ERROR||A|5|11|=1|
|transactionStatusCode|Unique code signifying detailed transaction status|R||N|1|3|=1|
|referenceTransactionID|Unique ID for each Transaction which could be used to trace a transaction.
**It is highly recommended that merchants should store the ID on their side. This can be used for researching the transactions in case issue arises**|O||A,N,S0,S1,S2|1|100|<=1|
|transactionStatusDescription|Short description of statusCode|O||A,S0,S1,S2|1|30|<=1|
|responseVerbiage|Detailed description of transactionStatus|O||A,N,S0,S1,S2|1|1000|<=1|
|errorCode|Code signifying what kind of error occurred|O||N|1|4|<=1|
|errorField|Signifies which input field that caused the error|O||A|1|30|<=1|
|errorReason|Short description of the error|O||A|1|100|<=1|
<br>
JSON sample data without payload encryption (componentFallBack)

```json 
{
"componentFallBack": "{\r\n \"transactionStatus\" : \"DECLINED\",\r\n \"transactionStatusCode\ " : 420,\r\n \"referenceTransactionID\" : \"APIGEE-a-90f-4946-ff14-
36aa4b9a6325\",\r\n \"transactionStatusDescription\" : \"Unauthorized\",\r\n \"responseVerbia ge\" : \"Unauthorized\",\r\n \"errorDetails\" : [ {\r\n \"errorCode\" : 4250,\r\n \"errorField\" :
\"Client-Token\",\r\n \"errorReason\" : \"Session time out\"\r\n } ]\r\n}" }

```
<br>
Datatype definition without payload encryption (componentFallBack)
<br>

Data Element|Description|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|----------|---------|-----|---------|--------------|--------------|-------|
|transactionStatus|Overall status of the call|R|Allowable Values: APPROVED DECLINED ERROR||A|5|11|=1|
|transactionStatusCode|Unique code signifying detailed transaction status|R||N|1|3|=1|
|referenceTransactionID|Unique ID for each Transaction which could be used to trace a transaction.
**It is highly recommended that merchants should store the ID on their side. This can be used for researching the transactions in case issue arises**|O||A,N,S0,S1,S2|1|100|<=1|
|transactionStatusDescription|Short description of statusCode|O||A,S0,S1,S2|1|30|<=1|
|responseVerbiage|Detailed description of transactionStatus|O||A,N,S0,S1,S2|1|1000|<=1|
|errorCode|Code signifying what kind of error occurred|O||N|1|4|<=1|
|errorField|Signifies which input field that caused the error|O||A|1|30|<=1|
|errorReason|Short description of the error|O||A|1|100|<=1|
<br>





<br>
Sample request body with NONCE before payload encryption:

```json
95199DC2AE5700D0E0530AAE8CADC15C3594
```
<br>

Data Element|Description|Requires Encryption|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|-----------|-------------------|---------------|---------|--------------|--------------|-------|
|nonce|NONCE|N|R||A,N|1|100|<=1|
<br>
Sample request body after payload encryption and before transmission:

```json
{
"componentX":
"eev1q/gsq1Z3VxBLczB0IKGoOMoXpB3jhchXVP0RD7F2uGqUONp7BUhZxIY8kfVs6gaZnELNQ+btyNeBt7+rW 36UoQm3zX0LYgrDkRyFqG92TZIqEdJscHIrua4xoW+btNd6qZR1wgfMrA2IIj+gOGk2XwRoCod4i1n4ZOKyNWo 8KSLRVCiAzLHB49nY7fBgEDFEEAKhukL3LQ+Cvz0Q5E4rEV7BIAlRr+Wv+AxDstEkjhbUjlySBiJ5fpZsIwrAaT16 S16J/sqi0DF8JRXy8ulT6a2uIZYZAAjLsWlnyhEkDWy2Kp2CZNpnI112BbuMq5xr+wQlFmMzrI+9SWlM6g==",
"componentY": "SMZ6uXVRIQaaG8V/P9celJglciwTsB5+u8TgM81fUcrTRydsGLy0RXE1OGzOcmLmKU+fNy07IL0Y59M2UndTr TJ1dd4dMT3iT5TynUlLcUJpXAwS2Bvbars0HAKEJOiIuJstckG7/Rcl+XlZnaEsD5NgXeLnH+PyMaNnZA6cHsySl kEtCSIS/JC3E+PoirsFLRFBUH0Yds7fRE1/76WpvVy2G1iaRAm69ySht2rRH8PAXvNN3jrSzHrzJUy9ppYaOLCW JcdTxvFpRDMFHbtblcG7BZQy3AfbxYAsju8wdEn/I2Gy6BwsqSzY5hSEfvftqLQXU9lq1J3hsBB5yByTWw==",
"componentDelta": "q0dKj5HpPgIC7QROE8q9NQGMg3mcuRQT3OvGmyNGPxv49b3zXhN+FCLw232rwarz" 
}
```
<br>
Data Element|Description|Requires Encryption|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|-----------|-------------------|---------------|---------|--------------|--------------|-------|
|componentDelta|Encrypted Payload|Y|R||A,N|1||<=1|
|componentX|Secret for AES encryption|Y|R||A,N|32|32|<=1|
|componentY|IV for Data Encryption and Decryption|Y|R|A,N|16|16|<=1|
<br>

#### Get Data Request Specification (need subtitle)
<br>
Sample response body received with payload encryption:

```json
{
"componentDelta":
"n689JQiDumqRxIMP5HPDNW7BArz3BhvZU5DpA1j14MzZI8KM4JjQh9ahBeJG3SVJAF428zQj7TjaVFrSkBVV Quhz6p0WD+vze4Skm9EOV6j3P1X7CCPEG9a43AInKrczxpVWzBfqyRhV3yutGVDAbOGWEuqYe8+VIqEvi2gY TeQg6J/Z/Whgcd1Xz0l8JffNsWkv4qFVny1ehHi9zBOQMo27HY/ipaHMbGjqHkd3Cf+HlJ47HjcZh597h7740yjkD olLGHx4DW8hdZh5vEqZu9zBJy+rXXRhMxLcGD0IidUT6FHQWpNV7KQKYHDFNIX42dVrXqGI7hZzZB4AfiHb+/ pxFTONeM0+cKA/u2DbAFNjsPlPwLtD77yVfsCT2X6IpnXtKc8TgdtyxujooQH7npK2IpsSUAHfxwuioYy/QoL2rgP UkLZmO0Pi7pkPb8Zo4ll+5tXpUfxj9KrCXjHeQBGhUg7VVidrjmcR7Cz3XMS+2m96Vbo8GAWxNhKrO+OAMH6k 1RxnMcgUg4s5AOcne2IwoLz/b71oNJGi8SVdLhVmaWsBrL2MrKq1YXR/pLyW"
}
```
<br>
Data Element|Description|Requires Encryption|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|-----------|-------------------|---------------|---------|--------------|--------------|-------|
|componentDelta|Encrypted GetData response|N|R||A,N|1||<=1|
<br>
Sample response body after payload is decrypted:

```json
{
    "transactionStatus": "APPROVED",
    "transactionStatusCode": 0,
    "referenceTransactionID": "2433d950-6cab-4a6e-a6e1-647a04985c1f", 
    "transactionStatusDescription": "OK",
    "customer": {
        "fdCustomerID": "0bf52d6bac534a96a9c300d143f0689a"
    }, 
    "account": [
        {
            "fdAccountID": "8a7f42087ee46e0c017ee8187c1a016a", 
            "type": "ACH",
            "accountStatus": "70",
            "accountStatusDesc": "PENDING_VALIDATIONS", 
            "accountValidationDetails": [
                {
                    "validationCode": "10",
                    "validationCodeDesc": "Bank Validation Status", 
                    "validationCodeStatus": "PENDING"
                }, 
                {
                    "validationCode": "50", 
                    "validationCodeDesc": "Pin Update Status", 
                    "validationCodeStatus": "COMPLETE"             
                },
                {
                    "validationCode": "70",
                    "validationCodeDesc": "Email Validation Status", 
                    "validationCodeStatus": "COMPLETE"
                }, 
                {
                   "validationCode": "80",
                   "validationCodeDesc": "Phone Validation Status", 
                   "validationCodeStatus": "COMPLETE" 
                } 
            ]
        } 
    ]
}
```
<br>
JSON datatype definition for APPROVED response body after payload decryption
<br>

Data Element|Description|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|----------|---------|-----|---------|--------------|--------------|-------|
|transactionStatus|Overall status of the call|R|Allowable Values: APPROVED DECLINED ERROR||A|5|11|=1|
|transactionStatusCode|Unique code signifying detailed transaction status|R||N|1|3|=1|
|referenceTransactionID|Unique ID for each Transaction which could be used to trace a transaction.
**It is highly recommended that merchants should store the ID on their side. This can be used for researching the transactions in case issue arises**|O||A,N,S0,S1,S2|1|100|<=1|
|transactionStatusDescription|Short description of statusCode|O||A,S0,S1,S2|1|30|<=1|
|fdCustomerID|Unique consumer identifier in Fiserv Telecheck|O||A,N|1|50|<=1|
|fdAccountID|fdAccountID for Request|O||A,N|1|50|<=1|
|account.type|Always "ACH"|O||A|3|3|<=1|
|account Status|Numeric value which defines the status of ACH account|O||N|1|3|<=1|
|accountStatusDesc|Short description which describes the accountStatus|O||A|1|20|<=1|
<br>
JSON sample data for ERROR response body after payload decryption

```json
{
 "transactionStatus": "ERROR",
 "transactionStatusCode": 100,
 "referenceTransactionID": "49eac2d3-b0be-3c39-c791-ef2e5a91ab36", 
 "transactionStatusDescription": "Input is invalid",
 "responseVerbiage": "Input is invalid",
 "errorDetails": [
  {
   "errorCode": 1070,
   "errorField": "NONCE",
   "errorReason": "The URI Param is Missing or Invalid"
  } 
 ]
}
```
<br>
JSON datatype definition for ERROR response body after payload decryption
<br>

Data Element|Description|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|----------|---------|-----|---------|--------------|--------------|-------|
|transactionStatus|Overall status of the call|R|Allowable Values: APPROVED DECLINED ERROR||A|5|11|=1|
|transactionStatusCode|Unique code signifying detailed transaction status|R||N|1|3|=1|
|referenceTransactionID|Unique ID for each Transaction which could be used to trace a transaction.
**It is highly recommended that merchants should store the ID on their side. This can be used for researching the transactions in case issue arises**|O||A,N,S0,S1,S2|1|100|<=1|
|transactionStatusDescription|Short description of statusCode|O||A,S0,S1,S2|1|30|<=1|
|responseVerbiage|Detailed description of transactionStatus|O||A,N,S0,S1,S2|1|1000|<=1|
|errorCode|Code signifying what kind of error occurred|O||N|1|4|<=1|
|errorField|Signifies which input field that caused the error|O||A|1|30|<=1|
|errorReason|Short description of the error|O||A,S1|1|100|<=1|
<br>
JSON sample data without payload encryption (componentFallBack)
<br>

```json
{
"componentFallBack": "{\r\n \"transactionStatus\" : \"DECLINED\",\r\n \"transactionStatusCode\ " : 420,\r\n \"referenceTransactionID\" : \"APIGEE-a-90f-4946-ff14-
36aa4b9a6325\",\r\n \"transactionStatusDescription\" : \"Unauthorized\",\r\n \"responseVerbia ge\" : \"Unauthorized\",\r\n \"errorDetails\" : [ {\r\n \"errorCode\" : 4250,\r\n \"errorField\" :
\"Client-Token\",\r\n \"errorReason\" : \"Session time out\"\r\n } ]\r\n}" }
```
Datatype definition without payload encryption (componentFallBack)
Data Element|Description|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|----------|---------|-----|---------|--------------|--------------|-------|
|transactionStatus|Overall status of the call|R|Allowable Values: APPROVED DECLINED ERROR||A|5|11|=1|
|transactionStatusCode|Unique code signifying detailed transaction status|R||N|1|3|=1|
|referenceTransactionID|Unique ID for each Transaction which could be used to trace a transaction.
**It is highly recommended that merchants should store the ID on their side. This can be used for researching the transactions in case issue arises**|O||A,N,S0,S1,S2|1|100|<=1|
|transactionStatusDescription|Short description of statusCode|O||A,S0,S1,S2|1|30|<=1|
|responseVerbiage|Detailed description of transactionStatus|O||A,N,S0,S1,S2|1|1000|<=1|
|errorCode|Code signifying what kind of error occurred|O||N|1|4|<=1|
|errorField|Signifies which input field that caused the error|O||A|1|30|<=1|
|errorReason|Short description of the error|O||A|1|100|<=1|




<br>

Data Element|Description|Required?|Rules|Data Type|Minimum Length (Clear Value)|Maximum Length(Clear Value)| #occur|
|------------|----------|---------|-----|---------|--------------|--------------|-------|
|fdCustomerID|Customer ID|R||A,N|1|50|<=1|
|type|Type of account|R|Only ACH account upported|A|1|10|<=1|
|fdAccountID|Account ID|R||A,N|1|50|<=1|
|fetchAccountDetails|List types of data needed to be fetched for that consumer|O||||||
|fetch|Group name of the data needed to be fetched|R||A|1|1|<=1|
|masked|Set masking is required for that group or not|O|Y,N|A|1|1|<=1|
<br>
Type of Fetch currently supported
<ol>
    <li>getAllDetails</li>
    <li>getPersonalDetails</li>
    <li>getIdentificationDetails</li>
    <li>getAddressDetails</li>
    <li>getCardDetails</li>
    <li>getBankDetails</li>
    <li>getSecurityQuestionDetails</li>
    <li>getOtherDetails</li>
    <li>getReportingDetails</li>
</ol>
<br>
Sample request body after payload encryption and before transmission:
<br>

```json
{
"componentX":
"eev1q/gsq1Z3VxBLczB0IKGoOMoXpB3jhchXVP0RD7F2uGqUONp7BUhZxIY8kfVs6gaZnELNQ+btyNeBt7+rW 36UoQm3zX0LYgrDkRyFqG92TZIqEdJscHIrua4xoW+btNd6qZR1wgfMrA2IIj+gOGk2XwRoCod4i1n4ZOKyNWo 8KSLRVCiAzLHB49nY7fBgEDFEEAKhukL3LQ+Cvz0Q5E4rEV7BIAlRr+Wv+AxDstEkjhbUjlySBiJ5fpZsIwrAaT16 S16J/sqi0DF8JRXy8ulT6a2uIZYZAAjLsWlnyhEkDWy2Kp2CZNpnI112BbuMq5xr+wQlFmMzrI+9SWlM6g==",
"componentY": "SMZ6uXVRIQaaG8V/P9celJglciwTsB5+u8TgM81fUcrTRydsGLy0RXE1OGzOcmLmKU+fNy07IL0Y59M2UndTr TJ1dd4dMT3iT5TynUlLcUJpXAwS2Bvbars0HAKEJOiIuJstckG7/Rcl+XlZnaEsD5NgXeLnH+PyMaNnZA6cHsySl kEtCSIS/JC3E+PoirsFLRFBUH0Yds7fRE1/76WpvVy2G1iaRAm69ySht2rRH8PAXvNN3jrSzHrzJUy9ppYaOLCW JcdTxvFpRDMFHbtblcG7BZQy3AfbxYAsju8wdEn/I2Gy6BwsqSzY5hSEfvftqLQXU9lq1J3hsBB5yByTWw==",
"componentDelta": "q0dKj5HpPgIC7QROE8q9NQGMg3mcuRQT3OvGmyNGPxv49b3zXhN+FCLw232rwarz" 
}
```
<br>
Data Element|Description|Requires Encryption|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|-----------|-------------------|---------------|---------|--------------|--------------|-------|
|componentDelta|Encrypted Payload|Y|R||A,N|1||<=1|
|componentX|Secret for AES encryption|Y|R||A,N|32|32|<=1|
|componentY|IV for Data Encryption and Decryption|Y|R|A,N|16|16|<=1|
<br>

#### Get Data Response Specification (Need Title)
<br>
Sample response body received with payload encryption:

```json
{
"componentDelta":
"dtK9nYajxhLqqTAiFoFxMfh8Gj0VnQxbu30c6vuvmIboOw+fd+7N5sp6WeZ9eXElRFu/P/PXvQJrYysq6JG6tONzj voqWg1JUeM0LOkB2EYpPl3huQl1TSSOtZ9bkCO4v6LAeokaUMdPmRVS/9RtStiV4EgsMHMgCkicSfHxCDRh CEDEC+2xtXbmujMGUsTIDm+WU4mluEWPr9niTgg7LOyFn+dUW6cKIrb54vG/mNS/P/pjOvPxbOJ9aca1Vl8Xk dXZ6gKl4FgToQID34BON5ln+zf/5SzcRKvswta2LvLp093yQX2ytu1fak5KztYp8ePqeNwNt5ZtnzUItojqzR/vDeBN
Ic826Zh5aGZq0tGfuOZPQV1QEYj0YO5MZ6WYf05h57n5bo1L0+b32dNDnuK0lNYe1/5qB1lcz/rZO/1mVsJCjM CNuZDUxAdmPFW1BKYxsFuBfuwGKxBWi4XXHk8NfRZgv47IMa0r8Az9AITyRwj9eIwQI0k3msyoaHGAgNWYfO jC+/lADjfjMmdfxYuBnZiNTKDKPTqommADflmvJKYoS2qGghIrxhUPhezU"
}
```
<br>
Data Element|Description|Requires Encryption|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|-----------|-------------------|---------------|---------|--------------|--------------|-------|
|componentDelta|Encrypted GetData response|N|R||A,N|1||<=1|
<br>
Sample response body after payload is decrypted:

```json
```json
{
   "transactionStatus": "APPROVED",
   "transactionStatusCode": 0,
   "referenceTransactionID": "2cad9e56-0837-fd3b-ca8b-cdeb38529814", 
   "transactionStatusDescription": "OK",
   "customer": {
      "fdCustomerID": "0bf52d6bac534a96a9c300d143f0689a" 
    },
    "account": [ 
        {
           "fdAccountID": "8a7f42087ee46e0c017ee7e92a6d013e", 
           "type": "ACH",
           "accountStatus": "70",
           "accountStatusDesc": "PENDING_VALIDATIONS", 
           "accountValidationDetails": [
             {
                "validationCode": "10",
                "validationCodeDesc": "Bank Validation Status", 
                "validationCodeStatus": "PENDING"
             },
             { 
                "validationCode": "50", 
                "validationCodeDesc": "Pin Update Status", 
                "validationCodeStatus": "COMPLETE"
            }, 
            {
                "validationCode": "70",
                "validationCodeDesc": "Email Validation Status", 
                "validationCodeStatus": "COMPLETE"
            }, 
            {
                "validationCode": "80",
                "validationCodeDesc": "Phone Validation Status", 
                "validationCodeStatus": "COMPLETE"
            } 
        ],
        "userDetails": {
            "firstName": "Joe",
            "lastName": "Smith",
            "email": "Joe.Smith@fiserv.com", 
            "gender": "M",
            "dob": "19871115", 
            "memberSince": "20150226",
            "agreedTncVersion": "v1"
        }, 
        "userAddressDetails": {
            "street": "112 Freeway", 
            "street2": "APT 999", 
            "state": "TX",
            "city": "Houston", 
            "country": "840", 
            "postalCode": "77478"
        }, 
        "userIdentificationDetails": {
            "ssn": "986525482",
            "routingNumber": "311080311",
            "accountNumber": "8262192877",
            "bankName": "SUN CU",
            "connectPayPaymentNumber": "4341120000000019108", 
            "corporateAccountFlag": "personal_check", 
            "driverLicenseNumber": "86090280",
            "driverLicenseState": "TX"
        }, 
        "userPhone": [
            {
                "type": "MOBILE", 
                "number": "8652547895", 
                "primary": "Y"
            }, 
            {
                "type": "HOME", 
                "number": "8652547895", 
                "primary": "N"  
            }, 
            {
                "type": "BUSINESS", 
                "number": "8652545789", 
                "primary": "N"
            },
            {
                "type": "OTHERS", 
                "number": "6525434789", 
                "primary": "N"
            } 
        ],
        "sqnA": [ 
            {
                "securityQuestionId": "1",
                "securityQuestion": "ABC" 
            },
            {
                "securityQuestionId": "2", 
                "securityQuestion": "GHI"
            }, 
                        {
                "securityQuestionId": "3", 
                "securityQuestion": "GHI"
            }, 
            {
                "securityQuestionId": "4", 
                "securityQuestion": "GHI"
            },
                        {
                "securityQuestionId": "5", 
                "securityQuestion": "GHI"
            } 
        ], 
        "reportingFields": {
            "reportingField1": "123", 
            "reportingField2": "1234", 
            "reportingField3": "12345"
        }, 
        "genericCodes": {
            "genericCode1": "1", 
            "genericCode2": "2", 
            "genericCode3": "3"
        }, 
        "genericFlags": {
            "genericFlag1": "Y", 
            "genericFlag2": "Y", 
            "genericFlag3": "Y"
        } 
    }
  ] 
}
```
JSON datatype definition for APPROVED response body after payload decryption

<br>
<!--Need to finish this table. Starts on page 88-90-->
Data Element|Description|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|----------|---------|-----|---------|--------------|--------------|-------|
|customer.fdCustomerID||R|Allowable Values: APPROVED DECLINED ERROR||A|5|11|=1|
|account||R||N|1|3|=1|
|account.type||O||A,N,S0,S1,S2|1|100|<=1|
|account.userDetails.firstName||O||A,S0,S1,S2|1|30|<=1|
|account.userDetails.lastName|Unique consumer identifier in Fiserv Telecheck|O||A,N|1|50|<=1|
|account.userDetails.email|fdAccountID for Request|O||A,N|1|50|<=1|
|account.userDetails.dob|Always "ACH"|O||A|3|3|<=1|
|account.userDetails.mmemberSince|Numeric value which defines the status of ACH account|O||N|1|3|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userAddressDetails.street|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|
|account.userDetails.agreedTncVersion|Short description which describes the accountStatus|O||A|1|20|<=1|


<br>
JSON sample data for ERROR response body after payload decryption
<br>

```json
{
 "transactionStatus" : "ERROR",
 "transactionStatusCode" : 100,
 "referenceTransactionID" : "3ff4dccc-1feb-f4c5-fb79-4cf58ae48554", 
 "transactionStatusDescription" : "Input is invalid ", 
 "responseVerbiage": "Input is invalid",
"errorDetails" : [ {
  "errorCode" : 1030,
  "errorField" : "Masked",
  "errorReason" : "Required field did not have a value"
}] 
}
```
<br>
JSON datatype definition for ERROR response body after payload decryption
<br>

Data Element|Description|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|----------|---------|-----|---------|--------------|--------------|-------|
|transactionStatus|Overall status of the call|R|Allowable Values: APPROVED DECLINED ERROR||A|5|11|=1|
|transactionStatusCode|Unique code signifying detailed transaction status|R||N|1|3|=1|
|referenceTransactionID|Unique ID for each Transaction which could be used to trace a transaction.
**It is highly recommended that merchants should store the ID on their side. This can be used for researching the transactions in case issue arises**|O||A,N,S0,S1,S2|1|100|<=1|
|transactionStatusDescription|Short description of statusCode|O||A,S0,S1,S2|1|30|<=1|
|responseVerbiage|Detailed description of transactionStatus|O||A,N,S0,S1,S2|1|1000|<=1|
|errorCode|Code signifying what kind of error occurred|O||N|1|4|<=1|
|errorField|Signifies which input field that caused the error|O||A|1|30|<=1|
|errorReason|Short description of the error|O||A,S1|1|100|<=1|
<br>
JSON sample data without payload encryption (componentFallBack)

```json
{
"componentFallBack": "{\r\n \"transactionStatus\" : \"DECLINED\",\r\n \"transactionStatusCode\ " : 420,\r\n \"referenceTransactionID\" : \"APIGEE-a-90f-4946-ff14-
36aa4b9a6325\",\r\n \"transactionStatusDescription\" : \"Unauthorized\",\r\n \"responseVerbia ge\" : \"Unauthorized\",\r\n \"errorDetails\" : [ {\r\n \"errorCode\" : 4250,\r\n \"errorField\" :
\"Client-Token\",\r\n \"errorReason\" : \"Session time out\"\r\n } ]\r\n}" 
}
```
Datatype definition without payload encryption (componentFallBack)
<br>

Data Element|Description|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|----------|---------|-----|---------|--------------|--------------|-------|
|transactionStatus|Overall status of the call|R|Allowable Values: APPROVED DECLINED ERROR||A|5|11|=1|
|transactionStatusCode|Unique code signifying detailed transaction status|R||N|1|3|=1|
|referenceTransactionID|Unique ID for each Transaction which could be used to trace a transaction.
**It is highly recommended that merchants should store the ID on their side. This can be used for researching the transactions in case issue arises**|O||A,N,S0,S1,S2|1|100|<=1|
|transactionStatusDescription|Short description of statusCode|O||A,S0,S1,S2|1|30|<=1|
|responseVerbiage|Detailed description of transactionStatus|O||A,N,S0,S1,S2|1|1000|<=1|
|errorCode|Code signifying what kind of error occurred|O||N|1|4|<=1|
|errorField|Signifies which input field that caused the error|O||A|1|30|<=1|
|errorReason|Short description of the error|O||A|1|100|<=1|
<br>
<br>
Sample request body before payload encryption:

```json
{
    "customer": {
    "fdCustomerID": "CPX8lY16074639744570000921EKCfWM" 
},
"account": [ 
    {
        "type": "ACH",
        "fdAccountID": "CPX8lY1607463998985721BKCeBf", 
        "fetchAccountDetails": [
    {
        "fetch": "getAllDetails", 
        "masked": "N"
    } 
  ]
 } 
]
}
```
<br>




Data Element|Description|Required?|Rules|Data Type|Minimum Length (Clear Value)|Maximum Length(Clear Value)| #occur|
|------------|----------|---------|-----|---------|--------------|--------------|-------|
|fdCustomerID|Customer ID|R||A,N|1|50|<=1|
|type|Type of account|R|Only ACH account upported|A|1|10|<=1|
|fdAccountID|Account ID|R||A,N|1|50|<=1|
|fetchAccountDetails|List types of data needed to be fetched for that consumer|O||||||
|fetch|Group name of the data needed to be fetched|R||A|1|1|<=1|
|masked|Set masking is required for that group or not|O|Y,N|A|1|1|<=1|
<br>
Type of Fetch currently supported
<ol>
<li>getAllDetails</li>
<li>getPersonalDetails</li>
<li>getIdentificationDetails</li>
<li>getAddressDetails</li>
<li>getCardDetails</li>
<li>getBankDetails</li>
<li>getSecurityQuestionDetails</li>
<li>getOtherDetails</li>
<li>getReportingDetails</li>
</ol>
<br>
Sample request body after payload encryption and before transmission:
<br>

```json
{
"componentX":
"eev1q/gsq1Z3VxBLczB0IKGoOMoXpB3jhchXVP0RD7F2uGqUONp7BUhZxIY8kfVs6gaZnELNQ+btyNeBt7+rW 36UoQm3zX0LYgrDkRyFqG92TZIqEdJscHIrua4xoW+btNd6qZR1wgfMrA2IIj+gOGk2XwRoCod4i1n4ZOKyNWo 8KSLRVCiAzLHB49nY7fBgEDFEEAKhukL3LQ+Cvz0Q5E4rEV7BIAlRr+Wv+AxDstEkjhbUjlySBiJ5fpZsIwrAaT16 S16J/sqi0DF8JRXy8ulT6a2uIZYZAAjLsWlnyhEkDWy2Kp2CZNpnI112BbuMq5xr+wQlFmMzrI+9SWlM6g==",
"componentY": "SMZ6uXVRIQaaG8V/P9celJglciwTsB5+u8TgM81fUcrTRydsGLy0RXE1OGzOcmLmKU+fNy07IL0Y59M2UndTr TJ1dd4dMT3iT5TynUlLcUJpXAwS2Bvbars0HAKEJOiIuJstckG7/Rcl+XlZnaEsD5NgXeLnH+PyMaNnZA6cHsySl kEtCSIS/JC3E+PoirsFLRFBUH0Yds7fRE1/76WpvVy2G1iaRAm69ySht2rRH8PAXvNN3jrSzHrzJUy9ppYaOLCW JcdTxvFpRDMFHbtblcG7BZQy3AfbxYAsju8wdEn/I2Gy6BwsqSzY5hSEfvftqLQXU9lq1J3hsBB5yByTWw==",
"componentDelta": "q0dKj5HpPgIC7QROE8q9NQGMg3mcuRQT3OvGmyNGPxv49b3zXhN+FCLw232rwarz" 
}
```
<br>
Data Element|Description|Requires Encryption|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|-----------|-------------------|---------------|---------|--------------|--------------|-------|
|componentDelta|Encrypted Payload|Y|R||A,N|1||<=1|
|componentX|Secret for AES encryption|Y|R||A,N|32|32|<=1|
|componentY|IV for Data Encryption and Decryption|Y|R|A,N|16|16|<=1|
<br>

#### Get Data Response Specification (Need Title)
<br>
Sample response body received with payload encryption:

```json
{
"componentDelta":
"dtK9nYajxhLqqTAiFoFxMfh8Gj0VnQxbu30c6vuvmIboOw+fd+7N5sp6WeZ9eXElRFu/P/PXvQJrYysq6JG6tONzj voqWg1JUeM0LOkB2EYpPl3huQl1TSSOtZ9bkCO4v6LAeokaUMdPmRVS/9RtStiV4EgsMHMgCkicSfHxCDRh CEDEC+2xtXbmujMGUsTIDm+WU4mluEWPr9niTgg7LOyFn+dUW6cKIrb54vG/mNS/P/pjOvPxbOJ9aca1Vl8Xk dXZ6gKl4FgToQID34BON5ln+zf/5SzcRKvswta2LvLp093yQX2ytu1fak5KztYp8ePqeNwNt5ZtnzUItojqzR/vDeBN
Ic826Zh5aGZq0tGfuOZPQV1QEYj0YO5MZ6WYf05h57n5bo1L0+b32dNDnuK0lNYe1/5qB1lcz/rZO/1mVsJCjM CNuZDUxAdmPFW1BKYxsFuBfuwGKxBWi4XXHk8NfRZgv47IMa0r8Az9AITyRwj9eIwQI0k3msyoaHGAgNWYfO jC+/lADjfjMmdfxYuBnZiNTKDKPTqommADflmvJKYoS2qGghIrxhUPhezU"
}
```
<br>
Data Element|Description|Requires Encryption|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|-----------|-------------------|---------------|---------|--------------|--------------|-------|
|componentDelta|Encrypted GetData response|N|R||A,N|1||<=1|
<br>
Sample response body after payload is decrypted:

```json
```json
{
   "transactionStatus": "APPROVED",
   "transactionStatusCode": 0,
   "referenceTransactionID": "2cad9e56-0837-fd3b-ca8b-cdeb38529814", 
   "transactionStatusDescription": "OK",
   "customer": {
      "fdCustomerID": "0bf52d6bac534a96a9c300d143f0689a" 
    },
    "account": [ 
        {
           "fdAccountID": "8a7f42087ee46e0c017ee7e92a6d013e", 
           "type": "ACH",
           "accountStatus": "70",
           "accountStatusDesc": "PENDING_VALIDATIONS", 
           "accountValidationDetails": [
             {
                "validationCode": "10",
                "validationCodeDesc": "Bank Validation Status", 
                "validationCodeStatus": "PENDING"
             },
             { 
                "validationCode": "50", 
                "validationCodeDesc": "Pin Update Status", 
                "validationCodeStatus": "COMPLETE"
            }, 
            {
                "validationCode": "70",
                "validationCodeDesc": "Email Validation Status", 
                "validationCodeStatus": "COMPLETE"
            }, 
            {
                "validationCode": "80",
                "validationCodeDesc": "Phone Validation Status", 
                "validationCodeStatus": "COMPLETE"
            } 
        ],
        "userDetails": {
            "firstName": "Joe",
            "lastName": "Smith",
            "email": "Joe.Smith@fiserv.com", 
            "gender": "M",
            "dob": "19871115", 
            "memberSince": "20150226",
            "agreedTncVersion": "v1"
        }, 
        "userAddressDetails": {
            "street": "112 Freeway", 
            "street2": "APT 999", 
            "state": "TX",
            "city": "Houston", 
            "country": "840", 
            "postalCode": "77478"
        }, 
        "userIdentificationDetails": {
            "ssn": "986525482",
            "routingNumber": "311080311",
            "accountNumber": "8262192877",
            "bankName": "SUN CU",
            "connectPayPaymentNumber": "4341120000000019108", 
            "corporateAccountFlag": "personal_check", 
            "driverLicenseNumber": "86090280",
            "driverLicenseState": "TX"
        }, 
        "userPhone": [
            {
                "type": "MOBILE", 
                "number": "8652547895", 
                "primary": "Y"
            }, 
            {
                "type": "HOME", 
                "number": "8652547895", 
                "primary": "N"  
            }, 
            {
                "type": "BUSINESS", 
                "number": "8652545789", 
                "primary": "N"
            },
            {
                "type": "OTHERS", 
                "number": "6525434789", 
                "primary": "N"
            } 
        ],
        "sqnA": [ 
            {
                "securityQuestionId": "1",
                "securityQuestion": "ABC" 
            },
            {
                "securityQuestionId": "2", 
                "securityQuestion": "GHI"
            }, 
                        {
                "securityQuestionId": "3", 
                "securityQuestion": "GHI"
            }, 
            {
                "securityQuestionId": "4", 
                "securityQuestion": "GHI"
            },
                        {
                "securityQuestionId": "5", 
                "securityQuestion": "GHI"
            } 
        ], 
        "reportingFields": {
            "reportingField1": "123", 
            "reportingField2": "1234", 
            "reportingField3": "12345"
        }, 
        "genericCodes": {
            "genericCode1": "1", 
            "genericCode2": "2", 
            "genericCode3": "3"
        }, 
        "genericFlags": {
            "genericFlag1": "Y", 
            "genericFlag2": "Y", 
            "genericFlag3": "Y"
        } 
    }
  ] 
}
```
JSON datatype definition for APPROVED response body after payload decryption

<br>
<!--Need to finish this table. Starts on page 96-99-->
Data Element|Description|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|----------|---------|-----|---------|--------------|--------------|-------|
|customer.fdCustomerID||R|Allowable Values: APPROVED DECLINED ERROR||A|5|11|=1|
|account||R||N|1|3|=1|
|account.type||O||A,N,S0,S1,S2|1|100|<=1|

<br>
JSON sample data for ERROR response body after payload decryption

```json
{
"transactionStatus" : "ERROR",
"transactionStatusCode" : 100,
"referenceTransactionID" : "3ff4dccc-1feb-f4c5-fb79-4cf58ae48554", "transactionStatusDescription" : "Input is invalid ", "responseVerbiage": "Input is invalid",
"errorDetails" : [ {
"errorCode" : 1030,
"errorField" : "Masked",
"errorReason" : "Required field did not have a value"
}] 
}
```
<br>
JSON datatype definition for ERROR response body after payload decryption

<br>

Data Element|Description|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|----------|---------|-----|---------|--------------|--------------|-------|
|transactionStatus|Overall status of the call|R|Allowable Values: APPROVED DECLINED ERROR||A|5|11|=1|
|transactionStatusCode|Unique code signifying detailed transaction status|R||N|1|3|=1|
|referenceTransactionID|Unique ID for each Transaction which could be used to trace a transaction.
**It is highly recommended that merchants should store the ID on their side. This can be used for researching the transactions in case issue arises**|O||A,N,S0,S1,S2|1|100|<=1|
|transactionStatusDescription|Short description of statusCode|O||A,S0,S1,S2|1|30|<=1|
|responseVerbiage|Detailed description of transactionStatus|O||A,N,S0,S1,S2|1|1000|<=1|
|errorCode|Code signifying what kind of error occurred|O||N|1|4|<=1|
|errorField|Signifies which input field that caused the error|O||A|1|30|<=1|
|errorReason|Short description of the error|O||A,S1|1|100|<=1|
<br>
JSON sample data without payload encryption (componentFallBack)

```json
{
"componentFallBack": "{\r\n \"transactionStatus\" : \"DECLINED\",\r\n \"transactionStatusCode\ " : 420,\r\n \"referenceTransactionID\" : \"APIGEE-a-90f-4946-ff14-
36aa4b9a6325\",\r\n \"transactionStatusDescription\" : \"Unauthorized\",\r\n \"responseVerbia ge\" : \"Unauthorized\",\r\n \"errorDetails\" : [ {\r\n \"errorCode\" : 4250,\r\n \"errorField\" :
\"Client-Token\",\r\n \"errorReason\" : \"Session time out\"\r\n } ]\r\n}" 
}
```
<br>
Datatype definition without payload encryption (componentFallBack)
<br>

Data Element|Description|Required?|Rules|Data Type|Minimum Length|Maximum Length| #occur|
|------------|----------|---------|-----|---------|--------------|--------------|-------|
|transactionStatus|Overall status of the call|R|Allowable Values: APPROVED DECLINED ERROR||A|5|11|=1|
|transactionStatusCode|Unique code signifying detailed transaction status|R||N|1|3|=1|
|referenceTransactionID|Unique ID for each Transaction which could be used to trace a transaction.
**It is highly recommended that merchants should store the ID on their side. This can be used for researching the transactions in case issue arises**|O||A,N,S0,S1,S2|1|100|<=1|
|transactionStatusDescription|Short description of statusCode|O||A,S0,S1,S2|1|30|<=1|
|responseVerbiage|Detailed description of transactionStatus|O||A,N,S0,S1,S2|1|1000|<=1|
|errorCode|Code signifying what kind of error occurred|O||N|1|4|<=1|
|errorField|Signifies which input field that caused the error|O||A|1|30|<=1|
|errorReason|Short description of the error|O||A|1|100|<=1|
<br>
