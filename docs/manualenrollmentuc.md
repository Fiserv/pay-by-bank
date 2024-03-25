# Manual Enrollment Architecture
## Explanation of Feature
<p>
The consumer has an option to manually key in all information required for ConnectPay enrollment into the enrollment screen.
</p>
<p>
Usually after a manual enrollment, two micro deposits are made to the consumer’s bank account. The consumer waits for 1-3 business days for these micro deposits to appear in their bank account, following which he/she needs to validate their account by answering micro deposit amount questions via the Micro Deposit Validation process.
</p>
<p>
The consumer is in a pending validation status and will not be able to transact until the validation is completed.
</p>

## Implementation Steps: Manual Enrollment
### Create Consumer Profile (If fdCustomerId not already present for the user) 

[Create Consumer Profile](?path=./docs/implementationguide.md)

### Create Session Token 
[Create Session Token](?path=./docs/implementationguide.md)
>Note: See section labeled Create Session Token

### Initialize and Launch ConnectPay SDK 
You will want to go to the specific mobile operating section and look to initialize the App

[WebSDK](?path=./docs/websdk.md)

[iOS](?path=./docs/iossdk.md)

[Android](?path=./docs/androidsdk.md)

### Additional Steps
<ol>
  <li>Pass necessary data to the SDK(including `fdCustomerId`)</li>
  <li>SDK presents the screens to consumer to capture consumer information</li>
  <li>SDK completes enrollment process and returns NONCE to merchantApp</li>
  <li>NONCE passed back to merchant server</li>
  <li>Merchant server does a server-to-server GetData call to retrieve `fdAccountId` generated after consumer data vaulting. Merchant additionally receives the current consumer status as a part of this call</li>
  <li>Merchant server stores the `fdCustomerId`, `fdAccountId` (optional) against the externalId in their system for future use</li>
</ol>

<!-- theme: danger 
Note: Merchant server stores the fdCustomerId, fdAccountId (optional) against the externalID in their system for future use.
-->

### Issues with Integration
[Fiserv Implementation Support Team](mailto:DL-GBL-VASDelivery@fiserv.com)
<p>Image on the flow of the activity</p>
<center><img src="https://raw.githubusercontent.com/Fiserv/connect-pay/develop/assets/images/Manual Enrollment Arch.png" alt="Manual Enrollment Architecture" class="center"></center>