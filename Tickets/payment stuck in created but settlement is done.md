pid : pay_RrbnwChKfm6hPR
gateway : hitachi
status : created
recurring : 1
type : auto
cps 5
gateway curr : inr
curr : inr
https://razorpay-prod.app.coralogix.in/#/query-new/archive-logs?permalink=true&startTime=1765740899000&endTime=1765740901000&logId=c032cfd1-a7e6-4e1d-87b8-30f8a03b4180
this is the log that says pg router failure was there : SERVER_ERROR_PGROUTER_SERVICE_FAILURE"
err message: Unhandled critical exception occured


earlier there was an incident with the same error : https://razorpay.slack.com/archives/C02B75CA8V9/p1744106856043009?thread_ts=1744106236.010789&cid=C02B75CA8V9


message:ERROR_UNMARSHALLING_CPS_RESPONSE_DATA
pg_sdk_str:{"error":"parse error: syntax error near offset 0 of 'Bad Gateway'"}

logs for error https://razorpay-prod.app.coralogix.in/#/query-new/archive-logs?permalink=true&startTime=1765740898000&endTime=1765740900000&logId=cde85388-7c07-426f-88e8-bd1f39b44a62




  ```
public function getByTokenAndCustomerId(string $tokenId, string $customerId)  
{  
    $this->entityName = $this->entity;  
  
    $apiToken = $this->getByTokenAndCustomerIdFromAPI($tokenId, $customerId);  
  
    if ($apiToken != null)  
    {  
        return $apiToken;  
    }  
  
    try  
    {  
        if ((EntityConstants::validateExternalRepoEntity($this->entityName) === true)  
            and $this->validateExternalFetchEnabledForTokens())  
        {  
            return $this->fetchExternalToken([Token\Entity::CUSTOMER_ID => $customerId, Token\Entity::TOKEN => $tokenId]);  
        }  
    }  
    catch (\Throwable $ex)  
    {  
        $this->trace->traceException(  
            $ex,  
            Trace::ERROR,  
            TraceCode::TOKENS_ENTITY_FETCH_FAILURE,  
            [  
                'exception_message' => $ex->getMessage(),  
                'function_name'     => __FUNCTION__  
            ]);  
    }  
  
    return $apiToken;  
}
```
api/app/Models/Base/Traits/ExternalTokensRepo.php
this function is failing: TOKENS_ENTITY_FETCH_FAILURE


```
public function fetchExternalToken($params, $input=[])  
{  
    $class = Entity::getExternalRepoSingleton($this->entity);  
  
    try  
    {  
        $entity = $class->fetchToken($params);  
  
        if (empty($entity) === false)  
        {  
            $relations = $this->getExpandsForQueryFromInput($input);  
  
            $entity->loadMissing($relations);  
  
            return $entity;  
        }  
    }  
    catch (\Throwable $e)  
    {  
        $this->trace->traceException(  
            $e,  
            Trace::ERROR,  
            TraceCode::EXTERNAL_REPO_REQUEST_FAILURE,  
            [  
                'data'        => $e->getMessage(),  
            ]);  
    }  
  
    $data = [  
        'model'      => $this->entityName,  
        'operation'  => 'find'  
    ];  
  
    throw new BadRequestException(  
        ErrorCode::BAD_REQUEST_INVALID_ID, null, $data);  
}
```
for above : https://razorpay-prod.app.coralogix.in/#/query-new/archive-logs?permalink=true&startTime=1765740898000&endTime=1765740900000&logId=7282454f-43d0-4b54-95ae-e56a2f10acc2

"message":"Call to a member function relationLoaded() on null","data":{"data":"Call to a member function relationLoaded() on null"},"class":"Error","code":0}

action item:
- we have received 504 from gateway. 
- raise with hitachi for confirm if it was processed. if yes then kindly ask them to stage the payment and refund the amount.
- we will mark the payment as failed at our end.