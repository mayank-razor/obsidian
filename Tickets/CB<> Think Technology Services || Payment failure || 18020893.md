
for payment id:
SBekAZLxAq7qQL
the payment failed with ROUTER_SERVICE_ERROR

in logs we have log of TIMEOUT_terminals_service (POST https://terminals-live.razorpay.com/v1/merchants/terminals giving up after 3 attempts) 
https://razorpay-prod.app.coralogix.in/#/query-new/archive-logs?permalink=true&startTime=1770118053000&endTime=1770118055000&logId=e1e50473-f1d9-4136-a50e-90b22f73dd22

for 1st attempt
1st call -> no terminal found
"filters": {
    "terminal_ids": null,
    "merchant_ids": [
      "CjdO1M5YLsir2h"
    ],
    "gateway": "hitachi",
    "gateways": null,
    "org_id": "",
    "status": "pending",


2nd call -> 8 terminals found
"filters": {
    "terminal_ids": null,
    "merchant_ids": [
      "CjdO1M5YLsir2h"
    ],
    "gateway": "hitachi",
    "gateways": null,
    "org_id": "",
    "status": "",
3rd call -> 8 terminals found
"filters": {
    "terminal_ids": null,
    "merchant_ids": [
      "CjdO1M5YLsir2h"
    ],
    "gateway": "hitachi",
    "gateways": null,
    "org_id": "",
    "status": "",

4th call -> 0 terminals found
"filters": {
    "terminal_ids": null,
    "merchant_ids": [
      "CjdO1M5YLsir2h"
    ],
    "gateway": "fulcrum",
    "gateways": null,
    "org_id": "",
    "status": "pending",

5th call -> 10 terminals found
"filters": {
    "terminal_ids": null,
    "merchant_ids": [
      "CjdO1M5YLsir2h"
    ],
    "gateway": "fulcrum",
    "gateways": null,
    "org_id": "",
    "status": "",
  6th call ->10 terminals found
"filters": {
    "terminal_ids": null,
    "merchant_ids": [
      "CjdO1M5YLsir2h"
    ],
    "gateway": "fulcrum",
    "gateways": null,
    "org_id": "",
    "status": "",
  then I could found any rule evaluation logs, also for all the onboarding request, it is failing with duplicate terminal.
  in 2nd and 3rd attempt we have similar logs
  reference logs for terminal fetch attempts: https://razorpay-prod.app.coralogix.in/#/query-new/archive-logs?id=JS84ZEBNuglRffw1IDUSc&time=from:2026-02-02T12:30:08.574Z,to:2026-02-04T12:35:08.574Z&page=2&permalink=true