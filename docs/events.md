During all this little tutorial on events, I will use an intranet connection. If you need to, use HTTPS instead of HTTP. <br/>
In HTTPS the event port used is 8016 and in HTTP the port used is 8014.

## Subscription

For this example, I want to subscribe to events to user oxe19141.

* First, you need to do a <span style="color:orange">POST</span> query to this URL :<br/><span style="color:blue">http://o2g-instance1.ale-aapp.com/api/rest/1.0/subscriptions/</span>

![download](pics/sub_19141_query.png)

with this body :

##
    {
        "filter": 
        {
           "selectors":
           [ 
                {"ids": [ "oxe19141" ],"names": [ "telephony" ]},
                {"ids": [ "oxe19141" ],"names": [ "eventSummary" ]}
           ]
        },
        "version":"1.0"
    }

* If the request worked you have a <span style="color:green">"Status: 200 OK"</span> and the response body will return us the <span style="color:orange">URL to use for a long polling</span> and the "subscriptionId", mandatory if you want to unsubscribe to someone :

![download](pics/res_query_sub.png)

##
    {
        "subscriptionId": "eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJhZG1pbkM1IiwiaWF0IjoxNTM3NDUwMTg2fQ.jDDsEPtoW3Ae8Fiw5YLWE9MdflEcMz-RoWLweAtPDvS",
        "publicPollingUrl": "http://o2g-instance1.ale-aapp.com:8014/OTEvents?subscriptionId=eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJhZG1pbkM1IiwiaWF0IjoxNTM3NDUwMTg2fQ.jDDsEPtoW3Ae8Fiw5YLWE9MdflEcMz-RoWLweAtPDvS",
        "privatePollingUrl": "http://o2g-instance1.ale-aapp.com:8014/OTEvents?subscriptionId=eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJhZG1pbkM1IiwiaWF0IjoxNTM3NDUwMTg2fQ.jDDsEPtoW3Ae8Fiw5YLWE9MdflEcMz-RoWLweAtPDvS",
        "status": "ACCEPTED",
        "mode": "CHUNK",
        "format": "JSON"
    }

---

## Long Polling

In this example, my device (subscribed) is 19141 and i will have a call from 19140.

* Now that you have your "PollingUrl", open your favorite browser (in my case chrome) and past your <span style="color:green">URL</span>.

![download](pics/url_browser.png)

* If it's all right, you have the "Chunck started" status.

![download](pics/connection_to_subscription.png)

* Now I connect my <span style="color:orange">device 19141</span> who is a softphone. You can see his state is <span style="color:green">"FREE"</span>

![download](pics/connection_device_19141.png)

* Now the 19140 call the 19141. You can see that the "state" change to <span style="color:green">"RINGING_INCOMING"</span>. You are able to see the <span style="color:red">phone number of the device who call you </span> ("participants") and <span style="color:orange">more informations </span>on him.

![download](pics/appel_du_device.png)


* During the call, you can see a lot of informations. Your "state" change to <span style="color:green">"BUSY"</span> for example.

![download](pics/pendent_le_call.png)

* Now, the 19140 device <span style="color:blue">stopped the call</span>. The 19141's state change to <span style="color:orange">"FREE"</span>

![download](pics/raccroché.png)

---

## Unsubscribe

* To unsubscribe someone you just have to do a <span style="color:red">DELETE</span> on <br>`http://o2g-instance1.ale-aapp.com/api/rest/1.0/subscriptions/` + "subscriptionId"

for example : <br> http://o2g-instance1.ale-aapp.com/api/rest/1.0/subscriptions/<span style="color:red">eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJhZG1pbkM1IiwiaWF0IjoxNTM3NDUwMTg2fQ.jDDsEPtoW3Ae8Fiw5YLWE9MdflEcMz-RoWLweAtPDvS</span>

* On succes you have the <span style="color:green">"204 No Content"</span> status.

