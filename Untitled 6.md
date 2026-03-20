**SR 10 dec notes**

  

For Swiggy AzaPxFRJ5Zz6Sp

Most payments timed out due to transaction id not found. It is genuine case where customer dropped at the otp page

Few are failing where auth init log is not there and acs url is not present.

  

For flipkart C1fnUMHBmitlPB

Most payments timed out due to transaction id not found. It is genuine case where customer dropped at the otp page

Count: 79

  

Sample reponse/:

‘{

  "Data": {

    "acsOperatorID": "ACS-V210-CARDINAL_COMMERCE-45565",

    "acsChallengeMandated": "N",

    "p_messageVersion": "1.0.5",

    "acsReferenceNumber": "3DS_LOA_ACS_CACC_020200_00813",

    "transStatus": "C",

    "authenticationType": "02",

    "messageVersion": "2.2.0",

    "acsTransID": "9ca7d8fc-fee6-41d1-a194-ff28fbad3ae0",

    "messageType": "pArs",

    "threeDSServerTransID": "0d271ce6-9a4a-466b-b3b5-3a522cf39cd5",

    "dsTransID": "cf7cde0c-9eb5-4d93-9e9c-b4a9802045e7",

    "acsURL": "https://authentication.cardinalcommerce.com/ThreeDSecure/V2_1_0/CReq?oid=5afdd7913bb1266e84329bfd&tid=9ca7d8fc-fee6-41d1-a194-ff28fbad3ae0",

    "dsReferenceNumber": "3DS_LOA_DIS_MAST_020301_00931"

  }

}

  

  

Others are failing where auth init log is not there and acs url is not present.

Count: 33

Sample  response:  
{

  "Data": {

    "acsStartProtocolVersion": "2.2.0",

    "acsEndProtocolVersion": "2.2.0",

    "acsInfoInd": "[\"01\",\"02\",\"81\"]",

    "threeDSProtocolSupported": "2.0",

    "threeDSServerTransID": "0f3771c6-5979-4d23-b0b1-2f25028b2eb4",

    "threeDSMethodURL": "https://geoissuer.cardinalcommerce.com/DeviceFingerprintWeb/V2/Browser/RenderMethodURL?id=5ab177af247978bf2887e850"

  }

}