# Bank Login Enrollment Architecture
## Explanation of Feature
This is the preferred method of consumer enrollment into ConnectPay
<!-- theme: danger 
>For uCom merchants, you will continue to Create Session Token as well as Initialize and launch ConnectPay SDK. However, you will want to follow the additional uCom steps section instead of additional steps:
-->
<p>
The consumer is presented with an option to login into his/her bank account using their bank username and password. Once the consumer logs in, authorizes the bank account he/she wants to use for this enrollment, and submits, ConnectPay fetches the consumer demographic and/or bank information from the bank using a secure backend connection and populates all the details on the consumers enrollment screen. The consumer will then verify all the details and edit them as he/she sees fit (except for bank account details) and submits the enrollment.
</p>
<p>
This method of enrollment is preferred because it is easier for a consumer to remember the bank username and password as opposed to routing and account number to be keyed in (manual enrollment process). Additionally this method of enrollment is, in most cases, instantly activated and the consumer is ready to transact once their enrollment is successful.
Sequence of activities for completing bank login enrollment:
</p>

## Implementation Steps: Bank Login Process
### Create Consumer Profile (If fdCustomerId not already present for the user) 
<p>

[Create Consumer Profile](https://qa-developer.fiserv.com/product/ConnectPay/docs/?path=./documentation/implementationguide.md&branch=develop)
</p>

### Create Session Token 
<p>

[Create Session Token](https://qa-developer.fiserv.com/product/ConnectPay/api/?type=post&path=/security/createsessiontoken&branch=develop&version=1.0.0)
</p>

### Initialize and Launch ConnectPay SDK 
You will want to go to the specific mobile operating section and look to initialize the App
<p>

[WebSDK](https://qa-developer.fiserv.com/product/ConnectPay/docs/?path=documentation/websdk.md&branch=develop)
</p>
<p>

[iOS]([(https://qa-developer.fiserv.com/product/ConnectPay/docs/?path=documentation/iossdk.md&branch=develop)
</p>
<p>

[Android]((https://qa-developer.fiserv.com/product/ConnectPay/docs/?path=documentation/androidsdk.md&branch=develop)
</p>

### Additional Steps
<p>Following are the steps to take to complete bank login</p>
<ol>
  <li>Pass necessary data to the SDK </li>
  <li>SDK presents the screens to the consumer to login into the bank </li>
  <li>Consumer logs in and authorizes a bank account and submits</li>
  <li>ConnectPay encrypts retrieved information and sends encrypted data back to SDK</li>
  <li>SDK decrypts the data and populates the details on the consumer enrollment screen</li>
  <li>Consumer verifies and edits information (except bank number) and submits data for enrollment</li>
  <li>SDK completes enrollment process and returns NONCE to merchantApp</li>
  <li>NONCE passed back to merchant server</li>
  <li>Merchant server does a server-to-server GetData call to retrieve fdAccountId generated after consumer data vaulting. Merchant receives the current consumer status as a part of this call</li>
  <li>Merchant server stores the fdCustomerId,fdAccountId(optional) against the `externalId` in their system for future use</li>
</ol>

### Additional uCOM Steps
<ol>
<li>Pass necessary data to the SDK (including uCom provided `fdCustomerId`)</li>
<li>SDK presents the screens to the consumer to login into the bank </li>
<li>Consumer logs in and authorizes a bank account and submits</li>
<li>ConnectPay fetches consumer demographic and bank information using a secure backend connection</li>
<li>ConnectPay encrypts retrieved information and sends encrypted data back to SDK</li>
<li>SDK decrypts the data and populates the details on the consumer enrollment screen</li>
<li>Consumer verifies and edits information (except bank number) and submits data for enrollment</li>
<li>SDK completes enrollment process and returns NONCE to merchant App</li>
<li>NONCE passed back to merchant server</li>
<li>Merchant server does a server-to-server GetData call to retrieve fdAccountId generated after consumer data vaulting. Merchant receives the current consumer status as a part of this call</li>
<li>Merchant server stores the `fdCustomerId`,`fdAccountId`(optional) against the `externalId` in their system for future use</li>
</ol>

### Issues with Integration
[Fiserv Implementation Support Team](mailto:DL-GBL-VASDelivery@fiserv.com)
<p>Image on the flow of the activity</p>
<center><img src="https://raw.githubusercontent.com/Fiserv/connect-pay/develop/assets/images/Online Bank Login Enrollment Architecture.png" alt="Bank Login Architecture" class="center"></center>

