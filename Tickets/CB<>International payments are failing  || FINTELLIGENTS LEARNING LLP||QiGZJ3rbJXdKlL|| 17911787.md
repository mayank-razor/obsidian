
impacted ids: 
S9OpV73WVbUhB7 S9OusVJbgtQ0QX
for pid : S9OpV73WVbUhB7
gateway hitachi:
terminal id: RjwVzMZ4WTVQEL
order id :order_S9OnKGzJYZJDwV -> 2 attempts 
card id: card_S9OpV73WVbUhB7

here flow happened: auth setup , auth init , auth setup , auth setup, auth verify , pay init, smart retry.

In logs we found the flow :

```
auth _setup -&gt; auth_init -&gt; auth_setup -&gt; auth_setup -&gt;auth_verify -&gt; pay_init -&gt; retries of pay init
```

But the expected flow is:

```
 auth_setup -&gt;auth_init-&gt;auth_verify -&gt; pay_init
```

we are getting validation failure in pay_init
```
{"code":"BAD_REQUEST_VALIDATION_FAILURE","description":"INPUT_VALIDATION_FAILED {\\\\"component\\\\":\\\\"Validate\\\\",\\\\"data\\\\":\\\\"{\\\\\\\\\\\\"actions.authenticate_init.xid\\\\\\\\\\\\":[\\\\\\\\\\\\"The actions.authenticate_init.xid field is required\\\\\\\\\\\\"]}\\\\",\\\\"message\\\\":\\\\"Error performing validation\\\\",\\\\"step_name\\\\":\\\\"Validator\\\\"}"
```

here xid is missing.

but in the auth init call we can see that xid is present
```
{"xid":"MDAwMDAwUzlPcFY3M1dWYlVoQjc="
```

here the extra auth_setup calls have wiped the value of xid causing the validation failure![[Screenshot 2026-02-02 at 11.52.12 AM.png]]
1st auth_setup call: MOZART_REQUEST_RESPONSE https://razorpay-prod.app.coralogix.in/#/query-new/archive-logs?permalink=true&startTime=1769625330000&endTime=1769625332000&logId=b6a0f805-c6d1-484a-baed-4cb87eb1d29e
auth_init call : MOZART_REQUEST_RESPONSE https://razorpay-prod.app.coralogix.in/#/query-new/archive-logs?permalink=true&startTime=1769625338000&endTime=1769625340000&logId=8ebafbd8-7810-4417-b76a-73ae666141df
2nd auth_setup call: MOZART_REQUEST_RESPONSE https://razorpay-prod.app.coralogix.in/#/query-new/archive-logs?permalink=true&startTime=1769625339000&endTime=1769625341000&logId=ae6bdc6d-2180-4871-99b4-c6511c2f3626
3rd auth_setup call: MOZART_REQUEST_RESPONSE https://razorpay-prod.app.coralogix.in/#/query-new/archive-logs?permalink=true&startTime=1769625340000&endTime=1769625342000&logId=843d142e-a85d-4214-8512-6ce87a9a6de6
auth_verify call: MOZART_REQUEST_RESPONSE https://razorpay-prod.app.coralogix.in/#/query-new/archive-logs?permalink=true&startTime=1769625359000&endTime=1769625361000&logId=97406f09-a712-4693-ae67-85e208c0e89b

