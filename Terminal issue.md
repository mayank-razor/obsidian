Terminal issue

  

  

  

  

Payments capture must be true in order entity incase default config is used

RCA is with integration team: why merchant is not sending payment capture as true but it is marked as false resulting in not auto capture

Action item: raise with integration team.

  

  

**Things to ask during terminal calls**

What’s the next step, multiple merchant are facing the issue

Ask that do we need to apply data fix on. The terminals that were created during the Time of new version of go utils

  

We want to do the data fix on terminals

God mode edit api : this will skip all the validation , ask with pm to hit curl to remove those currency:

Total 6 currencies 

Steps: fetch for 6 currencies. 8 dec 9pm to 9 dec 1pm (apprx time)

Get all merchant id

filter our merchants

Apply data fix to just remove the currencies.

  

—

1.2: ars tha

1.2.1ars hatey but terminal is using 1.2

1.2.2 me are hate and fan add huh

Ismein terminal bana to sare currency agay

Roll back to 1.0.5

But terminals has afn and during mcc update afn check is failing

  

Suggestion for cxb to pos create new package inside go utils

```

Go utils:

currency 1.2.2

pos currency (new package)

```

—

  

  

  

Transstatus c issue:  
most payment that failed was of date 30th nov  
there was a spike at 30th move where 3ds serves were unreachable  404 at time duration: 16:35 to 16:45

  

  

  

In order to unblock the merchant we will perform data fix :  
will be removing the non intended currencies from currency list :   'AFN’, 'GEL', 'BYN’, ‘AOA','PAB’,’TJS',

  

@jay shah could you please help me with the hackathon idea. I have picked the topic for central global search across multiple platforms. Need help in understanding structural and inter-connection for the platform and internal services

  

Fairs vector db ->  

Rancher : alternative docker

  

  

  

  

Change data capture : feature of database for event

  

Royal brothers