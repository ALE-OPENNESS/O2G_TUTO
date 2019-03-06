## Find your PBX nodeId

* First you need to <span style="color:orange">GET</span> the nodeId of your PBX with this URL :<br/><span style="color:blue">https://o2g-instance1.ale-aapp.com/api/rest/1.0/pbxs/</span>

![download](pics/get_node.png)

* If the request worked you have a <span style="color:green">"Status: 200 OK"</span> and this type of body with your <span style="color:blue">nodeIds</span> :

![download](pics/node_body.png)

---

## Check for a free number

* To check all the number used, you can do a <span style="color:orange">GET</span> on <br/><span style="color:blue">https://o2g-instance1.ale-aapp.com/api/rest/1.0/pbxs/407/instances/Subscriber</span> <br />and find if a phone number is used or not.

![download](pics/body_subscriber.png)

___

## Create a new user

You need an Admin account for this query.

* Now you can complete this URL :<br/><span style="color:blue">https://o2g-instance1.ale-aapp.com/api/rest/1.0/pbxs/<span style="color:red">407</span>/instances/Subscriber</span><br/> with your own <span style="color:red">nodeIds</span> do a <span style="color:orange">POST</span> query and fill the in JSON body as below :<br/>
##
    {
        "attributes": [
        {
            "name": "Directory_Number",
            "value": ["19999"]
        },
 		{
            "name": "Annu_Name",
            "value": ["Darmon"]
 		},
 		{
            "name": "Annu_First_Name",
            "value": ["Gerard"]
 		},
        {
            "name": "Cost_Center_Name",
            "value": ["administrator1"]
        },
        {
            "name": "ClickAndPh",
            "value": ["A4980_Pro"]
        },
        {
            "name": "Station_Type",
            "value": ["SIP_Extension"]
        }
        ]
    }

* If you have the <span style="color:green">"Status: 201 Created"</span>, the query succeded.

---

## Get all information about user

When you create a user, all the value that you don't set, will be set by default. If you do this query, you will be able to see <b>all the settings that you can do on a single user</b>.
In this case, i want to see all informations about user 19997.

* You juste have to do a <span style="color:orange">GET</span> with this URL <span style="color:blue">https://o2g-instance1.ale-aapp.com/api/rest/1.0/pbxs/407/instances/Subscriber/<span style="color:red">19997</span></span>

![download](pics/getèuser_cartman.png)

* And you will have informations like this

![download](pics/getèuser_cartman_body.png)

* If you have the <span style="color:green">"Status: 200 OK"</span>, the query succeded.

___

## Edit a user

If you want to change one (or more) parameter on an existant user, you have to do that :
In this example, I want to change the name and the first name of the user 19996.

* Do a <span style="color:orange">PUT</span> with URL <span style="color:blue">https://o2g-instance1.ale-aapp.com/api/rest/1.0/pbxs/407/instances/Subscriber/<span style="color:red">19996</span></span> and fill the body like this in RAW JSON

##
    {
        "attributes": [
 		{
            "name": "Annu_Name",
            "value": ["Pitiot"]
 		},
 		{
            "name": "Annu_First_Name",
            "value": ["Franck"]
 		}
        ]
    }

* If you have the <span style="color:green">"Status: 204 NO Content"</span>, the query succeded.

---

## Delete a user

I want to delete user 19996

* Juste do a <span style="color:orange">DELETE</span> with URL <span style="color:blue">https://o2g-instance1.ale-aapp.com/api/rest/1.0/pbxs/407/instances/Subscriber/<span style="color:red">19996</span></span>

![download](pics/delete_user_19996.png)

* If you have the <span style="color:green">"Status: 204 No Content"</span>, the query succeded.

---

