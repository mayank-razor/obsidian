**G**

  

Set Git username ->p

Set Git email ->p

  

Git add .

Read data

Git commit {$data}

  

Git push

  

Set Git username ->c

Set Git email ->c

  

**Total Tickets Analyzed:** 16

**Breakdown by Priority:**

- **P0 (Critical):** 1 ticket (6%)
- **P1 (High):** 5 tickets (31%)
- **P2 (Medium):** 10 tickets (63%)

**Breakdown by Status:**

- **Escalated:** 3 tickets (19%)
- **Understood:** 13 tickets (81%)

**Breakdown by Inferred Issue Type:**

- **Technical Error:** 5 tickets
- **Forex & Currency:** 4 tickets
- **International Payments:** 3 tickets
- **Success Rate:** 2 tickets
- **Refunds:** 1 ticket
- **Payment Lifecycle:** 1 ticket

  

  

Discussed with @gokul, @abhishek , this is an existing issue only where the payment is going into non reach and the reason for this is the fee bearer is dynamic. 

  

Escalated ticket to drev

Analysed SR drop ticket

  

  

POD/Group: Pse cross border core

Total Open Tickets: 5

P0/P1: 1

PSE: 5

Engg: 0

Pre Sept:0

Sept: (edited) 5


  

[REDACTED - GitHub Token Removed]

  

  

Gopi Varun

Avantika Gupta

  

Razor1234@! -> dashboard

  

Fee apis -> check , its also getting multiplied by 100x

Refund call check -> request to backend is also 100x

Sub text below the refund amount that is also 100x

  

  

Talk dev is currency convert flag need to be enabled to get international transactions

  

{

    "orderUpdate": "true",

    "order_id": "ROhHyTpGV52T94",

    "merchant_id":"PgvgiE0fVDekFU",

    "payload":

    {

        "status": “paid”

    }

}

  

  

i've not checked this. but can you cross check with any devs whom you know if they have added any condition for max amount?

[10:40](https://razorpay.slack.com/archives/D09HN2L6CM8/p1759900251860779)

even i'm not sure on why max amount is not populated

[10:41](https://razorpay.slack.com/archives/D09HN2L6CM8/p1759900298547179)

was that passed in creation.(if recurring token then i believe it should be mandatory)  if yes on what condition is it expected to be set.

  

  

  

  

02/10/2025 23:38:17.837 at here payment was authorised , found both in order logs and payments logs

  

  

For international  we don’t set default max_amount, and we are not receiving the max_amount , and I have checked the payments they are of type CAW not subscripton

  

  

  

  

  

[4:58](https://razorpay.slack.com/archives/D09F2510WJU/p1761218904398669)

{

    "status": "captured",

    "refund_status": "null",

    "amount_refunded": 0

}

  

  

  

  

  

https://razorpay.slack.com/archives/C7WEGELHJ/p1761223132437589?thread_ts=1760700843.641349&cid=C7WEGELHJ