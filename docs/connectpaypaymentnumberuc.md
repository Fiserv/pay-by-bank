# ConnectPay Payment Number update

## Explanation of Feature

ConnectPayPaymentNumber update generates a new `fdAccountId`, which is different than other updates to consumer information and needs to be called out. At the end of the ConnectPayPaymentNumber update, the merchant needs to update their record with the new `fdAccountId` for the payment instrument.


>Note: Only for uCom merchants, you will continue to Create Session Token as well as Initialize and launch ConnectPay SDK. However, you will want to follow the additional uCom steps section instead of additional steps.

## Implementation Steps: Bank Login Process
### Create Session Token 
[Create Session Token](?path=./docs/implementationguide.md)
>Note: See section labeled Create Session Token

### Initialize and Launch PaybyBank SDK 


>Only for uCom merchants, you will continue to Create Session Token as well as Initialize and launch ConnectPay SDK. However, you will want to follow the additional uCom steps section instead of additional steps.

[WebSDK](?path=./docs/websdk.md)

[iOS](?path=./docs/iossdk.md)

[Android](?path=./docs/androidsdk.md)

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

### Image of Flow
<center><img src="https://raw.githubusercontent.com/Fiserv/connect-pay/develop/assets/images/Payment Number Architecture.png" alt="ConnectPay Payment Number Update" class="center"></center>
