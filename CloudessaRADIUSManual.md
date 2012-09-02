# Cloudessa RADIUS Manual

## Chapter 1: 60 second lessons



[Lesson 1: Create a user and a group.](https://github.com/cloudess/Cloudessa-Documentation/blob/master/CloudessaRADIUSManual.md#lesson-1-create-a-user-and-a-group-1)

[Lesson 2: Create a simple PAP server.]

[Lesson 3: Create a simple WPA2-Enteprise/PEAP server.]

[Lesson 4: Restrict Client access by source IP addresses.

[Lesson 5: Enable Two-Factor Authentication.]

### Lesson 1: Create a user and a group.

Lets create a group of RADIUS users, and add at least one user to this group. You'll need this for all other lessons.

First create a user

* Go to `Users` and click `Create`
* Specify login as `test` and password as `test123456`
* Click OK

Now create a group

* Go to `User Groups` and click `Create`
* Specify name as `Group1`
* Click OK

Now add the user to the group

* Select `Group1`
* Go to `Users` tab.
* Click `Add user` and select user `test` 
* Click OK


Now we have created user `test` which is a member of `Group1`. 


### Lesson 2: Create a simple PAP server

Lets create a simple authentication server that implements PAP protocol.

First lets create a virtual server

* Go to `Virtual Servers`, click `Create`
* In the pop-up windows set server name to `PAP Server` and protocol to `PAP`.
* Click `OK`. Now the server is created.
* Now click the server to see the IP address as well as the authentication and accounting port numbers for the server. You need this information to configure your RADIUS client.

Now we need to specify user groups that have access to the RADIUS server.

* Select `PAP Server` in the server table.
* Go to `User Groups` tab.
* Click `Add Group` and select `Group` (we have created it in Lesson 1).

Now lets specify that the server will accept PAP requests from all sources. 

* Select `PAP Server` in the server table.
* Click `Edit`
* Set `Disable IP filtering`.

Now the PAP server is running and authenticating users from `Group1`.

### Lesson 3: Create a simple WPA2-Enteprise/PEAP server.

PEAP is a protocol widely used to secure Wi-Fi.

Lets create a simple PEAP server.

* Go to `Virtual Servers`, click `Create`
* In the pop-up windows set server name to `PEAP Server` and protocol to `PEAP`.
* Click `OK`. Now the server is created.
* Now click the server to see the IP address as well as the authentication and accounting port numbers for the server. You need this information to configure your RADIUS client.

Now we need to specify user groups that have access to the RADIUS server.

* Select `PEAP Server` in the server table.
* Go to `User Groups` tab.
* Click `Add Group` and select `Group1` (we have created it in Lesson 1).

Now lets specify that the server will accept PEAP requests from all sources. 

* Select `PEAP Server` in the server table.
* Click `Edit`
* Set `Disable IP filtering`.

Now the PEAP server is running and authenticating users from `Group1`.


### Lesson 3. Restrict Client access by source IP addresses.

For security reasons it is important to restrict access to the server to a 


Lets create a simple authentication server that implements PAP protocol.

First lets create a virtual server

* Go to `Virtual Servers`, click `Create`
* In the pop-up windows set server name to `PAP Server` and protocol to `PAP`.
* Click `OK`. Now the server is created.
* Now click the server to see the IP address as well as the authentication and accounting port numbers for the server. You need this information to configure your RADIUS client.

Now we need to specify user groups that have access to the RADIUS server.

* Select `PAP Server` in the server table.
* Go to `User Groups` tab.
* Click `Add Group` and select `Group` (we have created it in Lesson 1).

Now lets specify that the server will accept PAP requests from all sources. 

* Select `PAP Server` in the server table.
* Click `Edit`
* Set `Disable IP filtering`.

Now the PAP server is running and authenticating users from `Group1`.








*View the [source of this content](http://github.github.com/github-flavored-markdown/sample_content.html).*



