# Architecture and Flows 

UNKNOWN WHAT I WANT TO DO

## Introduction to Important Calls in ConnectPay Architecture
The below calls are used in most of the ConnectPay use cases. An overall understanding of these calls is required before doing a deep dive into each use case. Technical details of these calls can be found in later sections of this document.
### Step 1 Create Consumer Profile:
The first step in the enrollment process is to create the fdCustomerId.
Follow this link for specific details on configuration <LINK>
### Step 2 Create Session Token:
For all functionalities in ConnectPay, the merchant’s server needs to make a server-to-server call to ConnectPay to get a Public Encryption Key and Session Token. The Public Encryption Key would be used in the payload encryption process described later in the document. The Session Token (OAuth2 Token) is a time-limited (10 Minutes duration) token which is sent back to the merchant’s server.
The merchant’s server needs to pass the Public Encryption Key and Session Token to the ConnectPay SDK. The SDK uses the Session Token to authorize itself with ConnectPay for the functional flows and uses the Public Encryption Key for the full payload encryption before the transmission over the network.
Follow this link for specific details on configuration <LINK>
### Step 3 SDK use cases:
The ConnectPay SDK comes in three flavors, IOS, Android, and Web. The SDK should be included into Merchant’s App. When a ConnectPay business use case like Consumer Enrollment, Micro Deposit Validation, Consumer Profile Load from backend, Consumer Updates, and ACH account closure are performed, the Merchant’s App needs to initialize the proper ConnectPay SDK use case and pass necessary data. SDK would do all the orchestration with the ConnectPay backend to complete the business use case.
In case of Consumer Enrollments, Consumer Profile Load, /ConnectPay Payment Number updates, ConnectPay sends back a NONCE as part of the response.

*Note: Since fdAccountId is a unique token representing the consumer’s actual payment information, for security reasons this information is not sent back to the SDK/Mobile App. Instead, this information needs to be retrieved by using a NONCE over a secure server-to-server communication channel.*

#### Integration
Utilize These pages 
IOS 
WEBOS
ANDROID 


### USE CASES

