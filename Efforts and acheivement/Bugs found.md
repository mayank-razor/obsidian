* Payments card -> **Incorrect data retrieval from database <> same epoch** `created_at`  
In payment flow, when pay_init call is sent and if this call is rejected then instant retry occurs and pay_init call is again sent.  
Resulting in chance of exactly same created at for both calls. Sample payment id: `pay_RMN29r19us6VPX`  
Issue occurs here: `order by created_at desc` . Since both created at is same there is no guarantee that latest call will be returned.  
This issue had impacted multiple refunds. Kindly look into it
==thread link==:https://razorpay.slack.com/archives/C024U3B04LD/p1761128775241769

- in mozart amout* 100 is hardcoded
==thread linik==:https://razorpay.slack.com/archives/C7WEGELHJ/p1767350663966839
https://app.devrev.ai/razorpay/works/ISS-1540200

----
In payments-card there is difference in callback.go and capture.go while capturing.
int callback.go is being used in auto capture where we have gaurd that prevents the fee to stay in INR. but that gurad is absent in capture.go
