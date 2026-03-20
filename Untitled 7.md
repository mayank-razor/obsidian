**Postman run timestamps**

Run 1  4:00:35pm 2 iterations duration 6s 78ms

Run 2 4:02:17 pm 295 iterations durations: 8m 12 s

Run 3  10:57:05 pm 13264 iterations duration 3h 38 min

  

  

  

  

Payments getting auto refunded

In past week we have observed that we are getting tickets for issue - payment was refunded instead of capture.

Auto capture for the merchant was enabled and payment was NOT late auth still it was refunded

Upon checking logs we found logs saying that auto_capture is false for the merchant. There are successful payments also for the merchant where we can see the auto capture happened

Reference tickets: [ISS-1476106](https://app.devrev.ai/razorpay/works/ISS-1476106), [**ISS-1477741**](https://app.devrev.ai/razorpay/works/ISS-1477741)**Ticket**  [ISS-1476106](https://app.devrev.ai/razorpay/works/ISS-1476106)  
success case: Rmxc6AKfVMIgTJ

Failed case : RjUWvjUng1CnBx

  

**Ticket**  [**ISS-1477741**](https://app.devrev.ai/razorpay/works/ISS-1477741)

Success case: RlYqdY59cfZVH1, RnBdoQzLUA3ohN

Failed case: RloTnZesnjXyVo