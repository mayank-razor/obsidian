for pid S6P48ecMvHhukL
```{

"caller": {

"File": "/go/src/github.com/razorpay/mozart/app/logger/logrus_logger.go",

"Line": 250,

"Name": "(*LogrusLogger).Log"

},

"content": {

"acctNumber": "********",

"acctType": "03",

"acquirerBIN": "411075",

"acquirerMerchantID": "JI1lNgG0l0rfyH",

"billAddrCity": "Bangalore",

"billAddrCountry": "356",

"brand": "VISA",

"browserAcceptHeader": "*/*",

"browserColorDepth": "32",

"browserIP": "********",

"browserJavaEnabled": "true",

"browserJavascriptEnabled": "true",

"browserLanguage": "en",

"browserScreenHeight": "100",

"browserScreenWidth": "23",

"browserTZ": "0",

"browserUserAgent": "********",

"callBackURL": "https://api.razorpay.com/pg_router/v1/payments/pay_S6P48ecMvHhukL/callback/dc8e302f9b71082b328a84b3f798bb7311156633",

"cardExpiryDate": "********",

"cardholderName": "********",

"deviceChannel": "02",

"deviceRenderOptions": {

"sdkInterface": "03",

"sdkUiType": [

"01",

"02",

"03",

"04",

"05"

]

},

"email": "noreply-VPA_MASKED.com",

"mcc": "5411",

"merchantCountryCode": "356",

"merchantName": "Blinkit",

"messageCategory": "01",

"messageType": "pArq",

"messageVersion": "2.2.0",

"notificationURL": "https://api.razorpay.com/pg_router/v1/payments/pay_S6P48ecMvHhukL/callback/dc8e302f9b71082b328a84b3f798bb7311156633",

"p_messageVersion": "1.0.5",

"purchaseAmount": 42100,

"purchaseCurrency": "356",

"purchaseDate": "20260121045225",

"purchaseExponent": 2,

"sdkAppID": null,

"sdkEncData": null,

"sdkEphemPubKey": null,

"sdkMaxTimeout": "06",

"sdkReferenceNumber": null,

"sdkTransID": null,

"shipAddrCountry": "356",

"shipAddrPostCode": "840",

"threeDSCompInd": "N",

"threeDSRequestorAuthenticationInd": "01",

"threeDSRequestorChallengeInd": "01",

"threeDSRequestorID": "10075249*JI1lNgG0l0rfyH",

"threeDSRequestorName": "BLINK COMMERCE PRIVATE LIMITED",

"threeDSRequestorURL": "https://ul.com/9cf15144-95ad-4134-af7e-fae578839444",

"transType": "01",

"zealMacIIID": "********",

"zealMacIIPwd": "********"

},

"external_trace_id": "dab9236a-23c4-4ab7-83ad-049103a63abe",

"header": {

"Content-Type": "application/json"

},

"host": "mozart-whitelisted.razorpay.com",

"level": "info",

"method": "POST",

"msg": "GATEWAY_REQUESTDATA",

"referer": "",

"request_id": "d5o5n2bnrb5c71ebt4dg",

"time": "2026-01-21T04:52:25.273291452Z",

"uri": "/cardPayments/mpi_blade/v2/authenticate_init",

"url": "https://emv-3ds-server.razorpay.com/ZealMac2Server/Transaction/2.0/authRequest"

}
```

this was the gateway request and the validation failed with "Conditional Evaluate\\\\",\\\\"step_name\\\\":\\\\"ares_error_check\\\\"

upon check the step executed log we found: https://razorpay-prod.app.coralogix.in/#/query-new/archive-logs?permalink=true&startTime=1768971144000&endTime=1768971146000&logId=9cbc4cf3-98de-48b4-95bd-b02a99324614

relevant logs:
https://razorpay-prod.app.coralogix.in/#/query-new/archive-logs?id=ao1iEnNqkC5raZttwaZFq&time=from:2026-01-21T04:52:25.200Z,to:2026-01-21T04:52:26.300Z&page=0&permalink=true
![[Screenshot 2026-01-24 at 8.33.23 PM.png]]
impacted case : left, success case right(S6PHNmHkWFqPER).
upon comparing with success case with only found that 
1) "acquirerMerchantID" is in different format for the impacted, and its same for other impacted ids also
2) "threeDSServerOperatorID" field is missing in impacted payments