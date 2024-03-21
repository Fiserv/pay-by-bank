# This will be the page for Android

## SDK Setup
Add following repositories in the project root build.gradle file.
```java
- google()
- mavenCentral() - jcenter()
- maven {
url 'https://gyftwallet.jfrog.io/gyftwallet/repo'
}
- flatDir {
dirs project(':app').file('libs')
}
```

## Dependencies

Add the following dependencies in the application: 
### Connect Pay Dependencies

```java
implementation 'com.firstdata.util:library:3.0.11'
implementation(name:'cpsdk-release-1.0.3.6', ext:'aar') 
implementation(name:'cpsdkexternal-release-1.0.3.6', ext:'aar') 
implementation(name:'paymentsdk-release-1.0.3.6', ext:'aar') 
implementation(name:'paywithmybank-android-sdk-2.2.1', ext:'aar') 
implementation(name:'TMXProfiling-RL-6.2-102', ext:'aar') 
implementation(name:'TMXProfilingConnections-RL-6.2-102', ext:'aar')
```

|Library|Version|Usage|
|-------|-------|-----|
|FirstData-Util|3.0.11|FirstData utility|
|cpsdkexternal|1.0.3.6|Client facing library acts as an entry point, exposed API's to the third party integrations|
|cpsdk|1.0.3.6|Library provides Connect-Pay specific implementation|
|payment-sdk|1.0.3.6|Core Payment library|
|paywithmybank-android-sdk|2.2.1|Pay with My Bank Library Integration|
|TMXProfiling-RL|6.2-102|Real-time Security|
|TMXProfilingCOnnections-RL|6.2-102|Real-time Security|

### External Support Dependencies
Need to write what the difference is between the two
```java
implementation "org.jetbrains.kotlin:kotlin-stdlib-jdk7:1.3.72" 
implementation "org.jetbrains.kotlin:kotlin-reflect:1.3.72"

implementation "org.koin:koin-core:2.0.1" 
implementation "org.koin:koin-core-ext:2.0.1" 
implementation "org.koin:koin-android:2.0.1"

implementation "androidx.constraintlayout:constraintlayout:2.0.1" 
implementation "androidx.navigation:navigation-fragment:2.3.0" 
implementation "androidx.navigation:navigation-ui-ktx:2.3.0" 
implementation "androidx.browser:browser:1.4.0"

implementation 'com.github.salomonbrys.kotson:kotson:2.5.0' 
implementation 'org.apache.commons:commons-text:1.8' 
implementation 'com.madgag.spongycastle:prov:1.54.0.0'

implementation 'com.github.wnameless:json-flattener:0.7.1' 
implementation 'commons-codec:commons-codec:1.12' 
implementation group: 'commons-io', name: 'commons-io', version: 2.6
```
|Library|Version|Usage|
|-------|-------|-----|
|kotlin|1.3.72|SDK-Development Language|
|koin|2.0.1|Dependency Injection|
|navigation|2.3.0|Android OS Navigation Framework|
|kotson|2.5.0|Json Utility|
|apache commons|1.8|Common Utility|
|spongycastle|1.54.0.0|Crypto Utility|
### Android Component depdendency

Place this in Android Manifest.xml
```xml

<activity 
    android:name="com.firstdata.sdk.ui.SDKActivity" 
    android:launchMode="singleTop" 
    android:theme="@style/FDSDKTheme">
        <intent-filter>
            <action android:name="android.intent.action.VIEW" />
            <category android:name="android.intent.category.DEFAULT" /> 
            <category android:name="android.intent.category.BROWSABLE" />
             <data android:scheme="cpsdk"
                android:host="bank.oauth"
                
                //This attribute's value must be unique(no space and special character) to identify the application and must start with "/" as in the following example.
                android:path="/cpsdksampleapp" /> 
    </intent-filter>
</activity>
```

## SDK Initialization
Prerequisite and steps involved to initialize the ConnectPay SDK:

```java
CPSDK ( 
    API_KEY,
    Environment,
    ApplicationContext, 
    DEBUG_LOGGING
)
```

