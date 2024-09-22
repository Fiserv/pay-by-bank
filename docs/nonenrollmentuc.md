# Non-enrollment Architecture

## Explanation of Feature

This section would cover business use cases like Micro Deposit Validation,Consumer Updates (other than ConnectPayPaymentNumber updates) and ACH account closure.

### Create Session Token 
[Create Session Token](?path=./docs/implementationguide.md)
>Note: See section labeled Create Session Token

>For uCom merchants, you will continue to Create Session Token as well as Initialize and launch ConnectPay SDK. However, you will want to follow the additional uCom steps section instead of additional steps:
[uCOM](https://developer.fiserv.com/product/ConnectedCommerce/docs/?path=docs/documentation/Standard_Implementation_Guide.md)

### Initialize and Launch ConnectPay SDK

You will want to go to the specific mobile operating section and look to initialize the App


[WebSDK](?path=./docs/websdk.md)

[iOS](?path=./docs/iossdk.md)

[Android](?path=./docs/androidsdk.md)

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

### Image of Flow
<center><img src="https://raw.githubusercontent.com/Fiserv/connect-pay/develop/assets/images/Non-Enrollment Architecture.png" alt="Non Enrollment Architecture" class="center"></center>
