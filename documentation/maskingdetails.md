# If client has elected to masking here are the following attributes with details and examples

|Field Name| Groups| Masking Format|
|----------|------------------|---------------------------------------|
|first Name|getPersonalDetails|Display only first letter (ex. A**** ) |
|last Name| getPersonalDetails|Display only first letter (ex. L**** ) |
|Gender| getPersonalDetails| Full Masked (Ex. * )|
|DOB| getPersonalDetails|(ex. 1978**02|
|Phone Number [i] | getPersonalDetails| ******2342|
|Phone Type [i] | getPersonalDetails| No Masking|
|Primary Phone [i] | getPersonalDetails| No Masking|
|Drivers License Number | getIdentificationDetails| No Masking |
|Drivers License State| getIdentificationDetails| No Masking|
|SSN| getIdentificationDetails|Display only last digit (ex. ********4)|
|Street Address| getAddressDetails|Display first 2 and last 5 (ex. 12** *********ng Dr.|
|Street Address 2| getAddressDetails| Display last 3 (ex. *******311|
|City| getAddressDetails| No Masking|
|State| getAddressDetails| No Masking|
|Postal Code| getAddressDetails| Display only last 2 ex. ***62|
|Country| getAddressDetails| No Masking|
|Connectpay Payment Number| getCardDetails| Display only last 4 ex. *****5462|
|ConsumerStatus| getCardDetails| No Masking|
|ValidationStatus| getCardDetails| No Masking|
|BankName | getBankDetails| No Masking|(ex. Wells Fargo)|
|Routing Number|  getBankDetails| Display only last 4 ex. *****5462|
|Account Number| getBankDetails| Display only last 4 ex. *****1122|
|corporateAccountFlag | getBankDetails||
|Security Question ID [i]|getSecurityQuestionDetails| No Masking|
|Security Question [i] ]|getSecurityQuestionDetails| No Masking|
|Member Date| getOtherDetails| Display only first 4 ex. 2007****|
|TnC Version| getOtherDetails|No Masking|
|Generic Code 1| getOtherDetails| Display only last 4 ex. *****5462|
|Generic Code 2| getOtherDetails| Display only last 4 ex. *****5463|
|Generic Code 3| getOtherDetails| Display only last 4 ex. *****5464|
|Generic Flag 1| getOtherDetails| Display only last 4 ex. *****5465|
|Generic Flag 2| getOtherDetails| Display only last 4 ex. *****5466|
|Generic Flag 3|getOtherDetails| Display only last 4 ex. *****5467|
|Reporting Field 1| getReportingDetails| Display only last 4 ex. *****5468|
|Reporting Field 2| getReportingDetails| Display only last 4 ex. *****5469|
|Reporting Field 3|getReportingDetails| Display only last 4 ex. *****5470|