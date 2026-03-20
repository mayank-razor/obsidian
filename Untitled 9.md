  

**Request refund  team to fix** 

  

  

  

We have check 

  

[**[ISS-1445389]**](https://app.devrev.ai/razorpay/works/ISS-1445389) -> callout for query 

  

  

  

  

  

  

—

public function getEnabledFeatures(): array

{

    $merchantId = $this->getId();

  

    // For HTTP requests, use static cache optimization

    // For worker requests, use instance-level cache (current approach)

    if ($this->isWorkerOrTestCaseRunning() === false)

    {

        // HTTP request - check static cache first (keyed by merchant ID)

        if (isset(self::_$loadedFeatures_[$merchantId]))

        {

            app('trace')->debug(

                TraceCode::_FEATURES_FETCH_FROM_CACHE_,

                [

                    "features" => self::_$loadedFeatures_[$merchantId],

                    "merchantID" => $merchantId,

                    "cache_type" => "static_cache"

                ]

            );

            return self::_$loadedFeatures_[$merchantId];

        }

    }

    else

    {

        // Worker request - use instance-level cache (current approach)

        if ($this->instanceLoadedFeatures !== null)

        {

            app('trace')->debug(

                TraceCode::_FEATURES_FETCH_FROM_CACHE_,

                [

                    "features" => $this->instanceLoadedFeatures,

                    "merchantID" => $merchantId,

                    "cache_type" => "instance_cache"

                ]

            );

  

            return $this->instanceLoadedFeatures;

        }

    }

  

    $cacheTtl = app('repo')->feature->getCacheTtl(Feature\Entity::_FEATURE_);

  

    if (Pricing\Repository::_shouldDistributeQueryCacheLoad_($this) === true)

    {

        $cacheTags = Feature\Entity::_getDistrubutedCacheTagsForNames_($this->entity, $this->getId());

    }

    else

    {

        $cacheTags = Feature\Entity::_getCacheTagsForNames_($this->entity, $this->getId());

    }

  

    $apiResponse = $this->features()

                         ->remember($cacheTtl)

                         ->cacheTags($cacheTags)

                         ->pluck(Feature\Entity::_NAME_)

                         ->toArray();

  

    $dcs = App::_getFacadeRoot_()['dcs'];

  

    $dcsResponse = $dcs->getDcsEnabledFeatures(Feature\Constants::_MERCHANT_, $this->getId())

                       ->pluck(Feature\Entity::_NAME_)

                       ->toArray();

  

    app('trace')->debug(

        TraceCode::_FEATURES_FETCH_FROM_DATABASE_AND_DCS_,

        [

            "features"      => [],

            "apiResponse"   => $apiResponse,

            "dcsResponse"   => $dcsResponse,

            "merchantID"    => $merchantId,

            "cacheTags"     => $cacheTags,

        ]

    );

  

    $features = $this->mergeUniqueArrays($apiResponse, $dcsResponse);

  

    // Store in appropriate cache based on request type

    if ($this->isWorkerOrTestCaseRunning() === false)

    {

        // HTTP request - store in static cache

        self::_$loadedFeatures_[$merchantId] = $features;

    }

    else

    {

        // Worker request - store in instance cache

        $this->instanceLoadedFeatures = $features;

    }

  

    return $features;

}

  

  

—

if (Pricing\Repository::_shouldDistributeQueryCacheLoad_($this) === true)

{

    $cacheTags = Feature\Entity::_getDistrubutedCacheTagsForNames_($this->entity, $this->getId());

}

else

{

    $cacheTags = Feature\Entity::_getCacheTagsForNames_($this->entity, $this->getId());

}

  

———————————

  

Not -> RbuEcq36bsfGYc , RbnVAntvFVoDXW, Rbqe4j412tbo7j, RbtNZ2esPL2GvI, RbuENydyKLGyRF, RbxOd98cMR9tUR, RbuDvWbsC8d6ZT, RbndHqU2CRNCbY, Rbu16XONY3py98, RbxQmSAVNt1DEu, RbsiajvXg8T5WB, RbxOkLCxYGDYb3,RbsRrAxsnTiBM0, Rbp6z370aI6Wa4, RbskdmMl2gsvkJ, Rbp2ncsffgV5Ul, RbsUBI7atz6aME, Rbp0WVp4y8Dlm6, RbsBmzYd8dpHuy, Rbp0dNTSf0ZYT1, RbsBtrKpaw3mC7, Rbp75kblbao8Ng, Rbx5OGi1C1tVUm, Rbx35xaZH8Ml5v, Rbx3D3CUpf9yKD, RbkEhNW6rh3FtX, RbkrMVk7sffJ6N

Astrotalk error code null:

  

Following are cancelled by user

**Payment** **cancelled** **by** **user.   https://razorpay-prod.app.coralogix.in/#/query-new/archive-logs?permalink=true&startTime=1762290680000&endTime=1762290682000&logId=39af01f3-fcb4-43d9-a952-6885527250b6**

  

Rbr5cVEWPpS8eH  
RbrkkjlMoE42I6  
Rbo2QJ5PpOdBFA  
RboJ2CPIEnQJbt

Rbo4Q9zfF205m5

RbtvAhsVHeGMVT

RbtELIN4xzQyck

Rbo8tXLTSX7KaG

RbsiTog3RvxHqV

RbnzxQe3brlVan

RbqAA5PDESjkvH

  

  

fetchbillingaddress

  

  

  

  

  

avs_required is a field NOT tag or feature which is responsible for the rendering of address input page

[https://querybook.de.razorpay.com/prod/query_execution/4787309/](https://querybook.de.razorpay.com/prod/query_execution/4787309/) here is the logs of frontend event and we can see there is not input of address means this was not rendered. Upon checking the logs we found that in API REQUEST log we have the address_required as a featured mentioned(because api fetches both features and tags) upon checking the logic we got to know that avs_required as set as false. 

Since address is not provided but we still have the validation of address_required resulting is payment failure.

Why we can still see some successful payments?

Ans: there is a DCS call that is fetching  ONLY FEATURES not tags that is overriding the fetched tags and in API REQUEST we don’t have the address_required feature. Hence there is no validation check also avs_required is false in frontend resulting in successful payment

Action needs: either enable the address_required feature or disable  the address_required tag whichever merchant wish to do