1) fixed issue in dashboard repo where currency exponent was not being used to covert between major and minor instead there was hardcoding of * 100 and / 100. fixed this to use the exponent conversion of amount
==pr link==: https://github.com/razorpay/dashboard/pull/18409/files

2) fixed issue of incorrect cvv check of amex card, earlier it was 3 or 4 digit, now it is only 4 digit
==pr link==:https://github.com/razorpay/payments-card/pull/4834

3) fixed issue of fee conversion handling while adjust the amount for CFB MCC payment post capture scenerio
==pr link==:https://github.com/razorpay/pg-router/pull/4267/commits

4) fixed currency bug in i18nify repo that was causing error at checkout page, incorrect currency data was present in the repo
==pr link==:https://github.com/razorpay/i18nify/pull/603

