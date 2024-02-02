# WebSDK Integration

## Download SDK

>Note: Ensure you are adding this code under your <head> tag 

Download javascript file

```javascript
<head>
<!-- Based on Environment, comment and uncomment below codes-->
<!--Sandbox Environment-->
<script src="https://cat.api.firstdata.com/gateway/v2/connectpay/static/v1/js/PaymentSDK.js" ></script>
<!-- Prod Environment -->
<!-- <script src="https://prod.api.firstdata.com/gateway/v2/connectpay/static/v1/js/PaymentSDK.js" ></script> -->
</head>
```

## Configure

### Create Container

Inside <body> tag create a <div> container with the “sdk-container” as the id (as given below) where you would like the payment screen to appear:

```javascript
<!-- SDK container -->
<div id="sdk-container">
<!-- SDK elements will be inserted within this div-->
</div>
```

### Initialize SDK

```javascript
<script>
/*
const cp = CPSDK(<apiKey>, loggingEnabled(true/false)); @params
apiKey - is the API key provided
loggingEnabled - pass true to enable console debug logging(true/false) */
//Create SDK instance
const CP = CPSDK(apiKey, false); </script>
```

### Create Connect Pay Configuration Object

```javascript
var sdkConfiguration = {
accessToken: 'xxxxxx', // received from your server
fdCustomerId: ‘342342342’ // this is fdCustomerId
configId: '432907a3-6282-40da-8526-axxxxxx', // this is the configuration to load
}
```

## Use Case Integration

To integrate into a specific use case of the ConnectPay SDK, below steps needs to be followed: 
<<<<<<< HEAD

>Note: Define any extraParam/default parameters to be passed into the use case as a JSON object: (It is mandatory to pass all the required fields in extra params for Streamlined enrollment flow.)*

Below values are optional

