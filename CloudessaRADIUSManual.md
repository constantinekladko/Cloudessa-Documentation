# Cloudessa RADIUS Manual

(c) [Cloudessa, Inc.](https://www.cloudessa.com) 2012



## Table of Contents


**Chapter 1: 60 second lessons**


* [Lesson 1: Create a user and a group](https://github.com/cloudess/Cloudessa-Documentation/blob/master/CloudessaRADIUSManual.md#lesson-1-create-a-user-and-a-group)

* [Lesson 2: Create a simple PAP server](https://github.com/cloudess/Cloudessa-Documentation/blob/master/CloudessaRADIUSManual.md#lesson-2-create-a-simple-pap-server)

* [Lesson 3: Create a simple WPA2-Enteprise/PEAP server](https://github.com/cloudess/Cloudessa-Documentation/blob/master/CloudessaRADIUSManual.md#lesson-3-create-a-simple-wpa2-enteprisepeap-server)

* [Lesson 4: Restrict client access by source IP addresses](https://github.com/cloudess/Cloudessa-Documentation/blob/master/CloudessaRADIUSManual.md#lesson-4-restrict-client-access-by-source-ip-addresses)

* [Lesson 5: Enable Two-Factor Authentication](https://github.com/cloudess/Cloudessa-Documentation/blob/master/CloudessaRADIUSManual.md#lesson-5-enable-two-factor-authentication)

* [Lesson 6: Let users change and reset passwords](https://github.com/cloudess/Cloudessa-Documentation/blob/master/CloudessaRADIUSManual.md#lesson-6-let-users-change-and-reset-passwords)

* [Lesson 7: Manage RADIUS attributes] (https://github.com/cloudess/Cloudessa-Documentation/blob/master/CloudessaRADIUSManual.md#lesson-7-manage-radius-attributes)

* [Lesson 8: Create a guest login](https://github.com/cloudess/Cloudessa-Documentation/blob/master/CloudessaRADIUSManual.md#lesson-8-create-guest-login)


**Chapter 2: Users and Groups**

* User roles
* Users
* Bulk User Export
* User Groups

**Chapter 3: Virtual RADIUS Servers**

* Virtual RADIUS Servers
* Supported Protocols
* Src IP addresses
* Vendor Specific Atrributes
* Accounting
* Audit

**Chapter 4: Network access control**

In development


**Chapter 5: Account administration**

In development

## Chapter 1: 60 Second Lessons

### Lesson 1: Create a user and a group

In this lesson you create a group of RADIUS users, and add at least one user to this group. You'll need this for all other lessons.

First create a user

* Go to `Users` and click `Create`
* Specify login as `test`, email as `test@cloudessa.com` and password as `mypassword`
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

In this lesson we create a simple authentication server that implements PAP protocol.

First lets create a virtual server

* Go to `Virtual Servers`, click `Create`
* In the pop-up windows set server name to `PAP Server` and protocol to `PAP`
* Click `OK`. Now the server is created
* Now click the server to see the IP address as well as the authentication and accounting port numbers for the server. You need this information to configure your RADIUS client

Now we need to specify user groups that have access to the RADIUS server.

* Select `PAP Server` in the server table
* Go to `User Groups` tab
* Click `Add Group` and select `Group` (we have created it in Lesson 1)

Now lets specify that the server will accept PAP requests from all sources. 

* Select `PAP Server` in the server table
* Click `Edit`
* Set `Disable IP filtering`

Now the PAP server is running and authenticating users from `Group1`.

### Lesson 3: Create a simple WPA2-Enteprise/PEAP server

PEAP is a protocol widely used to secure Wi-Fi. In this lesson create a simple PEAP server.

* Go to `Virtual Servers`, click `Create`
* In the pop-up windows set server name to `PEAP Server` and protocol to `PEAP`
* Click `OK`. Now the server is created
* Now click the server to see the IP address as well as the authentication and accounting port numbers for the server. You need this information to configure your RADIUS client

Now we need to specify user groups that have access to the RADIUS server.

* Select `PEAP Server` in the server table
* Go to `User Groups` tab
* Click `Add Group` and select `Group1` (we have created it in Lesson 1)

Now lets specify that the server will accept PEAP requests from all sources. 

* Select `PEAP Server` in the server table
* Click `Edit`
* Set `Disable IP filtering`

Now the PEAP server is running and authenticating users from `Group1`.


### Lesson 4: Restrict Client access by source IP addresses

For security reasons it is important to restrict access to the server to a set of allowed source IP addresses.
The server will then only accept a RADIUS request if it comes from one of the allowed source IP addresses.

If your RADIUS client or Network Access Server is behind a firewall, then the source IP address that Cloudessa will see is the IP address of the firewall.

Let us assume that the ip address of your firewall is `20.21.22.23`.


First lets create a source IP address. 

* Go to `Src IP Addresses`, click `Create`
* In the pop-up window set the IP address to `20.21.22.23` and the name to `Gateway1`
* Click `OK`. Now the source IP address is creared

Now we need to use this source IP address with the PAP server we created in Lesson 2.

* Select `PAP Server` in the server table
* Click `Edit`, unset `Disable IP filtering` checkbox, and click `Save`
* Go to `Src IP Addresses` tab
* Click `Add src IP address", and select `Gateway1`

Now the PAP server is running and accepting only requests that come from the ip address `20.21.22.23`.

### Lesson 5: Enable Two-factor authentication

To enable two-factor authentication for user `test`.

* Select user `test` in the Users panel
* Select "Google Auth" tab
* Set "Enable Google Authenticator". A bar code will be generated

Now one needs to setup the smartphone for the user.

* Download Google Authenticator app for

  [iPhone](http://itunes.apple.com/us/app/google-authenticator/id388497605?mt=8)
  
  [Android] (https://play.google.com/store/search?q=google+authenticator)
  
  [WindowsPhone] (http://www.windowsphone.com/en-US/apps/021dd79f-0598-e011-986b-78e7d1fa76f8) 
  
  [Blackberry] (m.google.com/authenticator)
  
* Scan user barcode into Google Authenticator app
* The app will start displaying temporary six-digit codes


To perform two-factor authentication into Cloudessa RADIUS

* enter the password composed of your regular password and the six digit code, separated by a comma

    `login:test`

    `password:mypassword,315425`


### Lesson 6: Let users change and reset passwords

Cloudessa enables regular RADIUS users to change their passwords using a simple web interface.
If you do not want a particular user to be able to change or reset her password, you can unset `Allow user to manage her password` checkbox in the user settings tab.

To access the simple web interface for user `test` created in Lesson 1.

* Go to [Cloudessa login page](https://app.cloudessa.com/account/login)
* Enter user email `test@cloudessa.com` and password `mypassword`
* You will be presented with the simple web interface panel.

To change user password

* Go to the "Set Password" panel
* Set the new password

If the user needs to reset her password 

* User clicks on the `Reset password` link included in [Cloudessa login page](https://app.cloudessa.com/account/login)
* Password reset instructions are emailed to the user

### Lesson 7: Manage RADIUS attributes

Cloudessa lets you set RADIUS attributes to return in RADIUS response messages. You can set return attributes for a server, a user group or a particular user.

To return `Framed-IP-Address` attribute value of `12.13.14.15` for user `test` created in Lession 1

* Select user `test` in the `Users` panel
* Select `Attributes` panel and click `Add`
* Select `RFCs` dictionary
* Select `Framed-IP-Address` attribute and set attribute value to `12.13.14.15`
* Click `OK`

Note: for a particular authentication request, Cloudessa RADIUS first identifies the user, the user group and the virtual RADIUS server, and then adds up the corresponding three sets of attributes. If the same attribute value is set for the user, the user group and/or the RADIUS server, then the user group attribute overrides the server attribute, and the user attribute overrides the user group attribute.

### Lesson 8: Create guest login


To give your guest `guest1@gmail.com` a temporary login into the `PEAP server` created in Lesson 3.

* Go to `Guest Users` tab
* Click `Create Guest User`
* Enter guest email `guest1@gmail.com` and login expiration date
* Set the login expiration date to, e.g., `May 1, 2013`
* Click `OK`