|Parameter|Usage|
|---------|-----|
|API_KEY|Merchant’s API Key|
|ENVIRONMENT|Environment end Point for the CP-SDK|
|ApplicationContext|Application context|
|VERBOSE_DEBUG_LOGGING|Enable Debug logging(It should be set to false for production release)|

```java
Sample
val cpsdk = CPSDK ( 
                  webConfiguration.apiKey,
                  Environment.SANDBOX 
                  applicationContext,
                  true
        )

```

## Prerequisite - Connect Pay-Configuration

Create CPSDK client specific configuration required to launch the supported use cases object based on information received from the createSessionToken API call.

|Parameter|Usage|
|---------|-----|
|USE_CASE_CONFIG_ID|Unique ID to launch the specific use-case|
|FD_CUSTOMER_ID|(Optional) First data customer ID|
|SESSION_TOKEN|Session token|
|ENCRYPTION_KEY|Public key received as part of token generation process|
|API_KEY|Merchant’s API Key|
|DEEPLINK_PATH|Unique value to identify the application for OAuth process|
|POST_URL|(Optional) End point to be called after the use case completion|

Sample

```java
val cpConfiguration = CPConfiguration (
    webConfiguration.configId, // Unique ID specific to the selected CP-SDK use case 
    webConfiguration.fdCustomerId, // (Optional) FD-Customer ID 
    webConfiguration.accessToken, // Access token 
    webConfiguration.encryptionKey, // Encryption public key 
    webConfiguration.apiKey, // API-Key

    "/cpsdksampleapp", //It must be changed with the "android:path" attribute's value as defined in your AndroidManifest file(for the above example "/cpsdksampleapp").
    webConfiguration.postUrl // (Optional) URL to be called after the use-case completion. )
```

### Extra Parameters

Extra parameters to configure SDK with the pre-defined values:

```java
val extraParams = webConfiguration.extraParams
```

Extra Params for Enrollment sample:
(It is mandatory to pass all the required fields in extra params for Streamlined enrollment flow.)

```json
"firstName": "John",
"lastName": "Doe",
"email": "john@email.com",
"userPhone[0].primary": "Y",
"userPhone[0].number": "1234567890", "userPhone[0].type": "MOBILE",
"street": "1234 Road",
"street2": "", //optional
"city": "New York",
"state": "NY",
"postalCode": "12345",
"country": "USA",
"driverLicenseNumber": "12345678", //optional "driverLicenseState": "TX", //optional
"ssn": "123456789", //optional
"gender": "M", //optional
"pin": "1234", //optional
"dob": "20001225", //optional 
"sqnA[0].securityQuestion": "question1", //optional 
"sqnA[0].securityQuestionId": "1", //optional 
"sqnA[0].securityAnswer": "Test Answer", //optional 
"routingNumber": "123456789", 
"confirmRoutingNumber": "123456789", 
"accountNumber": "1234567890", 
"confirmAccountNumber": "1234567890", 
"connectPayPaymentNumber": "123456789012345", 
“genericFlag1”: “<Generic Flag1 (Y/N)”, //optional 
“genericFlag2”: “<Generic Flag2 (Y/N)”, //optional 
“genericFlag3”: “<Generic Flag3 (Y/N)”, //optional 
“genericCode1”: “<Generic Code1>”, //optional 
“genericCode2”: “<Generic Code2>”, //optional 
“genericCode3”: “<Generic Code3>”, //optional
“reportingField1”: “<Reporting Field1>”, //optional 
“reportingField2”: “<Reporting Field2>”, //optional 
“reportingField3”: “<Reporting Field3>”, //optional
```

### Configuration Call Back

Listener to listen the SDK use case initialization state with the give configuration. After the successful SDK initialization onSuccess callback will be called with the selected use case workflow object as argument. Using this object starts the workflow for the requested use case. In case of initialization error, the call back onError will be called with the error object as argument. End user application can handle the UI states in their application based on these callbacks.

```java
val configurationCallback = object: ConfigurationCallback<Workflow> { 
    
    override fun onSuccess(workflow: Workflow) {

        // Start the use case work flow
        workflow.start( context ) 
        
    }
    override fun onError(sdkError: CPSDKError) { 
        // Handle error here
    }
}
```

## SDK Use Case Integration

