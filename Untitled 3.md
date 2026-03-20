**Xid issue**

  

[https://razorpay-prod.app.coralogix.in/#/query-new/archive-logs?permalink=true&startTime=1765900385000&endTime=1765900387000&logId=67aba3f2-41c3-4c70-9332-21da960ac7ce](https://razorpay-prod.app.coralogix.in/#/query-new/archive-logs?permalink=true&startTime=1765900385000&endTime=1765900387000&logId=67aba3f2-41c3-4c70-9332-21da960ac7ce)

Issue log

  

  

  

For payment id: RsL5gY1ApakNlP

In logs we found the flow :

Auth _setup -> auth_init -> auth_setup -> auth_setup ->auth_verify -> pay_init -> retries of pay init

But the expected flow is auth_setup ->auth_init->auth_verify -> pay_init

  

For auth_init call:  
**response":{"formatted":{"xid":"MDAwMDAwUnNMNWdZMUFwYWtObFA=","enrolled":"C","enrolled_status_reason":"","acs_url":"","protocol_version":"2.2.0","reason_code":"","gateway_reference_id1":"e8759673-cb7f-498c-9fff-e41f7a006936","gateway_transaction_id1":"c1983e46-4511-45e2-ae57-49f2222e8368","gateway_transaction_id2":"0204f7e7-9402-4bc5-90d8-f3fe1e7c7a3b","amount":15000,"next":{"redirect":{"content":{"MD":"RsL5gY1ApakNlP"},"method":"post","url":"https://authentication.cardinalcommerce.com/ThreeDSecure/V2_1_0/CReq?oid=6740d72b8e93c140e5f3ab62&tid=0204f7e7-9402-4bc5-90d8-f3fe1e7c7a3b","gateway_content":null}},"three_ds_server_trans_id":"","acs_trans_id":"","challenge_window_size":"","payment_id":"","payload":"","sdkTransID":"","acsRenderingType":null,"acsSignedContent":"","acs_reference_number":"","directory_server_public_key":""}**

  

**Here we have xid but due to 2 extra auth_setup calls it was overwritten. Resulting in validation failure**

  

Upon comparing the all 3 auth_setup calls, i found no anomalies between them.

Since this is checkout payment we don’t have option of clarity here.

  

**PAYMENT_REDIRECT_RESPONSE** for auth_init call [https://razorpay-prod.app.coralogix.in/#/query-new/archive-logs?permalink=true&startTime=1765900383000&endTime=1765900385000&logId=d29686f8-a9b3-46fb-b8ca-8ce6de04c3bf](https://razorpay-prod.app.coralogix.in/#/query-new/archive-logs?permalink=true&startTime=1765900383000&endTime=1765900385000&logId=d29686f8-a9b3-46fb-b8ca-8ce6de04c3bf)

  

Just after the auth init call response. We can see **PAYMENT_REDIRECT_REQUEST which is for that extra auth_setup call** [**https://razorpay-prod.app.coralogix.in/#/query-new/archive-logs?permalink=true&startTime=1765900385000&endTime=1765900387000&logId=67aba3f2-41c3-4c70-9332-21da960ac7ce**](https://razorpay-prod.app.coralogix.in/#/query-new/archive-logs?permalink=true&startTime=1765900385000&endTime=1765900387000&logId=67aba3f2-41c3-4c70-9332-21da960ac7ce)

  

After this call again we saw **PAYMENT_REDIRECT_REQUEST for another auth_setup call:**[**https://razorpay-prod.app.coralogix.in/#/query-new/archive-logs?permalink=true&startTime=1765900386000&endTime=1765900388000&logId=85c5ff59-1d9a-4af3-ab21-828c21977309**](https://razorpay-prod.app.coralogix.in/#/query-new/archive-logs?permalink=true&startTime=1765900386000&endTime=1765900388000&logId=85c5ff59-1d9a-4af3-ab21-828c21977309)

  

After this we can find the log of auth_verify: **MOZART_REQUEST_RESPONSE** [**https://razorpay-prod.app.coralogix.in/#/query-new/archive-logs?permalink=true&startTime=1765900398000&endTime=1765900400000&logId=5e0a56db-1153-45f3-a1ca-73c01da4ffd7**](https://razorpay-prod.app.coralogix.in/#/query-new/archive-logs?permalink=true&startTime=1765900398000&endTime=1765900400000&logId=5e0a56db-1153-45f3-a1ca-73c01da4ffd7)

  

  

  

Here is the comparison with success case for same merchant and same terminal:  
failed payment: RsL5gY1ApakNlP

Success payment : Ra3EBgP6OBVSLz  
follow image is comparison of pay_init request body where 1st image is of failed payment and other is of captured

  

  

  

1st image is of failed case pay_init request body and other one is of success case.

  

Above image is comparison of auth_init response body , 1st one is of failed case and other is of success case