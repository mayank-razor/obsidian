

caller:core/capture.go:670

cluster:cde-blue-eks

flag:F

k8s_container_name:pg-router-dark

k8s_namespace_name:pg-router-dark

k8s_pod_name:pg

log:{"level":"INFO","time":"2026-02-03T14:15:08.631Z","caller":"core/capture.go:670","message":"DEBUG_adjustPaymentAmount_entry","context":{"amazon_trace_id":"Root=1-698202ea-4f69b62977e0d9836f3a95ed","razorpay_request_id":"876a1d22-587a-4d56-89cc-126e17b6531f","request_id":"571287d8c3a64743bacdad8e1d077fa7","route_name":"v1/payments/{paymentId}/callback/{hash}","task_id":"876a1d22-587a-4d56-89cc-126e17b6531f","trace_id":"0e36967ad04ac1b6-394819e6a5e0ee15","uri":"/v1/payments/pay_SBha8F63GRWTz6/callback/6034a412d82d8be73fec25a4369f116845f35809"},"pg_sdk":{"amount":103,"convenience_fee":0,"currency":"USD","fee":271,"fee_bearer":"customer","international":true,"mcc_forex_rate":90.225614,"merchant_id":"M48sRU8t4YD2P4","payment_id":"SBha8F63GRWTz6"}}

log_context_task_id:876a1d22-587a-4d56-89cc-126e17b6531f

merchant_id:M48sRU8t4YD2P4

message:DEBUG_adjustPaymentAmount_entry

request_id:571287d8c3a64743bacdad8e1d077fa7

stream:stdout

tailed_file:/var/log/containers/pg-router-dark-5b6f4985b9-trk7w_pg-router-dark_pg-router-dark-eb3ccc58fd9d7ad2a73dc912d54e5f9a91f27ba316874b8c75d1dac4e9f88322.log

task_id:876a1d22-587a-4d56-89cc-126e17b6531f

time:2026-02-03T14:15:08.631279686Z

uri:/v1/payments/pay_SBha8F63GRWTz6/callback/6034a412d82d8be73fec25a4369f116845f35809

pg-router-dark

pg-router-dark

  

03/02/2026 19:45:08.653

DEBUG_adjustPaymentAmount_conditions

caller:core/capture.go:687

cluster:cde-blue-eks

flag:F

k8s_container_name:pg-router-dark

k8s_namespace_name:pg-router-dark

k8s_pod_name:pg

log:{"level":"INFO","time":"2026-02-03T14:15:08.653Z","caller":"core/capture.go:687","message":"DEBUG_adjustPaymentAmount_conditions","context":{"amazon_trace_id":"Root=1-698202ea-4f69b62977e0d9836f3a95ed","razorpay_request_id":"876a1d22-587a-4d56-89cc-126e17b6531f","request_id":"571287d8c3a64743bacdad8e1d077fa7","route_name":"v1/payments/{paymentId}/callback/{hash}","task_id":"876a1d22-587a-4d56-89cc-126e17b6531f","trace_id":"0e36967ad04ac1b6-394819e6a5e0ee15","uri":"/v1/payments/pay_SBha8F63GRWTz6/callback/6034a412d82d8be73fec25a4369f116845f35809"},"pg_sdk":{"combined_condition_result":true,"is_payment_international":true,"is_splitz_enabled_for_non_inr":true,"payment_id":"SBha8F63GRWTz6"}}

log_context_task_id:876a1d22-587a-4d56-89cc-126e17b6531f

message:DEBUG_adjustPaymentAmount_conditions

request_id:571287d8c3a64743bacdad8e1d077fa7

stream:stdout

tailed_file:/var/log/containers/pg-router-dark-5b6f4985b9-trk7w_pg-router-dark_pg-router-dark-eb3ccc58fd9d7ad2a73dc912d54e5f9a91f27ba316874b8c75d1dac4e9f88322.log

task_id:876a1d22-587a-4d56-89cc-126e17b6531f

time:2026-02-03T14:15:08.653254099Z

uri:/v1/payments/pay_SBha8F63GRWTz6/callback/6034a412d82d8be73fec25a4369f116845f35809

pg-router-dark

pg-router-dark

03/02/2026 19:45:08.653

adjusting_order_amount_paid_for_non_INR

caller:core/capture.go:708

cluster:cde-blue-eks

flag:F

k8s_container_name:pg-router-dark

k8s_namespace_name:pg-router-dark

k8s_pod_name:pg

log:{"level":"INFO","time":"2026-02-03T14:15:08.653Z","caller":"core/capture.go:708","message":"adjusting_order_amount_paid_for_non_INR","context":{"amazon_trace_id":"Root=1-698202ea-4f69b62977e0d9836f3a95ed","razorpay_request_id":"876a1d22-587a-4d56-89cc-126e17b6531f","request_id":"571287d8c3a64743bacdad8e1d077fa7","route_name":"v1/payments/{paymentId}/callback/{hash}","task_id":"876a1d22-587a-4d56-89cc-126e17b6531f","trace_id":"0e36967ad04ac1b6-394819e6a5e0ee15","uri":"/v1/payments/pay_SBha8F63GRWTz6/callback/6034a412d82d8be73fec25a4369f116845f35809"},"pg_sdk":{"amount":99,"convertedFee":4,"currency":"USD","international":true,"mccForexRate":90.225614}}