To integrate into a specific use case of the ConnectPay SDK, below steps needs to be followed.
Call the specific Use Case method exposed by the CP SDK class with the configuration, extra parameters, and the handle to the callback method. For example, the below code snippet shows how to call the manual enrollment use case.

```java
cpsdk.manualEnrollment( 
    cpConfiguration,
    extraParams,
    configurationCallback as ConfigurationCallback<ManualEnrollment>)
```

Once a use case is called, the SDK will present the user interface for the consumer to key in the details. When the SDK completes the use case (either success or error scenario), the onActivityResult of the parent activity will be fired. The result of the specific use case can be analyzed and used further by the Merchant mobile app.

```java
override fun onActivityResult(requestCode: Int, resultCode: Int, data: Intent?) { 
  super.onActivityResult(requestCode, resultCode, data) 
  parseOnActivityResult(requestCode, resultCode, data)?.also { cpsdkResult ->
    (cpsdkResult.result?.toString() ?:cpsdkResult.error?.toString())
        ?.also { Toast.makeText(this, it, Toast.LENGTH_LONG).show() }
}
```

## Enrollments and Account Activities

### Enrollments

#### Manual Enrollment

To call the Manual Enrollment Use Case, use the below code sample:

```java
cpsdk.manualEnrollment( 
    cpConfiguration,
    gson.fromJson(extraParams, EnrollmentRequest::class.java), 
    configurationCallback as ConfigurationCallback<ManualEnrollment>)
```

#### Micro Deposit Validation

To call the Micro deposit Validation (typically after the Manual Enrollment Use Case when customer receives the micro deposit in his/her account), use the below code sample:
```java

cpsdk.manualDeposit( 
    cpConfiguration,
    gson.fromJson(extraParams, AccountValidationRequest::class.java), 
    configurationCallback as ConfigurationCallback<ManualDeposit>)
```

#### Bank Login Enrollment

To call the Bank Login Enrollment Use Case with PayWithMyBank or AllData, use the below code sample:

```java
cpsdk.pwmbEnrollment( 
    cpConfiguration,
    gson.fromJson(extraParams, EnrollmentRequest::class.java), 
    configurationCallback as ConfigurationCallback<PWMBEnrollment>)
```

>Note: To call the Enrollment use case with both the options (to let customer choose either manual or bank login), use the below code sample:

```java
cpsdk.bothEnrollment( 
        cpConfiguration,
        gson.fromJson(extraParams, EnrollmentRequest::class.java), 
        configurationCallback as ConfigurationCallback<BothEnrollment>
```

#### Streamlined Enrollment

To call the Streamlined Enrollment Use Case with AllData, use the below code sample:
```java
cpsdk.streamLinedEnrollment( 
    cpConfiguration,
    gson.fromJson(extraParams, EnrollmentRequest::class.java), 
    configurationCallback as ConfigurationCallback<StreamLinedEnrollment>)
```

#### Close Enrollment

To call the Close Enrollment use case, use the below code sample:

```java
cpsdk.closeAccount( 
    cpConfiguration,
    gson.fromJson(extraParams, CloseAccountRequest::class.java), 
    configurationCallback as ConfigurationCallback<CloseAccount>)
```

### Account Activities

#### Relink Account

To call the Relink Account Use Case, use the below code sample:

```java
cpsdk.relinkAccount( 
    cpConfiguration,
    gson.fromJson(extraParams, RelinkAccountRequest::class.java), 
    configurationCallback as ConfigurationCallback<RelinkAccount>)

```

#### Account Validation

To call the Account Validation Use Case, use the below code sample:

```java
cpsdk.accountValidation( 
    cpConfiguration,
    gson.fromJson(extraParams, AccountValidationRequest::class.java), 
    configurationCallback as ConfigurationCallback<AccountValidation>)
```

#### Update Account

To call the Update Enrollment use case, use the below code sample:

```java
cpsdk.updateEnrollment( 
    cpConfiguration,
    gson.fromJson(extraParams, EnrollmentRequest::class.java), 
    configurationCallback as ConfigurationCallback<UpdateEnrollment>)
```
## Extras

>If you experience Errors while developing, you will want to utilize our API Explorer (on the left) in the sample request and responses so that you can see the desired errors and why. 