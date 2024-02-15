# Error Codes 
 Listed Below are common codes being returned in Connect Pay. 

|Service|Endpoint| HTTP Status Code | Transaction Status Code | Transaction Status Description | Transaction Error Code | Transaction Error Description | Field Name|
|-------|--------|------------------|-------------------------|--------------------------------|------------------------|-------------------------------|-----------|
|TRANSACTIONS|AUTHORIZE|200|0|Approved||||
|TRANSACTIONS|AUTHORIZE|200|0|Approved Preferred||||
|TRANSACTIONS|AUTHORIZE|200|0|Adjustment accepted for processing||||
|TRANSACTIONS|AUTHORIZE|200|0|Approved but Issued on a Function Z||||
|TRANSACTIONS|AUTHORIZE|200|0|Approved but no Guarantee for it Being Settled||||
|TRANSACTIONS|AUTHORIZE|200|0|The transactions has verified approval and has been accepted||||
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1010|Field did not have a valid format|type|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1010|Field did not have a valid format|amount|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1010|Field did not have a valid format|connectPaymentNumber|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1010|Field did not have a valid format|currencyCode|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1010|Field contained a bad value|SubscriberID|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1010|Field did not have a valid format|fdAccountID|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1010|Field did not have a valid format|pinData|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1010|Field did not have a valid format|merchantTransactionId|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1010|Field did not have a valid format|splitShipmentFlag|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1010|Field did not have a valid format|productCode|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1020|Field contained a bad value|type|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1020|Field contained a bad value|amount|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1020|Field contained a bad value|connectPaymentNumber|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1020|Field contained a bad value|currencyCode|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1020|Field contained a bad value|fdAccountID|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1020|Field contained a bad value|pinData|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1020|Field contained a bad value|merchantTransactionId|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1020|Field contained a bad value|splitShipmentFlag|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1030|Required field did not have a value|PassPhase|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1030|Required field did not have a value|InitializationVector|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1030|Required field did not have a value|fdCustomerID|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1030|Required field did not have a value|type|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1030|Required field did not have a value|amount|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1030|Required field did not have a value|connectPaymentNumber|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1030|Required field did not have a value|currencyCode|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1030|Required field did not have a value|SubscriberID|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1030|Required field did not have a value|fdAccountID|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1030|Required field did not have a value|pinData|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1030|Required field did not have a value|merchantTransactionId|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1035|Required field is missing|PassPhase|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1035|Required field is missing|InitializationVector|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1035|Required field is missing|fdCustomerID|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1035|Required field is missing|type|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1035|Required field is missing|amount|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1035|Required field is missing|connectPaymentNumber|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1035|Required field is missing|currencyCode|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1035|Required field is missing|SubscriberID|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1035|Required field is missing|fdAccountID|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1035|Required field is missing|pinData|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1035|Required field is missing|merchantTransactionId|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1035|Required field is missing|accountNumber|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1035|Required field is missing|routingNumber|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1040|Required block did not have a value|customer|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1040|Required block did not have a value|account|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1040|Required block did not have a value|transactionDetails|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1045|Required block is missing|customer|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1045|Required block is missing|account|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1045|Required block is missing|transactionDetails|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1045|Required block is missing|partner|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1060|Required Header Field is missing|PartnerID|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1060|Required Header Field is missing|Client-Token|
|TRANSACTIONS|AUTHORIZE|400|100|Input is invalid|1080|Block contain values more than that is allowed|account|
|TRANSACTIONS|AUTHORIZE|400|140|Customer profile not found|2220|Customer profile not found|fdCustomerID|
|TRANSACTIONS|AUTHORIZE|400|150|Account detail not found|2310|Account detail not found|fdAccountID|
|TRANSACTIONS|AUTHORIZE|401|401|Unauthorized|4550|Partner is not opt for this service|PartnerID|
|TRANSACTIONS|AUTHORIZE|401|401|Unauthorized|4980|Payment Transaction ID is not Valid|ConfigurationError|
|TRANSACTIONS|AUTHORIZE|400|420|NON_F2F_ACCOUNT|4130|Partner is not Configure for the NF2F|ConFiguration Issue|
|TRANSACTIONS|AUTHORIZE|400|420|Unauthorized|4250|Session time out|Client-Token|
|TRANSACTIONS|AUTHORIZE|400|450|Partner Not Found|4500|PartnerID not Found|PartnerID|
|TRANSACTIONS|AUTHORIZE|500|500|General Error|5110|Please try again after some time, If issue persist please contact customer support|UCOMM_CLEAR_DATA|
|TRANSACTIONS|AUTHORIZE|500|500|General Error|5340|Configuration Error, Please contact customer support|AES|
|TRANSACTIONS|AUTHORIZE|500|500|General Error|5340|Configuration Error, Please contact customer support|PublicKey Expired|
|ONLINEBANKLOGIN|CPAPI_BANK_ESTABLISH|200|0|OK||||
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1010|Field did not have a valid format|type|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1010|Field did not have a valid format|fdCustomerID|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1010|Field did not have a valid format|PassPhase|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1010|Field did not have a valid format|InitializationVector|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1010|Field did not have a valid format|adapter|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1020|Field contained a bad value|fdCustomerID|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1020|Field contained a bad value|type|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1020|Field contained a bad value|PassPhase|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1020|Field contained a bad value|InitializationVector|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1020|Field contained a bad value|adapter|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1030|Required field did not have a value|type|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1030|Required field did not have a value|CallType|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1030|Required field did not have a value|fdCustomerID|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1030|Required field did not have a value|PassPhase|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1030|Required field did not have a value|InitializationVector|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1030|Required field did not have a value|adapter|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1030|Required field did not have a value|AllDataSessionId|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1035|Required field is missing|type|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1035|Required field is missing|CallType|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1035|Required field is missing|fdCustomerID|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1035|Required field is missing|PassPhase|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1035|Required field is missing|InitializationVector|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1035|Required Block is missing|allData|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1035|Required Block is missing|adapter|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1040|Required block did not have a value|customer|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Required block did not have a value|1040|Required block did not have a value|adapter|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1045|Required block is missing|customer|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1045|Required block is missing|account|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1060|Required Header Field is missing|PartnerID|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1060|Required Header Field is missing|SubscriberId|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1060|Required Header Field is missing|Client-Token|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1080|Block contain values more than that is allowed|account|
|ONLINEBANKLOGIN|ESTABLISH|400|140|Customer profile not found|2220|Customer profile not found|fdCustomerID|
|ONLINEBANKLOGIN|ESTABLISH|400|140|Customer profile not found|2220|Customer profile not found|fdCustomerID|
|ONLINEBANKLOGIN|ESTABLISH|401|401|Unauthorized|4550|Partner is not opt for this service|PartnerID|
|ONLINEBANKLOGIN|ESTABLISH|400|420|Unauthorized|4250|Session time out|Client-Token|
|ONLINEBANKLOGIN|ESTABLISH|400|440|Other Telecheck Decline|4410|alldatanotenabled|alldatanotenabled|
|ONLINEBANKLOGIN|ESTABLISH|400|450|Partner Not Found|4500|PartnerID not Found|PartnerID|
|ONLINEBANKLOGIN|ESTABLISH|500|500|General Error|5110|Please try again after some time, If issue persist please contact customer support|UCOMM_CLEAR_DATA|
|ONLINEBANKLOGIN|ESTABLISH|500|500|General Error|5340|Configuration Error, Please contact customer support|PublicKey Expired|
|ONLINEBANKLOGIN|ESTABLISH|500|500|General Error||||
|ONLINEBANKLOGIN|ESTABLISH|200|0|OK||||
|ONLINEBANKLOGIN|ESTABLISH|200|0|OK||||
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1010|Field did not have a valid format|fdCustomerID|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1010|Field did not have a valid format|type|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1010|Field did not have a valid format|PassPhase|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1010|Field did not have a valid format|InitializationVector|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1010|Field did not have a valid format|adapter|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1020|Field contained a bad value|fdCustomerID|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1020|Field contained a bad value|type|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1020|Field contained a bad value|PassPhase|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1020|Field contained a bad value|InitializationVector|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1020|Field contained a bad value|adapter|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1030|Required field did not have a value|fdCustomerID|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1030|Required field did not have a value|type|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1030|Required field did not have a value|CallType|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1030|Required field did not have a value|PassPhase|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1030|Required field did not have a value|InitializationVector|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1030|Required field did not have a value|adapter|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1030|Required field did not have a value|AllDataSessionId|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1035|Required field is missing|fdCustomerID|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1035|Required field is missing|type|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1035|Required field is missing|CallType|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1035|Required field is missing|PassPhase|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1035|Required field is missing|InitializationVector|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1035|Required Block is missing|allData|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1035|Required Block is missing|adapter|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1040|Required block did not have a value|customer|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Required block did not have a value|1040|Required block did not have a value|adapter|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid|1045|Required block is missing|customer|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1045|Required block is missing|account|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1060|Required Header Field is missing|PartnerID|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1060|Required Header Field is missing|SubscriberId|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1060|Required Header Field is missing|Client-Token|
|ONLINEBANKLOGIN|ESTABLISH|400|100|Input is invalid |1080|Block contain values more than that is allowed|account|
|ONLINEBANKLOGIN|ESTABLISH|400|140|Customer profile not found|2220|Customer profile not found|fdCustomerID|
|ONLINEBANKLOGIN|ESTABLISH|401|401|Unauthorized|4550|Partner is not opt for this service|PartnerID|
|ONLINEBANKLOGIN|ESTABLISH|400|420|Account not ACH-able|4200|Field contained a bad value|OnlineBankTransactionId|
|ONLINEBANKLOGIN|ESTABLISH|400|420|Unauthorized|4250|Session time out|Client-Token|
|ONLINEBANKLOGIN|ESTABLISH|400|440|Other Telecheck Decline|4410|Field contained a bad value|OnlineBankTransactionId|
|ONLINEBANKLOGIN|ESTABLISH|400|440|Other Telecheck Decline|4410|alldatanotenabled|alldatanotenabled|
|ONLINEBANKLOGIN|ESTABLISH|400|450|Partner Not Found|4500|PartnerID not Found|PartnerID|
|ONLINEBANKLOGIN|ESTABLISH|500|500|General Error|5110|Please try again after some time, If issue persist please contact customer support|UCOMM_CLEAR_DATA|
|ONLINEBANKLOGIN|ESTABLISH|500|500|General Error|5340|Configuration Error, Please contact customer support|PublicKey Expired|
|ONLINEBANKLOGIN|ESTABLISH|500|500|General Error||||
|TRANSACTIONS|CAPTURE|200|0|Approved||||
|TRANSACTIONS|CAPTURE|200|0|Approved Preferred||||
|TRANSACTIONS|CAPTURE|200|0|Adjustment accepted for processing||||
|TRANSACTIONS|CAPTURE|200|0|Approved but Issued on a Function Z||||
|TRANSACTIONS|CAPTURE|200|0|Approved but no Guarantee for it Being Settled||||
|TRANSACTIONS|CAPTURE|200|0|The transactions has verified approval and has been accepted||||
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1010|Field did not have a valid format|type|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1010|Field did not have a valid format|amount|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1010|Field did not have a valid format|connectPaymentNumber|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1010|Field did not have a valid format|currencyCode|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1010|Field contained a bad value|SubscriberID|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1010|Field did not have a valid format|fdAccountID|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1010|Field did not have a valid format|merchantTransactionId|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1010|Field did not have a valid format|splitShipmentFlag|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1010|Field did not have a valid format|splitShipmentId|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1010|Field did not have a valid format|productCode|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1020|Field contained a bad value|type|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1020|Field contained a bad value|amount|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1020|Field contained a bad value|connectPaymentNumber|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1020|Field contained a bad value|currencyCode|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1020|Field contained a bad value|fdAccountID|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1020|Field contained a bad value|merchantTransactionId|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1020|Field contained a bad value|splitShipmentFlag|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1020|Field contained a bad value|splitShipmentId|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1030|Required field did not have a value|PassPhase|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1030|Required field did not have a value|InitializationVector|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1030|Required field did not have a value|fdCustomerID|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1030|Required field did not have a value|type|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1030|Required field did not have a value|amount|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1030|Required field did not have a value|connectPaymentNumber|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1030|Required field did not have a value|currencyCode|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1030|Required field did not have a value|SubscriberID|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1030|Required field did not have a value|fdAccountID|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1030|Required field did not have a value|merchantTransactionId|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1030|Required field did not have a value|splitShipmentId|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1035|Required field is missing|PassPhase|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1035|Required field is missing|InitializationVector|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1035|Required field is missing|fdCustomerID|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1035|Required field is missing|type|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1035|Required field is missing|amount|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1035|Required field is missing|connectPaymentNumber|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1035|Required field is missing|currencyCode|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1035|Required field is missing|SubscriberID|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1035|Required field is missing|fdAccountID|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1035|Required field is missing|merchantTransactionId|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1035|Required field is missing|splitShipmentId|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1035|Required field is missing|accountNumber|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1035|Required field is missing|routingNumber|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1040|Required block did not have a value|customer|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1040|Required block did not have a value|account|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1040|Required block did not have a value|transactionDetails|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1045|Required block is missing|customer|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1045|Required block is missing|account|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1045|Required block is missing|transactionDetails|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1045|Required block is missing|partner|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1060|Required Header Field is missing|PartnerID|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1060|Required Header Field is missing|Client-Token|
|TRANSACTIONS|CAPTURE|400|100|Input is invalid|1080|Block contain values more than that is allowed|account|
|TRANSACTIONS|CAPTURE|400|140|Customer profile not found|2220|Customer profile not found|fdCustomerID|
|TRANSACTIONS|CAPTURE|400|150|Account detail not found|2310|Account detail not found|fdAccountID|
|TRANSACTIONS|CAPTURE|401|401|Unauthorized|4550|Partner is not opt for this service|PartnerID|
|TRANSACTIONS|CAPTURE|401|401|Unauthorized|4980|Payment Transaction ID is not Valid||
|TRANSACTIONS|CAPTURE|400|420|NON_F2F_ACCOUNT|4130|Partner is not Configure for the NF2F|ConFiguration Issue|
|TRANSACTIONS|CAPTURE|400|420|Unauthorized|4250|Session time out|Client-Token|
|TRANSACTIONS|CAPTURE|400|450|Partner Not Found|4500|PartnerID not Found|PartnerID|
|TRANSACTIONS|CAPTURE|500|500|General Error|5110|Please try again after some time, If issue persist please contact customer support|UCOMM_CLEAR_DATA|
|TRANSACTIONS|CAPTURE|500|500|General Error|5340|Configuration Error, Please contact customer support|AES|
|TRANSACTIONS|CAPTURE|500|500|General Error|5340|Configuration Error, Please contact customer support|PublicKey Expired|
|CONSUMERPROFILE|CLOSE|200|0|OK||||
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid |1010|Field did not have a valid format|type|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid|1010|Field did not have a valid format|PassPhase|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid|1010|Field did not have a valid format|InitializationVector|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid |1010|Field did not have a valid format|reason|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid|1010|Field did not have a valid format|FDACCOUNTID|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid|1020|Field contained a bad value|PassPhase|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid|1020|Field contained a bad value|InitializationVector|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid|1020|Field contained a bad value|FDACCOUNTID|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid |1030|Required field did not have a value|fdCustomerID|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid |1030|Required field did not have a value|type|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid|1030|Required field did not have a value|PassPhase|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid|1030|Required field did not have a value|InitializationVector|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid |1030|Required field did not have a value|reason|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid|1030|Required field did not have a value|FDACCOUNTID|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid |1035|Required field is missing|fdCustomerID|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid |1035|Required field is missing|type|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid|1035|Required field is missing|PassPhase|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid|1035|Required field is missing|InitializationVector|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid |1035|Required field is missing|reason|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid|1035|Required field is missing|FDACCOUNTID|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid |1045|Required block is missing|account|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid |1060|Required Header Field is missing|fdAccountID|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid|1060|Required Header Field is missing|Client-Token|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid |1080|Block contain values more than that is allowed|account|
|CONSUMERPROFILE|CLOSE|400|140|Customer profile not found|2220|Customer profile not found|fdCustomerID|
|CONSUMERPROFILE|CLOSE|400|150|Account detail not found|2310|Account detail not found|fdAccountID|
|CONSUMERPROFILE|CLOSE|400|150|Account detail not found|2310|Account detail not found|fdAccountID|
|CONSUMERPROFILE|CLOSE|401|401|Unauthorized|4550|Partner is not opt for this service|PartnerID|
|CONSUMERPROFILE|CLOSE|400|420|Unauthorized|4250|Session time out|Client-Token|
|CONSUMERPROFILE|CLOSE|400|450|Partner Not Found|4500|PartnerID not Found|PartnerID|
|CONSUMERPROFILE|CLOSE|500|500|General Error|5110|Please try again after some time, If issue persist please contact customer support|UCOMM_CLEAR_DATA|
|CONSUMERPROFILE|CLOSE|500|500|General Error|5340|Configuration Error, Please contact customer support|PublicKey Expired|
|TRANSACTIONS|COLLECTIONFEE|200|0|Approved||||
|TRANSACTIONS|COLLECTIONFEE|200|0|Approved Preferred||||
|TRANSACTIONS|COLLECTIONFEE|200|0|Adjustment accepted for processing||||
|TRANSACTIONS|COLLECTIONFEE|200|0|Approved but Issued on a Function Z||||
|TRANSACTIONS|COLLECTIONFEE|200|0|Approved but no Guarantee for it Being Settled||||
|TRANSACTIONS|COLLECTIONFEE|200|0|The transactions has verified approval and has been accepted||||
|TRANSACTIONS|COLLECTIONFEE|400|100|Input is invalid|1010|Field did not have a valid format|type|
|TRANSACTIONS|COLLECTIONFEE|400|100|Input is invalid|1010|Field contained a bad value|SubscriberID|
|TRANSACTIONS|COLLECTIONFEE|400|100|Input is invalid|1010|Field did not have a valid format|gpsState|
|TRANSACTIONS|COLLECTIONFEE|400|100|Input is invalid|1020|Field contained a bad value|type|
|TRANSACTIONS|COLLECTIONFEE|400|100|Input is invalid|1020|Field contained a bad value|gpsState|
|TRANSACTIONS|COLLECTIONFEE|400|100|Input is invalid|1030|Required field did not have a value|PassPhase|
|TRANSACTIONS|COLLECTIONFEE|400|100|Input is invalid|1030|Required field did not have a value|InitializationVector|
|TRANSACTIONS|COLLECTIONFEE|400|100|Input is invalid|1030|Required field did not have a value|type|
|TRANSACTIONS|COLLECTIONFEE|400|100|Input is invalid|1030|Required field did not have a value|SubscriberID|
|TRANSACTIONS|COLLECTIONFEE|400|100|Input is invalid|1030|Required field did not have a value|gpsState|
|TRANSACTIONS|COLLECTIONFEE|400|100|Input is invalid|1035|Required field is missing|PassPhase|
|TRANSACTIONS|COLLECTIONFEE|400|100|Input is invalid|1035|Required field is missing|InitializationVector|
|TRANSACTIONS|COLLECTIONFEE|400|100|Input is invalid|1035|Required field is missing|type|
|TRANSACTIONS|COLLECTIONFEE|400|100|Input is invalid|1035|Required field is missing|SubscriberID|
|TRANSACTIONS|COLLECTIONFEE|400|100|Input is invalid|1035|Required field is missing|gpsState|
|TRANSACTIONS|COLLECTIONFEE|400|100|Input is invalid|1040|Required block did not have a value|account|
|TRANSACTIONS|COLLECTIONFEE|400|100|Input is invalid|1040|Required block did not have a value|transactionDetails|
|TRANSACTIONS|COLLECTIONFEE|400|100|Input is invalid|1045|Required block is missing|account|
|TRANSACTIONS|COLLECTIONFEE|400|100|Input is invalid|1045|Required block is missing|transactionDetails|
|TRANSACTIONS|COLLECTIONFEE|400|100|Input is invalid|1045|Required block is missing|partner|
|TRANSACTIONS|COLLECTIONFEE|400|100|Input is invalid|1060|Required Header Field is missing|PartnerID|
|TRANSACTIONS|COLLECTIONFEE|400|100|Input is invalid|1060|Required Header Field is missing|Client-Token|
|TRANSACTIONS|COLLECTIONFEE|400|100|Input is invalid|1080|Block contain values more than that is allowed|account|
|TRANSACTIONS|COLLECTIONFEE|400|150|Account detail not found|2310|Account detail not found|fdAccountID|
|TRANSACTIONS|COLLECTIONFEE|401|401|Unauthorized|4550|Partner is not opt for this service|PartnerID|
|TRANSACTIONS|COLLECTIONFEE|400|420|Unauthorized|4250|Session time out|Client-Token|
|TRANSACTIONS|COLLECTIONFEE|400|450|Partner Not Found|4500|PartnerID not Found|PartnerID|
|TRANSACTIONS|COLLECTIONFEE|500|500|General Error|5110|Please try again after some time, If issue persist please contact customer support|UCOMM_CLEAR_DATA|
|TRANSACTIONS|COLLECTIONFEE|500|500|General Error|5340|Configuration Error, Please contact customer support|AES|
|TRANSACTIONS|COLLECTIONFEE|500|500|General Error|5340|Configuration Error, Please contact customer support|PublicKey Expired|
|CONSUMERPROFILE|ADD|201|0|Created||||
|CONSUMERPROFILE|ADD|200|10|Previously Created||||
|CONSUMERPROFILE|ADD|400|100|Input is invalid |1010|Field did not have a valid format|externalID|
|CONSUMERPROFILE|ADD|400|100|Input is invalid|1020|Field contained a bad value|externalID|
|CONSUMERPROFILE|ADD|400|100|Input is invalid |1030|Required field did not have a value|externalID|
|CONSUMERPROFILE|ADD|400|100|Input is invalid |1035|Required field is missing|externalID|
|CONSUMERPROFILE|ADD|400|100|Input is invalid|1035|Required field is missing|PassPhase|
|CONSUMERPROFILE|ADD|400|100|Input is invalid|1035|Required field is missing|InitializationVector|
|CONSUMERPROFILE|ADD|400|100|Input is invalid|1040|Required block did not have a value|customer|
|CONSUMERPROFILE|ADD|400|100|Input is invalid|1045|Required block is missing|customer|
|CONSUMERPROFILE|ADD|400|100|Input is invalid |1060|Required Header Field is missing|PartnerID|
|CONSUMERPROFILE|ADD|400|100|Input is invalid |1060|Required Header Field is missing|SubscriberId|
|CONSUMERPROFILE|ADD|400|100|Input is invalid |1060|Required Header Field is missing|Client-Token|
|CONSUMERPROFILE|ADD|401|401|Unauthorized|4550|Partner is not opt for this service|PartnerID|
|CONSUMERPROFILE|ADD|400|450|Partner Not Found|4500|PartnerID not Found|PartnerID|
|CONSUMERPROFILE|ADD|500|500|General Error|5120|Please try again after some time, If issue persist please contact customer support|UCOMM_CUSTOMER_ADD|
|CONSUMERPROFILE|ADD|500|500|General Error||||
|CONSUMERPROFILE|CLOSE|200|0|OK||||
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid |1010|Field did not have a valid format|fdCustomerID|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid|1020|Field contained a bad value|fdCustomerID|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid |1030|Required field did not have a value|fdCustomerID|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid |1035|Required field is missing|fdCustomerID|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid|1035|Required field is missing|PassPhase|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid|1035|Required field is missing|InitializationVector|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid|1040|Required block did not have a value|customer|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid|1045|Required block is missing|customer|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid |1060|Required Header Field is missing|PartnerID|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid |1060|Required Header Field is missing|SubscriberId|
|CONSUMERPROFILE|CLOSE|400|100|Input is invalid |1060|Required Header Field is missing|Client-Token|
|CONSUMERPROFILE|CLOSE|400|140|Customer profile not found|2220|Customer profile not found|fdCustomerID|
|CONSUMERPROFILE|CLOSE|400|140|Customer has active accounts|2230|Customer has active accounts|fdCustomerID|
|CONSUMERPROFILE|CLOSE|401|401|Unauthorized|4550|Partner is not opt for this service|PartnerID|
|CONSUMERPROFILE|CLOSE|400|450|Partner Not Found|4500|PartnerID not Found|PartnerID|
|CONSUMERPROFILE|CLOSE|500|500|General Error|5133|Please try again after some time, If issue persist please contact customer support|UCOMM_CLOSE|
|CONSUMERPROFILE|CLOSE|500|500|General Error|5230|Please try again after some time, If issue persist please contact customer support|MIE_CLOSE|
|CONSUMERPROFILE|CLOSE|500|500|General Error||||
|CONSUMERPROFILE|ENROLLMENT|201|0|Created||||
|CONSUMERPROFILE|ENROLLMENT|200|70|Validations Pending||||
|CONSUMERPROFILE|ENROLLMENT|200|90|Prior Pending||||
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid |1010|Field did not have a valid format|fdCustomerID|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid |1010|Field did not have a valid format|type|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid |1010|Field did not have a valid format|securityQuestionId|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid |1010|Field did not have a valid format|securityQuestion|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid |1010|Field did not have a valid format|securityAnswer|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid|1010|Field did not have a valid format|PassPhase|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid|1010|Field did not have a valid format|InitializationVector|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid |1010|Field did not have a valid format|partnerId|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid |1010|Field did not have a valid format|supplementalId|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid |1020|Field contained a bad value|fdCustomerID|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid |1020|Field contained a bad value|type|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid|1020|Field contained a bad value|PassPhase|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid|1020|Field contained a bad value|InitializationVector|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid |1030|Required field did not have a value|fdCustomerID|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid |1030|Required field did not have a value|type|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid |1030|Required field did not have a value|securityQuestionId|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid |1030|Required field did not have a value|securityQuestion|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid |1030|Required field did not have a value|securityAnswer|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid|1030|Required field did not have a value|PassPhase|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid|1030|Required field did not have a value|InitializationVector|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid |1030|Required field did not have a value|aggregatorTransactionId|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid |1035|Required field is missing|fdCustomerID|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid |1035|Required field is missing|type|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid |1035|Required field is missing|securityQuestionId|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid |1035|Required field is missing|securityQuestion|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid |1035|Required field is missing|securityAnswer|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid|1035|Required field is missing|PassPhase|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid|1035|Required field is missing|InitializationVector|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid |1040|Required block did not have a value|account|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid |1040|Required block did not have a value|customer|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid |1045|Required block is missing|account|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid |1045|Required block is missing|customer|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid |1060|Required Header Field is missing|PartnerID|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid |1060|Required Header Field is missing|SubscriberId|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid |1060|Required Header Field is missing|Client-Token|
|CONSUMERPROFILE|ENROLLMENT|400|100|Input is invalid |1080|Block contain values more than that is allowed|account|
|CONSUMERPROFILE|ENROLLMENT|400|140|The Customer has already enrolled the maximum allowable number of accounts|2210|The Customer has already enrolled the maximum allowable number of accounts.|fdCustomerID|
|CONSUMERPROFILE|ENROLLMENT|400|140|Customer profile not found|2220|Customer profile not found|fdCustomerID|
|CONSUMERPROFILE|ENROLLMENT|400|400|Bad Request|400|Bad Request. Either required parameters are missing or message Format is incorrect||
|CONSUMERPROFILE|ENROLLMENT|401|401|Unauthorized|401|Unauthorized||
|CONSUMERPROFILE|ENROLLMENT|401|401|Unauthorized|4550|Partner is not opt for this service|PartnerID|
|CONSUMERPROFILE|ENROLLMENT|409|409|Conflict|4920|ConnectPayPaymentNumber is already enrolled|ConnectPayPaymentNumber|
|CONSUMERPROFILE|ENROLLMENT|400|420|Unauthorized|4250|Session time out|Client-Token|
|CONSUMERPROFILE|ENROLLMENT|400|450|Partner Not Found|4500|PartnerID not Found|PartnerID|
|CONSUMERPROFILE|ENROLLMENT|500|500|General Error|5110|Please try again after some time, If issue persist please contact customer support|UCOMM_CLEAR_DATA|
|CONSUMERPROFILE|ENROLLMENT|500|500|General Error|5130|Please try again after some time, If issue persist please contact customer support|UCOMM_ADD|
|CONSUMERPROFILE|ENROLLMENT|500|500|General Error|5140|Please try again after some time, If issue persist please contact customer support|UCOMM_GET_ALL_ACCOUNT|
|CONSUMERPROFILE|ENROLLMENT|500|500|General Error|5210|Please try again after some time, If issue persist please contact customer support|MIE_ENROLLMENT|
|CONSUMERPROFILE|ENROLLMENT|500|500|General Error|5230|Please try again after some time, If issue persist please contact customer support|MIE_CLOSE|
|CONSUMERPROFILE|ENROLLMENT|500|500|General Error|5340|Configuration Error, Please contact customer support|PartnerID|
|CONSUMERPROFILE|ENROLLMENT|500|500|General Error|5340|Configuration Error, Please contact customer support|SubscriberId|
|CONSUMERPROFILE|ENROLLMENT|500|500|General Error|5340|Configuration Error, Please contact customer support|AES|
|CONSUMERPROFILE|ENROLLMENT|500|500|General Error|5340|Configuration Error, Please contact customer support|PublicKey Expired|
|CONSUMERPROFILE|ENROLLMENT|500|500|General Error||||
|ACCOUNT|GETACCOUNTDETAILS|200|0|OK||||
|ACCOUNT|GETACCOUNTDETAILS|400|100|Input is invalid |1010|Field did not have a valid format|type|
|ACCOUNT|GETACCOUNTDETAILS|400|100|Input is invalid |1020|Field contained a bad value|type|
|ACCOUNT|GETACCOUNTDETAILS|400|100|Input is invalid |1030|Required field did not have a value|PassPhase|
|ACCOUNT|GETACCOUNTDETAILS|400|100|Input is invalid |1030|Required field did not have a value|InitializationVector|
|ACCOUNT|GETACCOUNTDETAILS|400|100|Input is invalid |1030|Required field did not have a value|type|
|ACCOUNT|GETACCOUNTDETAILS|400|100|Input is invalid |1030|Required field did not have a value|fdCustomerID|
|ACCOUNT|GETACCOUNTDETAILS|400|100|Input is invalid |1030|Required field did not have a value|fdAccountID|
|ACCOUNT|GETACCOUNTDETAILS|400|100|Input is invalid|1035|Required field is missing|PassPhase|
|ACCOUNT|GETACCOUNTDETAILS|400|100|Input is invalid|1035|Required field is missing|InitializationVector|
|ACCOUNT|GETACCOUNTDETAILS|400|100|Input is invalid |1035|Required field is missing|type|
|ACCOUNT|GETACCOUNTDETAILS|400|100|Input is invalid |1035|Required field is missing|fdCustomerID|
|ACCOUNT|GETACCOUNTDETAILS|400|100|Input is invalid |1035|Required field is missing|fdAccountID|
|ACCOUNT|GETACCOUNTDETAILS|400|100|Input is invalid|1060|Required Header Field is missing|Client-Token|
|ACCOUNT|GETACCOUNTDETAILS|400|140|Customer profile not found|2220|Customer profile not found|fdCustomerID|
|ACCOUNT|GETACCOUNTDETAILS|400|150|Account detail not found|2310|Account detail not found|fdAccountID|
|ACCOUNT|GETACCOUNTDETAILS|401|401|Unauthorized|4550|Partner is not opt for this service|PartnerID|
|ACCOUNT|GETACCOUNTDETAILS|500|500|General Error|5340|Configuration Error, Please contact customer support|PublicKey Expired|
|ACCOUNT|GETACCOUNTDETAILS|200|0|OK||||
|ACCOUNT|GETACCOUNTDETAILS|400|100|Input is invalid |1030|Required field did not have a value|InitializationVector|
|ACCOUNT|GETACCOUNTDETAILS|400|100|Input is invalid |1030|Required field did not have a value|PassPhase|
|ACCOUNT|GETACCOUNTDETAILS|400|100|Input is invalid |1030|Required field did not have a value|fdCustomerID|
|ACCOUNT|GETACCOUNTDETAILS|400|100|Input is invalid |1035|Required field is missing|InitializationVector|
|ACCOUNT|GETACCOUNTDETAILS|400|100|Input is invalid |1035|Required field is missing|PassPhase|
|ACCOUNT|GETACCOUNTDETAILS|400|100|Input is invalid |1035|Required field is missing|fdCustomerID|
|ACCOUNT|GETACCOUNTDETAILS|400|100|Input is invalid|1060|Required Header Field is missing|Client-Token|
|ACCOUNT|GETACCOUNTDETAILS|400|140|Customer profile not found|2220|Customer profile not found|fdCustomerID|
|ACCOUNT|GETACCOUNTDETAILS|400|150|Account detail not found|2310|Account detail not found|fdAccountID|
|ACCOUNT|GETACCOUNTDETAILS|401|401|Unauthorized|4550|Partner is not opt for this service|PartnerID|
|ACCOUNT|GETACCOUNTDETAILS|500|500|General Error|5340|Configuration Error, Please contact customer support|PublicKey Expired|
|SECURITY|GETDATA|200|0|OK||||
|SECURITY|GETDATA|400|100|Input is invalid|1070|The URI Param is Missing or Invalid|NONCE|
|SECURITY|GETDATA|401|401|Unauthorized|4550|Partner is not opt for this service|PartnerID|
|SECURITY|GETDATA|400|450|Partner Not Found|4500|PartnerID not Found|PartnerID|
|SECURITY|GETDATA|200|0|OK||||
|SECURITY|GETDATA|400|100|Input is invalid |1010|Field did not have a valid format|Masked|
|SECURITY|GETDATA|400|100|Input is invalid |1010|Field did not have a valid format|Fetch|
|SECURITY|GETDATA|400|100|Input is invalid |1010|Field did not have a valid format|type|
|SECURITY|GETDATA|400|100|Input is invalid |1010|Field did not have a valid format|fdCustomerID|
|SECURITY|GETDATA|400|100|Input is invalid |1020|Field contained a bad value|type|
|SECURITY|GETDATA|400|100|Input is invalid |1020|Field contained a bad value|fdCustomerID|
|SECURITY|GETDATA|400|100|Input is invalid |1030|Required field did not have a value|Masked|
|SECURITY|GETDATA|400|100|Input is invalid |1030|Required field did not have a value|Fetch|
|SECURITY|GETDATA|400|100|Input is invalid |1030|Required field did not have a value|fdAccountID|
|SECURITY|GETDATA|400|100|Input is invalid |1030|Required field did not have a value|type|
|SECURITY|GETDATA|400|100|Input is invalid |1030|Required field did not have a value|fdCustomerID|
|SECURITY|GETDATA|400|100|Input is invalid |1035|Required field is missing|type|
|SECURITY|GETDATA|400|100|Input is invalid |1035|Required field is missing|fdCustomerID|
|SECURITY|GETDATA|400|100|Input is invalid |1040|Required block did not have a value|account|
|SECURITY|GETDATA|400|100|Input is invalid |1040|Required block did not have a value|customer|
|SECURITY|GETDATA|400|100|Input is invalid|1045|Required block is missing|CPAPIAccount|
|SECURITY|GETDATA|400|100|Input is invalid |1045|Required block is missing|account|
|SECURITY|GETDATA|400|100|Input is invalid |1045|Required block is missing|customer|
|SECURITY|GETDATA|400|100|Input is invalid|1045|Required block is missing|FetchAccountDetails|
|SECURITY|GETDATA|400|100|Input is invalid |1060|Required Header Field is missing|SubscriberId|
|SECURITY|GETDATA|400|100|Input is invalid |1060|Required Header Field is missing|PartnerID|
|SECURITY|GETDATA|400|100|Input is invalid |1060|Required Header Field is missing|Client-Token|
|SECURITY|GETDATA|400|100|Input is invalid|1070|TheáURI Param is Missing or Invalid|NONCE|
|SECURITY|GETDATA|400|100|Input is invalid |1080|Block contain values more than that is allowed|account|
|SECURITY|GETDATA|400|120|Consumer Cannot Be Validated|2020|Original ConnectPayPaymentNumber is not Active|ConnectPayPaymentNumber|
|SECURITY|GETDATA|400|140|Customer profile not found|2220|Customer profile not found|fdCustomerID|
|SECURITY|GETDATA|400|150|Account detail not found|2310|Account detail not found|fdAccountID|
|SECURITY|GETDATA|401|401|Unauthorized|4550|Partner is not opt for this service|PartnerID|
|SECURITY|GETDATA|400|450|Partner Not Found|4500|PartnerID not Found|PartnerID|
|SECURITY|GETDATA|500|500|General Error|5110|Please try again after some time, If issue persist please contact customer support|UCOMM_CLEAR_DATA|
|SECURITY|GETDATA|500|500|General Error|5340|Configuration Error, Please contact customer support|PublicKey Expired|
|SECURITY|GETPUBLICKEY|201|0|Created||||
|SECURITY|GETPUBLICKEY|401|401|Unauthorized|4550|Partner is not opt for this service|PartnerID|
|SECURITY|GETPUBLICKEY|400|450|Partner Not Found|4500|PartnerID not Found|PartnerID|
|SECURITY|GETPUBLICKEY|500|500|General Error|5112|Please try again after some time, If issue persist please contact customer support|UCOMM_GET_PUBLIC_KEY|
|SECURITY|GETPUBLICKEY|500|500|General Error||||
|SECURITY|CREATESESSIONTOKEN|200|0|OK||||
|SECURITY|CREATESESSIONTOKEN|400|100|Input is invalid |1010|Field did not have a valid format|publicKeyRequired|
|SECURITY|CREATESESSIONTOKEN|400|100|Input is invalid |1010|Field did not have a valid format|type|
|SECURITY|CREATESESSIONTOKEN|400|100|Input is invalid|1020|Field contained a bad value|publicKeyRequired|
|SECURITY|CREATESESSIONTOKEN|400|100|Input is invalid |1030|Required field did not have a value|publicKeyRequired|
|SECURITY|CREATESESSIONTOKEN|400|100|Input is invalid |1030|Required field did not have a value|type|
|SECURITY|CREATESESSIONTOKEN|400|100|Input is invalid |1035|Required field is missing|publicKeyRequired|
|SECURITY|CREATESESSIONTOKEN|400|100|Input is invalid |1035|Required field is missing|type|
|SECURITY|CREATESESSIONTOKEN|400|100|Input is invalid|1040|Required block did not have a value|customer|
|SECURITY|CREATESESSIONTOKEN|400|100|Input is invalid|1040|Required block did not have a value|security|
|SECURITY|CREATESESSIONTOKEN|400|100|Input is invalid |1040|Required block did not have a value|account|
|SECURITY|CREATESESSIONTOKEN|400|100|Input is invalid|1045|Required block is missing|customer|
|SECURITY|CREATESESSIONTOKEN|400|100|Input is invalid|1045|Required block is missing|security|
|SECURITY|CREATESESSIONTOKEN|400|100|Input is invalid |1045|Required block is missing|account|
|SECURITY|CREATESESSIONTOKEN|400|100|Input is invalid |1060|Required Header Field is missing|PartnerID|
|SECURITY|CREATESESSIONTOKEN|400|100|Input is invalid |1060|Required Header Field is missing|SubscriberId|
|SECURITY|CREATESESSIONTOKEN|400|100|Input is invalid |1060|Required Header Field is missing|fdAccountID|
|SECURITY|CREATESESSIONTOKEN|400|100|Input is invalid |1060|Required Header Field is missing|issuedOn|
|SECURITY|CREATESESSIONTOKEN|400|100|Input is invalid |1060|Required Header Field is missing|expiresInSeconds|
|SECURITY|CREATESESSIONTOKEN|400|100|Input is invalid |1060|Required Header Field is missing|Client-Token|
|SECURITY|CREATESESSIONTOKEN|400|100|Input is invalid |1080|Block contain values more than that is allowed|account|
|SECURITY|CREATESESSIONTOKEN|401|401|Unauthorized|4550|Partner is not opt for this service|PartnerID|
|SECURITY|CREATESESSIONTOKEN|400|450|Partner Not Found|4500|PartnerID not Found|PartnerID|
|SECURITY|CREATESESSIONTOKEN|500|500|General Error|5112|Please try again after some time, If issue persist please contact customer support|UCOMM_GET_PUBLIC_KEY|
|SECURITY|CREATESESSIONTOKEN|500|500|General Error|5340|Configuration Error, Please contact customer support|Oauth Token|
|SECURITY|CREATESESSIONTOKEN|500|500|General Error||||
|TRANSACTIONS|KEYEXCHANGE|200|0|Approved||||
|TRANSACTIONS|KEYEXCHANGE|400|100|Input is invalid|1010|Field did not have a valid format|type|
|TRANSACTIONS|KEYEXCHANGE|400|100|Input is invalid|1010|Field contained a bad value|SubscriberID|
|TRANSACTIONS|KEYEXCHANGE|400|100|Input is invalid|1020|Field contained a bad value|type|
|TRANSACTIONS|KEYEXCHANGE|400|100|Input is invalid|1030|Required field did not have a value|PassPhase|
|TRANSACTIONS|KEYEXCHANGE|400|100|Input is invalid|1030|Required field did not have a value|InitializationVector|
|TRANSACTIONS|KEYEXCHANGE|400|100|Input is invalid|1030|Required field did not have a value|type|
|TRANSACTIONS|KEYEXCHANGE|400|100|Input is invalid|1030|Required field did not have a value|SubscriberID|
|TRANSACTIONS|KEYEXCHANGE|400|100|Input is invalid|1035|Required field is missing|PassPhase|
|TRANSACTIONS|KEYEXCHANGE|400|100|Input is invalid|1035|Required field is missing|InitializationVector|
|TRANSACTIONS|KEYEXCHANGE|400|100|Input is invalid|1035|Required field is missing|type|
|TRANSACTIONS|KEYEXCHANGE|400|100|Input is invalid|1035|Required field is missing|SubscriberID|
|TRANSACTIONS|KEYEXCHANGE|400|100|Input is invalid|1040|Required block did not have a value|account|
|TRANSACTIONS|KEYEXCHANGE|400|100|Input is invalid|1045|Required block is missing|account|
|TRANSACTIONS|KEYEXCHANGE|400|100|Input is invalid|1045|Required block is missing|partner|
|TRANSACTIONS|KEYEXCHANGE|400|100|Input is invalid|1060|Required Header Field is missing|PartnerID|
|TRANSACTIONS|KEYEXCHANGE|400|100|Input is invalid|1060|Required Header Field is missing|Client-Token|
|TRANSACTIONS|KEYEXCHANGE|400|100|Input is invalid|1080|Block contain values more than that is allowed|account|
|TRANSACTIONS|KEYEXCHANGE|400|150|Account detail not found|2310|Account detail not found|fdAccountID|
|TRANSACTIONS|KEYEXCHANGE|401|401|Unauthorized|4550|Partner is not opt for this service|PartnerID|
|TRANSACTIONS|KEYEXCHANGE|400|420|Unauthorized|4250|Session time out|Client-Token|
|TRANSACTIONS|KEYEXCHANGE|400|450|Partner Not Found|4500|PartnerID not Found|PartnerID|
|TRANSACTIONS|KEYEXCHANGE|500|500|General Error|5110|Please try again after some time, If issue persist please contact customer support|UCOMM_CLEAR_DATA|
|TRANSACTIONS|KEYEXCHANGE|500|500|General Error|5340|Configuration Error, Please contact customer support|AES|
|TRANSACTIONS|KEYEXCHANGE|500|500|General Error|5340|Configuration Error, Please contact customer support|PublicKey Expired|
|CONSUMERPROFILE|LOAD|201|0|Created||||
|CONSUMERPROFILE|LOAD|200|70|Validations Pending||||
|CONSUMERPROFILE|LOAD|200|90|Prior Pending||||
|CONSUMERPROFILE|LOAD|400|100|Input is invalid |1010|Field did not have a valid format|fdCustomerID|
|CONSUMERPROFILE|LOAD|400|100|Input is invalid|1010|Field did not have a valid format|PassPhase|
|CONSUMERPROFILE|LOAD|400|100|Input is invalid|1010|Field did not have a valid format|InitializationVector|
|CONSUMERPROFILE|LOAD|400|100|Input is invalid |1010|Field did not have a valid format|type|
|CONSUMERPROFILE|LOAD|400|100|Input is invalid|1020|Field contained a bad value|fdCustomerID|
|CONSUMERPROFILE|LOAD|400|100|Input is invalid |1020|Field contained a bad value|type|
|CONSUMERPROFILE|LOAD|400|100|Input is invalid|1020|Field contained a bad value|PassPhase|
|CONSUMERPROFILE|LOAD|400|100|Input is invalid|1020|Field contained a bad value|InitializationVector|
|CONSUMERPROFILE|LOAD|400|100|Input is invalid |1030|Required field did not have a value|fdCustomerID|
|CONSUMERPROFILE|LOAD|400|100|Input is invalid|1030|Required field did not have a value|PassPhase|
|CONSUMERPROFILE|LOAD|400|100|Input is invalid|1030|Required field did not have a value|InitializationVector|
|CONSUMERPROFILE|LOAD|400|100|Input is invalid |1030|Required field did not have a value|type|
|CONSUMERPROFILE|LOAD|400|100|Input is invalid |1035|Required field is missing|fdCustomerID|
|CONSUMERPROFILE|LOAD|400|100|Input is invalid|1035|Required field is missing|PassPhase|
|CONSUMERPROFILE|LOAD|400|100|Input is invalid|1035|Required field is missing|InitializationVector|
|CONSUMERPROFILE|LOAD|400|100|Input is invalid |1035|Required field is missing|type|
|CONSUMERPROFILE|LOAD|400|100|Input is invalid|1040|Required block did not have a value|customer|
|CONSUMERPROFILE|LOAD|400|100|Input is invalid|1045|Required block is missing|customer|
|CONSUMERPROFILE|LOAD|400|100|Input is invalid |1045|Required block is missing|account|
|CONSUMERPROFILE|LOAD|400|100|Input is invalid |1060|Required Header Field is missing|PartnerID|
|CONSUMERPROFILE|LOAD|400|100|Input is invalid |1060|Required Header Field is missing|SubscriberId|
|CONSUMERPROFILE|LOAD|400|100|Input is invalid |1060|Required Header Field is missing|Client-Token|
|CONSUMERPROFILE|LOAD|400|100|Input is invalid |1080|Block contain values more than that is allowed|account|
|CONSUMERPROFILE|LOAD|400|140|The Customer has already enrolled the maximum allowable number of accounts|2210|The Customer has already enrolled the maximum allowable number of accounts.|fdCustomerID|
|CONSUMERPROFILE|LOAD|400|140|Customer profile not found|2220|Customer profile not found|fdCustomerID|
|CONSUMERPROFILE|LOAD|401|401|Unauthorized|4550|Partner is not opt for this service|PartnerID|
|CONSUMERPROFILE|LOAD|409|409|Conflict|4920|ConnectPayPaymentNumber is already enrolled|ConnectPayPaymentNumber|
|CONSUMERPROFILE|LOAD|400|420|Unauthorized|4250|Session time out|Client-Token|
|CONSUMERPROFILE|LOAD|400|450|Partner Not Found|4500|PartnerID not Found|PartnerID|
|CONSUMERPROFILE|LOAD|500|500|General Error|5110|Please try again after some time, If issue persist please contact customer support|UCOMM_CLEAR_DATA|
|CONSUMERPROFILE|LOAD|500|500|General Error|5130|Please try again after some time, If issue persist please contact customer support|UCOMM_ADD|
|CONSUMERPROFILE|LOAD|500|500|General Error|5140|Please try again after some time, If issue persist please contact customer support|UCOMM_GET_ALL_ACCOUNT|
|CONSUMERPROFILE|LOAD|500|500|General Error|5340|Configuration Error, Please contact customer support|PartnerID|
|CONSUMERPROFILE|LOAD|500|500|General Error|5340|Configuration Error, Please contact customer support|SubscriberId|
|CONSUMERPROFILE|LOAD|500|500|General Error|5340|Configuration Error, Please contact customer support|PublicKey Expired|
|CONSUMERPROFILE|LOAD|500|500|General Error||||
|TRANSACTIONS|PURCHASE|200|0|Approved||||
|TRANSACTIONS|PURCHASE|200|0|Approved Preferred||||
|TRANSACTIONS|PURCHASE|200|0|Adjustment accepted for processing||||
|TRANSACTIONS|PURCHASE|200|0|Approved but Issued on a Function Z||||
|TRANSACTIONS|PURCHASE|200|0|Approved but no Guarantee for it Being Settled||||
|TRANSACTIONS|PURCHASE|200|0|The transactions has verified approval and has been accepted||||
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1010|Field did not have a valid format|connectPaymentNumber|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1010|Field did not have a valid format|currency_code|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1010|Field contained a bad value|SubscriberID|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1010|Field did not have a valid format|fdAccountID|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1010|Field did not have a valid format|pinData|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1010|Field did not have a valid format|merchantTransactionId|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1010|Field did not have a valid format|type|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1010|Field did not have a valid format|amount|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1010|Field did not have a valid format|productCode|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1020|Field contained a bad value|connectPaymentNumber|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1020|Field contained a bad value|currency_code|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1020|Field contained a bad value|fdAccountID|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1020|Field contained a bad value|pinData|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1020|Field contained a bad value|merchantTransactionId|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1020|Field contained a bad value|type|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1020|Field contained a bad value|amount|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1030|Required field did not have a value|connectPaymentNumber|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1030|Required field did not have a value|currency_code|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1030|Required field did not have a value|SubscriberID|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1030|Required field did not have a value|fdAccountID|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1030|Required field did not have a value|pinData|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1030|Required field did not have a value|merchantTransactionId|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1030|Required field did not have a value|PassPhase|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1030|Required field did not have a value|InitializationVector|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1030|Required field did not have a value|fdCustomerID|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1030|Required field did not have a value|type|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1030|Required field did not have a value|amount|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1035|Required field is missing|connectPaymentNumber|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1035|Required field is missing|currency_code|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1035|Required field is missing|SubscriberID|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1035|Required field is missing|fdAccountID|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1035|Required field is missing|pinData|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1035|Required field is missing|merchantTransactionId|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1035|Required field is missing|PassPhase|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1035|Required field is missing|InitializationVector|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1035|Required field is missing|fdCustomerID|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1035|Required field is missing|type|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1035|Required field is missing|amount|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1035|Required field is missing|accountNumber|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1035|Required field is missing|routingNumber|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1040|Required block did not have a value|customer|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1040|Required block did not have a value|account|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1040|Required block did not have a value|transactionDetails|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1045|Required block is missing|partner|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1045|Required block is missing|customer|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1045|Required block is missing|account|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1045|Required block is missing|transactionDetails|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1060|Required Header Field is missing|PartnerID|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1060|Required Header Field is missing|Client-Token|
|TRANSACTIONS|PURCHASE|400|100|Input is invalid|1080|Block contain values more than that is allowed|account|
|TRANSACTIONS|PURCHASE|400|140|Customer profile not found|2220|Customer profile not found|fdCustomerID|
|TRANSACTIONS|PURCHASE|400|150|Account detail not found|2310|Account detail not found|fdAccountID|
|TRANSACTIONS|PURCHASE|401|401|Unauthorize|4550|Partner is not opt for this service|PartnerID|
|TRANSACTIONS|PURCHASE|401|401|Unauthorize|4980|Payment Transaction ID is not Valid|ConfigurationError|
|TRANSACTIONS|PURCHASE|400|420|NON_F2F_ACCOUNT|4130|Partner is not Configure for the NF2F|ConFiguration Issue|
|TRANSACTIONS|PURCHASE|400|420|Unauthorized|4250|Session time out|Client-Token|
|TRANSACTIONS|PURCHASE|400|450|Partner Not Found|4500|PartnerID not Found|PartnerID|
|TRANSACTIONS|PURCHASE|500|500|General Error|5110|Please try again after some time, If issue persist please contact customer support|UCOMM_CLEAR_DATA|
|TRANSACTIONS|PURCHASE|500|500|General Error|5340|Configuration Error, Please contact customer support|AES|
|TRANSACTIONS|PURCHASE|500|500|General Error|5340|Configuration Error, Please contact customer support|PublicKey Expired|
|TRANSACTIONS|REFUND|200|0|Approved||||
|TRANSACTIONS|REFUND|200|0|Approved Preferred||||
|TRANSACTIONS|REFUND|200|0|Adjustment accepted for processing||||
|TRANSACTIONS|REFUND|200|0|Approved but Issued on a Function Z||||
|TRANSACTIONS|REFUND|200|0|Approved but no Gurantee for it Being Settled||||
|TRANSACTIONS|REFUND|200|0|The transactions has verified approval and has been accepted||||
|TRANSACTIONS|REFUND|200|0|Approved||||
|TRANSACTIONS|REFUND|400|100|Input is invalid|1010|Field did not have a valid format|type|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1010|Field did not have a valid format|amount|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1010|Field did not have a valid format|connectPaymentNumber|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1010|Field did not have a valid format|currencyCode|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1010|Field contained a bad value|SubscriberID|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1010|Field did not have a valid format|fdAccountID|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1010|Field did not have a valid format|merchantTransactionId|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1020|Field contained a bad value|type|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1020|Field contained a bad value|amount|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1020|Field contained a bad value|connectPaymentNumber|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1020|Field contained a bad value|currencyCode|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1020|Field contained a bad value|fdAccountID|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1020|Field contained a bad value|merchantTransactionId|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1030|Required field did not have a value|PassPhase|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1030|Required field did not have a value|InitializationVector|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1030|Required field did not have a value|fdCustomerID|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1030|Required field did not have a value|type|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1030|Required field did not have a value|amount|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1030|Required field did not have a value|connectPaymentNumber|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1030|Required field did not have a value|currencyCode|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1030|Required field did not have a value|SubscriberID|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1030|Required field did not have a value|fdAccountID|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1030|Required field did not have a value|merchantTransactionId|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1035|Required field is missing|PassPhase|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1035|Required field is missing|InitializationVector|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1035|Required field is missing|fdCustomerID|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1035|Required field is missing|type|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1035|Required field is missing|amount|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1035|Required field is missing|connectPaymentNumber|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1035|Required field is missing|currencyCode|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1035|Required field is missing|SubscriberID|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1035|Required field is missing|fdAccountID|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1035|Required field is missing|merchantTransactionId|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1040|Required block did not have a value|customer|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1040|Required block did not have a value|account|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1040|Required block did not have a value|transactionDetails|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1045|Required block is missing|customer|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1045|Required block is missing|account|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1045|Required block is missing|transactionDetails|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1045|Required block is missing|partner|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1060|Required Header Field is missing|PartnerID|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1060|Required Header Field is missing|Client-Token|
|TRANSACTIONS|REFUND|400|100|Input is invalid|1080|Block contain values more than that is allowed|account|
|TRANSACTIONS|REFUND|400|140|Customer profile not found|2220|Customer profile not found|fdCustomerID|
|TRANSACTIONS|REFUND|400|150|Account detail not found|2310|Account detail not found|fdAccountID|
|TRANSACTIONS|REFUND|401|401|Unauthorize|4550|Partner is not opt for this service|PartnerID|
|TRANSACTIONS|REFUND|400|420|Unauthorized|4250|Session time out|Client-Token|
|TRANSACTIONS|REFUND|400|450|Partner Not Found|4500|PartnerID not Found|PartnerID|
|TRANSACTIONS|REFUND|500|500|General Error|5110|Please try again after some time, If issue persist please contact customer support|UCOMM_CLEAR_DATA|
|TRANSACTIONS|REFUND|500|500|General Error|5340|Configuration Error, Please contact customer support|AES|
|TRANSACTIONS|REFUND|500|500|General Error|5340|Configuration Error, Please contact customer support|PublicKey Expired|
|CONSUMERPROFILE|UPDATE|200|0|OK||||
|CONSUMERPROFILE|UPDATE|200|70|Validations Pending||||
|CONSUMERPROFILE|UPDATE|200|90|Prior Pending||||
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid |1010|Field did not have a valid format|fdCustomerID|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid |1010|Field did not have a valid format|type|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid |1010|Field did not have a valid format|securityQuestionId|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid |1010|Field did not have a valid format|securityQuestion|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid |1010|Field did not have a valid format|securityAnswer|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid|1010|Field did not have a valid format|PassPhase|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid|1010|Field did not have a valid format|InitializationVector|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid|1010|Field did not have a valid format|FDACCOUNTID|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid |1010|Field did not have a valid format|homeId|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid |1010|Field did not have a valid format|supplementalId|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid |1020|Field contained a bad value|fdCustomerID|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid |1020|Field contained a bad value|type|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid|1020|Field contained a bad value|PassPhase|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid|1020|Field contained a bad value|InitializationVector|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid|1020|Field contained a bad value|FDACCOUNTID|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid |1030|Required field did not have a value|fdCustomerID|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid |1030|Required field did not have a value|type|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid |1030|Required field did not have a value|securityQuestionId|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid |1030|Required field did not have a value|securityQuestion|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid |1030|Required field did not have a value|securityAnswer|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid|1030|Required field did not have a value|PassPhase|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid|1030|Required field did not have a value|InitializationVector|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid|1030|Required field did not have a value|FDACCOUNTID|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid |1030|Required field did not have a value|aggregatorTransactionId|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid |1035|Required field is missing|fdCustomerID|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid |1035|Required field is missing|type|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid |1035|Required field is missing|securityQuestionId|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid |1035|Required field is missing|securityQuestion|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid |1035|Required field is missing|securityAnswer|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid|1035|Required field is missing|PassPhase|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid|1035|Required field is missing|InitializationVector|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid|1035|Required field is missing|FDACCOUNTID|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid |1040|Required block did not have a value|account|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid |1040|Required block did not have a value|customer|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid |1045|Required block is missing|account|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid |1045|Required block is missing|customer|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid |1060|Required Header Field is missing|PartnerID|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid |1060|Required Header Field is missing|SubscriberId|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid |1060|Required Header Field is missing|Client-Token|
|CONSUMERPROFILE|UPDATE|400|100|Input is invalid |1080|Block contain values more than that is allowed|account|
|CONSUMERPROFILE|UPDATE|400|120|Consumer Cannot Be Validated|2020|Original ConnectPayPaymentNumber is not Active|ConnectPayPaymentNumber|
|CONSUMERPROFILE|UPDATE|400|140|Customer profile not found|2220|Customer profile not found|fdCustomerID|
|CONSUMERPROFILE|UPDATE|400|150|Account detail not found|2310|Account detail not found|fdAccountID|
|CONSUMERPROFILE|UPDATE|400|150|Account detail not found|2310|Account detail not found|fdAccountID|
|CONSUMERPROFILE|UPDATE|401|401|Unauthorize|4550|Partner is not opt for this service|PartnerID|
|CONSUMERPROFILE|UPDATE|400|420|Unauthorized|4250|Session time out|Client-Token|
|CONSUMERPROFILE|UPDATE|400|450|Partner Not Found|4500|PartnerID not Found|PartnerID|
|CONSUMERPROFILE|UPDATE|500|500|General Error|5110|Please try again after some time, If issue persist please contact customer support|UCOMM_CLEAR_DATA|
|CONSUMERPROFILE|UPDATE|500|500|General Error|5130|Please try again after some time, If issue persist please contact customer support|UCOMM_ADD|
|CONSUMERPROFILE|UPDATE|500|500|General Error|5132|Please try again after some time, If issue persist please contact customer support|UCOMM_UPDATE|
|CONSUMERPROFILE|UPDATE|500|500|General Error|5133|Please try again after some time, If issue persist please contact customer support|UCOMM_CLOSE|
|CONSUMERPROFILE|UPDATE|500|500|General Error|5220|Please try again after some time, If issue persist please contact customer support|MIE_UPDATE|
|CONSUMERPROFILE|UPDATE|500|500|General Error|5340|Configuration Error, Please contact customer support|PublicKey Expired|
|ONLINEBANKLOGIN|VALIDATE|200|0|OK||||
|ONLINEBANKLOGIN|VALIDATE|400|100|Input is invalid |1010|Field did not have a valid format|type|
|ONLINEBANKLOGIN|VALIDATE|400|100|Input is invalid|1010|Field did not have a valid format|PassPhase|
|ONLINEBANKLOGIN|VALIDATE|400|100|Input is invalid|1010|Field did not have a valid format|InitializationVector|
|ONLINEBANKLOGIN|VALIDATE|400|100|Input is invalid|1010|Field did not have a valid format|FDACCOUNTID|
|ONLINEBANKLOGIN|VALIDATE|400|100|Input is invalid |1020|Field contained a bad value|type|
|ONLINEBANKLOGIN|VALIDATE|400|100|Input is invalid|1020|Field contained a bad value|ValidationType|
|ONLINEBANKLOGIN|VALIDATE|400|100|Input is invalid|1020|Field contained a bad value|PassPhase|
|ONLINEBANKLOGIN|VALIDATE|400|100|Input is invalid|1020|Field contained a bad value|InitializationVector|
|ONLINEBANKLOGIN|VALIDATE|400|100|Input is invalid|1020|Field contained a bad value|FDACCOUNTID|
|ONLINEBANKLOGIN|VALIDATE|400|100|Input is invalid |1030|Required field did not have a value|type|
|ONLINEBANKLOGIN|VALIDATE|400|100|Input is invalid |1030|Required field did not have a value|fdCustomerID|
|ONLINEBANKLOGIN|VALIDATE|400|100|Input is invalid |1030|Required field did not have a value|ValidationType|
|ONLINEBANKLOGIN|VALIDATE|400|100|Input is invalid|1030|Required field did not have a value|PassPhase|
|ONLINEBANKLOGIN|VALIDATE|400|100|Input is invalid|1030|Required field did not have a value|InitializationVector|
|ONLINEBANKLOGIN|VALIDATE|400|100|Input is invalid|1030|Required field did not have a value|FDACCOUNTID|
|ONLINEBANKLOGIN|VALIDATE|400|100|Input is invalid |1035|Required field is missing|type|
|ONLINEBANKLOGIN|VALIDATE|400|100|Input is invalid |1035|Required field is missing|fdCustomerID|
|ONLINEBANKLOGIN|VALIDATE|400|100|Input is invalid |1035|Required field is missing|ValidationType|
|ONLINEBANKLOGIN|VALIDATE|400|100|Input is invalid|1035|Required field is missing|PassPhase|
|ONLINEBANKLOGIN|VALIDATE|400|100|Input is invalid|1035|Required field is missing|InitializationVector|
|ONLINEBANKLOGIN|VALIDATE|400|100|Input is invalid|1035|Required field is missing|FDACCOUNTID|
|ONLINEBANKLOGIN|VALIDATE|400|100|Input is invalid |1045|Required block is missing|account|
|ONLINEBANKLOGIN|VALIDATE|400|100|Input is invalid |1045|Required block is missing|customer|
|ONLINEBANKLOGIN|VALIDATE|400|100|Input is invalid|1060|Required Header Field is missing|Client-Token|
|ONLINEBANKLOGIN|VALIDATE|400|100|Input is invalid |1080|Block contain values more than that is allowed|account|
|ONLINEBANKLOGIN|VALIDATE|400|140|Customer profile not found|2220|Customer profile not found|fdCustomerID|
|ONLINEBANKLOGIN|VALIDATE|400|150|Account detail not found|2310|Account detail not found|fdAccountID|
|ONLINEBANKLOGIN|VALIDATE|400|150|Account detail not found|2310|Account detail not found|fdAccountID|
|ONLINEBANKLOGIN|VALIDATE|401|401|Unauthorize|4550|Partner is not opt for this service|PartnerID|
|ONLINEBANKLOGIN|VALIDATE|400|420|Unauthorized|4250|Session time out|Client-Token|
|ONLINEBANKLOGIN|VALIDATE|400|450|Partner Not Found|4500|PartnerID not Found|PartnerID|
|ONLINEBANKLOGIN|VALIDATE|500|500|General Error|5110|Please try again after some time, If issue persist please contact customer support|UCOMM_CLEAR_DATA|
|ONLINEBANKLOGIN|VALIDATE|500|500|General Error|5340|Configuration Error, Please contact customer support|PublicKey Expired|
|TRANSACTIONS|VOID|200|0|Approved||||
|TRANSACTIONS|VOID|200|0|Approved Preferred||||
|TRANSACTIONS|VOID|200|0|Adjustment accepted for processing||||
|TRANSACTIONS|VOID|200|0|Approved but Issued on a Function Z||||
|TRANSACTIONS|VOID|200|0|Approved but no Gurantee for it Being Settled||||
|TRANSACTIONS|VOID|200|0|The transactions has verified approval and has been accepted||||
|TRANSACTIONS|VOID|200|0|Approved||||
|TRANSACTIONS|VOID|400|100|Input is invalid|1010|Field did not have a valid format|type|
|TRANSACTIONS|VOID|400|100|Input is invalid|1010|Field did not have a valid format|amount|
|TRANSACTIONS|VOID|400|100|Input is invalid|1010|Field did not have a valid format|connectPaymentNumber|
|TRANSACTIONS|VOID|400|100|Input is invalid|1010|Field did not have a valid format|currencyCode|
|TRANSACTIONS|VOID|400|100|Input is invalid|1010|Field contained a bad value|SubscriberID|
|TRANSACTIONS|VOID|400|100|Input is invalid|1010|Field did not have a valid format|fdAccountID|
|TRANSACTIONS|VOID|400|100|Input is invalid|1010|Field did not have a valid format|merchantTransactionId|
|TRANSACTIONS|VOID|400|100|Input is invalid|1020|Field contained a bad value|merchantTransactionId|
|TRANSACTIONS|VOID|400|100|Input is invalid|1020|Field contained a bad value|type|
|TRANSACTIONS|VOID|400|100|Input is invalid|1020|Field contained a bad value|amount|
|TRANSACTIONS|VOID|400|100|Input is invalid|1020|Field contained a bad value|connectPaymentNumber|
|TRANSACTIONS|VOID|400|100|Input is invalid|1020|Field contained a bad value|currencyCode|
|TRANSACTIONS|VOID|400|100|Input is invalid|1020|Field contained a bad value|fdAccountID|
|TRANSACTIONS|VOID|400|100|Input is invalid|1030|Required field did not have a value|merchantTransactionId|
|TRANSACTIONS|VOID|400|100|Input is invalid|1030|Required field did not have a value|PassPhase|
|TRANSACTIONS|VOID|400|100|Input is invalid|1030|Required field did not have a value|InitializationVector|
|TRANSACTIONS|VOID|400|100|Input is invalid|1030|Required field did not have a value|fdCustomerID|
|TRANSACTIONS|VOID|400|100|Input is invalid|1030|Required field did not have a value|type|
|TRANSACTIONS|VOID|400|100|Input is invalid|1030|Required field did not have a value|amount|
|TRANSACTIONS|VOID|400|100|Input is invalid|1030|Required field did not have a value|connectPaymentNumber|
|TRANSACTIONS|VOID|400|100|Input is invalid|1030|Required field did not have a value|currencyCode|
|TRANSACTIONS|VOID|400|100|Input is invalid|1030|Required field did not have a value|SubscriberID|
|TRANSACTIONS|VOID|400|100|Input is invalid|1030|Required field did not have a value|fdAccountID|
|TRANSACTIONS|VOID|400|100|Input is invalid|1035|Required field is missing|merchantTransactionId|
|TRANSACTIONS|VOID|400|100|Input is invalid|1035|Required field is missing|PassPhase|
|TRANSACTIONS|VOID|400|100|Input is invalid|1035|Required field is missing|InitializationVector|
|TRANSACTIONS|VOID|400|100|Input is invalid|1035|Required field is missing|fdCustomerID|
|TRANSACTIONS|VOID|400|100|Input is invalid|1035|Required field is missing|type|
|TRANSACTIONS|VOID|400|100|Input is invalid|1035|Required field is missing|amount|
|TRANSACTIONS|VOID|400|100|Input is invalid|1035|Required field is missing|connectPaymentNumber|
|TRANSACTIONS|VOID|400|100|Input is invalid|1035|Required field is missing|currencyCode|
|TRANSACTIONS|VOID|400|100|Input is invalid|1035|Required field is missing|SubscriberID|
|TRANSACTIONS|VOID|400|100|Input is invalid|1035|Required field is missing|fdAccountID|
|TRANSACTIONS|VOID|400|100|Input is invalid|1040|Required block did not have a value|customer|
|TRANSACTIONS|VOID|400|100|Input is invalid|1040|Required block did not have a value|account|
|TRANSACTIONS|VOID|400|100|Input is invalid|1040|Required block did not have a value|transactionDetails|
|TRANSACTIONS|VOID|400|100|Input is invalid|1045|Required block is missing|customer|
|TRANSACTIONS|VOID|400|100|Input is invalid|1045|Required block is missing|account|
|TRANSACTIONS|VOID|400|100|Input is invalid|1045|Required block is missing|transactionDetails|
|TRANSACTIONS|VOID|400|100|Input is invalid|1045|Required block is missing|partner|
|TRANSACTIONS|VOID|400|100|Input is invalid|1060|Required Header Field is missing|PartnerID|
|TRANSACTIONS|VOID|400|100|Input is invalid|1060|Required Header Field is missing|Client-Token|
|TRANSACTIONS|VOID|400|100|Input is invalid|1080|Block contain values more than that is allowed|account|
|TRANSACTIONS|VOID|400|140|Customer profile not found|2220|Customer profile not found|fdCustomerID|
|TRANSACTIONS|VOID|400|150|Account detail not found|2310|Account detail not found|fdAccountID|
|TRANSACTIONS|VOID|401|401|Unauthorize|4550|Partner is not opt for this service|PartnerID|
|TRANSACTIONS|VOID|400|420|Unauthorized|4250|Session time out|Client-Token|
|TRANSACTIONS|VOID|400|450|Partner Not Found|4500|PartnerID not Found|PartnerID|
|TRANSACTIONS|VOID|500|500|General Error|5110|Please try again after some time, If issue persist please contact customer support|UCOMM_CLEAR_DATA|
|TRANSACTIONS|VOID|500|500|General Error|5340|Configuration Error, Please contact customer support|AES|
|TRANSACTIONS|VOID|500|500|General Error|5340|Configuration Error, Please contact customer support|PublicKey Expired|