log_context_task_id:876a1d22-587a-4d56-89cc-126e17b6531f

message:adjusting_order_amount_paid_for_non_INR

request_id:571287d8c3a64743bacdad8e1d077fa7

stream:stdout

tailed_file:/var/log/containers/pg-router-dark-5b6f4985b9-trk7w_pg-router-dark_pg-router-dark-eb3ccc58fd9d7ad2a73dc912d54e5f9a91f27ba316874b8c75d1dac4e9f88322.log

task_id:876a1d22-587a-4d56-89cc-126e17b6531f

time:2026-02-03T14:15:08.653283059Z

uri:/v1/payments/pay_SBha8F63GRWTz6/callback/6034a412d82d8be73fec25a4369f116845f35809

pg-router-dark

pg-router-dark

03/02/2026 19:45:08.653

ORDER_AMOUNT_ADJUST

caller:core/capture.go:239

cluster:cde-blue-eks

flag:F

k8s_container_name:pg-router-dark

k8s_namespace_name:pg-router-dark

k8s_pod_name:pg

log:{"level":"INFO","time":"2026-02-03T14:15:08.653Z","caller":"core/capture.go:239","message":"ORDER_AMOUNT_ADJUST","context":{"amazon_trace_id":"Root=1-698202ea-4f69b62977e0d9836f3a95ed","razorpay_request_id":"876a1d22-587a-4d56-89cc-126e17b6531f","request_id":"571287d8c3a64743bacdad8e1d077fa7","route_name":"v1/payments/{paymentId}/callback/{hash}","task_id":"876a1d22-587a-4d56-89cc-126e17b6531f","trace_id":"0e36967ad04ac1b6-394819e6a5e0ee15","uri":"/v1/payments/pay_SBha8F63GRWTz6/callback/6034a412d82d8be73fec25a4369f116845f35809"},"pg_sdk":{"adjusted_amount":99,"convenience_fee_and_gst":0,"discount_amount":0,"fee_bearer":"customer","is_partial_order":false,"merchant_id":"M48sRU8t4YD2P4","order_amount":103,"order_status":null,"payment_amount":103,"payment_id":"SBha8F63GRWTz6","released_amount":0}}

log_context_task_id:876a1d22-587a-4d56-89cc-126e17b6531f

merchant_id:M48sRU8t4YD2P4

message:ORDER_AMOUNT_ADJUST

request_id:571287d8c3a64743bacdad8e1d077fa7

stream:stdout

tailed_file:/var/log/containers/pg-router-dark-5b6f4985b9-trk7w_pg-router-dark_pg-router-dark-eb3ccc58fd9d7ad2a73dc912d54e5f9a91f27ba316874b8c75d1dac4e9f88322.log

task_id:876a1d22-587a-4d56-89cc-126e17b6531f

time:2026-02-03T14:15:08.653425348Z

uri:/v1/payments/pay_SBha8F63GRWTz6/callback/6034a412d82d8be73fec25a4369f116845f35809

pg-router-dark

pg-router-dark

03/02/2026 19:45:08.653

ADJUST_ORDER_PAID

caller:core/capture.go:612

cluster:cde-blue-eks

flag:F

k8s_container_name:pg-router-dark

k8s_namespace_name:pg-router-dark

k8s_pod_name:pg

log:{"level":"INFO","time":"2026-02-03T14:15:08.653Z","caller":"core/capture.go:612","message":"ADJUST_ORDER_PAID","context":{"amazon_trace_id":"Root=1-698202ea-4f69b62977e0d9836f3a95ed","razorpay_request_id":"876a1d22-587a-4d56-89cc-126e17b6531f","request_id":"571287d8c3a64743bacdad8e1d077fa7","route_name":"v1/payments/{paymentId}/callback/{hash}","task_id":"876a1d22-587a-4d56-89cc-126e17b6531f","trace_id":"0e36967ad04ac1b6-394819e6a5e0ee15","uri":"/v1/payments/pay_SBha8F63GRWTz6/callback/6034a412d82d8be73fec25a4369f116845f35809"},"pg_sdk":{"convenienceFee":0,"convenienceFeeGst":0,"currentPaidAmount":99,"discountAmount":0,"fee":271,"feeBearer":"customer","modifiedOrder":false,"newPaidAmount":-168,"orderAmountPaid":99,"originalOrderPaidAmount":0,"paymentAmount":103,"paymentID":"SBha8F63GRWTz6","releasedAmount":0}}

log_context_task_id:876a1d22-587a-4d56-89cc-126e17b6531f

message:ADJUST_ORDER_PAID

request_id:571287d8c3a64743bacdad8e1d077fa7

stream:stdout

tailed_file:/var/log/containers/pg-router-dark-5b6f4985b9-trk7w_pg-router-dark_pg-router-dark-eb3ccc58fd9d7ad2a73dc912d54e5f9a91f27ba316874b8c75d1dac4e9f88322.log

task_id:876a1d22-587a-4d56-89cc-126e17b6531f

time:2026-02-03T14:15:08.653445771Z

uri:/v1/payments/pay_SBha8F63GRWTz6/callback/6034a412d82d8be73fec25a4369f116845f35809