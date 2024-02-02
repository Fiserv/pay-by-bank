#  IOS – Mobile SDK Integration
<<<<<<< HEAD

=======
>>>>>>> 3532121 (Updated Implementation Guide file and landing page)
Utilize this guide for your SDK Integration with Apple iOS

## General Setup

Drag and drop the provided Universal Binary (.framework file) into your project structure (you can drop this framework anywhere into your Xcode Project. Ideally, you would drop it into your "Frameworks" directory where your other frameworks exist.)

<<<<<<< HEAD

>Note: During your drag and drop, Xcode will prompt you to configure whether the binary should live within your project structure as a copy or simply have a reference to the binary outside of your project structure. We want to ensure you have a deep copy of the binary in your project and not just a reference.

=======
*Note: During your drag and drop, Xcode will prompt you to configure whether the binary should live within your project structure as a copy or simply have a reference to the binary outside of your project structure. We want to ensure you have a deep copy of the binary in your project and not just a reference.*
>>>>>>> 3532121 (Updated Implementation Guide file and landing page)
## General Setup Part 2

Ensure that the PaymentSDK Universal binary is linked and embedded, navigate to your target settings and ensure that the binary appears under the "Embedded Binaries" and "Linked Frameworks and Libraries" section. (If you don't see the PaymentSDK Universal library listed there, you can use the "+" button to manually embed and link the binary for your target).

## Configuration
### Step 1 Import
t
Import the ConnectPay SDK

```ios
import "PaymentSDK/PaymentSDK.h" 
```

### Step 1 Initialize

Initialize the SDK with required information
```ios

CPSDK *cpSdk = [[CPSDK alloc] initWithApiKey:<API_KEY> andEnvironment:EnvironmentSandbox];
```

### Create ConnectPay Configuration

```ios
CPSdkConfiguration *configuration = [[CPSdkConfiguration alloc] initWithFdCustomerId:<FD_CUSTOMER_ID> encryptionKey:<ENCRYPTION_KEY> accessToken:<ACCESS_TOKEN>
configId:<CONFIG_ID> andPostUrl:<POST_URL>];
```
## Use Case Integration

Integrate into a specific use case of the ConnectPay SDK.

>Note:Define any extraParam/default parameters to be passed into the Use Case as shown below: (It is mandatory to pass all the required fields in extra params for Streamlined enrollment flow.)

```json
ManualEnrollmentConfiguration *extraParams = [[ManualEnrollmentConfiguration alloc] init]; extraParams.routingNumber = <ROUTING_NUMBER>;
extraParams.accountNumber = <BANK_ACCOUNT_NUMBER>; extraParams.accountType = <ACCOUNT_TYPE>;
extraParams.cpCardNumber = <CP_CARD_NUMBER>; extraParams.firstName = <FIRST_NAME>;
extraParams.lastName = <LAST_NAME>;
extraParams.email = <EMAIL>;
extraParams.streetAddress = <STREET_ADDRESS>; extraParams.apartmentNumber = <APARTMENT_NUMBER>; //optional extraParams.city = <CITY>;
extraParams.state = <STATE>;
extraParams.zipCode = <ZIP_CODE>;
extraParams.driversLicense = <DRIVERS_LICENSE>; //optional 
extraParams.driversLicenseIssuingState = <DRIVERS_LICENSE_ISSUING_STATE>; //optional 
extraParams.ssn = <SSN>; //optional
extraParams.gender = <GENDER>; //optional
extraParams.dob = <DOB>; //optional
extraParams.pin = <PIN>; //optional
extraParams.newPin = <NEW_PIN>; //optional
extraParams.memberSince = <MEMBER_SINCE>; //optional
extraParams.supplementalId = <SUPPLEMENTAL_ID>; //optional 
PhoneNumberConfiguration *phoneConfiguration = [[PhoneNumberConfiguration alloc] init]; 
phoneConfiguration.phoneNumber = <PHONE_NUMBER>;
phoneConfiguration.type = <PHONE_TYPE>;
phoneConfiguration.isPrimary = < Y/N >;
extraParams.phoneNumbers = < phoneConfiguration >;
extraParams.supplementalId = <SUPPLEMENTAL_ID>; //optional
extraParams.genericFlag1 = <GENERIC_FLAG(Y/N)>; // optional
extraParams.genericFlag2 = <GENERIC_FLAG(Y/N)>; // optional
extraParams.genericFlag3 = <GENERIC_FLAG(Y/N)>; // optional
extraParams.genericCode1 = <GENERIC_CODE1>; // optional
extraParams.genericCode2 = <GENERIC_CODE2>; // optional
extraParams.genericCode3 = <GENERIC_CODE3>; // optional
extraParams.reportingField1 = <REPORTING_FIELD1>; // optional 
extraParams.reportingField2 = <REPORTING_FIELD2>; // optional 
extraParams.reportingField3 = <REPORTING_FIELD3>; // optional
```

## Enrollments and Account Activities

### Enrollments

#### Manual Enrollment

Call the specific use case method exposed by the CP SDK class with the configuration, extra parameters and the handle to the callback method. For example, the below code snippet shows how to call the manual enrollment use case:

```ios
ManualEnrollment *manualEnrollment = [cpSdk manualEnrollmentWithCpSdkConfiguration:configuration andExtraParams:extraParams];
[manualEnrollment startWithCompletionHandler:<PASS_YOUR_BLOCK_HERE>];
```

Once a use case is called, the SDK will present the user interface for the consumer to key in the details. When the SDK completes the result of the specific use case (either success or error scenario) it is passed to the completion handler of the start method. Refer to the response section to see the structure of this response object.

#### Micro Deposit Validation

To call the Micro Deposit Validation use case (typically after the Manual Enrollment Use Case when customer receives the micro deposit in his account)

```ios
ManualDeposit *manualDeposit = [cpSdk manualDepositWithCpSdkConfiguration:configuration andManualDepositConfiguration:manualDepositConfiguration];
[manualDeposit startWithCompletionHandler:<PASS_YOUR_BLOCK_HERE>];
```

#### Bank Login Enrollment

To call the Bank Login Enrollment use case with PayWithMyBank or AllData, use the below code

```ios
ManualEnrollment *manualEnrollment = [cpSdk manualEnrollmentWithCpSdkConfiguration:configuration andManualEnrollmentConfiguration:manualEnrollmentConfiguration];
[manualEnrollment startWithCompletionHandler:<PASS_YOUR_BLOCK_HERE>];
```
 
>Note: To call the Enrollment use case with both the options (to let customer choose either manual or bank login), use the below code sample:

```ios
ManualEnrollment *manualEnrollment = [cpSdk manualEnrollmentWithCpSdkConfiguration:configuration andManualEnrollmentConfiguration:manualEnrollmentConfiguration];
[manualEnrollment startWithCompletionHandler:<PASS_YOUR_BLOCK_HERE>];
```

#### Streamlined Enrollment

To call the Streamlined Enrollment Use Case with AllData, use the below code sample:

```ios
StreamlinedEnrollmentConfiguration *extraParams = [[StreamlinedEnrollmentConfiguration alloc] init];
StreamlinedEnrollment *streamlinedEnrolment = [cpSdk streamlinedEnrollmentWithCpSdkConfiguration:configuration andStreamlinedEnrollmentConfiguration: extraParams];
[streamlinedEnrolment startWithCompletionHandler:<PASS_YOUR_BLOCK_HERE>];
```

#### Close Enrollment

To call the Close Enrollment

```ios
CloseAccount *closeAccount = [cpSdk closeAccountWithCpSdkConfiguration:configuration andCloseAccountConfiguration:closeAccountConfiguration];
[closeAccount startWithCompletionHandler:<PASS_YOUR_BLOCK_HERE>];
```

### Account Activities

#### Relink Account

To call the Relink Account Use Case

```ios
RelinkEnrolmentConfiguration *relinkConfiguration = [[RelinkEnrolmentConfiguration alloc] init];
RelinkEnrolment *relinkAccount = [cpSdk relinkEnrolmentWithCpSdkConfiguration:configuration andRelinkEnrolmentConfiguration:relinkConfiguration];
[relinkAccount startWithCompletionHandler:<PASS_YOUR_BLOCK_HERE>];
```

#### Account Validation

To call the Account Validation use case:

```ios
AccountValidation *accountValidation = [cpSdk accountValidationWithCpSdkConfiguration:configuration andAccountValidationConfiguration:accountValidationConfiguration];
```

#### Update Account

To call Update Enrollment:

```ios
UpdateEnrollment *updateEnrollment = [cpSdk updateEnrollmentWithCpSdkConfiguration:configuration andUpdateEnrollmentConfiguration:manualEnrollmentConfiguration];
[updateEnrollment startWithCompletionHandler:<PASS_YOUR_BLOCK_HERE>];
```

<script>
  // Function to copy text to clipboard
  function copySnippet(snippetId) {
    var snippet = document.getElementById(snippetId);
    var textarea = document.createElement('textarea');
    textarea.textContent = snippet.textContent;
    document.body.appendChild(textarea);
    textarea.select();
    document.execCommand('copy');
    document.body.removeChild(textarea);
    alert('Snippet copied to clipboard!');
  }
</script>


## Extras

[ERROR CODE LIST](https://qa-developer.fiserv.com/product/ConnectPay/docs/?path=./documentation/statuscodes.md&branch=develop)