```json
var extraParams = 
=======
*Note: Define any extraParam/default parameters to be passed into the use case as a JSON object: (It is mandatory to pass all the required fields in extra params for Streamlined enrollment flow.)*
```json
//passing values to SDK. Below values are optional
var extraParams = {
>>>>>>> 3532121 (Updated Implementation Guide file and landing page)
accountNumber:"<account_number>", routingNumber:"<routing_number>",
firstName:"<first_name>",
lastName:"<last_name>",
email:"<email>",
connecPayPaymentNumber:"<connect_pay_payment_number>",
corporateAccountFlag:"<personal_check/corporate_check>",
"userePhone[0].number":"<phone_number",
"userPhone[0].type":"<HOME/MOBILE/BUSINESS/OTHERS>",
street:"<street>",
street2:"<street2>", //optional
city:"<city>",
state:"<state>",
postalCode:"<postalCode>",
driverLicenseNumber:"<driver_license_number", //optional
driverLicenseState:"<state>", //optional
ssn:"<ssn>", //optional
gender:"male/female", //optional
dob:"<mmddyyyy>", //optional
memberSince: “member since in date format”, //optional
pin:"<pin_number>", //optional
genericFlag1: “<Generic Flag1(Y/N)>”, //optional 
genericFlag2: “<Generic Flag2(Y/N)>”, //optional 
genericFlag3: “<Generic Flag3(Y/N)>”, //optional
genericCode1: “<Generic Code1>”, //optional 
genericCode2: “<Generic Code2>”, //optional 
genericCode3: “<Generic Code3>”, //optional
reportingField1: “<Reporting Field1>”, //optional 
reportingField2: “<Reporting Field2>”, //optional 
reportingField3: “<Reporting Field3>”, //optional
```

Call the specific use case method exposed by the CP SDK with the configuration, extra parameters and the handle to the callback method.
## Enrollments and Account Activities

### Enrollments

#### Enrollment Call

How to Call Enrollment Service

```javascript
//Take Enrollment Instance
const enrollment = CP.EnrollmentOption(sdkConfiguration, extraParams, returnCallBack);
//Start the SDK UI with mount id where UI can be rendered
enrollment.start('sdk-container');
```
Once a use case is called, the SDK will present the user interface for the consumer to key in the details. When the SDK completes the use case (either success or error scenario), the returnCallBack of the webpage will be fired. The result of the specific use case can be analyzed and used further by the Merchant web app.
```js
// This is the callback where sdk will post results
function returnCallBack(response) {
}
console.log('SDK response:', response);
// here you can handle the success or failure result
// failure - throw the error
// success - inform your server
```

#### Manual Enrollment

To call the Manual Enrollment use case
<<<<<<< HEAD

```javascript
=======
```js
>>>>>>> 3532121 (Updated Implementation Guide file and landing page)
const enrollment = CP.ManualEnrollment(sdkConfiguration, extraParams, returnCallBack);
//Start the SDK UI with mount id where UI can be rendered
enrollment.start('sdk-container');
```

#### Micro Deposit Validation

To call the Micro deposit Validation use case (typically after the Manual Enrollment when customer receives the micro deposit in his account), use the below code sample
<<<<<<< HEAD

```javascript
=======
```js
>>>>>>> 3532121 (Updated Implementation Guide file and landing page)
const manualDeposit = CP.ManualDeposit(sdkConfiguration, extraParams, returnCallBack);
//Start the SDK UI with mount id where UI can be rendered
manualDeposit.start('sdk-container');
```

#### Bank Login Enrollment

To call the Bank Login Enrollment use case with PayWithMyBank or AllData, use the below code
<<<<<<< HEAD

```javascript
=======
```js
>>>>>>> 3532121 (Updated Implementation Guide file and landing page)
const bankOnly = CP.BankOnly(sdkConfiguration, extraParams, returnCallBack);
//Start the SDK UI with mount id where UI can be rendered
bankOnly.start('sdk-container');
```

#### Special Enrollment - Choice
<<<<<<< HEAD

>Note: To call the Enrollment use case with both the options (to let customer choose either manual or bank login), use the below code sample:

```javascript
=======
*Note: To call the Enrollment use case with both the options (to let customer choose either manual or bank login), use the below code sample:*
```js
>>>>>>> 3532121 (Updated Implementation Guide file and landing page)
const enrollment = CP.EnrollmentOption(sdkConfiguration, extraParams, returnCallBack);
//Start the SDK UI with mount id where UI can be rendered
enrollment.start('sdk-container')
```

#### Streamlined Enrollment

To call Streamlined Enrollment use case, use below sample:
<<<<<<< HEAD

```javascript
=======
```js
>>>>>>> 3532121 (Updated Implementation Guide file and landing page)
const streamlinedEnrollment = CP.StreamlinedEnrollment(sdkConfiguration, extraParams,
returnCallBack);
//Start the SDK UI with mount id where UI can be rendered
streamlinedEnrollment.start('sdk-container');
```

#### Close Enrollment

To call the Close Enrollment use case, use the below code sample:

```javascript
const closeAccount = CP.CloseAccount(sdkConfiguration, extraParams, returnCallBack);
//Start the SDK UI with mount id where UI can be rendered
closeAccount.start('sdk-container');
```

### Account Activities

#### Relink Account

To call the relink use case, use the below sample: 
<<<<<<< HEAD

```javascript
=======
```js
>>>>>>> 3532121 (Updated Implementation Guide file and landing page)
const relink = CP.Relink(sdkConfiguration, extraParams, returnCallBack);
//Start the SDK UI with mount id where UI can be rendered
relink.start('sdk-container');
```

#### Account Validation

To call the Account Validation use case, use the below code sample:
<<<<<<< HEAD

```javascript
=======
```js
>>>>>>> 3532121 (Updated Implementation Guide file and landing page)
const accountValidation = CP.AccountValidation(sdkConfiguration, extraParams,
returnCallBack);
//Start the SDK UI with mount id where UI can be rendered
accountValidation.start('sdk-container');
```

#### Update Account

To call the Update Enrollment use case, use the below code sample:
<<<<<<< HEAD

```javascript
=======
```js
>>>>>>> 3532121 (Updated Implementation Guide file and landing page)
const updateEnrollment = CP.UpdateEnrollment(sdkConfiguration, extraParams,
returnCallBack);
//Start the SDK UI with mount id where UI can be rendered
updateEnrollment.start('sdk-container');
```

## Handling ConnectPay SDK Response

The generic response model will be a JSON object as shown below: 

```json
{
"transactionStatus":"APPROVED/ERROR/DECLINED", "transactionStatusCode":xxx,
"referenceTransactionID":"xxx",
"transactionStatusDescription":"xxx",
"responseVerbiage":"message to be shown by the user", "nonce":"89F0A5475A780018E0530xxxx", //may not be present for all responses "errorDetails":{
"errorCode":errCode "errorField":"fieldName", "errorReason":"Reason for the error",
} "customer":{
"fdCustomerID":"8c9633587xxxx" }
}
```

The transactionStatus will be either APPROVED, ERROR or DECLINED.
If there was an error, the errorDetails object will be included. The response Verbiage can also be used to display the error to the end user. Please refer the ConnectPay SDK Error Codes section of this document for detailed error codes and applicable descriptions.

## Extras

[ERROR CODE LIST](https://qa-developer.fiserv.com/product/ConnectPay/docs/?path=./documentation/statuscodes.md&branch=develop)
