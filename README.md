# Cloud Identity Verify API Samples

This repository contains postman and other basic web API client samples that demonstrate the features of Cloud Identity Verify.  A Cloud Identity tenant with CIV subscription will be needed to successfully run most of the samples.

## Getting Started
Before executing the samples, you will require access to a CIV tenant and a set of administrator account credentials and [Postman](https://www.getpostman.com/).

Edit the values for the following envrionment variables contained within `postman/environments/ibm-verify-web-api-envrionment.postman_environment.json`:

<table>
  <tr>
    <th>Envrionment variable name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>tenant</td>
    <td>The tenant host address</td>
  </tr>
  <tr>
    <td>username</td>
    <td>An administrator username</td>
  </tr>
  <tr>
    <td>password</td>
    <td>The administrator password</td>
  </tr>
</table>


Import the collections and environment files into your Postman runtime
* `postman/collections/IBM-Verify-Web-API.postman_collection.json`
* `postman/environments/ibm-verify-web-api-envrionment.postman_environment.json`

Execute all requests within the `Setup prerequisites` folder then execute requests from `Runtime Examples`

## IBM Verify Mobile Multi Factor Authenticator Overview

IBM Verify is a 2FA authenticator that delivers out-of-band 2FA via a separate secure channel leveraging a users mobile device.  Users register their IBM Verify instances via a simple user self care style initiated work flow.  Users enroll authentication methods such as device based biometrics including fingerprint and face biometrics where supported by the mobile device.  Using Cloud Identity platform policies and API's, an application can initiate an IBM Verify 2FA authentication transaction, wait for that authentication to be completed by the user with IBM Verify, then permit runtime access to continue.

IBM Verify lifecycle and features are comprised three main functional areas.  All of these are supported by web API's which drive and manage IBM Verify.

* Registration - after installing IBM Verify from the app store, a user will be required to register their new instance of IBM Verify with their Cloud Identity user account.  The registration process basically requires displaying a QRCode to the user which they may then scan with their new instance of IBM Verify.

* Authenticator Factor Enrollment - Immediately following successful registration, the IBM Verify mobile app will guide the user through an authenticator factor enrollment flow which includes enrollment for TOTP, user presence, and device based biometrics.  In the case of user presence and device based biometrics, the enrollment will be embodied by a cryptographic public key exchange between IBM Verify and the users Cloud Identity tenant.

* Runtime verification transactions - Once the registration and enrollment steps have been completed, IBM Verify is ready for productive use.  Applications can validate an end users identity by initiating an IBM Verify verification transaction.  This includes the ability to send mobile push notification to the end users registered instance of IBM Verify.

Full web API documenation is available from your tenant at the following location:
```
https://<your tenant>/developer/explorer/
```


#### Executing API client sample postman scripts

Before executing the samples, you will require access to a CIV tenant and a set of administrator account credentials.

Postman collections and envrionments are located within this repository.  The structure is as follows:

* `postman/collections` - the postman collections
* `postman/environments` - the initial postman environment variables

The IBM Verify collections are:
* `postman/collections/IBM-Verify-Web-API.postman_collection.json`
* `postman/environments/ibm-verify-web-api-envrionment.postman_environment.json`

Before importing or using these postman files, using a text editor set values for the following envrionment variables contained within `postman/environments/ibm-verify-web-api-envrionment.postman_environment.json`:
* tenant - The tenant host address
* username - An administrator username
* password - The administrator password

Import these collection and envrionment files into your postman runtime.

Once imported, you should have a collection named `IBM-Verify-Web-API`.  You should execute all requests within the `Setup prerequisites` folder.  The basic flow of steps here includes:
* Login to your tenant as an administrator using a simulated browser style of interaction
* Create an API client that will be used to configure IBM Verify
* Create an end user to represent a user who may register, enroll and authenticate with IBM Verify
* Get an access token using the API client created just above

Once these `Setup prerequisites` have successfully completed, a recommended sequence of requests contained with `Runtime Examples` may be executed as listed below.  

* `Create Authenticator configuration`
* `Get Authenticator configuration`
* `Initiate IBM Verify registration`

Use you phone to scan the resulting QR Code here.

* `Get all IBM Verify Registrations`
* `Get all IBM Verify signature factor enrollments`
* `Initate user presence authentication `

Respond to authentication notification using the IBM Verify app on your phone

## License
See [LICENSE](LICENSE).







