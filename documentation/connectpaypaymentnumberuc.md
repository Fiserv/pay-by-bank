# ConnectPay Payment Number update
## Explanation of Feature

ConnectPayPaymentNumber update generates a new `fdAccountId`, which is different than other updates to consumer information and needs to be called out. At the end of the ConnectPayPaymentNumber update, the merchant needs to update their record with the new `fdAccountId` for the payment instrument.
 
>Only for uCom merchants, you will continue to Create Session Token as well as Initialize and launch ConnectPay SDK. However, you will want to follow the additional uCom steps section instead of additional steps.

## Implementation Steps: Bank Login Process
### Create Session Token 

[Create Session Token](https://qa-developer.fiserv.com/product/ConnectPay/api/?type=post&path=/security/createsessiontoken&branch=develop&version=1.0.0)


### Initialize and Launch ConnectPay SDK 
You will want to go to the specific mobile operating section and look to initialize the App

[WebSDK](https://qa-developer.fiserv.com/product/ConnectPay/docs/?path=documentation/websdk.md&branch=develop)
[iOS](https://qa-developer.fiserv.com/product/ConnectPay/docs/?path=documentation/iossdk.md&branch=develop)
[Android](https://qa-developer.fiserv.com/product/ConnectPay/docs/?path=documentation/androidsdk.md&branch=develop)

### Additional Steps
<ol>
  <li>Pass necessary data to the SDK(including `fdCustomerId`)</li>
  <li>SDK presents the screens to consumer to capture consumer information</li>
  <li>SDK completes update process and returns NONCE to merchantApp</li>
  <li>NONCE passed back to merchant server</li>
  <li>Merchant server does a server-to-server GetData call to retrieve fdAccountId generated after consumer data update</li>
  <li>Merchant server stores/updates the new fdAccountId against the externalId,for the payment instrument in question, in their system for future use</li>
</ol>

### Additional uCOM Steps
<ol>
  <li>Pass necessary data to the SDK(including uCom provided `fdCustomerId`)</li>
  <li>SDK presents the screens to consumer to capture consumer information</li>
  <li>SDK completes update process and returns NONCE to merchantApp</li>
  <li>NONCE passed back to merchant server</li>
  <li>Merchant server does a server-to-server GetData call to retrieve fdAccountId generated after consumer data update</li>
  <li>Merchant server stores/updates the new fdAccountId against the externalId,for the payment instrument in question, in their system for future use</li>
</ol>

### Issues with Integration
[Fiserv Implementation Support Team](mailto:DL-GBL-VASDelivery@fiserv.com)
<center><img src="https://raw.githubusercontent.com/Fiserv/connect-pay/develop/assets/images/Payment Number Architecture.png" alt="ConnectPay Payment Number Update" class="center"></center>
