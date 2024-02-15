# Non-enrollment Architecture
## Explanation of Feature
<p>
This section would cover business use cases like Micro Deposit Validation,Consumer Updates (other than ConnectPayPaymentNumber updates) and ACH account closure.
</p>

<!-- theme: danger 
>For uCom merchants, you will continue to Create Session Token as well as Initialize and launch ConnectPay SDK. However, you will want to follow the additional uCom steps section instead of additional steps:
-->

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

[iOS](https://qa-developer.fiserv.com/product/ConnectPay/docs/?path=documentation/iossdk.md&branch=develop)
</p>
<p>

[Android](https://qa-developer.fiserv.com/product/ConnectPay/docs/?path=documentation/androidsdk.md&branch=develop)
</p>

### Additional Steps
<ol>
  <li>Pass necessary data to the SDK(including fdCustomerId)</li>
  <li>SDK presents the screens to consumer to capture consumer information</li>
  <li>SDK completes update process and displays response to consumer</li>
</ol>

### Additional uCOM Steps
<ol>
  <li>Pass necessary data to the SDK(including uCom provided fdCustomerId)</li>
  <li>SDK presents the screens to consumer to capture consumer information</li>
  <li>SDK completes update process and displays response to consumer</li>
</ol>

### Issues with Integration
[Fiserv Implementation Support Team](mailto:DL-GBL-VASDelivery@fiserv.com)
<p>Image on the flow of the activity</p>
<center><img src="https://raw.githubusercontent.com/Fiserv/connect-pay/develop/assets/images/Non-Enrollment Architecture.png" alt="Non Enrollment Architecture" class="center"></center>