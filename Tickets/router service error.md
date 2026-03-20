CB <> RESEED TECHNOLOGIES || Payments are failing with ROUTER_SERVICE_ERROR || 
17746691

sample payment: S3BaA56CFNN95T
checkout id: S3BZxHpnE05Nk0
mid: GmpQbltUPwNeGY
currency USD
order id: order_RzKafBtD4SquM3

1st termianl fetch log :  https://razorpay-prod.app.coralogix.in/#/query-new/archive-logs?permalink=true&startTime=1768268647000&endTime=1768268649000&logId=a0ca61a6-1d3a-44fb-898b-8c6aef164026
{
  "level": "info",
  "ts": 1768268647.516427,
  "caller": "services/terminals.go:1688",
  "msg": "ALL_TERMINAL_IDS_SELECTED_FOR_MERCHANT",
  "request_id": "4905b703517347c3bde2baeb34bc95cc",
  "task_id": "4c145236-3523-4031-9e14-be56d62a6410",
  "mode": "live",
  "route": "/v1/merchants/terminals",
  "debug_enabled": false,
  "response_ids": [],
  "count": 0,
  "count_range": "0",
  "methods_concatenated": "",
  "filters_pattern": "gtw_mid_sts",
  "filters": {
    "terminal_ids": null,
    "merchant_ids": [
      "GmpQbltUPwNeGY"
    ],
    "gateway": "hitachi",
    "gateways": null,
    "org_id": "",
    "status": "pending",
    "statuses": null,
    "procurer": "",
    "methods": null,
    "currency": null,
    "enabled": null,
    "mode": null,
    "features": null,
    "api_type": null,
    "identifiers": null,
    "sub_merchant": false,
    "deleted": false,
    "onboarding_daos": null,
    "gateway_tokens": null,
    "fetch_where_submerchant": null,
    "fetch_secrets": false,
    "gateway_acquirer": "",
    "plan_id": "",
    "type": "",
    "not_equal_filter": {
      "gateways": null,
      "statuses": null,
      "methods": null,
      "currency": null,
      "features": null,
      "api_type": null,
      "terminal_ids": null
    },
    "_": null,
    "duplicates_not_allowed": false
  }
}

then terminal onboarding request occured: ONBOARD_TERMINAL_CREATION_REQUEST_RECEIVED


at internal/onboarding/internal_create_processor.go
if (fulcrumCurrencySupportEnabled && utils.StringSliceInSlice(onboardingDao.Currency, terminal.Currency)) ||  
    (!fulcrumCurrencySupportEnabled && utils.CheckEqualStringSlices(onboardingDao.Currency, terminal.Currency)) {  
    if !shouldUpdateTerminalForDuplicate {  
       rzpErr := rzpError.New(rzperrors.BadRequestTerminalAlreadyExist, "Duplicate terminal request")  
       logger.Error(ctx, rzperrors.PublicCodeBadRequest, "error", rzpErr)  
       return nil, &rzpErr  
    }
here the bad request error is logged means , duplicate terminal found