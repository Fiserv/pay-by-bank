# Authorization Response Code List

|AUTH RESPONSE|HTTP STATUS CODE|TRANSACTION STATUS|TRANSACTION STATUS CODE|TRANSACTION STATUS DESC|TRANSACTION ERROR CODE|TRANSACTION ERROR KEY |TRANSACTION ERROR DESC|
|-------------|----------------|------------------|-----------------------|-----------------------|----------------------|----------------------|----------------------|
|07|200|APPROVED|0|Approved||||
|19|200|APPROVED|0|Approved but issued on a Function Z Preferred||||
|26|200|APPROVED|0|Adjustment accepted for processing||||
|45|200|APPROVED|0|Approved but no guarantee for it Being Settled||||
|71|200|APPROVED|0|The transactions have verified approval and has been accepted ||||
|95|200|APPROVED|0|Preferred response approval||||
|OK|200|APPROVED|0|Accepted||||
|03|400|DECLINED|130|130|Partner Cannot Be Validated|2130|Merchant does not exist||
|11|400|DECLINED|460|Illegal Function|6010|An ECA transaction where decline is received post successful accept|which user cannot un-accept|
|08|400|DECLINED|460|Negative Decline|6020|The transaction was rejected|received code 4 (Negatives on file)|
|12|400|DECLINED|460|Recurring Payment Revoked|6030|Merchant with Recurring Product having RevokedAuthorizations addOn enabled but the ID got revoked|
|24|400|DECLINED|120|Consumer Cannot Be Validated|2010|The enrollment record was not found or is inactive|
|25|400|DECLINED|460|Ineligible|6040|The transactions is not eligible for Electronic Conversion or Draft|
|28|400|DECLINED|460|Pin Attempts Exceeded|6050|The pin attempts exceeded MAX number allowed for this transaction|
|31|400|DECLINED|460|No Transactions|6070|Partner is not opt for this service|
|37|400|DECLINED|460|Function Not Available|6080|Function is not available for this Merchant|
|41|400|DECLINED|460|Store Not Active|6090|The store has a non-active|canceled|or suspended merchant account|
|46|400|DECLINED|460|Transaction Not Valid|6100|The transaction is not a valid transaction for store|
|53|400|DECLINED|460|Authorization Error|6110|The transaction was subtracted from store|setting chargeable to 0|
|73|400|DECLINED|460|Code 4 decline/ Negative Decline|4310|Code 4 decline/ Negative Decline|
|76|400|DECLINED|460|Trans Union Number Not Found|6120|The Trans Union Number is Not Found In Store Records|
|82|400|DECLINED|409|Conflict|4970|There can not be a duplicate transaction used for an ECA sale|
|88|400|DECLINED|460|Code 3 is a Risk Decline|6140|Risk Decline/Business evaluation failed|
|09|400|DECLINED|460|More Information Needed|6150|Profile - Code 0 - Name and Bank needed (Need more information)|
|78|400|ERROR|Input is invalid|6130|The transactions has an  Invalid RT|
|15|400|ERROR|400|Cannot Be Blank|6160|Certain fields within the transactions data can not be blank|transactions will not be accepted|
|20|400|ERROR|100|Input is invalid|1030|TERMINAL ID missing on Enrollment record|
|27|400|ERROR|100|Input is invalid|1020|The transactions has an invalid or missing value in one or more fields|
|29|400|ERROR|100|Input is invalid|1010|The pin that is trying to be used for this transaction is invalid|
|40|400|ERROR|100|Input is invalid|1010|Zip Code did not have a valid value|
|49|400|ERROR|400|Processor not Available|6170|Issued whenever Payroll Extended Response is requested during FEP|
|79|400|ERROR|400|ECA change failed|6190|The transactions failed for an ECA change with an invalid ECA refund|
|80|400|ERROR|400|Invalid Amount|6200|Refund or partial amount is > original sale amount|
|81|400|ERROR|400|Original Transaction Not Found|6210|The requested action failed|the original transaction was not found in our records|
|83|400|ERROR|400|Prompt For 2ND ID|6220|The transaction was prompted for a second ID for processing|
|84|400|ERROR|400|Prompt For MICR|6230|The transaction was prompted for MICR|MICR does not match|
|85|400|ERROR|400|Prompt For MICR and ID|6250|The transaction was prompted for the MICR and ID|because the 2nd ID and MIRC are absent|
<!--In the documentation Anoop shared it mentions code 6250 however in the PDF it says the code is 6350 need clarification   -->
|86|400|ERROR|400|Send Check Images|6360|The check cannot be verified|send images If merchant is check 21 only|no images allowed|
|89|400|ERROR|400|DL Invalid|6370|The ID that is given on transactions is invalid  Drivers License|
|75|400|ERROR|400|Card Not Active|6380|The merchant/customer (PLC) card is not active|need voice confirmation|
|98|400|ERROR|100|Input is invalid|1070|The MICR for the transaction could not be detected/found|
|NAK|400|ERROR|400|Authorization Error|6390|Adjustment cannot be processed|
|44|400|ERROR|500|General Error|5330|Please try again after some time|If issue persist please contact customer support|
|69|400|ERROR|500|General Error|5331|Call center must be contacted after a transaction received an invalid response Auth request|
|96|400|ERROR|500|General Error|5332|The call to the  Merchant Data service has time out|
|97|400|ERROR|500|General Error|5333|We were unable to process the record for this transaction|
|16|400|ERROR|500|General Error|5334|This a a generic error message for computer failure|transactions cannot be completed|