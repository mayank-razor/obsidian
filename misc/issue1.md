
issue: payment failed due to NTF
checked logs and details : Fulcrum terminal for INR exists with International enabled for the merchant  term_RUqvoUwe1LnKTE
multiple attempts to fetch terminal and onboarding occurred in the logs
we checked the flow and got to know that router made multiple calls.
in 1st call all terminals got fetched
in 2nd call filter applied with hitachi and got result 0 terminals count
retry happened with filter of fulcrum (wrong filter of status pending) and got result 0 terminals count
onboarding for fulcrum terminal call happened here 
one more call sent with correct filter
then it continued with onboard request but failed with duplicate terminal error as it is already live
https://razorpay-prod.app.coralogix.in/#/query-new/archive-logs?id=g7l73JwxECrYebpfWSzDE&time=from:2025-10-21T18:30:00.000Z,to:2025-10-23T21:41:11.000Z&page=0&permalink=true