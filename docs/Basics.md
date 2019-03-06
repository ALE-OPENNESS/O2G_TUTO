To log in the API, you <b>have to authenticate</b> yourself, and then <b>create a session</b> with your user name.

---

## Authentification

* First, enter this URL : <span style="color:red">https://o2g-shared-sandbox.ale-aapp.com/api/rest/authenticate?version=1.0</span> in the field provided for this effect with the <span style="color:blue">GET</span> request.

![download](pics/requete%20get.png)

---

* Then go to the <span style="color:red">"Authorization"</span> tab then choose the type <span style="color:blue">"Basic Auth"</span> and enter your login in <span style="color:orange">"Username"</span> and password in <span style="color:green">"Password"</span> in the fields below.

![download](pics/authentification.png)

---

* If you have the <span style="color:green">"Status: 200 OK"</span>, the query succeded.
* Now, you have your <span style="color:red">Cookie</span> which will serve you to authenticate you during the next queries. It is automatically saved in <span style="color:green">the "Cookie" tab</span>.

![download](pics/cookie.png)

* You can manually enter the Alcatel Cookie, but it's really not practical. For your information, to do that by hand you have to fill the <b>KEY</b> in the Headers by "Cookie" with the <b>VALUE</b> "AlcUserId=*yourCookieValue*".

---

## Create a session

* Now that you have the registered authentication cookie, you can open your session by using the <span style="color:red">POST</span> request with the following URL <span style="color:blue">https://o2g-shared-sandbox.ale-aapp.com/api/rest/1.0//sessions </span>, and by adding in the <span style="color:green">Header</span> tab the <span style="color:orange">"Content-Type"</span> key and the <span style="color:#6600cc">« application/json »</span> value.

![download](pics/post_sessions.png)

---

* Then in the <span style="color:green">"Body"</span> tab, activate the <span style="color:orange">"raw"</span> button then select <span style="color:red">"JSON"</span>, then copy the body as the example below and replace the <span style="color:blue">"userName"</span> with your own application name.

![download](pics/body_session.png)

* If you have the <span style="color:green">"Status: 200 OK"</span>, the query succeded.