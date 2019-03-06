## Subscription for event notification

For this exemple, I want to subscribe to events to user oxe18013

* Make a <span style="color:orange">POST</span> request with this URL <br/> <span style="color:blue">https://o2g-shared-sandbox.ale-aapp.com/api/rest/1.0/subscriptions/</span>

![post_sub](pics/post_sub.png)

* Fill the body as below in "raw", "JSON"

##

    {
        "filter": 
        {
            "selectors":
	       [ 
            {"ids": [ "oxe18013" ],"names": [ "telephony" ]},
            {"ids": [ "oxe18013" ],"names": [ "eventSummary" ]}
	       ]
        },
    "version":"1.0"
    }

* If you have <span style="color:green">"Status: 200 OK"</span>, the query succeded.

---

## Change a Password

You have to connect with an <b>Admin account</b> to do this request !

Let's take for exemple a user called <span style="color:red">oxe18001</span> who have "1234" as password, and we want to change it to "toto".

* Do a <span style="color:orange">PUT</span> request with <br/> <span style="color:blue">https://o2g-shared-sandbox.ale-aapp.com/api/rest/1.0/users/<span style="color:red">oxe18001</span>/password</span> as URL.

![download](pics/header_change_pswd.png)

* Complete the body as below :

![download](pics/body_change_pswd.png)

##
        {
            "oldPassword":"1234"
            "newPassword":"toto"
        }

* If you have the <span style="color:green">"Status: 204 No Content"</span>, the request worked !

---

## Log out

To disconnect your account you have to <span style="color:blue">DELETE</span> your session.

* So, make a <span style="color:blue">DELETE</span> requery with `https://o2g-shared-sandbox.ale-aapp.com/api/rest/1.0/sessions` as URL.

![download](pics/delete_sessions.png)

* If you have the <span style="color:green">"Status: 204 No Content"</span>, the query succeded !

---