---
title: Mobiag API Documentation

language_tabs:
  - plaintext: REST
  - xml: SOAP

toc_footers:
  - <a href='http://mobile.mobiag.com' target="_blank">Mobiag</a>
  - <a href='https://github.com/tripit/slate' target="_blank">Documentation Powered by Slate</a>

search: true
---

# Introduction

Welcome to the Mobiag API! You can use our API to search available cars, book a car, unlock the doors, turn off the immobilizer, report damages, consult trip values, turn on the immobilizer, lock the doors and end the trip.
This documentation helps you to understand the services that we use to communicate with our backoffice and with the cars.

# Authentication

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:cus="http://mobics.criticalsoftware.com/v2/customer" xmlns:cus1="http://mobics.criticalsoftware.com/v2/customer">
<soapenv:Header>
  <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
    <wsse:UsernameToken>
      <wsse:Username>mobiag@mobiag.com</wsse:Username>
      <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">VvelOMVvR7LTJxPVoQkxti33GLg=</wsse:Password>
      <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ1NTg4ODEzNDY3Mg==</wsse:Nonce>
      <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">
      2016-02-19T13:22:14Z</wsu:Created>
    </wsse:UsernameToken>
  </wsse:Security>
</soapenv:Header>
</soapenv:Envelope>
```

```plaintext
GET /mobics-webservices/rs/customer/validateCustomer HTTP/1.1
Host: imobics.mobiag.com
Username: mobiag@mobiag.com
Password: VvelOMVvR7LTJxPVoQkxti33GLg=
Nonce: MTQ1NTg4ODEzNDY3Mg==
Created: 2016-02-19T13:22:14Z
Content-Type: application/json
Cache-Control: no-cache
```

This page contains the description of the Authentication Requests.
Many services of the web services requires authentication, here you can understand how to do an authentication on SOAP and REST and also how to generate a nonce and the password.

### Header Parameters

Name | Type | Description | Mandatory
--------- | ------- | ----------- | --------
Nonce | String | Arbitrary number that may only be used once. | Yes
Username | String | User's email or username. | Yes
Password | String | User's password. |  Yes
Created | String | User's creation date. | Yes

<aside class="notice">
Generate the Nonce with Java:
</aside>
byte[] nonceB = Long.toString(new Date().getTime()).getBytes();
String nonce = Base64.encodeBase64String(nonceB);

<aside class="notice">
Generate the Password with Java:
</aside>
String password = Hex.encodeHexString(DigestUtils.sha(customerPassword));
byte[] passwordB = password.getBytes(utf8Encoding);

# Load CarClub Data

After the authentication is advisable to load the car club characteristics.
To do that you can use some of these services:

* getAddonsByCarClubCode
* getAddonsByCarClubCodeSimple
* getAddOnDetails
* getCarClubAdditionalServices
* getCarClubByCarClubCode
* getCarClubImageByCarClubCode
* getCarClubPrivacyPolicy
* getCarClubSimpleByURL
* getCarClubSmallImageByCarClubCode
* getCarClubSmallThumbnailByCarClubCode
* getCarClubTermsOfService
* getCarClubThumbnailByCarClubCode
* getCountryConfigurationByCarClubCode
* getCustomerCarClub
* getLocationsByCarClubCode
* getParksByCarClubCodeAndLocationCode
* getPromotionsForCarClub
* getPromotionThumbnail
* getPromotionDetail
* getZonesByCarClubCode
* getZoneWithPolygonsByCode

## - getAddonsByCarClubCode

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:car="http://mobics.criticalsoftware.com/carclub">
   <soapenv:Header xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/">
  <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
    <wsse:UsernameToken>
      <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
      <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">ApPOW3FYKX+NjT4yaVmgoEo8fXE=</wsse:Password>
      <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ2NDAxOTcyNTU1Mw==</wsse:Nonce>
      <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-05-23T17:08:45Z</wsu:Created>
    </wsse:UsernameToken>
  </wsse:Security>
</soapenv:Header>
   <soapenv:Body>
      <car:getAddonsByCarClubCode>
         <car:carClubCode>NXT</car:carClubCode>
      </car:getAddonsByCarClubCode>
   </soapenv:Body>
</soapenv:Envelope>
```

```plaintext
This service is not yet available in REST.
```

This service gets the car club addons.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/CarClub?wsdl`

<aside class="warning">
This service requires authentication.
</aside>

### Input Parameters

Name | Type | Description | Mandatory
--------- | ------- | ----------- | --------
carClubCode | String | The user's car club. | Yes

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:getAddonsByCarClubCodeResponse xmlns:ns2="http://mobics.criticalsoftware.com/carclub" xmlns:ns3="http://www.criticalsoftware.com/mobios/country/configuration">
         <return>
            <addonCode>AONXT1508000003</addonCode>
            <canDelete>false</canDelete>
            <carClubCode>NXT</carClubCode>
            <changesId>11</changesId>
            <description>.</description>
            <discount>20.0000</discount>
            <monthlyFee>12.30</monthlyFee>
            <name>Adicional</name>
            <startDate>2015-08-30T23:00:00Z</startDate>
         </return>
         <return>
            <addonCode>AONXT1411000002</addonCode>
            <canDelete>false</canDelete>
            <carClubCode>NXT</carClubCode>
            <changesId>10</changesId>
            <description>Teste</description>
            <discount>100.0000</discount>
            <monthlyFee>0.00</monthlyFee>
            <name>Teste Inicio</name>
            <startDate>2014-11-28T00:00:00Z</startDate>
         </return>
      </ns2:getAddonsByCarClubCodeResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
This service is not yet available in REST.
```

Name | Type | Description
--------- | ------- | -----------
addonCode | String | The addon code.
canDelete | Boolean | If can delete addon.
carClubCode | String | The car's club code.
changesId | Integer | The addon id.
description | String | The addon description.
discount | BigDecimal | The addon discount.
monthlyFee | BigDecimal | The addon monthly fee.
name | String | The addon name.
startDate | Date | The start date of the addon.

## - getAddonsByCarClubCodeSimple

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:car="http://mobics.criticalsoftware.com/carclub">
   <soapenv:Header xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/">
  <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
    <wsse:UsernameToken>
      <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
      <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">ApPOW3FYKX+NjT4yaVmgoEo8fXE=</wsse:Password>
      <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ2NDAxOTcyNTU1Mw==</wsse:Nonce>
      <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-05-23T17:08:45Z</wsu:Created>
    </wsse:UsernameToken>
  </wsse:Security>
</soapenv:Header>
   <soapenv:Body>
      <car:getAddonsByCarClubCodeSimple>
         <car:carClubCode>NXT</car:carClubCode>
      </car:getAddonsByCarClubCodeSimple>
   </soapenv:Body>
</soapenv:Envelope>
```

```plaintext
This service is not yet available in REST.
```

This service gets the car club addons.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/CarClub?wsdl`

<aside class="warning">
This service requires authentication.
</aside>

### Input Parameters

Name | Type | Description | Mandatory
--------- | ------- | ----------- | --------
carClubCode | String | The user's car club. | Yes

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:getAddonsByCarClubCodeSimpleResponse xmlns:ns2="http://mobics.criticalsoftware.com/carclub" xmlns:ns3="http://www.criticalsoftware.com/mobios/country/configuration">
         <return>
            <addonCode>AONXT1508000003</addonCode>
            <canDelete>false</canDelete>
            <carClubCode>NXT</carClubCode>
            <changesId>11</changesId>
            <description>.</description>
            <discount>20.0000</discount>
            <monthlyFee>12.30</monthlyFee>
            <name>Adicional</name>
            <startDate>2015-08-30T23:00:00Z</startDate>
         </return>
         <return>
            <addonCode>AONXT1411000002</addonCode>
            <canDelete>false</canDelete>
            <carClubCode>NXT</carClubCode>
            <changesId>10</changesId>
            <description>Teste</description>
            <discount>100.0000</discount>
            <monthlyFee>0.00</monthlyFee>
            <name>Teste Inicio</name>
            <startDate>2014-11-28T00:00:00Z</startDate>
         </return>
      </ns2:getAddonsByCarClubCodeSimpleResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
This service is not yet available in REST.
```

Name | Type | Description
--------- | ------- | -----------
addonCode | String | The addon code.
canDelete | Boolean | If can delete addon.
carClubCode | String | The car's club code.
changesId | Integer | The addon id.
description | String | The addon description.
discount | BigDecimal | The addon discount.
monthlyFee | BigDecimal | The addon monthly fee.
name | String | The addon name.
startDate | Date | The start date of the addon.

## - getAddOnDetails

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:car="http://mobics.criticalsoftware.com/carclub">
   <soapenv:Header xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/">
  <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
    <wsse:UsernameToken>
      <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
      <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">ApPOW3FYKX+NjT4yaVmgoEo8fXE=</wsse:Password>
      <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ2NDAxOTcyNTU1Mw==</wsse:Nonce>
      <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-05-23T17:08:45Z</wsu:Created>
    </wsse:UsernameToken>
  </wsse:Security>
</soapenv:Header>
   <soapenv:Body>
      <car:getAddOnDetails>
         <car:carClubCode>NXT</car:carClubCode>
         <car:addOnCode>AONXT1411000002</car:addOnCode>
      </car:getAddOnDetails>
   </soapenv:Body>
</soapenv:Envelope>
```

```plaintext
GET /mobics-webservices/rs/carclub/getAddOnDetails HTTP/1.1
Host: imobics.mobiag.com
Content-Type: application/json
Username: ricardo.mendes@mobiag.com
Password: ApPOW3FYKX+NjT4yaVmgoEo8fXE=
Nonce: MTQ2NDAxOTcyNTU1Mw==
Created: 2016-05-23T17:08:45Z
carClubCode: NXT
addOnCode: AONXT1411000002
Cache-Control: no-cache
```

This service gets the addon details.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/CarClub?wsdl`

### WSDL

`http://imobics.mobiag.com/mobics-webservices/rs/carclub/getAddOnDetails`

<aside class="warning">
This service requires authentication.
</aside>

### Input Parameters

Name | Type | Description | Mandatory
--------- | ------- | ----------- | --------
carClubCode | String | The user's car club. | Yes
addOnCode | String | The addon code. | Yes

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:getAddOnDetailsResponse xmlns:ns2="http://mobics.criticalsoftware.com/carclub" xmlns:ns3="http://www.criticalsoftware.com/mobios/country/configuration">
         <return>
            <calendarRestricted>false</calendarRestricted>
            <carClubCode>NXT</carClubCode>
            <code>AONXT1411000002</code>
            <description>Teste</description>
            <discount>100.0000</discount>
            <extraKm>0.00</extraKm>
            <includedKm>0</includedKm>
            <message>.</message>
            <monthlyFee>0.00</monthlyFee>
            <name>Teste Inicio</name>
            <restrictions>
               <dayDisabled>false</dayDisabled>
               <dayOfWeek>MONDAY</dayOfWeek>
            </restrictions>
            <restrictions>
               <dayDisabled>false</dayDisabled>
               <dayOfWeek>TUESDAY</dayOfWeek>
            </restrictions>
            <restrictions>
               <dayDisabled>false</dayDisabled>
               <dayOfWeek>WEDNESDAY</dayOfWeek>
            </restrictions>
            <restrictions>
               <dayDisabled>false</dayDisabled>
               <dayOfWeek>THURSDAY</dayOfWeek>
            </restrictions>
            <restrictions>
               <dayDisabled>false</dayDisabled>
               <dayOfWeek>FRIDAY</dayOfWeek>
            </restrictions>
            <restrictions>
               <dayDisabled>false</dayDisabled>
               <dayOfWeek>SATURDAY</dayOfWeek>
            </restrictions>
            <restrictions>
               <dayDisabled>false</dayDisabled>
               <dayOfWeek>SUNDAY</dayOfWeek>
            </restrictions>
            <sendOnDate>2014-11-28T13:06:19.907Z</sendOnDate>
            <startDate>2014-11-28T00:00:00Z</startDate>
            <zonesList>
               <category>NORMAL</category>
               <code>ZNXT000015</code>
               <zone>Amoreiras</zone>
            </zonesList>
         </return>
      </ns2:getAddOnDetailsResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
{
  "getAddOnDetailsResponse": {
    "return": {
      "calendarRestricted": "false",
      "carClubCode": "NXT",
      "code": "AONXT1411000002",
      "description": "Teste",
      "discount": "100.0000",
      "extraKm": "0.00",
      "includedKm": "0",
      "message": ".",
      "monthlyFee": "0.00",
      "name": "Teste Inicio",
      "restrictions": [
        {
          "dayDisabled": "false",
          "dayOfWeek": "MONDAY"
        },
        {
          "dayDisabled": "false",
          "dayOfWeek": "TUESDAY"
        },
        {
          "dayDisabled": "false",
          "dayOfWeek": "WEDNESDAY"
        },
        {
          "dayDisabled": "false",
          "dayOfWeek": "THURSDAY"
        },
        {
          "dayDisabled": "false",
          "dayOfWeek": "FRIDAY"
        },
        {
          "dayDisabled": "false",
          "dayOfWeek": "SATURDAY"
        },
        {
          "dayDisabled": "false",
          "dayOfWeek": "SUNDAY"
        }
      ],
      "sendOnDate": "2014-11-28T13:06:19.907Z",
      "startDate": "2014-11-28T00:00:00Z",
      "zonesList": {
        "category": "NORMAL",
        "code": "ZNXT000015",
        "zone": "Amoreiras"
      }
    }
  }
}
```

Name | Type | Description
--------- | ------- | -----------
calendarRestricted
carClubCode | String | The car's club code.
code
description
discount
extraKm
includedKm
message
monthlyFee
name
restrictions
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dayDisabled
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dayOfWeek
sendOnDate
startDate
zonesList
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;category
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;code
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;zone

## - getCarClubByCarClubCode

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:car="http://mobics.criticalsoftware.com/carclub">
   <soapenv:Header xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/">
  <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
    <wsse:UsernameToken>
      <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
      <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">ApPOW3FYKX+NjT4yaVmgoEo8fXE=</wsse:Password>
      <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ2NDAxOTcyNTU1Mw==</wsse:Nonce>
      <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-05-23T17:08:45Z</wsu:Created>
    </wsse:UsernameToken>
  </wsse:Security>
</soapenv:Header>
   <soapenv:Body>
      <car:getCarClubByCarClubCode>
         <car:carClubCode>CTD</car:carClubCode>
      </car:getCarClubByCarClubCode>
   </soapenv:Body>
</soapenv:Envelope>
```

```plaintext
This service is not yet available in REST.
```

This service gets the car club resume characteristics.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/CarClub?wsdl`

<aside class="warning">
This service requires authentication.
</aside>

### Input Parameters

Name | Type | Description | Mandatory
--------- | ------- | ----------- | --------
carClubCode | String | The car club code. | Yes

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:getCarClubByCarClubCodeResponse xmlns:ns2="http://mobics.criticalsoftware.com/carclub" xmlns:ns3="http://www.criticalsoftware.com/mobios/country/configuration">
         <return>
            <carClubCode>CTD</carClubCode>
            <carClubColorScheme>LIGHT_GREEN</carClubColorScheme>
            <carClubContactEmail>info@citydrive.pt</carClubContactEmail>
            <carClubContactPhone>210136955</carClubContactPhone>
            <carClubName>Citydrive</carClubName>
            <carClubWebSiteURL>www.citydrive.pt</carClubWebSiteURL>
            <isStandalone>false</isStandalone>
         </return>
      </ns2:getCarClubByCarClubCodeResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
This service is not yet available in REST.
```

Name | Type | Description
--------- | ------- | -----------
carClubCode | String | The car's club code.
carClubColorScheme | String | The car's club color.
carClubContactEmail | String | The car's club email.
carClubContactPhone | String | The car's club phone number.
carClubName | String | The car's club name.
carClubWebSiteURL | String | The car's club web site url.
isStandalone | Boolean | If the car club is in standalone mode.

## - getCustomerCarClub

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:car="http://mobics.criticalsoftware.com/carclub">
   <soapenv:Header xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/">
  <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
    <wsse:UsernameToken>
      <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
      <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">ApPOW3FYKX+NjT4yaVmgoEo8fXE=</wsse:Password>
      <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ2NDAxOTcyNTU1Mw==</wsse:Nonce>
      <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-05-23T17:08:45Z</wsu:Created>
    </wsse:UsernameToken>
  </wsse:Security>
</soapenv:Header>
   <soapenv:Body>
      <car:getCustomerCarClub/>
   </soapenv:Body>
</soapenv:Envelope>
```

```plaintext
GET /mobics-webservices/rs/carclub/getCustomerCarClub HTTP/1.1
Host: imobics.mobiag.com
Content-Type: application/json
Username: ricardo.mendes@mobiag.com
Password: ApPOW3FYKX+NjT4yaVmgoEo8fXE=
Nonce: MTQ2NDAxOTcyNTU1Mw==
Created: 2016-05-23T17:08:45Z
Cache-Control: no-cache
```

This service gets the car club resume characteristics of the current customer.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/CarClub?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/carclub/getCustomerCarClub`

<aside class="warning">
This service requires authentication.
</aside>

### Input Parameters

This service has no input parameters.

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:getCustomerCarClubResponse xmlns:ns2="http://mobics.criticalsoftware.com/carclub" xmlns:ns3="http://www.criticalsoftware.com/mobios/country/configuration">
         <return>
            <carClubCode>CTD</carClubCode>
            <carClubColorScheme>LIGHT_GREEN</carClubColorScheme>
            <carClubContactEmail>info@citydrive.pt</carClubContactEmail>
            <carClubContactPhone>210136955</carClubContactPhone>
            <carClubName>Citydrive</carClubName>
            <carClubWebSiteURL>www.citydrive.pt</carClubWebSiteURL>
            <isStandalone>false</isStandalone>
         </return>
      </ns2:getCustomerCarClubResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
{
  "getCustomerCarClubResponse": {
    "return": {
      "carClubCode": "CTD",
      "carClubName": "Citydrive",
      "carClubColorScheme": "LIGHT_GREEN",
      "carClubContactPhone": "210136955",
      "carClubContactEmail": "info@citydrive.pt",
      "carClubWebSiteURL": "www.citydrive.pt",
      "isStandalone": false
    }
  }
}
```

Name | Type | Description
--------- | ------- | -----------
carClubCode | String | The car's club code.
carClubName | String | The car's club name.
carClubColorScheme | String | The car's club color.
carClubContactEmail | String | The car's club email.
carClubContactPhone | String | The car's club phone number.
carClubWebSiteURL | String | The car's club web site url.
isStandalone | Boolean | If the car club is in standalone mode.

# Find Cars

## Find Cars Immediate

This page contains the description of the process to Find Cars.
This process is the start of the booking flow and you can do the search using the services getCarOnRadius, searchCars and getCarsByLicensePlate from web services with SOAP or REST.

![Find Cars Immediate Diagram](/images/FindCarsImmediate.png)

You also can get all the cars of the car club with getFleet.

## - getCarOnRadius

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:fle="http://mobics.criticalsoftware.com/fleet">
<soapenv:Header/>
  <soapenv:Body>
    <fle:getCarsOnRadius>
      <!--Optional:-->
      <fle:carClubCode>CTD</fle:carClubCode>
      <!--Optional:-->
      <fle:latitude>38.72678700</fle:latitude>
      <!--Optional:-->
      <fle:longitude>-9.15427000</fle:longitude>
      <!--Optional:-->
      <fle:radius>3</fle:radius>
    </fle:getCarsOnRadius>
  </soapenv:Body>
</soapenv:Envelope>
```

```plaintext
This service is not yet available in REST.
```

This service gets all the cars around the user with the radius choosen. If the radius is bigger than 50 000 meters the value used is 50 000 meters.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Fleet?wsdl`

<aside class="success">
This service does not requires authentication.
</aside>

### Input Parameters

Name | Type | Description | Mandatory
--------- | ------- | ----------- | --------
carClubCode | String | The user's car club. | Yes
latitude | BigDecimal | The user's position (latitude). | Yes
longitude | BigDecimal | The user's position (longitude). |  Yes
radius | Integer | The radius that the user choosed. | No

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:getCarsOnRadiusResponse xmlns:ns2="http://mobics.criticalsoftware.com/fleet" xmlns:ns3="http://www.criticalsoftware.com/mobios/services/accounting/dto">
         <return>
            <carBrandName>Skoda</carBrandName>
            <carClubCode>NXT</carClubCode>
            <carClubName>Nextmotion</carClubName>
            <carFareType>STEP</carFareType>
            <carModelName>Fabia</carModelName>
            <carName>Skoda Fabia</carName>
            <carType>NORMAL</carType>
            <category>Small family car</category>
            <categoryDescription>main.car_class.small_familt_car</categoryDescription>
            <checkCard>false</checkCard>
            <checkKey>true</checkKey>
            <configurableTime>6</configurableTime>
            <costPerExtraKm>0.29</costPerExtraKm>
            <distance>0</distance>
            <distanceThreshold>20000</distanceThreshold>
            <fuelLevel>8</fuelLevel>
            <fuelType>
               <key>main.fuel_type.petrol</key>
               <name>PETROL</name>
            </fuelType>
            <includedDistancePerConfigurableHour>100000</includedDistancePerConfigurableHour>
            <includedDistancePerDay>200000</includedDistancePerDay>
            <latitude>38.72000504</latitude>
            <licensePlate>00-QE-07</licensePlate>
            <longitude>-9.14594173</longitude>
            <maxCostPerConfigurableHour>29.90</maxCostPerConfigurableHour>
            <maxCostPerDay>69.90</maxCostPerDay>
            <maxCostPerHour>9.90</maxCostPerHour>
            <obsConnectionStatus>OPERATIONAL</obsConnectionStatus>
            <obsNumber>41905</obsNumber>
            <priceBookedPerMinute>0.29</priceBookedPerMinute>
            <priceReservedPerMinute>0.10</priceReservedPerMinute>
            <showDamageReport>true</showDamageReport>
            <simNumber>123456789</simNumber>
            <standalone>false</standalone>
            <state>AVAILABLE</state>
            <totalDistanceTravelled>7783000</totalDistanceTravelled>
         </return>
      </ns2:getCarsOnRadiusResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
This service is not yet available in REST.
```

Name | Type | Description
--------- | ------- | -----------
carBrandName | String | The car's brand name.
carClubCode | String | The car's club code.
carFareType | Object | The car's fare type (Base or Step).
carModelName | String | The car's model name.
carType | Object | The car's type (Normal or Schedule Booking).
category | String | The car's category.
checkCard | Boolean | If check card device is active.
checkKey | Boolean | If check key device is active.
configurableTime | Integer | The car's seconds configurable time.
costPerExtraKm | BigDecimal | The cost of an extra km.
distance | BigDecimal | The distance that the car travelled.
distanceThreshold | BigDecimal | The car's limit distance.
fuelLevel | Integer | The car's fuel level.
fuelType | Object | The car's fuel type.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;key | String | The fuel's key code.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name | String | The fuel's name.
includedDistancePerConfigurableHour | Integer | The car's allowed distance to travel per hour.
includedDistancePerDay | Integer | The car's allowed distance to travel per day.
latitude | BigDecimal | The car's latitude.
licensePlate | String | The car's license plate.
longitude | BigDecimal | The car's longitude.
maxCostPerConfigurableHour | BigDecimal | The max cost per hour of the car (hour configurable).
maxCostPerDay | BigDecimal | The max cost per day of the car.
maxCostPerHour | BigDecimal | The max cost per hour of the car.
obsConnectionStatus | Object | The car's obs connection status.
obsNumber | String | The car's obs number.
priceBookedPerMinute | BigDecimal | The car's price booked per minute.
priceReservedPerMinute | BigDecimal | The car's price reserved per minute.
showDamageReport | Boolean | If damage report is to show.
simNumber | String | The car's sim number.
standalone | Boolean | If the car is in standlone mode.
state | String | The car's state.
totalDistanceTravelled | Integer | The car's total distance travelled.

## - searchCars

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:fle="http://mobics.criticalsoftware.com/fleet">
 <soapenv:Header>
   <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
       <wsse:UsernameToken>
         <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
         <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">Wxd4g3t79nCuHB3I+TnoxeCoNEs=</wsse:Password>
         <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ1NTk4NjI2MDQyNg==</wsse:Nonce>
         <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-02-20T16:37:40Z</wsu:Created>
       </wsse:UsernameToken>
   </wsse:Security>
</soapenv:Header>
   <soapenv:Body>
      <fle:searchCars>
         <!--Optional:-->
         <fle:carPrice></fle:carPrice>
         <!--Optional:-->
         <fle:carDistance></fle:carDistance>
         <!--Optional:-->
         <fle:carClass>Small family car</fle:carClass>
         <!--Optional:-->
         <fle:fuelType>DIESEL</fle:fuelType>
         <!--Optional:-->
         <fle:orderBy>CAR_DISTANCE</fle:orderBy>
         <!--Optional:-->
         <fle:maxResults></fle:maxResults>
         <!--Optional:-->
         <fle:latitude></fle:latitude>
         <!--Optional:-->
         <fle:longitude></fle:longitude>
         <!--Optional:-->
         <fle:carType>NORMAL</fle:carType>
      </fle:searchCars>
   </soapenv:Body>
</soapenv:Envelope>
```

```plaintext
GET /mobics-webservices/rs/fleet/searchCars HTTP/1.1
Host: imobics.mobiag.com
Username: ricardo.mendes@mobiag.com
Password: Wxd4g3t79nCuHB3I+TnoxeCoNEs=
Nonce: MTQ1NTk4NjI2MDQyNg==
Created: 2016-02-20T16:37:40Z
Content-Type: application/json
carClass: Supermini
fuelType: PETROL
orderBy: CAR_DISTANCE
carType: NORMAL
Cache-Control: no-cache
```

This service gets all the cars with the specific parameters.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Fleet?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/fleet/searchCars`

<aside class="warning">
This service requires authentication.
</aside>

### Input Parameters

Name | Type | Description | Mandatory
--------- | ------- | ----------- | --------
carPrice | BigDecimal | The car's price. | No
carDistance | BigDecimal | TThe car's distance from user. | No
carClass | String | The car's class. |  Yes
fuelType | String | The car's fuel type. | Yes
orderBy | String | The user's preference of order. | Yes
maxResults | Integer | The max results of cars. | No
latitude | BigDecimal | The user's position (latitude). | No
longitude | BigDecimal | The user's position (longitude). | No
carType | String | The car's type. | Yes

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:searchCarsResponse xmlns:ns2="http://mobics.criticalsoftware.com/fleet" xmlns:ns3="http://www.criticalsoftware.com/mobios/services/accounting/dto">
         <return>
            <carBrandName>Skoda</carBrandName>
            <carClubCode>NXT</carClubCode>
            <carClubName>Nextmotion</carClubName>
            <carFareType>STEP</carFareType>
            <carModelName>Fabia</carModelName>
            <carName>Skoda Fabia</carName>
            <carType>NORMAL</carType>
            <category>Small family car</category>
            <categoryDescription>main.car_class.small_familt_car</categoryDescription>
            <checkCard>false</checkCard>
            <checkKey>true</checkKey>
            <configurableTime>6</configurableTime>
            <costPerExtraKm>0.29</costPerExtraKm>
            <distance>0</distance>
            <distanceThreshold>20000</distanceThreshold>
            <fuelLevel>8</fuelLevel>
            <fuelType>
               <key>main.fuel_type.petrol</key>
               <name>PETROL</name>
            </fuelType>
            <includedDistancePerConfigurableHour>100000</includedDistancePerConfigurableHour>
            <includedDistancePerDay>200000</includedDistancePerDay>
            <latitude>38.72000504</latitude>
            <licensePlate>00-QE-07</licensePlate>
            <longitude>-9.14594173</longitude>
            <maxCostPerConfigurableHour>29.90</maxCostPerConfigurableHour>
            <maxCostPerDay>69.90</maxCostPerDay>
            <maxCostPerHour>9.90</maxCostPerHour>
            <obsConnectionStatus>OPERATIONAL</obsConnectionStatus>
            <obsNumber>41905</obsNumber>
            <priceBookedPerMinute>0.29</priceBookedPerMinute>
            <priceReservedPerMinute>0.10</priceReservedPerMinute>
            <showDamageReport>true</showDamageReport>
            <simNumber>123456789</simNumber>
            <standalone>false</standalone>
            <state>AVAILABLE</state>
            <totalDistanceTravelled>7783000</totalDistanceTravelled>
         </return>
      </ns2:searchCarsResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
{ 
 "searchCarsResponse": {
    "return": {
      "carBrandName": "Skoda",
      "carClubCode": "NXT",
      "carClubName": "Nextmotion",
      "carFareType": "STEP",
      "carModelName": "Fabia",
      "carName": "Skoda Fabia",
      "carType": "NORMAL",
      "category": "Small family car",
      "categoryDescription": "main.car_class.small_familt_car",
      "checkCard": "false",
      "checkKey": "true",
      "configurableTime": "6",
      "costPerExtraKm": "0.29",
      "distance": "0",
      "distanceThreshold": "20000",
      "fuelLevel": "8",
      "fuelType": {
        "key": "main.fuel_type.petrol",
        "name": "PETROL"
      },
      "includedDistancePerConfigurableHour": "100000",
      "includedDistancePerDay": "200000",
      "latitude": "38.72000504",
      "licensePlate": "00-QE-07",
      "longitude": "-9.14594173",
      "maxCostPerConfigurableHour": "29.90",
      "maxCostPerDay": "69.90",
      "maxCostPerHour": "9.90",
      "obsConnectionStatus": "OPERATIONAL",
      "obsNumber": "41905",
      "priceBookedPerMinute": "0.29",
      "priceReservedPerMinute": "0.10",
      "showDamageReport": "true",
      "simNumber": "123456789",
      "standalone": "false",
      "state": "AVAILABLE",
      "totalDistanceTravelled": "7783000"
    }
  }
}
```

Name | Type | Description
--------- | ------- | -----------
carBrandName | String | The car's brand name.
carClubCode | String | The car's club code.
carFareType | Object | The car's fare type (Base or Step).
carModelName | String | The car's model name.
carType | Object | The car's type (Normal or Schedule Booking).
category | String | The car's category.
checkCard | Boolean | If check card device is active.
checkKey | Boolean | If check key device is active.
configurableTime | Integer | The car's seconds configurable time.
costPerExtraKm | BigDecimal | The cost of an extra km.
distance | BigDecimal | The distance that the car travelled.
distanceThreshold | BigDecimal | The car's limit distance.
fuelLevel | Integer | The car's fuel level.
fuelType | Object | The car's fuel type.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;key | String | The fuel's key code.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name | String | The fuel's name.
includedDistancePerConfigurableHour | Integer | The car's allowed distance to travel per hour.
includedDistancePerDay | Integer | The car's allowed distance to travel per day.
latitude | BigDecimal | The car's latitude.
licensePlate | String | The car's license plate.
longitude | BigDecimal | The car's longitude.
maxCostPerConfigurableHour | BigDecimal | The max cost per hour of the car (hour configurable).
maxCostPerDay | BigDecimal | The max cost per day of the car.
maxCostPerHour | BigDecimal | The max cost per hour of the car.
obsConnectionStatus | Object | The car's obs connection status.
obsNumber | String | The car's obs number.
priceBookedPerMinute | BigDecimal | The car's price booked per minute.
priceReservedPerMinute | BigDecimal | The car's price reserved per minute.
showDamageReport | Boolean | If damage report is to show.
simNumber | String | The car's sim number.
standalone | Boolean | If the car is in standlone mode.
state | String | The car's state.
totalDistanceTravelled | Integer | The car's total distance travelled.

## - getCarsByLicensePlate

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:fle="http://mobics.criticalsoftware.com/fleet">
   <soapenv:Header>
   <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
      <wsse:UsernameToken>
         <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
         <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">Wxd4g3t79nCuHB3I+TnoxeCoNEs=</wsse:Password>
         <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ1NTk4NjI2MDQyNg==</wsse:Nonce>
         <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-02-20T16:37:40Z</wsu:Created>
      </wsse:UsernameToken>
   </wsse:Security>
</soapenv:Header>
   <soapenv:Body>
      <fle:getCarsByLicensePlate>
         <!--Optional:-->
         <fle:licensePlate></fle:licensePlate>
         <!--Optional:-->
         <fle:carType>NORMAL</fle:carType>
         <!--Optional:-->
         <fle:latitude></fle:latitude>
         <!--Optional:-->
         <fle:longitude></fle:longitude>
      </fle:getCarsByLicensePlate>
   </soapenv:Body>
</soapenv:Envelope>
```

```plaintext
GET /mobics-webservices/rs/fleet/getCarsByLicensePlate HTTP/1.1
Host: imobics.mobiag.com
Username: ricardo.mendes@mobiag.com
Password: Wxd4g3t79nCuHB3I+TnoxeCoNEs=
Nonce: MTQ1NTk4NjI2MDQyNg==
Created: 2016-02-20T16:37:40Z
Content-Type: application/json
carType: NORMAL
Cache-Control: no-cache
```

This service gets all the cars with the specific parameters. If the user set a license plate this service gets the car with that license plate.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Fleet?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/fleet/getCarsByLicensePlate`

<aside class="warning">
This service requires authentication.
</aside>

### Input Parameters

Name | Type | Description | Mandatory
--------- | ------- | ----------- | --------
licensePlate | String | The car's license plate. | No
carType | String | The car's type. | Yes
latitude | BigDecimal | The user's position (latitude). | No
longitude | BigDecimal | The user's position (longitude). | No

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:getCarsByLicensePlateResponse xmlns:ns2="http://mobics.criticalsoftware.com/fleet" xmlns:ns3="http://www.criticalsoftware.com/mobios/services/accounting/dto">
         <return>
            <carBrandName>Opel</carBrandName>
            <carClubCode>NXT</carClubCode>
            <carClubName>Nextmotion</carClubName>
            <carFareType>STEP</carFareType>
            <carModelName>Adam</carModelName>
            <carName>Opel Adam</carName>
            <carType>NORMAL</carType>
            <category>Supermini</category>
            <categoryDescription>main.car_class.supermini</categoryDescription>
            <checkCard>false</checkCard>
            <checkKey>true</checkKey>
            <configurableTime>12</configurableTime>
            <costPerExtraKm>0.29</costPerExtraKm>
            <distanceThreshold>20000</distanceThreshold>
            <fuelLevel>8</fuelLevel>
            <fuelType>
               <key>main.fuel_type.petrol</key>
               <name>PETROL</name>
            </fuelType>
            <includedDistancePerConfigurableHour>100000</includedDistancePerConfigurableHour>
            <includedDistancePerDay>200000</includedDistancePerDay>
            <licensePlate>48-OS-16</licensePlate>
            <maxCostPerConfigurableHour>29.90</maxCostPerConfigurableHour>
            <maxCostPerDay>49.90</maxCostPerDay>
            <maxCostPerHour>9.90</maxCostPerHour>
            <obsConnectionStatus>OPERATIONAL</obsConnectionStatus>
            <obsNumber>48151916</obsNumber>
            <priceBookedPerMinute>0.29</priceBookedPerMinute>
            <priceReservedPerMinute>0.10</priceReservedPerMinute>
            <promotions>
               <code>PCTD1512000023</code>
               <discount>100.0000</discount>
               <name>Embaixador Citydrive</name>
            </promotions>
            <promotions>
               <code>PCTD1604000032</code>
               <discount>100.0000</discount>
               <name>IndieLisboa</name>
            </promotions>
            <showDamageReport>true</showDamageReport>
            <simNumber>937930709</simNumber>
            <standalone>false</standalone>
            <state>UNAVAILABLE</state>
            <totalDistanceTravelled>10287000</totalDistanceTravelled>
         </return>      
    </ns2:getCarsByLicensePlateResponse>
  </soap:Body>
</soap:Envelope>
```

```plaintext
{
  "getCarsByLicensePlateResponse": {
    "return": {
      "carBrandName": "Opel",
      "carClubCode": "NXT",
      "carClubName": "Nextmotion",
      "carFareType": "STEP",
      "carModelName": "Adam",
      "carName": "Opel Adam",
      "carType": "NORMAL",
      "category": "Supermini",
      "categoryDescription": "main.car_class.supermini",
      "checkCard": "false",
      "checkKey": "true",
      "configurableTime": "12",
      "costPerExtraKm": "0.29",
      "distanceThreshold": "20000",
      "fuelLevel": "8",
      "fuelType": {
        "key": "main.fuel_type.petrol",
        "name": "PETROL"
      },
      "includedDistancePerConfigurableHour": "100000",
      "includedDistancePerDay": "200000",
      "licensePlate": "48-OS-16",
      "maxCostPerConfigurableHour": "29.90",
      "maxCostPerDay": "49.90",
      "maxCostPerHour": "9.90",
      "obsConnectionStatus": "OPERATIONAL",
      "obsNumber": "48151916",
      "priceBookedPerMinute": "0.29",
      "priceReservedPerMinute": "0.10",
      "promotions": [
        {
          "code": "PCTD1512000023",
          "discount": "100.0000",
          "name": "Embaixador Citydrive"
        },
        {
          "code": "PCTD1604000032",
          "discount": "100.0000",
          "name": "IndieLisboa"
        }
      ],
      "showDamageReport": "true",
      "simNumber": "937930709",
      "standalone": "false",
      "state": "UNAVAILABLE",
      "totalDistanceTravelled": "10287000"
    }
  }
}
```

Name | Type | Description
--------- | ------- | -----------
carBrandName | String | The car's brand name.
carClubCode | String | The car's club code.
carClubName | String | The car's club name.
carFareType | Object | The car's fare type (Base or Step).
carModelName | String | The car's model name.
carName | String | The car's name.
carType | Object | The car's type (Normal or Schedule Booking).
category | String | The car's category.
categoryDescription | String | The car's category description.
checkCard | Boolean | If check card device is active.
checkKey | Boolean | If check key device is active.
configurableTime | Integer | The car's seconds configurable time.
costPerExtraKm | BigDecimal | The cost of an extra km.
distanceThreshold | BigDecimal | The car's limit distance.
fuelLevel | Integer | The car's fuel level.
fuelType | Object | The car's fuel type.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;key | String | The fuel's key code.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name | String | The fuel's name.
includedDistancePerConfigurableHour | Integer | The car's allowed distance to travel per hour.
includedDistancePerDay | Integer | The car's allowed distance to travel per day.
latitude | BigDecimal | The car's latitude.
licensePlate | String | The car's license plate.
longitude | BigDecimal | The car's longitude.
maxCostPerConfigurableHour | BigDecimal | The max cost per hour of the car (hour configurable).
maxCostPerDay | BigDecimal | The max cost per day of the car.
maxCostPerHour | BigDecimal | The max cost per hour of the car.
obsConnectionStatus | Object | The car's obs connection status.
obsNumber | String | The car's obs number.
priceBookedPerMinute | BigDecimal | The car's price booked per minute.
priceReservedPerMinute | BigDecimal | The car's price reserved per minute.
promotions | Object | The car's available promotions.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;code | String | The promotion's code.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;discount | String | The promotion's discount.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name | String | The promotion's name.
showDamageReport | Boolean | If damage report is to show.
simNumber | String | The car's sim number.
standalone | Boolean | If the car is in standlone mode.
state | String | The car's state.
totalDistanceTravelled | Integer | The car's total distance travelled.

## - getFleet

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:fle="http://mobics.criticalsoftware.com/fleet">
   <soapenv:Header/>
   <soapenv:Body>
      <fle:getFleet>
         <!--Optional:-->
         <fle:carClubCode>CTD</fle:carClubCode>
      </fle:getFleet>
   </soapenv:Body>
</soapenv:Envelope>
```

```plaintext
GET /mobics-webservices/rs/fleet/getFleet HTTP/1.1
Host: imobics.mobiag.com
Content-Type: application/json
carClubCode: CTD
Cache-Control: no-cache
```

This service gets all the cars of the chosen car club.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Fleet?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/fleet/getFleet`

<aside class="success">
This service does not requires authentication.
</aside>

### Input Parameters

Name | Type | Description | Mandatory
--------- | ------- | ----------- | --------
carClubCode | String | The user's car club. | Yes

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:getFleetResponse xmlns:ns2="http://mobics.criticalsoftware.com/fleet">
         <return>
            <carBrandName>Porsche</carBrandName>
            <carClubCode>CTD</carClubCode>
            <carClubName>Citydrive @ Testes</carClubName>
            <carFareType>STEP</carFareType>
            <carModelName>911</carModelName>
            <carName>Porsche 911</carName>
            <carType>NORMAL</carType>
            <category>Supermini</category>
            <categoryDescription>main.car_class.supermini</categoryDescription>
            <checkCard>false</checkCard>
            <checkKey>true</checkKey>
            <configurableTime>4</configurableTime>
            <costPerExtraKm>0.29</costPerExtraKm>
            <distanceThreshold>20000</distanceThreshold>
            <fuelLevel>0</fuelLevel>
            <fuelType>
               <key>main.fuel_type.petrol</key>
               <name>PETROL</name>
            </fuelType>
            <includedDistancePerConfigurableHour>100000</includedDistancePerConfigurableHour>
            <includedDistancePerDay>200000</includedDistancePerDay>
            <latitude>47.50297928</latitude>
            <licensePlate>00-CB-00</licensePlate>
            <longitude>8.23988533</longitude>
            <maxCostPerConfigurableHour>29.90</maxCostPerConfigurableHour>
            <maxCostPerDay>68.90</maxCostPerDay>
            <maxCostPerHour>9.90</maxCostPerHour>
            <obsConnectionStatus>OPERATIONAL</obsConnectionStatus>
            <obsNumber>10101010</obsNumber>
            <priceBookedPerMinute>0.29</priceBookedPerMinute>
            <priceReservedPerMinute>0.10</priceReservedPerMinute>
            <showDamageReport>true</showDamageReport>
            <simNumber>123456789</simNumber>
            <standalone>true</standalone>
            <state>AVAILABLE</state>
            <totalDistanceTravelled>5000</totalDistanceTravelled>
         </return>
         <return>
            <carBrandName>Volkswagen</carBrandName>
            <carClubCode>CTD</carClubCode>
            <carClubName>Citydrive @ Testes</carClubName>
            <carFareType>STEP</carFareType>
            <carModelName>Polo</carModelName>
            <carName>Volkswagen Polo</carName>
            <carType>NORMAL</carType>
            <category>Supermini</category>
            <categoryDescription>main.car_class.supermini</categoryDescription>
            <checkCard>false</checkCard>
            <checkKey>true</checkKey>
            <configurableTime>4</configurableTime>
            <costPerExtraKm>3.69</costPerExtraKm>
            <distanceThreshold>1000</distanceThreshold>
            <fuelLevel>100</fuelLevel>
            <fuelType>
               <key>main.fuel_type.petrol</key>
               <name>PETROL</name>
            </fuelType>
            <includedDistancePerConfigurableHour>2000</includedDistancePerConfigurableHour>
            <includedDistancePerDay>3000</includedDistancePerDay>
            <latitude>40.19831848</latitude>
            <licensePlate>11-MR-75</licensePlate>
            <longitude>-8.51279259</longitude>
            <maxCostPerConfigurableHour>2.46</maxCostPerConfigurableHour>
            <maxCostPerDay>3.69</maxCostPerDay>
            <maxCostPerHour>1.23</maxCostPerHour>
            <obsConnectionStatus>UNTESTED</obsConnectionStatus>
            <obsNumber>36606</obsNumber>
            <priceBookedPerMinute>2.46</priceBookedPerMinute>
            <priceReservedPerMinute>1.23</priceReservedPerMinute>
            <showDamageReport>true</showDamageReport>
            <simNumber>123456789</simNumber>
            <standalone>true</standalone>
            <state>AVAILABLE</state>
            <totalDistanceTravelled>41447000</totalDistanceTravelled>
         </return>
      </ns2:getFleetResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
{
  "getFleetResponse": {
    "return": [
      {
        "carBrandName": "Porsche",
        "carClubCode": "CTD",
        "carClubName": "Citydrive @ Testes",
        "carFareType": "STEP",
        "carModelName": "911",
        "carName": "Porsche 911",
        "carType": "NORMAL",
        "category": "Supermini",
        "categoryDescription": "main.car_class.supermini",
        "checkCard": "false",
        "checkKey": "true",
        "configurableTime": "4",
        "costPerExtraKm": "0.29",
        "distanceThreshold": "20000",
        "fuelLevel": "0",
        "fuelType": {
          "key": "main.fuel_type.petrol",
          "name": "PETROL"
        },
        "includedDistancePerConfigurableHour": "100000",
        "includedDistancePerDay": "200000",
        "latitude": "47.50297928",
        "licensePlate": "00-CB-00",
        "longitude": "8.23988533",
        "maxCostPerConfigurableHour": "29.90",
        "maxCostPerDay": "68.90",
        "maxCostPerHour": "9.90",
        "obsConnectionStatus": "OPERATIONAL",
        "obsNumber": "10101010",
        "priceBookedPerMinute": "0.29",
        "priceReservedPerMinute": "0.10",
        "showDamageReport": "true",
        "simNumber": "123456789",
        "standalone": "true",
        "state": "AVAILABLE",
        "totalDistanceTravelled": "5000"
      },
      {
        "carBrandName": "Volkswagen",
        "carClubCode": "CTD",
        "carClubName": "Citydrive @ Testes",
        "carFareType": "STEP",
        "carModelName": "Polo",
        "carName": "Volkswagen Polo",
        "carType": "NORMAL",
        "category": "Supermini",
        "categoryDescription": "main.car_class.supermini",
        "checkCard": "false",
        "checkKey": "true",
        "configurableTime": "4",
        "costPerExtraKm": "3.69",
        "distanceThreshold": "1000",
        "fuelLevel": "100",
        "fuelType": {
          "key": "main.fuel_type.petrol",
          "name": "PETROL"
        },
        "includedDistancePerConfigurableHour": "2000",
        "includedDistancePerDay": "3000",
        "latitude": "40.19831848",
        "licensePlate": "11-MR-75",
        "longitude": "-8.51279259",
        "maxCostPerConfigurableHour": "2.46",
        "maxCostPerDay": "3.69",
        "maxCostPerHour": "1.23",
        "obsConnectionStatus": "UNTESTED",
        "obsNumber": "36606",
        "priceBookedPerMinute": "2.46",
        "priceReservedPerMinute": "1.23",
        "showDamageReport": "true",
        "simNumber": "123456789",
        "standalone": "true",
        "state": "AVAILABLE",
        "totalDistanceTravelled": "41447000"
      }
    ]
  }
}
```

Name | Type | Description
--------- | ------- | -----------
carBrandName | String | The car's brand name.
carClubCode | String | The car's club code.
carClubName | String | The car's club name.
carFareType | Object | The car's fare type (Base or Step).
carModelName | String | The car's model name.
carName | String | The car's name.
carType | Object | The car's type (Normal or Schedule Booking).
category | String | The car's category.
categoryDescription | String | The car's category description.
checkCard | Boolean | If check card device is active.
checkKey | Boolean | If check key device is active.
configurableTime | Integer | The car's seconds configurable time.
costPerExtraKm | BigDecimal | The cost of an extra km.
distanceThreshold | BigDecimal | The car's limit distance.
fuelLevel | Integer | The car's fuel level.
fuelType | Object | The car's fuel type.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;key | String | The fuel's key code.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name | String | The fuel's name.
includedDistancePerConfigurableHour | Integer | The car's allowed distance to travel per hour.
includedDistancePerDay | Integer | The car's allowed distance to travel per day.
latitude | BigDecimal | The car's latitude.
licensePlate | String | The car's license plate.
longitude | BigDecimal | The car's longitude.
maxCostPerConfigurableHour | BigDecimal | The max cost per hour of the car (hour configurable).
maxCostPerDay | BigDecimal | The max cost per day of the car.
maxCostPerHour | BigDecimal | The max cost per hour of the car.
obsConnectionStatus | Object | The car's obs connection status.
obsNumber | String | The car's obs number.
priceBookedPerMinute | BigDecimal | The car's price booked per minute.
priceReservedPerMinute | BigDecimal | The car's price reserved per minute.
showDamageReport | Boolean | If damage report is to show.
simNumber | String | The car's sim number.
standalone | Boolean | If the car is in standlone mode.
state | String | The car's state.
totalDistanceTravelled | Integer | The car's total distance travelled.

## Find Cars Advance

This page contains the description of the process to Find Cars.
This process is the start of the booking flow and you can do the search using the services getCarsForAdvanceBooking, getCarsInLocationByCarClubCodeAndLocationCode, getCarsInLocationByCarClubCode and getNextAvailableCarForAdvanceBooking from web services with SOAP or REST.

![Find Cars Immediate Diagram](/images/FindCarsAdvance.png)

You also can get all the cars of the car club with getFleet.

## - getCarsForAdvanceBooking

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:fle="http://mobics.criticalsoftware.com/fleet">
   <soapenv:Header/>
   <soapenv:Body>
      <fle:getCarsForAdvanceBooking>
         <!--Optional:-->
         <fle:carClubCode>CTD</fle:carClubCode>
         <!--Optional:-->
         <fle:parkName></fle:parkName>
         <!--Optional:-->
         <fle:locationCode></fle:locationCode>
         <!--Optional:-->
         <fle:beginBooking>1461920400000</fle:beginBooking>
         <!--Optional:-->
         <fle:endBooking>1461924000000</fle:endBooking>
      </fle:getCarsForAdvanceBooking>
   </soapenv:Body>
</soapenv:Envelope>
```

```plaintext
GET /mobics-webservices/rs/fleet/getCarsForAdvanceBooking HTTP/1.1
Host: imobics.mobiag.com
Content-Type: application/json
beginBooking: 1461920400000
endBooking: 1461924000000
carClubCode: CTD
Cache-Control: no-cache
```

This service gets all the cars available to book in a specific period.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Fleet?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/fleet/getCarsForAdvanceBooking`

<aside class="success">
This service does not requires authentication.
</aside>

### Input Parameters

Name | Type | Description | Mandatory
--------- | ------- | ----------- | --------
carClubCode | String | The user's car club. | Yes
parkName | String | The park's name. | No
locationCode | String | The location's code. | No
beginBooking | Long | The booking's begin date. | Yes
endBooking | Long | The booking's end date. | Yes

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:getCarsForAdvanceBookingResponse xmlns:ns2="http://mobics.criticalsoftware.com/fleet" xmlns:ns3="http://www.criticalsoftware.com/mobios/services/accounting/dto">
         <return>
            <carBrandName>Volkswagen</carBrandName>
            <carClubCode>NXT</carClubCode>
            <carClubName>Nextmotion</carClubName>
            <carFareType>STEP</carFareType>
            <carModelName>Up</carModelName>
            <carName>Volkswagen Up</carName>
            <carType>NORMAL</carType>
            <category>Supermini</category>
            <categoryDescription>main.car_class.supermini</categoryDescription>
            <checkCard>false</checkCard>
            <checkKey>true</checkKey>
            <configurableTime>6</configurableTime>
            <costPerExtraKm>0.29</costPerExtraKm>
            <distanceThreshold>20000</distanceThreshold>
            <fuelLevel>31</fuelLevel>
            <fuelType>
               <key>main.fuel_type.petrol</key>
               <name>PETROL</name>
            </fuelType>
            <includedDistancePerConfigurableHour>100000</includedDistancePerConfigurableHour>
            <includedDistancePerDay>200000</includedDistancePerDay>
            <licensePlate>15-OS-58</licensePlate>
            <maxCostPerConfigurableHour>29.90</maxCostPerConfigurableHour>
            <maxCostPerDay>69.90</maxCostPerDay>
            <maxCostPerHour>9.90</maxCostPerHour>
            <obsConnectionStatus>OPERATIONAL</obsConnectionStatus>
            <obsNumber>15151958</obsNumber>
            <priceBookedPerMinute>0.29</priceBookedPerMinute>
            <priceReservedPerMinute>0.10</priceReservedPerMinute>
            <showDamageReport>true</showDamageReport>
            <simNumber>123456789</simNumber>
            <standalone>false</standalone>
            <state>BOOKED</state>
            <totalDistanceTravelled>28618000</totalDistanceTravelled>
         </return>
       </ns2:getCarsForAdvanceBookingResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
{
  "getCarsForAdvanceBookingResponse": {
    "return": {
      "carBrandName": "Volkswagen",
      "carClubCode": "NXT",
      "carClubName": "Nextmotion",
      "carFareType": "STEP",
      "carModelName": "Up",
      "carName": "Volkswagen Up",
      "carType": "NORMAL",
      "category": "Supermini",
      "categoryDescription": "main.car_class.supermini",
      "checkCard": "false",
      "checkKey": "true",
      "configurableTime": "6",
      "costPerExtraKm": "0.29",
      "distanceThreshold": "20000",
      "fuelLevel": "31",
      "fuelType": {
        "key": "main.fuel_type.petrol",
        "name": "PETROL"
      },
      "includedDistancePerConfigurableHour": "100000",
      "includedDistancePerDay": "200000",
      "licensePlate": "15-OS-58",
      "maxCostPerConfigurableHour": "29.90",
      "maxCostPerDay": "69.90",
      "maxCostPerHour": "9.90",
      "obsConnectionStatus": "OPERATIONAL",
      "obsNumber": "15151958",
      "priceBookedPerMinute": "0.29",
      "priceReservedPerMinute": "0.10",
      "showDamageReport": "true",
      "simNumber": "123456789",
      "standalone": "false",
      "state": "BOOKED",
      "totalDistanceTravelled": "28618000"
    }
  }
}
```

Name | Type | Description
--------- | ------- | -----------
carBrandName | String | The car's brand name.
carClubCode | String | The car's club code.
carClubName | String | The car's club name.
carFareType | Object | The car's fare type (Base or Step).
carModelName | String | The car's model name.
carName | String | The car's name.
carType | Object | The car's type (Normal or Schedule Booking).
category | String | The car's category.
categoryDescription | String | The car's category description.
checkCard | Boolean | If check card device is active.
checkKey | Boolean | If check key device is active.
configurableTime | Integer | The car's seconds configurable time.
costPerExtraKm | BigDecimal | The cost of an extra km.
distanceThreshold | BigDecimal | The car's limit distance.
fuelLevel | Integer | The car's fuel level.
fuelType | Object | The car's fuel type.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;key | String | The fuel's key code.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name | String | The fuel's name.
includedDistancePerConfigurableHour | Integer | The car's allowed distance to travel per hour.
includedDistancePerDay | Integer | The car's allowed distance to travel per day.
latitude | BigDecimal | The car's latitude.
licensePlate | String | The car's license plate.
longitude | BigDecimal | The car's longitude.
maxCostPerConfigurableHour | BigDecimal | The max cost per hour of the car (hour configurable).
maxCostPerDay | BigDecimal | The max cost per day of the car.
maxCostPerHour | BigDecimal | The max cost per hour of the car.
obsConnectionStatus | Object | The car's obs connection status.
obsNumber | String | The car's obs number.
priceBookedPerMinute | BigDecimal | The car's price booked per minute.
priceReservedPerMinute | BigDecimal | The car's price reserved per minute.
showDamageReport | Boolean | If damage report is to show.
simNumber | String | The car's sim number.
standalone | Boolean | If the car is in standlone mode.
state | String | The car's state.
totalDistanceTravelled | Integer | The car's total distance travelled.

## - getNextAvailableCarForAdvanceBooking

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:fle="http://mobics.criticalsoftware.com/fleet">
   <soapenv:Header/>
   <soapenv:Body>
      <fle:getNextAvailableCarForAdvanceBooking>
         <!--Optional:-->
         <fle:carClubCode>CTD</fle:carClubCode>
         <!--Optional:-->
         <fle:locationCode>LSB</fle:locationCode>
         <!--Optional:-->
         <fle:beginBooking>1461920400000</fle:beginBooking>
         <!--Optional:-->
         <fle:endBooking>1461924000000</fle:endBooking>
      </fle:getNextAvailableCarForAdvanceBooking>
   </soapenv:Body>
</soapenv:Envelope>
```

```plaintext
GET /mobics-webservices/rs/fleet/getNextAvailableCarForAdvanceBooking HTTP/1.1
Host: imobics.mobiag.com
Content-Type: application/json
beginBooking: 1461920400000
endBooking: 1461924000000
carClubCode: CTD
locationCode: LSB
Cache-Control: no-cache
```

This service gets the car available to book in a specific period and location.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Fleet?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/fleet/getCarsForAdvanceBooking`

<aside class="success">
This service does not requires authentication.
</aside>

### Input Parameters

Name | Type | Description | Mandatory
--------- | ------- | ----------- | --------
carClubCode | String | The user's car club. | Yes
locationCode | String | The location's code. | Yes
beginBooking | Long | The booking's begin date. | Yes
endBooking | Long | The booking's end date. | Yes

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:getNextAvailableCarForAdvanceBookingCodeResponse xmlns:ns2="http://mobics.criticalsoftware.com/fleet" xmlns:ns3="http://www.criticalsoftware.com/mobios/services/accounting/dto">
         <return>
            <carBrandName>Volkswagen</carBrandName>
            <carClubCode>NXT</carClubCode>
            <carClubName>Nextmotion</carClubName>
            <carFareType>STEP</carFareType>
            <carModelName>Up</carModelName>
            <carName>Volkswagen Up</carName>
            <carType>NORMAL</carType>
            <category>Supermini</category>
            <categoryDescription>main.car_class.supermini</categoryDescription>
            <checkCard>false</checkCard>
            <checkKey>true</checkKey>
            <configurableTime>6</configurableTime>
            <costPerExtraKm>0.29</costPerExtraKm>
            <distanceThreshold>20000</distanceThreshold>
            <fuelLevel>31</fuelLevel>
            <fuelType>
               <key>main.fuel_type.petrol</key>
               <name>PETROL</name>
            </fuelType>
            <includedDistancePerConfigurableHour>100000</includedDistancePerConfigurableHour>
            <includedDistancePerDay>200000</includedDistancePerDay>
            <licensePlate>15-OS-58</licensePlate>
            <maxCostPerConfigurableHour>29.90</maxCostPerConfigurableHour>
            <maxCostPerDay>69.90</maxCostPerDay>
            <maxCostPerHour>9.90</maxCostPerHour>
            <obsConnectionStatus>OPERATIONAL</obsConnectionStatus>
            <obsNumber>15151958</obsNumber>
            <priceBookedPerMinute>0.29</priceBookedPerMinute>
            <priceReservedPerMinute>0.10</priceReservedPerMinute>
            <showDamageReport>true</showDamageReport>
            <simNumber>123456789</simNumber>
            <standalone>false</standalone>
            <state>BOOKED</state>
            <totalDistanceTravelled>28618000</totalDistanceTravelled>
         </return>
       </ns2:getNextAvailableCarForAdvanceBookingResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
{
  "getNextAvailableCarForAdvanceBookingResponse": {
    "return": {
      "carBrandName": "Volkswagen",
      "carClubCode": "NXT",
      "carClubName": "Nextmotion",
      "carFareType": "STEP",
      "carModelName": "Up",
      "carName": "Volkswagen Up",
      "carType": "NORMAL",
      "category": "Supermini",
      "categoryDescription": "main.car_class.supermini",
      "checkCard": "false",
      "checkKey": "true",
      "configurableTime": "6",
      "costPerExtraKm": "0.29",
      "distanceThreshold": "20000",
      "fuelLevel": "31",
      "fuelType": {
        "key": "main.fuel_type.petrol",
        "name": "PETROL"
      },
      "includedDistancePerConfigurableHour": "100000",
      "includedDistancePerDay": "200000",
      "licensePlate": "15-OS-58",
      "maxCostPerConfigurableHour": "29.90",
      "maxCostPerDay": "69.90",
      "maxCostPerHour": "9.90",
      "obsConnectionStatus": "OPERATIONAL",
      "obsNumber": "15151958",
      "priceBookedPerMinute": "0.29",
      "priceReservedPerMinute": "0.10",
      "showDamageReport": "true",
      "simNumber": "123456789",
      "standalone": "false",
      "state": "BOOKED",
      "totalDistanceTravelled": "28618000"
    }
  }
}
```

Name | Type | Description
--------- | ------- | -----------
carBrandName | String | The car's brand name.
carClubCode | String | The car's club code.
carClubName | String | The car's club name.
carFareType | Object | The car's fare type (Base or Step).
carModelName | String | The car's model name.
carName | String | The car's name.
carType | Object | The car's type (Normal or Schedule Booking).
category | String | The car's category.
categoryDescription | String | The car's category description.
checkCard | Boolean | If check card device is active.
checkKey | Boolean | If check key device is active.
configurableTime | Integer | The car's seconds configurable time.
costPerExtraKm | BigDecimal | The cost of an extra km.
distanceThreshold | BigDecimal | The car's limit distance.
fuelLevel | Integer | The car's fuel level.
fuelType | Object | The car's fuel type.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;key | String | The fuel's key code.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name | String | The fuel's name.
includedDistancePerConfigurableHour | Integer | The car's allowed distance to travel per hour.
includedDistancePerDay | Integer | The car's allowed distance to travel per day.
licensePlate | String | The car's license plate.
maxCostPerConfigurableHour | BigDecimal | The max cost per hour of the car (hour configurable).
maxCostPerDay | BigDecimal | The max cost per day of the car.
maxCostPerHour | BigDecimal | The max cost per hour of the car.
obsConnectionStatus | Object | The car's obs connection status.
obsNumber | String | The car's obs number.
priceBookedPerMinute | BigDecimal | The car's price booked per minute.
priceReservedPerMinute | BigDecimal | The car's price reserved per minute.
showDamageReport | Boolean | If damage report is to show.
simNumber | String | The car's sim number.
standalone | Boolean | If the car is in standlone mode.
state | String | The car's state.
totalDistanceTravelled | Integer | The car's total distance travelled.

## - getCarsInLocationByCarClubCodeAndLocationCode

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:fle="http://mobics.criticalsoftware.com/fleet">
   <soapenv:Header/>
   <soapenv:Body>
      <fle:getCarsInLocationByCarClubCodeAndLocationCode>
         <!--Optional:-->
         <fle:carClubCode>CTD</fle:carClubCode>
         <!--Optional:-->
         <fle:locationCode>LSB</fle:locationCode>
      </fle:getCarsInLocationByCarClubCodeAndLocationCode>
   </soapenv:Body>
</soapenv:Envelope>
```

```plaintext
GET /mobics-webservices/rs/fleet/getCarsInLocationByCarClubCodeAndLocationCode HTTP/1.1
Host: imobics.mobiag.com
Content-Type: application/json
carClubCode: CTD
locationCode: LSB
Cache-Control: no-cache
```

This service gets all the cars of a specific car club and a specific location.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Fleet?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/fleet/getCarsInLocationByCarClubCodeAndLocationCode`

<aside class="success">
This service does not requires authentication.
</aside>

### Input Parameters

Name | Type | Description | Mandatory
--------- | ------- | ----------- | --------
carClubCode | String | The user's car club. | Yes
locationCode | String | The location's code. | Yes

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:getCarsInLocationByCarClubCodeAndLocationCodeResponse xmlns:ns2="http://mobics.criticalsoftware.com/fleet" xmlns:ns3="http://www.criticalsoftware.com/mobios/services/accounting/dto">
         <return>
            <carBrandName>Volkswagen</carBrandName>
            <carClubCode>NXT</carClubCode>
            <carClubName>Nextmotion</carClubName>
            <carFareType>STEP</carFareType>
            <carModelName>Up</carModelName>
            <carName>Volkswagen Up</carName>
            <carType>NORMAL</carType>
            <category>Supermini</category>
            <categoryDescription>main.car_class.supermini</categoryDescription>
            <checkCard>false</checkCard>
            <checkKey>true</checkKey>
            <configurableTime>6</configurableTime>
            <costPerExtraKm>0.29</costPerExtraKm>
            <distanceThreshold>20000</distanceThreshold>
            <fuelLevel>31</fuelLevel>
            <fuelType>
               <key>main.fuel_type.petrol</key>
               <name>PETROL</name>
            </fuelType>
            <includedDistancePerConfigurableHour>100000</includedDistancePerConfigurableHour>
            <includedDistancePerDay>200000</includedDistancePerDay>
            <licensePlate>15-OS-58</licensePlate>
            <maxCostPerConfigurableHour>29.90</maxCostPerConfigurableHour>
            <maxCostPerDay>69.90</maxCostPerDay>
            <maxCostPerHour>9.90</maxCostPerHour>
            <obsConnectionStatus>OPERATIONAL</obsConnectionStatus>
            <obsNumber>15151958</obsNumber>
            <priceBookedPerMinute>0.29</priceBookedPerMinute>
            <priceReservedPerMinute>0.10</priceReservedPerMinute>
            <showDamageReport>true</showDamageReport>
            <simNumber>123456789</simNumber>
            <standalone>false</standalone>
            <state>BOOKED</state>
            <totalDistanceTravelled>28618000</totalDistanceTravelled>
         </return>
       </ns2:getCarsInLocationByCarClubCodeAndLocationCodeResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
{
  "getCarsInLocationByCarClubCodeAndLocationCodeResponse": {
    "return": {
      "carBrandName": "Volkswagen",
      "carClubCode": "NXT",
      "carClubName": "Nextmotion",
      "carFareType": "STEP",
      "carModelName": "Up",
      "carName": "Volkswagen Up",
      "carType": "NORMAL",
      "category": "Supermini",
      "categoryDescription": "main.car_class.supermini",
      "checkCard": "false",
      "checkKey": "true",
      "configurableTime": "6",
      "costPerExtraKm": "0.29",
      "distanceThreshold": "20000",
      "fuelLevel": "31",
      "fuelType": {
        "key": "main.fuel_type.petrol",
        "name": "PETROL"
      },
      "includedDistancePerConfigurableHour": "100000",
      "includedDistancePerDay": "200000",
      "licensePlate": "15-OS-58",
      "maxCostPerConfigurableHour": "29.90",
      "maxCostPerDay": "69.90",
      "maxCostPerHour": "9.90",
      "obsConnectionStatus": "OPERATIONAL",
      "obsNumber": "15151958",
      "priceBookedPerMinute": "0.29",
      "priceReservedPerMinute": "0.10",
      "showDamageReport": "true",
      "simNumber": "123456789",
      "standalone": "false",
      "state": "BOOKED",
      "totalDistanceTravelled": "28618000"
    }
  }
}
```

Name | Type | Description
--------- | ------- | -----------
carBrandName | String | The car's brand name.
carClubCode | String | The car's club code.
carClubName | String | The car's club name.
carFareType | Object | The car's fare type (Base or Step).
carModelName | String | The car's model name.
carName | String | The car's name.
carType | Object | The car's type (Normal or Schedule Booking).
category | String | The car's category.
categoryDescription | String | The car's category description.
checkCard | Boolean | If check card device is active.
checkKey | Boolean | If check key device is active.
configurableTime | Integer | The car's seconds configurable time.
costPerExtraKm | BigDecimal | The cost of an extra km.
distanceThreshold | BigDecimal | The car's limit distance.
fuelLevel | Integer | The car's fuel level.
fuelType | Object | The car's fuel type.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;key | String | The fuel's key code.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name | String | The fuel's name.
includedDistancePerConfigurableHour | Integer | The car's allowed distance to travel per hour.
includedDistancePerDay | Integer | The car's allowed distance to travel per day.
licensePlate | String | The car's license plate.
maxCostPerConfigurableHour | BigDecimal | The max cost per hour of the car (hour configurable).
maxCostPerDay | BigDecimal | The max cost per day of the car.
maxCostPerHour | BigDecimal | The max cost per hour of the car.
obsConnectionStatus | Object | The car's obs connection status.
obsNumber | String | The car's obs number.
priceBookedPerMinute | BigDecimal | The car's price booked per minute.
priceReservedPerMinute | BigDecimal | The car's price reserved per minute.
showDamageReport | Boolean | If damage report is to show.
simNumber | String | The car's sim number.
standalone | Boolean | If the car is in standlone mode.
state | String | The car's state.
totalDistanceTravelled | Integer | The car's total distance travelled.

## - getCarsInLocationByCarClubCode

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:fle="http://mobics.criticalsoftware.com/fleet">
   <soapenv:Header/>
   <soapenv:Body>
      <fle:getCarsInLocationsByCarClubCode>
         <!--Optional:-->
         <fle:carClubCode>CTD</fle:carClubCode>
      </fle:getCarsInLocationsByCarClubCode>
   </soapenv:Body>
</soapenv:Envelope>
```

```plaintext
GET /mobics-webservices/rs/fleet/getCarsInLocationByCarClubCode HTTP/1.1
Host: imobics.mobiag.com
Content-Type: application/json
carClubCode: CTD
Cache-Control: no-cache
```

This service gets all the cars of a specific car club and a specific location.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Fleet?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/fleet/getCarsInLocationByCarClubCode`

<aside class="success">
This service does not requires authentication.
</aside>

### Input Parameters

Name | Type | Description | Mandatory
--------- | ------- | ----------- | --------
carClubCode | String | The user's car club. | Yes

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:getCarsInLocationByCarClubCodeResponse xmlns:ns2="http://mobics.criticalsoftware.com/fleet" xmlns:ns3="http://www.criticalsoftware.com/mobios/services/accounting/dto">
         <return>
            <carBrandName>Volkswagen</carBrandName>
            <carClubCode>NXT</carClubCode>
            <carClubName>Nextmotion</carClubName>
            <carFareType>STEP</carFareType>
            <carModelName>Up</carModelName>
            <carName>Volkswagen Up</carName>
            <carType>NORMAL</carType>
            <category>Supermini</category>
            <categoryDescription>main.car_class.supermini</categoryDescription>
            <checkCard>false</checkCard>
            <checkKey>true</checkKey>
            <configurableTime>6</configurableTime>
            <costPerExtraKm>0.29</costPerExtraKm>
            <distanceThreshold>20000</distanceThreshold>
            <fuelLevel>31</fuelLevel>
            <fuelType>
               <key>main.fuel_type.petrol</key>
               <name>PETROL</name>
            </fuelType>
            <includedDistancePerConfigurableHour>100000</includedDistancePerConfigurableHour>
            <includedDistancePerDay>200000</includedDistancePerDay>
            <licensePlate>15-OS-58</licensePlate>
            <maxCostPerConfigurableHour>29.90</maxCostPerConfigurableHour>
            <maxCostPerDay>69.90</maxCostPerDay>
            <maxCostPerHour>9.90</maxCostPerHour>
            <obsConnectionStatus>OPERATIONAL</obsConnectionStatus>
            <obsNumber>15151958</obsNumber>
            <priceBookedPerMinute>0.29</priceBookedPerMinute>
            <priceReservedPerMinute>0.10</priceReservedPerMinute>
            <showDamageReport>true</showDamageReport>
            <simNumber>123456789</simNumber>
            <standalone>false</standalone>
            <state>BOOKED</state>
            <totalDistanceTravelled>28618000</totalDistanceTravelled>
         </return>
       </ns2:getCarsInLocationByCarClubCodeResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
{
  "getCarsInLocationByCarClubCodeResponse": {
    "return": {
      "carBrandName": "Volkswagen",
      "carClubCode": "NXT",
      "carClubName": "Nextmotion",
      "carFareType": "STEP",
      "carModelName": "Up",
      "carName": "Volkswagen Up",
      "carType": "NORMAL",
      "category": "Supermini",
      "categoryDescription": "main.car_class.supermini",
      "checkCard": "false",
      "checkKey": "true",
      "configurableTime": "6",
      "costPerExtraKm": "0.29",
      "distanceThreshold": "20000",
      "fuelLevel": "31",
      "fuelType": {
        "key": "main.fuel_type.petrol",
        "name": "PETROL"
      },
      "includedDistancePerConfigurableHour": "100000",
      "includedDistancePerDay": "200000",
      "licensePlate": "15-OS-58",
      "maxCostPerConfigurableHour": "29.90",
      "maxCostPerDay": "69.90",
      "maxCostPerHour": "9.90",
      "obsConnectionStatus": "OPERATIONAL",
      "obsNumber": "15151958",
      "priceBookedPerMinute": "0.29",
      "priceReservedPerMinute": "0.10",
      "showDamageReport": "true",
      "simNumber": "123456789",
      "standalone": "false",
      "state": "BOOKED",
      "totalDistanceTravelled": "28618000"
    }
  }
}
```

Name | Type | Description
--------- | ------- | -----------
carBrandName | String | The car's brand name.
carClubCode | String | The car's club code.
carClubName | String | The car's club name.
carFareType | Object | The car's fare type (Base or Step).
carModelName | String | The car's model name.
carName | String | The car's name.
carType | Object | The car's type (Normal or Schedule Booking).
category | String | The car's category.
categoryDescription | String | The car's category description.
checkCard | Boolean | If check card device is active.
checkKey | Boolean | If check key device is active.
configurableTime | Integer | The car's seconds configurable time.
costPerExtraKm | BigDecimal | The cost of an extra km.
distanceThreshold | BigDecimal | The car's limit distance.
fuelLevel | Integer | The car's fuel level.
fuelType | Object | The car's fuel type.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;key | String | The fuel's key code.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name | String | The fuel's name.
includedDistancePerConfigurableHour | Integer | The car's allowed distance to travel per hour.
includedDistancePerDay | Integer | The car's allowed distance to travel per day.
licensePlate | String | The car's license plate.
maxCostPerConfigurableHour | BigDecimal | The max cost per hour of the car (hour configurable).
maxCostPerDay | BigDecimal | The max cost per day of the car.
maxCostPerHour | BigDecimal | The max cost per hour of the car.
obsConnectionStatus | Object | The car's obs connection status.
obsNumber | String | The car's obs number.
priceBookedPerMinute | BigDecimal | The car's price booked per minute.
priceReservedPerMinute | BigDecimal | The car's price reserved per minute.
showDamageReport | Boolean | If damage report is to show.
simNumber | String | The car's sim number.
standalone | Boolean | If the car is in standlone mode.
state | String | The car's state.
totalDistanceTravelled | Integer | The car's total distance travelled.

## - getFleet

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:fle="http://mobics.criticalsoftware.com/fleet">
   <soapenv:Header/>
   <soapenv:Body>
      <fle:getFleet>
         <!--Optional:-->
         <fle:carClubCode>CTD</fle:carClubCode>
      </fle:getFleet>
   </soapenv:Body>
</soapenv:Envelope>
```

```plaintext
GET /mobics-webservices/rs/fleet/getFleet HTTP/1.1
Host: imobics.mobiag.com
Content-Type: application/json
carClubCode: CTD
Cache-Control: no-cache
```

This service gets all the cars of the chosen car club.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Fleet?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/fleet/getFleet`

<aside class="success">
This service does not requires authentication.
</aside>

### Input Parameters

Name | Type | Description | Mandatory
--------- | ------- | ----------- | --------
carClubCode | String | The user's car club. | Yes

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:getFleetResponse xmlns:ns2="http://mobics.criticalsoftware.com/fleet">
         <return>
            <carBrandName>Porsche</carBrandName>
            <carClubCode>CTD</carClubCode>
            <carClubName>Citydrive @ Testes</carClubName>
            <carFareType>STEP</carFareType>
            <carModelName>911</carModelName>
            <carName>Porsche 911</carName>
            <carType>NORMAL</carType>
            <category>Supermini</category>
            <categoryDescription>main.car_class.supermini</categoryDescription>
            <checkCard>false</checkCard>
            <checkKey>true</checkKey>
            <configurableTime>4</configurableTime>
            <costPerExtraKm>0.29</costPerExtraKm>
            <distanceThreshold>20000</distanceThreshold>
            <fuelLevel>0</fuelLevel>
            <fuelType>
               <key>main.fuel_type.petrol</key>
               <name>PETROL</name>
            </fuelType>
            <includedDistancePerConfigurableHour>100000</includedDistancePerConfigurableHour>
            <includedDistancePerDay>200000</includedDistancePerDay>
            <latitude>47.50297928</latitude>
            <licensePlate>00-CB-00</licensePlate>
            <longitude>8.23988533</longitude>
            <maxCostPerConfigurableHour>29.90</maxCostPerConfigurableHour>
            <maxCostPerDay>68.90</maxCostPerDay>
            <maxCostPerHour>9.90</maxCostPerHour>
            <obsConnectionStatus>OPERATIONAL</obsConnectionStatus>
            <obsNumber>10101010</obsNumber>
            <priceBookedPerMinute>0.29</priceBookedPerMinute>
            <priceReservedPerMinute>0.10</priceReservedPerMinute>
            <showDamageReport>true</showDamageReport>
            <simNumber>123456789</simNumber>
            <standalone>true</standalone>
            <state>AVAILABLE</state>
            <totalDistanceTravelled>5000</totalDistanceTravelled>
         </return>
         <return>
            <carBrandName>Volkswagen</carBrandName>
            <carClubCode>CTD</carClubCode>
            <carClubName>Citydrive @ Testes</carClubName>
            <carFareType>STEP</carFareType>
            <carModelName>Polo</carModelName>
            <carName>Volkswagen Polo</carName>
            <carType>NORMAL</carType>
            <category>Supermini</category>
            <categoryDescription>main.car_class.supermini</categoryDescription>
            <checkCard>false</checkCard>
            <checkKey>true</checkKey>
            <configurableTime>4</configurableTime>
            <costPerExtraKm>3.69</costPerExtraKm>
            <distanceThreshold>1000</distanceThreshold>
            <fuelLevel>100</fuelLevel>
            <fuelType>
               <key>main.fuel_type.petrol</key>
               <name>PETROL</name>
            </fuelType>
            <includedDistancePerConfigurableHour>2000</includedDistancePerConfigurableHour>
            <includedDistancePerDay>3000</includedDistancePerDay>
            <latitude>40.19831848</latitude>
            <licensePlate>11-MR-75</licensePlate>
            <longitude>-8.51279259</longitude>
            <maxCostPerConfigurableHour>2.46</maxCostPerConfigurableHour>
            <maxCostPerDay>3.69</maxCostPerDay>
            <maxCostPerHour>1.23</maxCostPerHour>
            <obsConnectionStatus>UNTESTED</obsConnectionStatus>
            <obsNumber>36606</obsNumber>
            <priceBookedPerMinute>2.46</priceBookedPerMinute>
            <priceReservedPerMinute>1.23</priceReservedPerMinute>
            <showDamageReport>true</showDamageReport>
            <simNumber>123456789</simNumber>
            <standalone>true</standalone>
            <state>AVAILABLE</state>
            <totalDistanceTravelled>41447000</totalDistanceTravelled>
         </return>
      </ns2:getFleetResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
{
  "getFleetResponse": {
    "return": [
      {
        "carBrandName": "Porsche",
        "carClubCode": "CTD",
        "carClubName": "Citydrive @ Testes",
        "carFareType": "STEP",
        "carModelName": "911",
        "carName": "Porsche 911",
        "carType": "NORMAL",
        "category": "Supermini",
        "categoryDescription": "main.car_class.supermini",
        "checkCard": "false",
        "checkKey": "true",
        "configurableTime": "4",
        "costPerExtraKm": "0.29",
        "distanceThreshold": "20000",
        "fuelLevel": "0",
        "fuelType": {
          "key": "main.fuel_type.petrol",
          "name": "PETROL"
        },
        "includedDistancePerConfigurableHour": "100000",
        "includedDistancePerDay": "200000",
        "latitude": "47.50297928",
        "licensePlate": "00-CB-00",
        "longitude": "8.23988533",
        "maxCostPerConfigurableHour": "29.90",
        "maxCostPerDay": "68.90",
        "maxCostPerHour": "9.90",
        "obsConnectionStatus": "OPERATIONAL",
        "obsNumber": "10101010",
        "priceBookedPerMinute": "0.29",
        "priceReservedPerMinute": "0.10",
        "showDamageReport": "true",
        "simNumber": "123456789",
        "standalone": "true",
        "state": "AVAILABLE",
        "totalDistanceTravelled": "5000"
      },
      {
        "carBrandName": "Volkswagen",
        "carClubCode": "CTD",
        "carClubName": "Citydrive @ Testes",
        "carFareType": "STEP",
        "carModelName": "Polo",
        "carName": "Volkswagen Polo",
        "carType": "NORMAL",
        "category": "Supermini",
        "categoryDescription": "main.car_class.supermini",
        "checkCard": "false",
        "checkKey": "true",
        "configurableTime": "4",
        "costPerExtraKm": "3.69",
        "distanceThreshold": "1000",
        "fuelLevel": "100",
        "fuelType": {
          "key": "main.fuel_type.petrol",
          "name": "PETROL"
        },
        "includedDistancePerConfigurableHour": "2000",
        "includedDistancePerDay": "3000",
        "latitude": "40.19831848",
        "licensePlate": "11-MR-75",
        "longitude": "-8.51279259",
        "maxCostPerConfigurableHour": "2.46",
        "maxCostPerDay": "3.69",
        "maxCostPerHour": "1.23",
        "obsConnectionStatus": "UNTESTED",
        "obsNumber": "36606",
        "priceBookedPerMinute": "2.46",
        "priceReservedPerMinute": "1.23",
        "showDamageReport": "true",
        "simNumber": "123456789",
        "standalone": "true",
        "state": "AVAILABLE",
        "totalDistanceTravelled": "41447000"
      }
    ]
  }
}
```

Name | Type | Description
--------- | ------- | -----------
carBrandName | String | The car's brand name.
carClubCode | String | The car's club code.
carClubName | String | The car's club name.
carFareType | Object | The car's fare type (Base or Step).
carModelName | String | The car's model name.
carName | String | The car's name.
carType | Object | The car's type (Normal or Schedule Booking).
category | String | The car's category.
categoryDescription | String | The car's category description.
checkCard | Boolean | If check card device is active.
checkKey | Boolean | If check key device is active.
configurableTime | Integer | The car's seconds configurable time.
costPerExtraKm | BigDecimal | The cost of an extra km.
distanceThreshold | BigDecimal | The car's limit distance.
fuelLevel | Integer | The car's fuel level.
fuelType | Object | The car's fuel type.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;key | String | The fuel's key code.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name | String | The fuel's name.
includedDistancePerConfigurableHour | Integer | The car's allowed distance to travel per hour.
includedDistancePerDay | Integer | The car's allowed distance to travel per day.
latitude | BigDecimal | The car's latitude.
licensePlate | String | The car's license plate.
longitude | BigDecimal | The car's longitude.
maxCostPerConfigurableHour | BigDecimal | The max cost per hour of the car (hour configurable).
maxCostPerDay | BigDecimal | The max cost per day of the car.
maxCostPerHour | BigDecimal | The max cost per hour of the car.
obsConnectionStatus | Object | The car's obs connection status.
obsNumber | String | The car's obs number.
priceBookedPerMinute | BigDecimal | The car's price booked per minute.
priceReservedPerMinute | BigDecimal | The car's price reserved per minute.
showDamageReport | Boolean | If damage report is to show.
simNumber | String | The car's sim number.
standalone | Boolean | If the car is in standlone mode.
state | String | The car's state.
totalDistanceTravelled | Integer | The car's total distance travelled.

# Book a Car

## Book a Car Immediate

This page contains the description of the process to create an Immediate Booking.
After the user find the car you have to check if:

* isCarAvailableForImmediateBooking
* isCustomerAuthorizedToBook

Then you can finally book the car with the service createImmediateBookingWithCustomerPin.
You can use these services with SOAP or REST.
But before all that you should check if the user is already on a trip. To do that you must use isCustomerInOngoingTrip.

![Find Cars Immediate Diagram](/images/BookACarImmediate.jpg)

## - isCustomerInOngoingTrip

```xml
<soapenv:Header>
   <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
         <wsse:UsernameToken>
            <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
            <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">Wxd4g3t79nCuHB3I+TnoxeCoNEs=</wsse:Password>
            <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ1NTk4NjI2MDQyNg==</wsse:Nonce>
            <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-02-20T16:37:40Z</wsu:Created>
         </wsse:UsernameToken>
   </wsse:Security>
</soapenv:Header>
```

```plaintext
GET /mobics-webservices/rs/booking/isCustomerInOngoingTrip HTTP/1.1
Host: imobics.mobiag.com
Username: ricardo.mendes@mobiag.com
Password: Wxd4g3t79nCuHB3I+TnoxeCoNEs=
Nonce: MTQ1NTk4NjI2MDQyNg==
Created: 2016-02-20T16:37:40Z
Content-Type: application/json
Cache-Control: no-cache
```

This service check if the user is already in a trip.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Booking?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/booking/isCustomerInOngoingTrip`

<aside class="warning">
This service requires authentication.
</aside>

### Input Parameters

This service has no input parameters.

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:isCustomerInOngoingTripResponse xmlns:ns2="http://mobics.criticalsoftware.com/booking" xmlns:ns3="http://www.criticalsoftware.com/mobios/services/accounting/dto">
         <return>true</return>
      </ns2:isCustomerInOngoingTripResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
{
  "isCustomerInOngoingTripResponse": {
    "return": "true"
  }
}
```

Name | Type | Description
--------- | ------- | -----------
isCustomerInOngoingTrip | Boolean | Check if the customer is already on trip.

## - isCarAvailableForImmediateBooking

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:book="http://mobics.criticalsoftware.com/booking">
   <soapenv:Header/>
   <soapenv:Body>
      <book:isCarAvailableForImmediateBooking>
         <!--Optional:-->
         <book:carLicensePlate>00-QE-37</book:carLicensePlate>
      </book:isCarAvailableForImmediateBooking>
   </soapenv:Body>
</soapenv:Envelope>
```

```plaintext
This service is not yet available in REST.
```

This service check if the car is available to a immediate booking.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Booking?wsdl`

<aside class="success">
This service does not requires authentication.
</aside>

### Input Parameters

Name | Type | Description | Mandatory
--------- | ------- | ----------- | --------
carLicensePlate | String | The car's license plate. | Yes

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:isCarAvailableForImmediateBookingResponse xmlns:ns2="http://mobics.criticalsoftware.com/booking" xmlns:ns3="http://www.criticalsoftware.com/mobios/services/accounting/dto">
         <return>true</return>
      </ns2:isCarAvailableForImmediateBookingResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
This service is not yet available in REST.
```

Name | Type | Description
--------- | ------- | -----------
isCarAvailableForImmediateBooking | Boolean | Check if the car is available to an immediate booking.

## - isCustomerAuthorizedToBook

```xml
<soapenv:Header>
   <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
         <wsse:UsernameToken>
            <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
            <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">Wxd4g3t79nCuHB3I+TnoxeCoNEs=</wsse:Password>
            <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ1NTk4NjI2MDQyNg==</wsse:Nonce>
            <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-02-20T16:37:40Z</wsu:Created>
         </wsse:UsernameToken>
   </wsse:Security>
</soapenv:Header>
```

```plaintext
This service is not yet available in REST.
```

This service check if the user is authorized to book.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Booking?wsdl`

<aside class="warning">
This service requires authentication.
</aside>

### Input Parameters

This service has no input parameters.

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:isCustomerAuthorizedToBookResponse xmlns:ns2="http://mobics.criticalsoftware.com/booking" xmlns:ns3="http://www.criticalsoftware.com/mobios/services/accounting/dto">
         <return>true</return>
      </ns2:isCustomerAuthorizedToBookResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
This service is not yet available in REST.
```

Name | Type | Description
--------- | ------- | -----------
isCustomerAuthorizedToBook | Boolean | Check if the user is authorized to book.

## - createImmediateBookingWithCustomerPin

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:book="http://mobics.criticalsoftware.com/booking">
   <soapenv:Header>
   <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
      <wsse:UsernameToken>
         <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
         <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">Wxd4g3t79nCuHB3I+TnoxeCoNEs=</wsse:Password>
         <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ1NTk4NjI2MDQyNg==</wsse:Nonce>
         <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-02-20T16:37:40Z</wsu:Created>
      </wsse:UsernameToken>
   </wsse:Security>
</soapenv:Header>
   <soapenv:Body>
      <book:createImmediateBookingWithCustomerPin>
         <!--Optional:-->
         <book:carLicensePlate>10-PU-10</book:carLicensePlate>
         <!--Optional:-->
         <book:customerPin>1234</book:customerPin>
      </book:createImmediateBookingWithCustomerPin>
   </soapenv:Body>
</soapenv:Envelope>
```

```plaintext
GET /mobics-webservices/rs/booking/createImmediateBookingWithCustomerPin HTTP/1.1
Host: imobics.mobiag.com
Username: ricardo.mendes@mobiag.com
Password: Wxd4g3t79nCuHB3I+TnoxeCoNEs=
Nonce: MTQ1NTk4NjI2MDQyNg==
Created: 2016-02-20T16:37:40Z
Content-Type: application/json
carLicensePlate: 10-PU-10
customerPin: 1234
Cache-Control: no-cache
```

This service creates an immediate booking to the user.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Booking?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/booking/createImmediateBookingWithCustomerPin`

<aside class="warning">
This service requires authentication.
</aside>

### Input Parameters

Name | Type | Description | Mandatory
--------- | ------- | ----------- | --------
carLicensePlate | String | The car's license plate. | Yes
customerPin | String | The user's pin. | Yes

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:createImmediateBookingWithCustomerPinResponse xmlns:ns2="http://mobics.criticalsoftware.com/booking">
         <return>
            <reservation>BCTD16040034</reservation>
            <startTime>27-04-2016 16:12</startTime>
         </return>
      </ns2:createImmediateBookingWithCustomerPinResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
{
  "createImmediateBookingWithCustomerPinResponse": {
    "return": {
      "reservation": "BCTD16040034",
      "startTime": "27-04-2016 16:12"
    }
  }
}
```

Name | Type | Description
--------- | ------- | -----------
reservation | String | The booking number.
startTime | String | The booking start date.

## Book a Car Advance

This page contains the description of the process to create an Advance Booking.
After the user find the car you have to check if:

* checkIfAdvanceBookingIsPermitted
* isCustomerAuthorizedToBook
* checkOverlappedBookingForCustomer

Then you can finally book the car with the service createAdvanceBookingWithCustomerPin.
You can use these services with SOAP or REST.
But before all that you should check if the user is already on a trip. To do that you must use isCustomerInOngoingTrip.

![Find Cars Immediate Diagram](/images/BookACarAdvance.jpg)

## - isCustomerInOngoingTrip

```xml
<soapenv:Header>
   <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
         <wsse:UsernameToken>
            <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
            <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">Wxd4g3t79nCuHB3I+TnoxeCoNEs=</wsse:Password>
            <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ1NTk4NjI2MDQyNg==</wsse:Nonce>
            <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-02-20T16:37:40Z</wsu:Created>
         </wsse:UsernameToken>
   </wsse:Security>
</soapenv:Header>
```

```plaintext
GET /mobics-webservices/rs/booking/isCustomerInOngoingTrip HTTP/1.1
Host: imobics.mobiag.com
Username: ricardo.mendes@mobiag.com
Password: Wxd4g3t79nCuHB3I+TnoxeCoNEs=
Nonce: MTQ1NTk4NjI2MDQyNg==
Created: 2016-02-20T16:37:40Z
Content-Type: application/json
Cache-Control: no-cache
```

This service check if the user is already in a trip.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Booking?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/booking/isCustomerInOngoingTrip`

<aside class="warning">
This service requires authentication.
</aside>

### Input Parameters

This service has no input parameters.

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:isCustomerInOngoingTripResponse xmlns:ns2="http://mobics.criticalsoftware.com/booking" xmlns:ns3="http://www.criticalsoftware.com/mobios/services/accounting/dto">
         <return>true</return>
      </ns2:isCustomerInOngoingTripResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
{
  "isCustomerInOngoingTripResponse": {
    "return": "true"
  }
}
```

Name | Type | Description
--------- | ------- | -----------
isCustomerInOngoingTrip | Boolean | Check if the customer is already on trip.

## - checkIfAdvanceBookingIsPermitted

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:book="http://mobics.criticalsoftware.com/booking">
   <soapenv:Header/>
   <soapenv:Body>
      <book:checkIfAdvanceBookingIsPermitted>
         <!--Optional:-->
         <book:licensePlate>00-QE-37</book:licensePlate>
         <!--Optional:-->
         <book:beginBooking>1461920400000</book:beginBooking>
         <!--Optional:-->
         <book:endBooking>1461924000000</book:endBooking>
      </book:checkIfAdvanceBookingIsPermitted>
   </soapenv:Body>
</soapenv:Envelope>
```

```plaintext
This service is not yet available in REST.
```

This service check if the car is available to an advance booking.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Booking?wsdl`

<aside class="success">
This service does not requires authentication.
</aside>

### Input Parameters

Name | Type | Description | Mandatory
--------- | ------- | ----------- | --------
carLicensePlate | String | The car's license plate. | Yes
beginBooking | Long | The booking's begin date of that user. | Yes
endBooking | Long | The booking's end date of that user. | Yes

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:checkIfAdvanceBookingIsPermittedResponse xmlns:ns2="http://mobics.criticalsoftware.com/booking" xmlns:ns3="http://www.criticalsoftware.com/mobios/services/accounting/dto">
         <return>true</return>
      </ns2:checkIfAdvanceBookingIsPermittedResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
This service is not yet available in REST.
```

Name | Type | Description
--------- | ------- | -----------
checkIfAdvanceBookingIsPermitted | Boolean | Check if the car is available to an advance booking.

## - isCustomerAuthorizedToBook

```xml
<soapenv:Header>
   <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
         <wsse:UsernameToken>
            <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
            <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">Wxd4g3t79nCuHB3I+TnoxeCoNEs=</wsse:Password>
            <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ1NTk4NjI2MDQyNg==</wsse:Nonce>
            <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-02-20T16:37:40Z</wsu:Created>
         </wsse:UsernameToken>
   </wsse:Security>
</soapenv:Header>
```

```plaintext
This service is not yet available in REST.
```

This service check if the user is authorized to book.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Booking?wsdl`

<aside class="warning">
This service requires authentication.
</aside>

### Input Parameters

This service has no input parameters.

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:isCustomerAuthorizedToBookResponse xmlns:ns2="http://mobics.criticalsoftware.com/booking" xmlns:ns3="http://www.criticalsoftware.com/mobios/services/accounting/dto">
         <return>true</return>
      </ns2:isCustomerAuthorizedToBookResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
This service is not yet available in REST.
```

Name | Type | Description
--------- | ------- | -----------
isCustomerAuthorizedToBook | Boolean | Check if the user is authorized to book.

## - checkOverlappedBookingForCustomer

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:book="http://mobics.criticalsoftware.com/booking">
   <soapenv:Header>
   <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
      <wsse:UsernameToken>
         <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
         <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">Wxd4g3t79nCuHB3I+TnoxeCoNEs=</wsse:Password>
         <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ1NTk4NjI2MDQyNg==</wsse:Nonce>
         <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-02-20T16:37:40Z</wsu:Created>
      </wsse:UsernameToken>
   </wsse:Security>
</soapenv:Header>
   <soapenv:Body>
      <book:checkOverlappedBookingForCustomer>
         <!--Optional:-->
         <book:beginBooking>1461920400000</book:beginBooking>
         <!--Optional:-->
         <book:endBooking>1461924000000</book:endBooking>
      </book:checkOverlappedBookingForCustomer>
   </soapenv:Body>
</soapenv:Envelope>
```

```plaintext
GET /mobics-webservices/rs/booking/checkOverlappedBookingForCustomer HTTP/1.1
Host: imobics.mobiag.com
Username: ricardo.mendes@mobiag.com
Password: Wxd4g3t79nCuHB3I+TnoxeCoNEs=
Nonce: MTQ1NTk4NjI2MDQyNg==
Created: 2016-02-20T16:37:40Z
Content-Type: application/json
beginBooking: 1461920400000
endBooking: 1461924000000
Cache-Control: no-cache
```

This service check if the user has already a booking for that period.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Booking?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/booking/checkOverlappedBookingForCustomer`

<aside class="warning">
This service requires authentication.
</aside>

### Input Parameters

Name | Type | Description | Mandatory
--------- | ------- | ----------- | --------
beginBooking | Long | The booking's begin date of that user. | Yes
endBooking | Long | The booking's end date of that user. | Yes

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:checkOverlappedBookingForCustomerResponse xmlns:ns2="http://mobics.criticalsoftware.com/booking" xmlns:ns3="http://www.criticalsoftware.com/mobios/services/accounting/dto">
         <return>false</return>
      </ns2:checkOverlappedBookingForCustomerResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
{
  "checkOverlappedBookingForCustomerResponse": {
    "return": "false"
  }
}
```

Name | Type | Description
--------- | ------- | -----------
checkOverlappedBookingForCustomer | Boolean | Check if the user has already a booking for that period.

## - createAdvanceBookingWithCustomerPin

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:book="http://mobics.criticalsoftware.com/booking">
   <soapenv:Header>
   <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
      <wsse:UsernameToken>
         <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
         <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">Wxd4g3t79nCuHB3I+TnoxeCoNEs=</wsse:Password>
         <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ1NTk4NjI2MDQyNg==</wsse:Nonce>
         <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-02-20T16:37:40Z</wsu:Created>
      </wsse:UsernameToken>
   </wsse:Security>
</soapenv:Header>
   <soapenv:Body>
      <book:createAdvanceBookingWithCustomerPin>
         <!--Optional:-->
         <book:carLicensePlate>10-PU-10</book:carLicensePlate>
         <!--Optional:-->
         <book:customerPin>1234</book:customerPin>
         <!--Optional:-->
         <book:beginBooking>1461920400000</book:beginBooking>
         <!--Optional:-->
         <book:endBooking>1461924000000</book:endBooking>
      </book:createAdvanceBookingWithCustomerPin>
   </soapenv:Body>
</soapenv:Envelope>
```

```plaintext
GET /mobics-webservices/rs/booking/createAdvanceBookingWithCustomerPin HTTP/1.1
Host: imobics.mobiag.com
Username: ricardo.mendes@mobiag.com
Password: Wxd4g3t79nCuHB3I+TnoxeCoNEs=
Nonce: MTQ1NTk4NjI2MDQyNg==
Created: 2016-02-20T16:37:40Z
Content-Type: application/json
beginBooking: 1461920400000
endBooking: 1461924000000
carLicensePlate: 10-PU-10
customerPin: 1234
Cache-Control: no-cache
```

This service creates an advance booking to the user.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Booking?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/booking/createAdvanceBookingWithCustomerPin`

<aside class="warning">
This service requires authentication.
</aside>

### Input Parameters

Name | Type | Description | Mandatory
--------- | ------- | ----------- | --------
carLicensePlate | String | The car's license plate. | Yes
customerPin | String | The user's pin. | Yes
beginBooking | Long | The booking's begin date of that user. | Yes
endBooking | Long | The booking's end date of that user. | Yes

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:createAdvanceBookingWithCustomerPinResponse xmlns:ns2="http://mobics.criticalsoftware.com/booking">
         <return>
            <bookingCode>BCTD16040035</bookingCode>
            <endTime>29-04-2016 11:00</endTime>
            <startTime>29-04-2016 10:00</startTime>
         </return>
      </ns2:createAdvanceBookingWithCustomerPinResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
{
  "createAdvanceBookingWithCustomerPinResponse": {
    "return": {
      "bookingCode": "BCTD16040035",
      "endTime": "29-04-2016 11:00",
      "startTime": "29-04-2016 10:00"
    }
  }
}
```

Name | Type | Description
--------- | ------- | -----------
bookingCode | String | The booking code.
endTime | String | The booking end date.
startTime | String | The booking start date.

# Manage a Booking

This page contains the description of the process to manage a Booking.
After finding the car and after the booking is done you can manage the booking using setBookingMessageAsDeleted, setBookingMessageAsRead, updateAdvanceBooking, extendAdvanceBooking, closeActiveBooking and cancelAdvanceBooking.

Also you can consult the booking current cancel cost (getBookingCurrentCancelCost), booking interest (getBookingInterest), booking messages (getBookingMessages), current trip details (getCurrentTripDetails), last trip details (getLastTripDetails), next advance booking (getNextAdvanceBooking), next booking (getNextBooking), next trip details (getNextTripDetails), trip details (getTripDetails) and trip history (getTripHistory). See Get Booking Information.

You can use these services with SOAP or REST.

## - setBookingMessageAsDeleted

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:book="http://mobics.criticalsoftware.com/booking">
   <soapenv:Header>
   <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
      <wsse:UsernameToken>
         <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
         <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">Wxd4g3t79nCuHB3I+TnoxeCoNEs=</wsse:Password>
         <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ1NTk4NjI2MDQyNg==</wsse:Nonce>
         <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-02-20T16:37:40Z</wsu:Created>
      </wsse:UsernameToken>
   </wsse:Security>
</soapenv:Header>
   <soapenv:Body>
      <book:setBookingMessageAsDeleted>
         <!--Optional:-->
         <book:bookingMessageCode>BCMBCA1601000002</book:bookingMessageCode>
      </book:setBookingMessageAsDeleted>
   </soapenv:Body>
</soapenv:Envelope>
```

```plaintext
GET /mobics-webservices/rs/booking/setBookingMessageAsDeleted HTTP/1.1
Host: imobics.mobiag.com
Username: ricardo.mendes@mobiag.com
Password: Wxd4g3t79nCuHB3I+TnoxeCoNEs=
Nonce: MTQ1NTk4NjI2MDQyNg==
Created: 2016-02-20T16:37:40Z
Content-Type: application/json
bookingMessageCode: BCMBCA1601000002
Cache-Control: no-cache
```

This service is used to set as deleted the booking messages.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Booking?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/booking/setBookingMessageAsDeleted`

<aside class="warning">
This service requires authentication.
</aside>

### Input Parameters

Name | Type | Description | Mandatory
--------- | ------- | ----------- | --------
bookingMessageCode | String | The booking message code. | Yes

### Output Parameters

This service has no output parameters.

## - setBookingMessageAsRead

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:book="http://mobics.criticalsoftware.com/booking">
   <soapenv:Header>
   <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
      <wsse:UsernameToken>
         <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
         <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">Wxd4g3t79nCuHB3I+TnoxeCoNEs=</wsse:Password>
         <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ1NTk4NjI2MDQyNg==</wsse:Nonce>
         <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-02-20T16:37:40Z</wsu:Created>
      </wsse:UsernameToken>
   </wsse:Security>
</soapenv:Header>
   <soapenv:Body>
      <book:setBookingMessageAsRead>
         <!--Optional:-->
         <book:bookingMessageCode>BCMBCA1601000002</book:bookingMessageCode>
      </book:setBookingMessageAsRead>
   </soapenv:Body>
</soapenv:Envelope>
```

```plaintext
GET /mobics-webservices/rs/booking/setBookingMessageAsRead HTTP/1.1
Host: imobics.mobiag.com
Username: ricardo.mendes@mobiag.com
Password: Wxd4g3t79nCuHB3I+TnoxeCoNEs=
Nonce: MTQ1NTk4NjI2MDQyNg==
Created: 2016-02-20T16:37:40Z
Content-Type: application/json
bookingMessageCode: BCMBCA1601000002
Cache-Control: no-cache
```

This service is used to set as read the booking messages.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Booking?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/booking/setBookingMessageAsRead`

<aside class="warning">
This service requires authentication.
</aside>

### Input Parameters

Name | Type | Description | Mandatory
--------- | ------- | ----------- | --------
bookingMessageCode | String | The booking message code. | Yes

### Output Parameters

This service has no output parameters.

## - updateAdvanceBooking

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:book="http://mobics.criticalsoftware.com/booking">
   <soapenv:Header>
   <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
      <wsse:UsernameToken>
         <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
         <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">Wxd4g3t79nCuHB3I+TnoxeCoNEs=</wsse:Password>
         <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ1NTk4NjI2MDQyNg==</wsse:Nonce>
         <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-02-20T16:37:40Z</wsu:Created>
      </wsse:UsernameToken>
   </wsse:Security>
</soapenv:Header>
   <soapenv:Body>
      <book:updateAdvanceBooking>
         <!--Optional:-->
         <book:bookingCode>BCTD16040038</book:bookingCode>
         <!--Optional:-->
         <book:updatedDate>1461924000000</book:updatedDate>
      </book:updateAdvanceBooking>
   </soapenv:Body>
</soapenv:Envelope>
```

```plaintext
GET /mobics-webservices/rs/booking/updateAdvanceBooking HTTP/1.1
Host: imobics.mobiag.com
Username: ricardo.mendes@mobiag.com
Password: Wxd4g3t79nCuHB3I+TnoxeCoNEs=
Nonce: MTQ1NTk4NjI2MDQyNg==
Created: 2016-02-20T16:37:40Z
Content-Type: application/json
bookingCode: BCTD16040038
updatedDate: 1461924000000
Cache-Control: no-cache
```

This service is used to update the advance booking.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Booking?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/booking/updateAdvanceBooking`

<aside class="warning">
This service requires authentication.
</aside>

### Input Parameters

Name | Type | Description | Mandatory
--------- | ------- | ----------- | --------
bookingCode | String | The booking code. | Yes
updatedDate | Long | The new date. | Yes

### Output Parameters

This service has no output parameters.

## - extendAdvanceBooking

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:book="http://mobics.criticalsoftware.com/booking">
   <soapenv:Header>
   <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
      <wsse:UsernameToken>
         <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
         <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">Wxd4g3t79nCuHB3I+TnoxeCoNEs=</wsse:Password>
         <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ1NTk4NjI2MDQyNg==</wsse:Nonce>
         <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-02-20T16:37:40Z</wsu:Created>
      </wsse:UsernameToken>
   </wsse:Security>
</soapenv:Header>
   <soapenv:Body>
      <book:extendAdvanceBooking>
         <!--Optional:-->
         <book:bookingCode>BCTD16040038</book:bookingCode>
         <!--Optional:-->
         <book:extendedDate>1461924000000</book:extendedDate>
      </book:extendAdvanceBooking>
   </soapenv:Body>
</soapenv:Envelope>
```

```plaintext
GET /mobics-webservices/rs/booking/extendAdvanceBooking HTTP/1.1
Host: imobics.mobiag.com
Username: ricardo.mendes@mobiag.com
Password: Wxd4g3t79nCuHB3I+TnoxeCoNEs=
Nonce: MTQ1NTk4NjI2MDQyNg==
Created: 2016-02-20T16:37:40Z
Content-Type: application/json
bookingCode: BCTD16040038
extendedDate: 1461924000000
Cache-Control: no-cache
```

This service is used to extend the advance booking.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Booking?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/booking/extendAdvanceBooking`

<aside class="warning">
This service requires authentication.
</aside>

### Input Parameters

Name | Type | Description | Mandatory
--------- | ------- | ----------- | --------
bookingCode | String | The booking code. | Yes
extendedDate | Long | The new end date. | Yes

### Output Parameters

This service has no output parameters.

## - closeActiveBooking

```xml
<soapenv:Header>
   <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
         <wsse:UsernameToken>
            <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
            <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">Wxd4g3t79nCuHB3I+TnoxeCoNEs=</wsse:Password>
            <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ1NTk4NjI2MDQyNg==</wsse:Nonce>
            <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-02-20T16:37:40Z</wsu:Created>
         </wsse:UsernameToken>
   </wsse:Security>
</soapenv:Header>
```

```plaintext
GET /mobics-webservices/rs/booking/closeActiveBooking HTTP/1.1
Host: imobics.mobiag.com
Username: ricardo.mendes@mobiag.com
Password: Wxd4g3t79nCuHB3I+TnoxeCoNEs=
Nonce: MTQ1NTk4NjI2MDQyNg==
Created: 2016-02-20T16:37:40Z
Content-Type: application/json
Cache-Control: no-cache
```

This service is used to close the active booking.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Booking?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/booking/closeActiveBooking`

<aside class="warning">
This service requires authentication.
</aside>

### Input Parameters

This service has no input parameters.

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:closeActiveBookingResponse xmlns:ns2="http://mobics.criticalsoftware.com/booking">
         <return>
            <bookingCost>0</bookingCost>
            <bookingCostWithTax>0.00</bookingCostWithTax>
            <bookingDuration>3598</bookingDuration>
            <bookingTaxCode>IVA23</bookingTaxCode>
            <costCalculationSuccess>true</costCalculationSuccess>
            <zoneCategory>PARKING</zoneCategory>
         </return>
      </ns2:closeActiveBookingResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
{
  "closeActiveBookingResponse": {
    "return": {
      "bookingCost": "0",
      "bookingCostWithTax": "0.00",
      "bookingDuration": "3598",
      "bookingTaxCode": "IVA23",
      "costCalculationSuccess": "true",
      "zoneCategory": "PARKING"
    }
  }
}
```

Name | Type | Description
--------- | ------- | -----------
bookingCost | BigDecimal | The booking cost.
bookingCostWithTax | BigDecimal | The booking cost with tax.
bookingDuration | Long | The booking duration.
bookingTaxCode | String | The booking tax code.
costCalculationSuccess | Boolean | If the cost calculation return sucess.
zoneCategory | Object | The zone category where the booking was closed (NORMAL, SPECIAL, UNWANTED, PARKING, FORBIDDEN).

## - cancelAdvanceBooking

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:book="http://mobics.criticalsoftware.com/booking">
   <soapenv:Header>
   <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
      <wsse:UsernameToken>
         <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
         <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">Wxd4g3t79nCuHB3I+TnoxeCoNEs=</wsse:Password>
         <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ1NTk4NjI2MDQyNg==</wsse:Nonce>
         <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-02-20T16:37:40Z</wsu:Created>
      </wsse:UsernameToken>
   </wsse:Security>
</soapenv:Header>
   <soapenv:Body>
      <book:cancelAdvanceBooking>
         <!--Optional:-->
         <book:bookingCode>BCTD16040040</book:bookingCode>
      </book:cancelAdvanceBooking>
   </soapenv:Body>
</soapenv:Envelope>
```

```plaintext
GET /mobics-webservices/rs/booking/cancelAdvanceBooking HTTP/1.1
Host: imobics.mobiag.com
Username: ricardo.mendes@mobiag.com
Password: Wxd4g3t79nCuHB3I+TnoxeCoNEs=
Nonce: MTQ1NTk4NjI2MDQyNg==
Created: 2016-02-20T16:37:40Z
Content-Type: application/json
bookingCode: BCTD16040040
Cache-Control: no-cache
```

This service is used to cancel the advance booking.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Booking?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/booking/cancelAdvanceBooking`

<aside class="warning">
This service requires authentication.
</aside>

### Input Parameters

Name | Type | Description | Mandatory
--------- | ------- | ----------- | --------
bookingCode | String | The booking code. | Yes

### Output Parameters

This service has no output parameters.

# Booking Flow

This page contains the description of the Booking Flow.
The Booking has many states and here you can understand the flow between the states and how to change it with WebServices requests.
And too understand better the booking flow you should understand the car flow too.

### Booking States

Name | Description
--------- | -----------
BLANK | Initial state of book before add car and zones characteristics.
OBS_WAITING | Communication with OBS provider for a immediate booking.
OBS_WAITING_ADVANCE | Communication with OBS provider for a advance book.
BOOKED | Booking is book with a start time and end time.
IN_USE | When start time arrives booking will change automatecally to IN_USE. If booking is immediate, once receive confirmation from OBS provider booking will be IN_USE.
ON_TRIP | When booking is active and car has the status ENGINE_WORKING.
CLOSED | This status means booking is closed and with a correct calculation.
UNDER_REVIEW | This means that booking is closed but will need operational review.
INVOICED | This state means that booking is already invoiced to user.
OBS_ERROR | This state is related with a wrong comunicattion with OBS provider and booking could not be confirm.
CANCELED | This state means that booking was canceled because the system couldn´t activate trip. This could be related with a previous ongoing trip.

### Booking Flow Diagram

![Find Cars Immediate Diagram](/images/BookingFlow.jpg)

### Car States

Name | Description
--------- | -----------
INCOMPLETE | This state indicates that a vehicle was created but it not yet have all the necessary information to be commercially available.
UNAVAILABLE | This state means the vehicle is not available.
AVAILABLE | This state means the vehicle is available.
BOOKED | This state means the vehicle is booked.
IN_USE | This state means the car was booked and the user has opened the doors already.
READY | The vehicle is ready when the imobilizer is off after the damage report.
ENGINE_RUNNING | This state means the vehicle has the engine running.
DEACTIVATED | In addition to not available it is disabled too and there is no communication with the vehicle's device.

### Car Flow Diagram

![Find Cars Immediate Diagram](/images/CarFlow.jpg)

# Get Booking Information

This page contains the description of the services available to get all kind of booking information.

## - getBookingCurrentCancelCost

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:book="http://mobics.criticalsoftware.com/booking">
   <soapenv:Header>
   <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
      <wsse:UsernameToken>
         <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
         <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">Wxd4g3t79nCuHB3I+TnoxeCoNEs=</wsse:Password>
         <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ1NTk4NjI2MDQyNg==</wsse:Nonce>
         <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-02-20T16:37:40Z</wsu:Created>
      </wsse:UsernameToken>
   </wsse:Security>
</soapenv:Header>
   <soapenv:Body>
      <book:getBookingCurrentCancelCost>
         <!--Optional:-->
         <book:bookingNumber>BCTD16041074</book:bookingNumber>
      </book:getBookingCurrentCancelCost>
   </soapenv:Body>
</soapenv:Envelope>
```

```plaintext
GET /mobics-webservices/rs/booking/getBookingCurrentCancelCost HTTP/1.1
Host: imobics.mobiag.com
Username: ricardo.mendes@mobiag.com
Password: Wxd4g3t79nCuHB3I+TnoxeCoNEs=
Nonce: MTQ1NTk4NjI2MDQyNg==
Created: 2016-02-20T16:37:40Z
Content-Type: application/json
bookingNumber: BCTD16041074
Cache-Control: no-cache
```

This service is used to get the booking current cancel cost.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Booking?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/booking/getBookingCurrentCancelCost`

<aside class="warning">
This service requires authentication.
</aside>

### Input Parameters

Name | Type | Description | Mandatory
--------- | ------- | ----------- | --------
bookingNumber | String | The booking number. | Yes

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:getBookingCurrentCancelCostResponse xmlns:ns2="http://mobics.criticalsoftware.com/booking" xmlns:ns3="http://www.criticalsoftware.com/mobios/services/accounting/dto">
         <return>10.00</return>
      </ns2:getBookingCurrentCancelCostResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
{
  "getBookingCurrentCancelCostResponse": {
    "return": "10.00"
  }
}
```

Name | Type | Description
--------- | ------- | -----------
bookingCurrentCancelCost | BigDecimal | The booking current cost.

## - getBookingInterest

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:book="http://mobics.criticalsoftware.com/booking">
   <soapenv:Header>
   <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
      <wsse:UsernameToken>
         <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
         <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">Wxd4g3t79nCuHB3I+TnoxeCoNEs=</wsse:Password>
         <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ1NTk4NjI2MDQyNg==</wsse:Nonce>
         <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-02-20T16:37:40Z</wsu:Created>
      </wsse:UsernameToken>
   </wsse:Security>
</soapenv:Header>
   <soapenv:Body>
      <book:getBookingInterest>
         <!--Optional:-->
         <book:bookingInterestCode>BCTD16041074</book:bookingInterestCode>
      </book:getBookingInterest>
   </soapenv:Body>
</soapenv:Envelope>
```

```plaintext
GET /mobics-webservices/rs/booking/getBookingInterest HTTP/1.1
Host: imobics.mobiag.com
Username: ricardo.mendes@mobiag.com
Password: Wxd4g3t79nCuHB3I+TnoxeCoNEs=
Nonce: MTQ1NTk4NjI2MDQyNg==
Created: 2016-02-20T16:37:40Z
Content-Type: application/json
bookingInterestCode: BCTD16041074
Cache-Control: no-cache
```

This service is used to get the booking interest of the user.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Booking?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/booking/getBookingInterest`

<aside class="warning">
This service requires authentication.
</aside>

### Input Parameters

Name | Type | Description | Mandatory
--------- | ------- | ----------- | --------
bookingNumber | String | The booking number. | Yes

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:getBookingInterestResponse xmlns:ns2="http://mobics.criticalsoftware.com/booking" xmlns:ns3="http://www.criticalsoftware.com/mobios/services/accounting/dto">
         <return>
            <carClubCarsOnly>false</carClubCarsOnly>
            <code>BICCTD1604000042</code>
            <creationDate>2016-04-27T22:37:40.310Z</creationDate>
            <isDeleteable>true</isDeleteable>
            <isEditable>true</isEditable>
            <location>
               <latitude>38.71113500</latitude>
               <longitude>-9.22600400</longitude>
            </location>
            <notificationStartTime>-900</notificationStartTime>
            <notificationStopTime>0</notificationStopTime>
            <numOfNotifications>2</numOfNotifications>
            <pickupDate>2016-04-28T21:45:00Z</pickupDate>
            <radius>50000</radius>
         </return>
      </ns2:getBookingInterestResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
{
  "getBookingInterestResponse": {
    "return": {
      "carClubCarsOnly": "false",
      "code": "BICCTD1604000042",
      "creationDate": "2016-04-27T22:37:40.310Z",
      "isDeleteable": "true",
      "isEditable": "true",
      "location": {
        "latitude": "38.71113500",
        "longitude": "-9.22600400"
      },
      "notificationStartTime": "-900",
      "notificationStopTime": "0",
      "numOfNotifications": "2",
      "pickupDate": "2016-04-28T21:45:00Z",
      "radius": "50000"
    }
  }
}
```

Name | Type | Description
--------- | ------- | -----------
carClubCarsOnly | Boolean | The option to choose cars from the car club only.
code | String | The notification code.
creationDate | Date | The creation date.
isDeleteable | Boolean | If the booking interest configuration is deleteable.
location | Object | The location to search for cars.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;latitude | BigDecimal | The latitude of the location.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;longitude | BigDecimal | The longitude of the location.
notificationStartTime | Integer | The time to start sending notifications before the pickup date - seconds.
notificationStopTime | Integer | The time to stop sending notifications before the pickup date - seconds.
numOfNotifications | Integer | The number of notifications to be sent.
pickupDate | Date | The pickup date.
radius | Integer | The radius - in meters.

## - getBookingMessages

```xml
<soapenv:Header>
   <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
         <wsse:UsernameToken>
            <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
            <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">Wxd4g3t79nCuHB3I+TnoxeCoNEs=</wsse:Password>
            <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ1NTk4NjI2MDQyNg==</wsse:Nonce>
            <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-02-20T16:37:40Z</wsu:Created>
         </wsse:UsernameToken>
   </wsse:Security>
</soapenv:Header>
```

```plaintext
GET /mobics-webservices/rs/booking/getBookingMessages HTTP/1.1
Host: imobics.mobiag.com
Username: ricardo.mendes@mobiag.com
Password: Wxd4g3t79nCuHB3I+TnoxeCoNEs=
Nonce: MTQ1NTk4NjI2MDQyNg==
Created: 2016-02-20T16:37:40Z
Content-Type: application/json
Cache-Control: no-cache
```

This service is used to get the booking messages of the user.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Booking?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/booking/getBookingMessages`

<aside class="warning">
This service requires authentication.
</aside>


### Input Parameters

This service has no input parameters.

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:getBookingMessagesResponse xmlns:ns2="http://mobics.criticalsoftware.com/booking" xmlns:ns3="http://www.criticalsoftware.com/mobios/services/accounting/dto">
         <return>
            <carDistance>961</carDistance>
            <carName>Adam Opel</carName>
            <carPlate>11-OS-03</carPlate>
            <carTaxCode>PT</carTaxCode>
            <code>BCMCTD1507000836</code>
            <distanceThreshold>20000</distanceThreshold>
            <fuelType>
               <key>main.fuel_type.petrol</key>
               <name>PETROL</name>
            </fuelType>
            <isRead>true</isRead>
            <pricePerMinute>0.24</pricePerMinute>
            <subject>user.car_available</subject>
            <timestamp>2015-07-29T18:20:00.552Z</timestamp>
         </return>
    </ns2:getBookingMessagesResponse>
  </soap:Body>
</soap:Envelope>
```

```plaintext
{
  "getBookingMessagesResponse": {
    "return": {
      "carDistance": "961",
      "carName": "Adam Opel",
      "carPlate": "11-OS-03",
      "carTaxCode": "PT",
      "code": "BCMCTD1507000836",
      "distanceThreshold": "20000",
      "fuelType": {
        "key": "main.fuel_type.petrol",
        "name": "PETROL"
      },
      "isRead": "true",
      "pricePerMinute": "0.24",
      "subject": "user.car_available",
      "timestamp": "2015-07-29T18:20:00.552Z"
    }
  }
}
```

Name | Type | Description
--------- | ------- | -----------
carDistance | Integer | The distance of the car.
carName | String | The car's name.
carPlate | String | The car's license plate.
carTaxCode | String | The car's tax code.
code | String | The code.
distanceThreshold | Integer | The car's limit distance.
fuelType | Object | The car's fuel type.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;key | String | The fuel's key code.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name | String | The fuel's name.
subject | String | The subject.
timestamp | Date | The timestamp.

## - getCurrentTripDetails

```xml
<soapenv:Header>
   <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
         <wsse:UsernameToken>
            <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
            <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">Wxd4g3t79nCuHB3I+TnoxeCoNEs=</wsse:Password>
            <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ1NTk4NjI2MDQyNg==</wsse:Nonce>
            <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-02-20T16:37:40Z</wsu:Created>
         </wsse:UsernameToken>
   </wsse:Security>
</soapenv:Header>
```

```plaintext
GET /mobics-webservices/rs/booking/getCurrentTripDetails HTTP/1.1
Host: imobics.mobiag.com
Username: ricardo.mendes@mobiag.com
Password: Wxd4g3t79nCuHB3I+TnoxeCoNEs=
Nonce: MTQ1NTk4NjI2MDQyNg==
Created: 2016-02-20T16:37:40Z
Content-Type: application/json
Cache-Control: no-cache
```

This service is used to get the current trip details of the user.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Booking?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/booking/getCurrentTripDetails`

<aside class="warning">
This service requires authentication.
</aside>

### Input Parameters

This service has no input parameters.

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:getCurrentTripDetailsResponse xmlns:ns2="http://mobics.criticalsoftware.com/booking" xmlns:ns3="http://www.criticalsoftware.com/mobios/services/accounting/dto">
         <return>
            <additionalServiceTaxCode>IVA23</additionalServiceTaxCode>
            <bookingCode>BCTD16040796</bookingCode>
            <bookingDuration>614101</bookingDuration>
            <bookingTaxCode>IVA23</bookingTaxCode>
            <bookingType>IMMEDIATE</bookingType>
            <cancelCost>10.00</cancelCost>
            <cancelTime>0</cancelTime>
            <carBrand>Skoda</carBrand>
            <carDTO>
               <carBrandName>Skoda</carBrandName>
               <carClubCode>NXT</carClubCode>
               <carClubName>Nextmotion</carClubName>
               <carFareType>STEP</carFareType>
               <carModelName>Fabia</carModelName>
               <carName>Skoda Fabia</carName>
               <carType>NORMAL</carType>
               <category>Small family car</category>
               <categoryDescription>main.car_class.small_familt_car</categoryDescription>
               <checkCard>false</checkCard>
               <checkKey>true</checkKey>
               <configurableTime>6</configurableTime>
               <costPerExtraKm>0.29</costPerExtraKm>
               <deviceDriverClass>com.criticalsoftware.mobics.driver.inosat.InoSatDriverProvider</deviceDriverClass>
               <distanceThreshold>20000</distanceThreshold>
               <fuelLevel>9</fuelLevel>
               <fuelType>
                  <key>main.fuel_type.diesel</key>
                  <name>DIESEL</name>
               </fuelType>
               <includedDistancePerConfigurableHour>100000</includedDistancePerConfigurableHour>
               <includedDistancePerDay>200000</includedDistancePerDay>
               <latitude>38.77875900</latitude>
               <licensePlate>56-QC-63</licensePlate>
               <longitude>-9.16385651</longitude>
               <maxCostPerConfigurableHour>29.90</maxCostPerConfigurableHour>
               <maxCostPerDay>69.90</maxCostPerDay>
               <maxCostPerHour>9.90</maxCostPerHour>
               <obsConnectionStatus>OPERATIONAL</obsConnectionStatus>
               <obsNumber>45722</obsNumber>
               <priceBookedPerMinute>0.29</priceBookedPerMinute>
               <priceReservedPerMinute>0.10</priceReservedPerMinute>
               <showDamageReport>true</showDamageReport>
               <simNumber>123456789</simNumber>
               <standalone>false</standalone>
               <state>READY</state>
               <totalDistanceTravelled>8566000</totalDistanceTravelled>
               <zones>
                  <category>NORMAL</category>
                  <code>ZNXT000024</code>
                  <location>Lisboa</location>
                  <parentZone>Grande Lisboa</parentZone>
                  <zone>Estacionamento - Parque das Nações</zone>
               </zones>
               <zones>
                  <category>NORMAL</category>
                  <code>ZNXT000023</code>
                  <location>Lisboa</location>
                  <parentZone>Grande Lisboa</parentZone>
                  <zone>Estacionamento - Centro</zone>
               </zones>
            </carDTO>
            <carModel>Fabia</carModel>
            <carState>READY</carState>
            <carTaxCode>IVA23</carTaxCode>
            <currentCost>308.4549</currentCost>
            <currentCostWithTax>379.39</currentCostWithTax>
            <currentDistance>48000</currentDistance>
            <currentZoneType>UNWANTED</currentZoneType>
            <extendCost>10.00</extendCost>
            <latitude>38.77875900</latitude>
            <licensePlate>56-QC-63</licensePlate>
            <longitude>-9.16385651</longitude>
            <neverStarted>false</neverStarted>
            <roamingCost>0.0000</roamingCost>
            <roamingCostWithTax>0.00</roamingCostWithTax>
            <showDamageReport>true</showDamageReport>
            <startDate>2016-04-21T07:52:59.149Z</startDate>
            <state>IN_USE</state>
            <timeBooked>467727</timeBooked>
            <timeInUse>7708</timeInUse>
            <undesirableZoneCost>10.00</undesirableZoneCost>
            <undesirableZoneCostTaxCode>IVA23</undesirableZoneCostTaxCode>
         </return>
      </ns2:getCurrentTripDetailsResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
{
  "getCurrentTripDetailsResponse": {
    "return": {
      "additionalServiceTaxCode": "IVA23",
      "bookingCode": "BCTD16040796",
      "bookingDuration": "614101",
      "bookingTaxCode": "IVA23",
      "bookingType": "IMMEDIATE",
      "cancelCost": "10.00",
      "cancelTime": "0",
      "carBrand": "Skoda",
      "carDTO": {
        "carBrandName": "Skoda",
        "carClubCode": "NXT",
        "carClubName": "Nextmotion",
        "carFareType": "STEP",
        "carModelName": "Fabia",
        "carName": "Skoda Fabia",
        "carType": "NORMAL",
        "category": "Small family car",
        "categoryDescription": "main.car_class.small_familt_car",
        "checkCard": "false",
        "checkKey": "true",
        "configurableTime": "6",
        "costPerExtraKm": "0.29",
        "deviceDriverClass": "com.criticalsoftware.mobics.driver.inosat.InoSatDriverProvider",
        "distanceThreshold": "20000",
        "fuelLevel": "9",
        "fuelType": {
          "key": "main.fuel_type.diesel",
          "name": "DIESEL"
        },
        "includedDistancePerConfigurableHour": "100000",
        "includedDistancePerDay": "200000",
        "latitude": "38.77875900",
        "licensePlate": "56-QC-63",
        "longitude": "-9.16385651",
        "maxCostPerConfigurableHour": "29.90",
        "maxCostPerDay": "69.90",
        "maxCostPerHour": "9.90",
        "obsConnectionStatus": "OPERATIONAL",
        "obsNumber": "45722",
        "priceBookedPerMinute": "0.29",
        "priceReservedPerMinute": "0.10",
        "showDamageReport": "true",
        "simNumber": "123456789",
        "standalone": "false",
        "state": "READY",
        "totalDistanceTravelled": "8566000",
        "zones": [
          {
            "category": "NORMAL",
            "code": "ZNXT000024",
            "location": "Lisboa",
            "parentZone": "Grande Lisboa",
            "zone": "Estacionamento - Parque das Nações"
          },
          {
            "category": "NORMAL",
            "code": "ZNXT000023",
            "location": "Lisboa",
            "parentZone": "Grande Lisboa",
            "zone": "Estacionamento - Centro"
          }
        ]
      },
      "carModel": "Fabia",
      "carState": "READY",
      "carTaxCode": "IVA23",
      "currentCost": "308.4549",
      "currentCostWithTax": "379.39",
      "currentDistance": "48000",
      "currentZoneType": "UNWANTED",
      "extendCost": "10.00",
      "latitude": "38.77875900",
      "licensePlate": "56-QC-63",
      "longitude": "-9.16385651",
      "neverStarted": "false",
      "roamingCost": "0.0000",
      "roamingCostWithTax": "0.00",
      "showDamageReport": "true",
      "startDate": "2016-04-21T07:52:59.149Z",
      "state": "IN_USE",
      "timeBooked": "467727",
      "timeInUse": "7708",
      "undesirableZoneCost": "10.00",
      "undesirableZoneCostTaxCode": "IVA23"
    }
  }
}
```

Name | Type | Description
--------- | ------- | -----------
additionalServiceTaxCode | String | The trips's additional service tax code.
bookingCode | String | The booking code.
bookingDuration | Integer | The booking duration time.
bookingTaxCode | String | The booking tax code.
bookingType | Object | The booking type.
cancelCost | BigDecimal | The booking cancel cost.
cancelTime | Integer | The booking cancel time.
carBrand | String | The car's brand.
carDTO | Object | The car.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;carBrandName | String | The car's brand name.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;carClubCode | String | The car's car club code.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;carClubName | String | The car's car club name.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;carFareType | Object | The car's fare type.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;carModelName | String | The car's model name.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;carName | String | The car's name.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;carType | Object | The car's type.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;category | String | The car's category.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;categoryDescription | String | The car's category description. 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;checkCard | Boolean | If check card device is active.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;checkKey | Boolean | If check key device is active.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;configurableTime | Integer | The car's seconds configurable time.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;costPerExtraKm | BigDecimal | The cost of an extra km.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;deviceDriverClass | String | The car's device driver class.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;distanceThreshold | BigDecimal | The car's limit distance.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;fuelLevel | Integer | The car's fuel level.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;fuelType | Object | The car's fuel type.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;key | String | The fuel's key code.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name | String | The fuel's name.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;includedDistancePerConfigurableHour | Integer | The car's allowed distance to travel per hour.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;includedDistancePerDay | Integer | The car's allowed distance to travel per day.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;latitude | BigDecimal | The car's latitude.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;licensePlate | String | The car's license plate.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;longitude | BigDecimal | The car's longitude.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;maxCostPerConfigurableHour | BigDecimal | The max cost per hour of the car (hour configurable).
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;maxCostPerDay | BigDecimal | The max cost per day of the car.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;maxCostPerHour | BigDecimal | The max cost per hour of the car.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;obsConnectionStatus | Object | The car's obs connection status.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;obsNumber | String | The car's obs number.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;priceBookedPerMinute | BigDecimal | The car's price booked per minute.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;priceReservedPerMinute | BigDecimal | The car's price reserved per minute.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;showDamageReport | Boolean | If damage report is to show.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;simNumber | String | The car's sim number.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;standalone | Boolean | If the car is in standlone mode.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;state | String | The car's state.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;totalDistanceTravelled | Integer | The car's total distance travelled.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;zones | Object | The car's zones 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;category | Object | The zone's category (NORMAL, SPECIAL, UNWANTED, PARKING, FORBIDDEN).
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;code | String | The zone's code.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;location | String | The location.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;parentZone | String | The parent location.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;zone | String | The zone.
carModel | String | The car's model.
carState | String | The car's state.
carTaxCode | String | The car's tax code.
currentCost | BigDecimal | The current cost.
currentCostWithTax | BigDecimal | The current cost with tax.
currentDistance | Integer | The cuurent distance traveled.
currentZoneType | String | The current zone type.
extendCost | BigDecimal | The extend cost.
latitude | BigDecimal | The car's latitude.
licensePlate | String | The car's license plate.
longitude | BigDecimal | The car's longitude.
neverStarted | Boolean | If the trip never started.
roamingCost | BigDecimal | The car's roaming cost.
roamingCostWithTax | BigDecimal | The car's roaming cost with tax.
showDamageReport | Boolean | If damage report is to show.
startDate | Date | The booking start date.
state | String | The booking state.
timeBooked | Integer | The time that the car was booked.
timeInUse | Integer | The time that the car was in use.
undesirableZoneCost | BigDecimal | The cost of parking in an undesirable zone.
undesirableZoneCostTaxCode | String | The cost tax code of parking in an undesirable zone.

## - getLastTripDetails

```xml
<soapenv:Header>
   <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
         <wsse:UsernameToken>
            <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
            <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">Wxd4g3t79nCuHB3I+TnoxeCoNEs=</wsse:Password>
            <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ1NTk4NjI2MDQyNg==</wsse:Nonce>
            <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-02-20T16:37:40Z</wsu:Created>
         </wsse:UsernameToken>
   </wsse:Security>
</soapenv:Header>
```

```plaintext
GET /mobics-webservices/rs/booking/getLastTripDetails HTTP/1.1
Host: imobics.mobiag.com
Username: ricardo.mendes@mobiag.com
Password: Wxd4g3t79nCuHB3I+TnoxeCoNEs=
Nonce: MTQ1NTk4NjI2MDQyNg==
Created: 2016-02-20T16:37:40Z
Content-Type: application/json
Cache-Control: no-cache
```

This service is used to get the last trip details of the user.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Booking?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/booking/getLastTripDetails`

<aside class="warning">
This service requires authentication.
</aside>

### Input Parameters

This service has no input parameters.

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:getLastTripDetailsResponse xmlns:ns2="http://mobics.criticalsoftware.com/booking" xmlns:ns3="http://www.criticalsoftware.com/mobios/services/accounting/dto">
         <return>
            <addOnDiscountGeneratedWithTax>0.0000</addOnDiscountGeneratedWithTax>
            <bookingNumber>BCTD16040795</bookingNumber>
            <bookingTaxCode>IVA23</bookingTaxCode>
            <bookingType>IMMEDIATE</bookingType>
            <canOpenCar>false</canOpenCar>
            <car>
               <carBrandName>Opel</carBrandName>
               <carClubCode>NXT</carClubCode>
               <carClubName>Nextmotion</carClubName>
               <carFareType>STEP</carFareType>
               <carModelName>Adam</carModelName>
               <carName>Opel Adam</carName>
               <carType>NORMAL</carType>
               <category>Supermini</category>
               <categoryDescription>main.car_class.supermini</categoryDescription>
               <checkCard>false</checkCard>
               <checkKey>true</checkKey>
               <configurableTime>6</configurableTime>
               <costPerExtraKm>0.29</costPerExtraKm>
               <deviceDriverClass>com.criticalsoftware.mobics.driver.convadis.ConvadisEDriverProvider</deviceDriverClass>
               <distanceThreshold>20000</distanceThreshold>
               <fuelLevel>11</fuelLevel>
               <fuelType>
                  <key>main.fuel_type.petrol</key>
                  <name>PETROL</name>
               </fuelType>
               <includedDistancePerConfigurableHour>100000</includedDistancePerConfigurableHour>
               <includedDistancePerDay>200000</includedDistancePerDay>
               <latitude>38.78128433</latitude>
               <licensePlate>48-OS-13</licensePlate>
               <longitude>-9.11329269</longitude>
               <maxCostPerConfigurableHour>29.90</maxCostPerConfigurableHour>
               <maxCostPerDay>69.90</maxCostPerDay>
               <maxCostPerHour>9.90</maxCostPerHour>
               <obsConnectionStatus>OPERATIONAL</obsConnectionStatus>
               <obsNumber>48151913</obsNumber>
               <priceBookedPerMinute>0.29</priceBookedPerMinute>
               <priceReservedPerMinute>0.10</priceReservedPerMinute>
               <showDamageReport>true</showDamageReport>
               <simNumber>937929718</simNumber>
               <standalone>false</standalone>
               <state>AVAILABLE</state>
               <taxCode>IVA23</taxCode>
               <totalDistanceTravelled>8839000</totalDistanceTravelled>
               <zones>
                  <category>NORMAL</category>
                  <code>ZNXT000024</code>
                  <location>Lisboa</location>
                  <parentZone>Grande Lisboa</parentZone>
                  <zone>Estacionamento - Parque das Nações</zone>
               </zones>
               <zones>
                  <category>NORMAL</category>
                  <code>ZNXT000023</code>
                  <location>Lisboa</location>
                  <parentZone>Grande Lisboa</parentZone>
                  <zone>Estacionamento - Centro</zone>
               </zones>
            </car>
            <carLicensePlate>48-OS-13</carLicensePlate>
            <carMake>Opel</carMake>
            <carModel>Adam</carModel>
            <costCalculationSuccess>true</costCalculationSuccess>
            <distance>0</distance>
            <duration>60</duration>
            <endDate>2016-04-21T08:49:48.197Z</endDate>
            <endLongitude>-9.15438271</endLongitude>
            <endPark>Estacionamento - Centro</endPark>
            <endtLatitude>38.75950623</endtLatitude>
            <isRelocation>false</isRelocation>
            <paidWithBonus>true</paidWithBonus>
            <percentageDiscount>0</percentageDiscount>
            <promotionBonusGeneratedWithTax>0.0000</promotionBonusGeneratedWithTax>
            <roamingCost>0.0000</roamingCost>
            <roamingCostWithTax>0.00</roamingCostWithTax>
            <startDate>2016-04-21T08:48:57.925Z</startDate>
            <startLatitude>38.75950623</startLatitude>
            <startLongitude>-9.15438271</startLongitude>
            <startPark>Estacionamento - Centro</startPark>
            <state>CLOSED</state>
            <timeBooked>60</timeBooked>
            <timeCreated>2016-04-21T07:48:58.018Z</timeCreated>
            <timeInUse>0</timeInUse>
            <timeUpdated>2016-04-21T07:48:58.018Z</timeUpdated>
            <totalCost>0.0000</totalCost>
            <totalCostWithTax>0.0000</totalCostWithTax>
            <tripCost>0.0000</tripCost>
            <tripCostWithTax>0.00</tripCostWithTax>
         </return>
      </ns2:getLastTripDetailsResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
{
  "getLastTripDetailsResponse": {
    "return": {
      "addOnDiscountGeneratedWithTax": "0.0000",
      "bookingNumber": "BCTD16040795",
      "bookingTaxCode": "IVA23",
      "bookingType": "IMMEDIATE",
      "canOpenCar": "false",
      "car": {
        "carBrandName": "Opel",
        "carClubCode": "NXT",
        "carClubName": "Nextmotion",
        "carFareType": "STEP",
        "carModelName": "Adam",
        "carName": "Opel Adam",
        "carType": "NORMAL",
        "category": "Supermini",
        "categoryDescription": "main.car_class.supermini",
        "checkCard": "false",
        "checkKey": "true",
        "configurableTime": "6",
        "costPerExtraKm": "0.29",
        "deviceDriverClass": "com.criticalsoftware.mobics.driver.convadis.ConvadisEDriverProvider",
        "distanceThreshold": "20000",
        "fuelLevel": "11",
        "fuelType": {
          "key": "main.fuel_type.petrol",
          "name": "PETROL"
        },
        "includedDistancePerConfigurableHour": "100000",
        "includedDistancePerDay": "200000",
        "latitude": "38.78128433",
        "licensePlate": "48-OS-13",
        "longitude": "-9.11329269",
        "maxCostPerConfigurableHour": "29.90",
        "maxCostPerDay": "69.90",
        "maxCostPerHour": "9.90",
        "obsConnectionStatus": "OPERATIONAL",
        "obsNumber": "48151913",
        "priceBookedPerMinute": "0.29",
        "priceReservedPerMinute": "0.10",
        "showDamageReport": "true",
        "simNumber": "937929718",
        "standalone": "false",
        "state": "AVAILABLE",
        "taxCode": "IVA23",
        "totalDistanceTravelled": "8839000",
        "zones": [
          {
            "category": "NORMAL",
            "code": "ZNXT000024",
            "location": "Lisboa",
            "parentZone": "Grande Lisboa",
            "zone": "Estacionamento - Parque das Nações"
          },
          {
            "category": "NORMAL",
            "code": "ZNXT000023",
            "location": "Lisboa",
            "parentZone": "Grande Lisboa",
            "zone": "Estacionamento - Centro"
          }
        ]
      },
      "carLicensePlate": "48-OS-13",
      "carMake": "Opel",
      "carModel": "Adam",
      "costCalculationSuccess": "true",
      "distance": "0",
      "duration": "60",
      "endDate": "2016-04-21T08:49:48.197Z",
      "endLongitude": "-9.15438271",
      "endPark": "Estacionamento - Centro",
      "endtLatitude": "38.75950623",
      "isRelocation": "false",
      "paidWithBonus": "true",
      "percentageDiscount": "0",
      "promotionBonusGeneratedWithTax": "0.0000",
      "roamingCost": "0.0000",
      "roamingCostWithTax": "0.00",
      "startDate": "2016-04-21T08:48:57.925Z",
      "startLatitude": "38.75950623",
      "startLongitude": "-9.15438271",
      "startPark": "Estacionamento - Centro",
      "state": "CLOSED",
      "timeBooked": "60",
      "timeCreated": "2016-04-21T07:48:58.018Z",
      "timeInUse": "0",
      "timeUpdated": "2016-04-21T07:48:58.018Z",
      "totalCost": "0.0000",
      "totalCostWithTax": "0.0000",
      "tripCost": "0.0000",
      "tripCostWithTax": "0.00"
    }
  }
}
```

Name | Type | Description
--------- | ------- | -----------
addOnDiscountGeneratedWithTax | BigDecimal | The discount of the addon with tax.
bookingNumber | String | The booking number.
bookingTaxCode | String | The booking tax code.
bookingType | Object | The booking type.
canOpenCar | Boolean | Check if the car can be open.
car | Object | The car.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;carBrandName | String | The car's brand name.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;carClubCode | String | The car's car club code.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;carClubName | String | The car's car club name.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;carFareType | Object | The car's fare type.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;carModelName | String | The car's model name.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;carName | String | The car's name.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;carType | Object | The car's type.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;category | String | The car's category.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;categoryDescription | String | The car's category description. 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;checkCard | Boolean | If check card device is active.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;checkKey | Boolean | If check key device is active.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;configurableTime | Integer | The car's seconds configurable time.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;costPerExtraKm | BigDecimal | The cost of an extra km.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;deviceDriverClass | String | The car's device driver class.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;distanceThreshold | BigDecimal | The car's limit distance.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;fuelLevel | Integer | The car's fuel level.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;fuelType | Object | The car's fuel type.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;key | String | The fuel's key code.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name | String | The fuel's name.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;maxCostPerHour | BigDecimal | The max cost per hour of the car.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;obsConnectionStatus | Object | The car's obs connection status.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;obsNumber | String | The car's obs number.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;priceReservedPerMinute | BigDecimal | The car's price booked per minute.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;showDamageReport | Boolean | If damage report is to show.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;simNumber | String | The car's sim number.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;standalone | Boolean | If the car is in standlone mode.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;state | String | The car's state.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;taxCode | String | The car's tax code.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;totalDistanceTravelled | Integer | The total distance travelled.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;zones | Object | The car's zones 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;category | Object | The zone's category (NORMAL, SPECIAL, UNWANTED, PARKING, FORBIDDEN).
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;code | String | The zone's code.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;location | String | The location.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;parentZone | String | The parent location.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;zone | String | The zone.
duration | Integer | The booking duration.
endDate | Date | The booking end date.
endLongitude | BigDecimal | The booking end location (longitude).
endPark | String | The booking end park.
endtLatitude | BigDecimal | The booking end location (latitude).
isRelocation | Boolean | Check if the car was relocated.
paidWithBonus | Boolean | Check if the user paid with bonus.
percentageDiscount | BigDecimal | The percentage of the discount.
promotionBonusGeneratedWithTax | BigDecimal | The promotion bonus with tax.
roamingCost | BigDecimal | The roaming cost.
roamingCostWithTax | BigDecimal | The roaming cost with tax.
startDate | Date | The booking start date.
startLatitude | BigDecimal | The booking start location (latitude).
startLongitude | BigDecimal | The booking start location (longitude).
startPark | String | The booking start park.
state | String | The booking state.
timeBooked | Integer | he time that the car was booked.
timeCreated | Date | The date that the booking was created.
timeInUse | Integer | The time that the car was in use.
timeUpdated | Date | The date that the booking was updated.
totalCost | BigDecimal | The total cost of the booking.
totalCostWithTax | BigDecimal | The total cost with tax of the booking.
tripCost | BigDecimal | The trip cost.
tripCostWithTax | BigDecimal | The trip cost with tax.

## - getNextAdvanceBooking

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:book="http://mobics.criticalsoftware.com/booking">
   <soapenv:Header>
   <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
      <wsse:UsernameToken>
         <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
         <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">Wxd4g3t79nCuHB3I+TnoxeCoNEs=</wsse:Password>
         <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ1NTk4NjI2MDQyNg==</wsse:Nonce>
         <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-02-20T16:37:40Z</wsu:Created>
      </wsse:UsernameToken>
   </wsse:Security>
</soapenv:Header>
   <soapenv:Body>
      <book:getNextAdvanceBooking>
         <!--Optional:-->
         <book:bookingNumber>BCTD16040034</book:bookingNumber>
      </book:getNextAdvanceBooking>
   </soapenv:Body>
</soapenv:Envelope>
```

```plaintext
GET /mobics-webservices/rs/booking/getNextAdvanceBooking HTTP/1.1
Host: imobics.mobiag.com
Username: ricardo.mendes@mobiag.com
Password: Wxd4g3t79nCuHB3I+TnoxeCoNEs=
Nonce: MTQ1NTk4NjI2MDQyNg==
Created: 2016-02-20T16:37:40Z
Content-Type: application/json
bookingNumber: BCTD16040034
Cache-Control: no-cache
```

This service is used to get the next advance booking date for car.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Booking?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/booking/getNextAdvanceBooking`

<aside class="warning">
This service requires authentication.
</aside>

### Input Parameters

Name | Type | Description | Mandatory
--------- | ------- | ----------- | --------
bookingNumber | String | The booking number. | Yes

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:getNextAdvanceBookingResponse xmlns:ns2="http://mobics.criticalsoftware.com/booking">
         <return>1461942738396</return>
      </ns2:getNextAdvanceBookingResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
{
  "getNextAdvanceBookingResponse": {
    "return": "1461942738396"
  }
}
```

Name | Type | Description
--------- | ------- | -----------
nextAdvanceBooking | Long | The next advance booking date in milliseconds.

## - getNextBooking

```xml
<soapenv:Header>
   <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
         <wsse:UsernameToken>
            <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
            <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">Wxd4g3t79nCuHB3I+TnoxeCoNEs=</wsse:Password>
            <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ1NTk4NjI2MDQyNg==</wsse:Nonce>
            <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-02-20T16:37:40Z</wsu:Created>
         </wsse:UsernameToken>
   </wsse:Security>
</soapenv:Header>
```

```plaintext
GET /mobics-webservices/rs/booking/getNextBooking HTTP/1.1
Host: imobics.mobiag.com
Username: ricardo.mendes@mobiag.com
Password: Wxd4g3t79nCuHB3I+TnoxeCoNEs=
Nonce: MTQ1NTk4NjI2MDQyNg==
Created: 2016-02-20T16:37:40Z
Content-Type: application/json
Cache-Control: no-cache
```

This service is used to get the next booking.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Booking?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/booking/getNextBooking`

<aside class="warning">
This service requires authentication.
</aside>

### Input Parameters

This service has no input parameters.

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:getNextBookingResponse xmlns:ns2="http://mobics.criticalsoftware.com/booking">
         <return>
            <code>BCTD16040036</code>
            <endTime>2016-04-28T17:00:00Z</endTime>
            <startTime>2016-04-28T16:00:00Z</startTime>
            <state>BOOKED</state>
         </return>
      </ns2:getNextBookingResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
{
  "getNextBookingResponse": {
    "return": {
      "code": "BCTD16040036",
      "endTime": "2016-04-28T17:00:00Z",
      "startTime": "2016-04-28T16:00:00Z",
      "state": "BOOKED"
    }
  }
}
```

Name | Type | Description
--------- | ------- | -----------
code | String | The booking code.
endTime | Date | The booking end date.
startTime | Date | The booking start date.
state | String | The booking state.

## - getNextTripDetails

```xml
<soapenv:Header>
   <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
         <wsse:UsernameToken>
            <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
            <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">Wxd4g3t79nCuHB3I+TnoxeCoNEs=</wsse:Password>
            <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ1NTk4NjI2MDQyNg==</wsse:Nonce>
            <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-02-20T16:37:40Z</wsu:Created>
         </wsse:UsernameToken>
   </wsse:Security>
</soapenv:Header>
```

```plaintext
GET /mobics-webservices/rs/booking/getNextTripDetails HTTP/1.1
Host: imobics.mobiag.com
Username: ricardo.mendes@mobiag.com
Password: Wxd4g3t79nCuHB3I+TnoxeCoNEs=
Nonce: MTQ1NTk4NjI2MDQyNg==
Created: 2016-02-20T16:37:40Z
Content-Type: application/json
Cache-Control: no-cache
```

This service is used to get the next trip details.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Booking?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/booking/getNextTripDetails`

<aside class="warning">
This service requires authentication.
</aside>

### Input Parameters

This service has no input parameters.

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:getNextTripDetailsResponse xmlns:ns2="http://mobics.criticalsoftware.com/booking">
         <return>
            <addOnDiscountGeneratedWithTax>0.0000</addOnDiscountGeneratedWithTax>
            <bookingNumber>BCTD16040036</bookingNumber>
            <bookingTaxCode>IVA23</bookingTaxCode>
            <bookingType>ADVANCE</bookingType>
            <canOpenCar>true</canOpenCar>
            <car>
               <carBrandName>BMW</carBrandName>
               <carClubCode>CTD</carClubCode>
               <carClubName>Citydrive @ Testes</carClubName>
               <carFareType>STEP</carFareType>
               <carModelName>Série 1</carModelName>
               <carName>BMW Série 1</carName>
               <carType>SCHEDULE_BOOKING</carType>
               <category>Supermini</category>
               <categoryDescription>main.car_class.supermini</categoryDescription>
               <checkCard>false</checkCard>
               <checkKey>true</checkKey>
               <configurableTime>3</configurableTime>
               <costPerExtraKm>0.00</costPerExtraKm>
               <deviceDriverClass>com.criticalsoftware.mobics.driver.convadis.ConvadisDriverProvider</deviceDriverClass>
               <distanceThreshold>2000</distanceThreshold>
               <fuelLevel>100</fuelLevel>
               <fuelType>
                  <key>main.fuel_type.petrol</key>
                  <name>PETROL</name>
               </fuelType>
               <includedDistancePerConfigurableHour>2000</includedDistancePerConfigurableHour>
               <includedDistancePerDay>2000</includedDistancePerDay>
               <latitude>38.71849442</latitude>
               <licensePlate>00-EB-00</licensePlate>
               <longitude>-9.14852238</longitude>
               <maxCostPerConfigurableHour>0.01</maxCostPerConfigurableHour>
               <maxCostPerDay>0.00</maxCostPerDay>
               <maxCostPerHour>0.01</maxCostPerHour>
               <obsConnectionStatus>UNTESTED</obsConnectionStatus>
               <obsNumber>1234567</obsNumber>
               <priceBookedPerMinute>0.00</priceBookedPerMinute>
               <priceReservedPerMinute>0.01</priceReservedPerMinute>
               <showDamageReport>true</showDamageReport>
               <simNumber>123456789</simNumber>
               <standalone>true</standalone>
               <state>AVAILABLE</state>
               <taxCode>IVA23</taxCode>
               <totalDistanceTravelled>100000</totalDistanceTravelled>
               <zones>
                  <category>PARKING</category>
                  <code>ZCTD0000025</code>
                  <location>Lisboa</location>
                  <zone>Inevo Parque 3</zone>
               </zones>
            </car>
            <carLicensePlate>00-EB-00</carLicensePlate>
            <carMake>BMW</carMake>
            <carModel>Série 1</carModel>
            <costCalculationSuccess>true</costCalculationSuccess>
            <distance>0</distance>
            <duration>0</duration>
            <endDate>2016-04-28T17:00:00Z</endDate>
            <isRelocation>false</isRelocation>
            <paidWithBonus>false</paidWithBonus>
            <percentageDiscount>0</percentageDiscount>
            <promotionBonusGeneratedWithTax>0.0000</promotionBonusGeneratedWithTax>
            <roamingCost>0.0000</roamingCost>
            <roamingCostWithTax>0.00</roamingCostWithTax>
            <startDate>2016-04-28T16:00:00Z</startDate>
            <startLatitude>38.71849442</startLatitude>
            <startLongitude>-9.14852238</startLongitude>
            <startPark>Inevo Parque 3</startPark>
            <state>BOOKED</state>
            <timeBooked>0</timeBooked>
            <timeCreated>2016-04-28T14:50:58.945Z</timeCreated>
            <timeInUse>0</timeInUse>
            <timeUpdated>2016-04-28T14:50:58.945Z</timeUpdated>
            <totalCost>0.0000</totalCost>
            <totalCostWithTax>0.00</totalCostWithTax>
            <tripCost>0.0000</tripCost>
            <tripCostWithTax>0.00</tripCostWithTax>
         </return>
      </ns2:getNextTripDetailsResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
{
  "getNextTripDetailsResponse": {
    "return": {
      "addOnDiscountGeneratedWithTax": "0.0000",
      "bookingNumber": "BCTD16040036",
      "bookingTaxCode": "IVA23",
      "bookingType": "ADVANCE",
      "canOpenCar": "true",
      "car": {
        "carBrandName": "BMW",
        "carClubCode": "CTD",
        "carClubName": "Citydrive @ Testes",
        "carFareType": "STEP",
        "carModelName": "Série 1",
        "carName": "BMW Série 1",
        "carType": "SCHEDULE_BOOKING",
        "category": "Supermini",
        "categoryDescription": "main.car_class.supermini",
        "checkCard": "false",
        "checkKey": "true",
        "configurableTime": "3",
        "costPerExtraKm": "0.00",
        "deviceDriverClass": "com.criticalsoftware.mobics.driver.convadis.ConvadisDriverProvider",
        "distanceThreshold": "2000",
        "fuelLevel": "100",
        "fuelType": {
          "key": "main.fuel_type.petrol",
          "name": "PETROL"
        },
        "includedDistancePerConfigurableHour": "2000",
        "includedDistancePerDay": "2000",
        "latitude": "38.71849442",
        "licensePlate": "00-EB-00",
        "longitude": "-9.14852238",
        "maxCostPerConfigurableHour": "0.01",
        "maxCostPerDay": "0.00",
        "maxCostPerHour": "0.01",
        "obsConnectionStatus": "UNTESTED",
        "obsNumber": "1234567",
        "priceBookedPerMinute": "0.00",
        "priceReservedPerMinute": "0.01",
        "showDamageReport": "true",
        "simNumber": "123456789",
        "standalone": "true",
        "state": "AVAILABLE",
        "taxCode": "IVA23",
        "totalDistanceTravelled": "100000",
        "zones": {
          "category": "PARKING",
          "code": "ZCTD0000025",
          "location": "Lisboa",
          "zone": "Inevo Parque 3"
        }
      },
      "carLicensePlate": "00-EB-00",
      "carMake": "BMW",
      "carModel": "Série 1",
      "costCalculationSuccess": "true",
      "distance": "0",
      "duration": "0",
      "endDate": "2016-04-28T17:00:00Z",
      "isRelocation": "false",
      "paidWithBonus": "false",
      "percentageDiscount": "0",
      "promotionBonusGeneratedWithTax": "0.0000",
      "roamingCost": "0.0000",
      "roamingCostWithTax": "0.00",
      "startDate": "2016-04-28T16:00:00Z",
      "startLatitude": "38.71849442",
      "startLongitude": "-9.14852238",
      "startPark": "Inevo Parque 3",
      "state": "BOOKED",
      "timeBooked": "0",
      "timeCreated": "2016-04-28T14:50:58.945Z",
      "timeInUse": "0",
      "timeUpdated": "2016-04-28T14:50:58.945Z",
      "totalCost": "0.0000",
      "totalCostWithTax": "0.00",
      "tripCost": "0.0000",
      "tripCostWithTax": "0.00"
    }
  }
}
```

Name | Type | Description
--------- | ------- | -----------
addOnDiscountGeneratedWithTax | BigDecimal | The discount of the addon with tax.
bookingNumber | String | The booking number.
bookingTaxCode | String | The booking tax code.
bookingType | Object | The booking type.
canOpenCar | Boolean | Check if the car can be open.
car | Object | The car.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;carBrandName | String | The car's brand name.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;carClubCode | String | The car's car club code.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;carClubName | String | The car's car club name.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;carFareType | Object | The car's fare type.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;carModelName | String | The car's model name.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;carName | String | The car's name.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;carType | Object | The car's type.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;category | String | The car's category.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;categoryDescription | String | The car's category description.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;checkCard | Boolean | If check card device is active.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;checkKey | Boolean | If check key device is active.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;configurableTime | Integer | The car's seconds configurable time.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;costPerExtraKm | BigDecimal | The cost of an extra km.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;deviceDriverClass | String | The car's device driver class.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;distanceThreshold | BigDecimal | The car's limit distance.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;fuelLevel | Integer | The car's fuel level.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;fuelType | Object | The car's fuel type.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;key | String | The fuel's key code.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name | String | The fuel's name.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;includedDistancePerConfigurableHour | Integer | The car's allowed distance to travel per hour.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;includedDistancePerDay | Integer | The car's allowed distance to travel per day.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;latitude | BigDecimal | The car's latitude.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;licensePlate | String | The car's license plate.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;longitude | BigDecimal | The car's longitude.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;maxCostPerConfigurableHour | BigDecimal | The max cost per hour of the car (hour configurable).
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;maxCostPerDay | BigDecimal | The max cost per day of the car.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;maxCostPerHour | BigDecimal | The max cost per hour of the car.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;obsConnectionStatus | Object | The car's obs connection status.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;obsNumber | String | The car's obs number.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;priceBookedPerMinute | BigDecimal | The car's price booked per minute.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;priceReservedPerMinute | BigDecimal | The car's price reserved per minute.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;showDamageReport | Boolean | If damage report is to show.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;simNumber | String | The car's sim number.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;standalone | Boolean | If the car is in standlone mode.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;state | String | The car's state.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;taxCode | String | The car's tax code.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;totalDistanceTravelled | Integer | The car's total distance travelled.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;zones | Object | The car's zones 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;category | Object | The zone's category (NORMAL, SPECIAL, UNWANTED, PARKING, FORBIDDEN).
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;code | String | The zone's code.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;location | String | The location.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;parentZone | String | The parent location.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;zone | String | The zone.
carLicensePlate | String | The car's license plate.
carMake | String | The car's make.
carModel | String | The car's model.
costCalculationSuccess | Boolean | Check if the calculation of the cost return sucess.
distance | Integer | The distance travelled.
duration | Integer | The booking duration.
endDate | Date | The booking end date.
isRelocation | Boolean | Check if the car was relocated.
paidWithBonus | Boolean | Check if the user paid with bonus.
percentageDiscount | BigDecimal | The percentage of the discount.
promotionBonusGeneratedWithTax | BigDecimal | The promotion bonus with tax.
roamingCost | BigDecimal | The roaming cost.
roamingCostWithTax | BigDecimal | The roaming cost with tax.
startDate | Date | The booking start date.
startLatitude | BigDecimal | The booking start location (latitude).
startLongitude | BigDecimal | The booking start location (longitude).
startPark | String | The booking start park.
state | String | The booking state.
timeBooked | Integer | The time that the car was booked.
timeCreated | Date | The date that the booking was created.
timeInUse | Integer | The time that the car was in use.
timeUpdated | Date | The date that the booking was updated.
totalCost | BigDecimal | The total cost of the booking.
totalCostWithTax | BigDecimal | The total cost with tax of the booking.
tripCost | BigDecimal | The trip cost.
tripCostWithTax | BigDecimal | The trip cost with tax.

## - getTripDetails

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:book="http://mobics.criticalsoftware.com/booking">
   <soapenv:Header>
   <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
      <wsse:UsernameToken>
         <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
         <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">Wxd4g3t79nCuHB3I+TnoxeCoNEs=</wsse:Password>
         <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ1NTk4NjI2MDQyNg==</wsse:Nonce>
         <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-02-20T16:37:40Z</wsu:Created>
      </wsse:UsernameToken>
   </wsse:Security>
</soapenv:Header>
   <soapenv:Body>
      <book:getTripDetails>
         <!--Optional:-->
         <book:bookingNumber>BCTD16040034</book:bookingNumber>
      </book:getTripDetails>
   </soapenv:Body>
</soapenv:Envelope>
```

```plaintext
GET /mobics-webservices/rs/booking/getTripDetails HTTP/1.1
Host: imobics.mobiag.com
Username: ricardo.mendes@mobiag.com
Password: Wxd4g3t79nCuHB3I+TnoxeCoNEs=
Nonce: MTQ1NTk4NjI2MDQyNg==
Created: 2016-02-20T16:37:40Z
Content-Type: application/json
bookingNumber: BCTD16040034
Cache-Control: no-cache
```

This service is used to get the trip details.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Booking?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/booking/getTripDetails`

<aside class="warning">
This service requires authentication.
</aside>

### Input Parameters

Name | Type | Description | Mandatory
--------- | ------- | ----------- | --------
bookingNumber | String | The booking number. | Yes

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:getTripDetailsResponse xmlns:ns2="http://mobics.criticalsoftware.com/booking">
         <return>
            <addOnDiscountGeneratedWithTax>0.0000</addOnDiscountGeneratedWithTax>
            <bonusIsDeferred>false</bonusIsDeferred>
            <bookingNumber>BCTD16040034</bookingNumber>
            <bookingTaxCode>IVA23</bookingTaxCode>
            <bookingType>IMMEDIATE</bookingType>
            <canOpenCar>false</canOpenCar>
            <car>
               <carBrandName>Skoda</carBrandName>
               <carClubCode>CTD</carClubCode>
               <carClubName>Citydrive @ Testes</carClubName>
               <carFareType>STEP</carFareType>
               <carModelName>Fabia</carModelName>
               <carName>Skoda Fabia</carName>
               <carType>NORMAL</carType>
               <category>Small family car</category>
               <categoryDescription>main.car_class.small_familt_car</categoryDescription>
               <checkCard>false</checkCard>
               <checkKey>true</checkKey>
               <configurableTime>6</configurableTime>
               <costPerExtraKm>0.29</costPerExtraKm>
               <deviceDriverClass>com.criticalsoftware.mobics.driver.convadis.ConvadisDriverProvider</deviceDriverClass>
               <distanceThreshold>20000</distanceThreshold>
               <fuelLevel>100</fuelLevel>
               <fuelType>
                  <key>main.fuel_type.diesel</key>
                  <name>DIESEL</name>
               </fuelType>
               <includedDistancePerConfigurableHour>100000</includedDistancePerConfigurableHour>
               <includedDistancePerDay>200000</includedDistancePerDay>
               <latitude>38.73658371</latitude>
               <licensePlate>10-PU-10</licensePlate>
               <longitude>-9.14249420</longitude>
               <maxCostPerConfigurableHour>29.90</maxCostPerConfigurableHour>
               <maxCostPerDay>69.90</maxCostPerDay>
               <maxCostPerHour>9.90</maxCostPerHour>
               <obsConnectionStatus>UNTESTED</obsConnectionStatus>
               <obsNumber>45725</obsNumber>
               <priceBookedPerMinute>0.29</priceBookedPerMinute>
               <priceReservedPerMinute>0.10</priceReservedPerMinute>
               <showDamageReport>true</showDamageReport>
               <simNumber>123456789</simNumber>
               <standalone>true</standalone>
               <state>AVAILABLE</state>
               <taxCode>IVA23</taxCode>
               <totalDistanceTravelled>100000</totalDistanceTravelled>
               <zones>
                  <category>NORMAL</category>
                  <code>ZCTD000022</code>
                  <location>Lisboa</location>
                  <parentZone>Grande Lisboa</parentZone>
                  <zone>Expansão 1</zone>
               </zones>
            </car>
            <carLicensePlate>10-PU-10</carLicensePlate>
            <carMake>Skoda</carMake>
            <carModel>Fabia</carModel>
            <costCalculationSuccess>true</costCalculationSuccess>
            <distance>0</distance>
            <duration>85103</duration>
            <endDate>2016-04-28T15:50:43.343Z</endDate>
            <endLongitude>-9.14249420</endLongitude>
            <endPark>Expansão 1</endPark>
            <endtLatitude>38.73658371</endtLatitude>
            <isRelocation>false</isRelocation>
            <paidWithBonus>true</paidWithBonus>
            <percentageDiscount>0.00</percentageDiscount>
            <promotionBonusGeneratedWithTax>0.0000</promotionBonusGeneratedWithTax>
            <roamingCost>0.0000</roamingCost>
            <roamingCostWithTax>0.00</roamingCostWithTax>
            <startDate>2016-04-27T16:12:18.396Z</startDate>
            <startLatitude>38.73658371</startLatitude>
            <startLongitude>-9.14249420</startLongitude>
            <startPark>Expansão 1</startPark>
            <state>UNDER_REVIEW</state>
            <timeBooked>85103</timeBooked>
            <timeCreated>2016-04-27T15:12:18.423Z</timeCreated>
            <timeInUse>0</timeInUse>
            <timeUpdated>2016-04-27T15:12:18.423Z</timeUpdated>
            <totalCost>56.8300</totalCost>
            <totalCostWithTax>69.9000</totalCostWithTax>
            <tripCost>56.8292</tripCost>
            <tripCostWithTax>69.90</tripCostWithTax>
         </return>
      </ns2:getTripDetailsResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
{
  "getTripDetailsResponse": {
    "return": {
      "addOnDiscountGeneratedWithTax": "0.0000",
      "bonusIsDeferred": "false",
      "bookingNumber": "BCTD16040034",
      "bookingTaxCode": "IVA23",
      "bookingType": "IMMEDIATE",
      "canOpenCar": "false",
      "car": {
        "carBrandName": "Skoda",
        "carClubCode": "CTD",
        "carClubName": "Citydrive @ Testes",
        "carFareType": "STEP",
        "carModelName": "Fabia",
        "carName": "Skoda Fabia",
        "carType": "NORMAL",
        "category": "Small family car",
        "categoryDescription": "main.car_class.small_familt_car",
        "checkCard": "false",
        "checkKey": "true",
        "configurableTime": "6",
        "costPerExtraKm": "0.29",
        "deviceDriverClass": "com.criticalsoftware.mobics.driver.convadis.ConvadisDriverProvider",
        "distanceThreshold": "20000",
        "fuelLevel": "100",
        "fuelType": {
          "key": "main.fuel_type.diesel",
          "name": "DIESEL"
        },
        "includedDistancePerConfigurableHour": "100000",
        "includedDistancePerDay": "200000",
        "latitude": "38.73658371",
        "licensePlate": "10-PU-10",
        "longitude": "-9.14249420",
        "maxCostPerConfigurableHour": "29.90",
        "maxCostPerDay": "69.90",
        "maxCostPerHour": "9.90",
        "obsConnectionStatus": "UNTESTED",
        "obsNumber": "45725",
        "priceBookedPerMinute": "0.29",
        "priceReservedPerMinute": "0.10",
        "showDamageReport": "true",
        "simNumber": "123456789",
        "standalone": "true",
        "state": "AVAILABLE",
        "taxCode": "IVA23",
        "totalDistanceTravelled": "100000",
        "zones": {
          "category": "NORMAL",
          "code": "ZCTD000022",
          "location": "Lisboa",
          "parentZone": "Grande Lisboa",
          "zone": "Expansão 1"
        }
      },
      "carLicensePlate": "10-PU-10",
      "carMake": "Skoda",
      "carModel": "Fabia",
      "costCalculationSuccess": "true",
      "distance": "0",
      "duration": "85103",
      "endDate": "2016-04-28T15:50:43.343Z",
      "endLongitude": "-9.14249420",
      "endPark": "Expansão 1",
      "endtLatitude": "38.73658371",
      "isRelocation": "false",
      "paidWithBonus": "true",
      "percentageDiscount": "0.00",
      "promotionBonusGeneratedWithTax": "0.0000",
      "roamingCost": "0.0000",
      "roamingCostWithTax": "0.00",
      "startDate": "2016-04-27T16:12:18.396Z",
      "startLatitude": "38.73658371",
      "startLongitude": "-9.14249420",
      "startPark": "Expansão 1",
      "state": "UNDER_REVIEW",
      "timeBooked": "85103",
      "timeCreated": "2016-04-27T15:12:18.423Z",
      "timeInUse": "0",
      "timeUpdated": "2016-04-27T15:12:18.423Z",
      "totalCost": "56.8300",
      "totalCostWithTax": "69.9000",
      "tripCost": "56.8292",
      "tripCostWithTax": "69.90"
    }
  }
}
```

Name | Type | Description
--------- | ------- | -----------
addOnDiscountGeneratedWithTax | BigDecimal | The discount of the addon with tax.
bonusIsDeferred | Boolean | Check if the bonus is deferred.
bookingNumber | String | The booking number.
bookingTaxCode | String | The booking tax code.
bookingType | Object | The booking type.
canOpenCar | Boolean | Check if the car can be open.
car | Object | The car.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;carBrandName | String | The car's brand name.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;carClubCode | String | The car's car club code.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;carClubName | String | The car's car club name.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;carFareType | Object | The car's fare type.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;carModelName | String | The car's model name.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;carName | String | The car's name.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;carType | Object | The car's type.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;category | String | The car's category.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;categoryDescription | String | The car's category description.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;checkCard | Boolean | If check card device is active.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;checkKey | Boolean | If check key device is active.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;configurableTime | Integer | The car's seconds configurable time.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;costPerExtraKm | BigDecimal | The cost of an extra km.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;deviceDriverClass | String | The car's device driver class.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;distanceThreshold | BigDecimal | The car's limit distance.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;fuelLevel | Integer | The car's fuel level.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;fuelType | Object | The car's fuel type.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;key | String | The fuel's key code.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name | String | The fuel's name.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;includedDistancePerConfigurableHour | Integer | The car's allowed distance to travel per hour.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;includedDistancePerDay | Integer | The car's allowed distance to travel per day.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;latitude | BigDecimal | The car's latitude.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;licensePlate | String | The car's license plate.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;longitude | BigDecimal | The car's longitude.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;maxCostPerConfigurableHour | BigDecimal | The max cost per hour of the car (hour configurable).
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;maxCostPerDay | BigDecimal | The max cost per day of the car.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;maxCostPerHour | BigDecimal | The max cost per hour of the car.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;obsConnectionStatus | Object | The car's obs connection status.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;obsNumber | String | The car's obs number.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;priceBookedPerMinute | BigDecimal | The car's price booked per minute.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;priceReservedPerMinute | BigDecimal | The car's price reserved per minute.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;showDamageReport | Boolean | If damage report is to show.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;simNumber | String | The car's sim number.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;standalone | Boolean | If the car is in standlone mode.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;state | String | The car's state.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;taxCode | String | The car's tax code.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;totalDistanceTravelled | Integer | The car's total distance travelled.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;zones | Object | The car's zones 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;category | Object | The zone's category (NORMAL, SPECIAL, UNWANTED, PARKING, FORBIDDEN).
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;code | String | The zone's code.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;location | String | The location.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;parentZone | String | The parent location.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;zone | String | The zone.
carLicensePlate | String | The car's license plate.
carMake | String | The car's make.
carModel | String | The car's model.
costCalculationSuccess | Boolean | Check if the calculation of the cost return sucess.
distance | Integer | The distance travelled.
duration | Integer | The booking duration.
endDate | Date | The booking end date.
isRelocation | Boolean | Check if the car was relocated.
paidWithBonus | Boolean | Check if the user paid with bonus.
percentageDiscount | BigDecimal | The percentage of the discount.
promotionBonusGeneratedWithTax | BigDecimal | The promotion bonus with tax.
roamingCost | BigDecimal | The roaming cost.
roamingCostWithTax | BigDecimal | The roaming cost with tax.
startDate | Date | The booking start date.
startLatitude | BigDecimal | The booking start location (latitude).
startLongitude | BigDecimal | The booking start location (longitude).
startPark | String | The booking start park.
state | String | The booking state.
timeBooked | Integer | The time that the car was booked.
timeCreated | Date | The date that the booking was created.
timeInUse | Integer | The time that the car was in use.
timeUpdated | Date | The date that the booking was updated.
totalCost | BigDecimal | The total cost of the booking.
totalCostWithTax | BigDecimal | The total cost with tax of the booking.
tripCost | BigDecimal | The trip cost.
tripCostWithTax | BigDecimal | The trip cost with tax.

## - getTripHistory

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:book="http://mobics.criticalsoftware.com/booking">
   <soapenv:Header>
   <wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
      <wsse:UsernameToken>
         <wsse:Username>ricardo.mendes@mobiag.com</wsse:Username>
         <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">Wxd4g3t79nCuHB3I+TnoxeCoNEs=</wsse:Password>
         <wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ1NTk4NjI2MDQyNg==</wsse:Nonce>
         <wsu:Created xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">2016-02-20T16:37:40Z</wsu:Created>
      </wsse:UsernameToken>
   </wsse:Security>
</soapenv:Header>
   <soapenv:Body>
      <book:getTripHistory>
         <!--Optional:-->
         <book:startDate>1111111</book:startDate>
         <!--Optional:-->
         <book:endDate>9999999999999</book:endDate>
         <!--Optional:-->
         <book:bookingType>ADVANCE</book:bookingType>
      </book:getTripHistory>
   </soapenv:Body>
</soapenv:Envelope>
```

```plaintext
GET /mobics-webservices/rs/booking/getTripHistory HTTP/1.1
Host: imobics.mobiag.com
Username: ricardo.mendes@mobiag.com
Password: Wxd4g3t79nCuHB3I+TnoxeCoNEs=
Nonce: MTQ1NTk4NjI2MDQyNg==
Created: 2016-02-20T16:37:40Z
Content-Type: application/json
startDate: 1111111
endDate: 9999999999999
bookingType: ADVANCE
Cache-Control: no-cache
```

This service is used to get the trip history.

### WSDL

`http://imobics.mobiag.com/mobics-webservices/Booking?wsdl`

### URL

`http://imobics.mobiag.com/mobics-webservices/rs/booking/getTripHistory`

<aside class="warning">
This service requires authentication.
</aside>

### Input Parameters

Name | Type | Description | Mandatory
--------- | ------- | ----------- | --------
startDate | Long | The searching start date. | Yes
endDate | Long | The searching end date. | Yes
bookingType | String | The booking type. | No

### Output Parameters

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
      <ns2:getTripHistoryResponse xmlns:ns2="http://mobics.criticalsoftware.com/booking" xmlns:ns3="http://www.criticalsoftware.com/mobios/services/accounting/dto">
         <return>
            <applicableAddon>false</applicableAddon>
            <applicablePromotion>false</applicablePromotion>
            <bookingNumber>BCTD15110241</bookingNumber>
            <bookingType>ADVANCE</bookingType>
            <cost>0.0000</cost>
            <costWithTax>0.00</costWithTax>
            <endDateTime>2015-11-05T12:42:00Z</endDateTime>
            <licensePlate>99-QD-99</licensePlate>
            <location>Lisboa</location>
            <startDateTime>2015-11-05T12:33:00Z</startDateTime>
            <taxCode>IVA23</taxCode>
            <timeBooked>486</timeBooked>
            <timeInUse>0</timeInUse>
         </return>
         <return>
            <applicableAddon>false</applicableAddon>
            <applicablePromotion>false</applicablePromotion>
            <bookingNumber>BCTD15110240</bookingNumber>
            <bookingType>ADVANCE</bookingType>
            <cost>0.0000</cost>
            <costWithTax>0.00</costWithTax>
            <endDateTime>2015-11-05T22:04:37.965Z</endDateTime>
            <licensePlate>99-QD-99</licensePlate>
            <location>Lisboa</location>
            <startDateTime>2015-11-05T13:29:00Z</startDateTime>
            <taxCode>IVA23</taxCode>
            <timeBooked>30900</timeBooked>
            <timeInUse>0</timeInUse>
         </return>
      </ns2:getTripHistoryResponse>
   </soap:Body>
</soap:Envelope>
```

```plaintext
{
  "getTripHistoryResponse": {
    "return": [
      {
        "applicableAddon": "false",
        "applicablePromotion": "false",
        "bookingNumber": "BCTD15110241",
        "bookingType": "ADVANCE",
        "cost": "0.0000",
        "costWithTax": "0.00",
        "endDateTime": "2015-11-05T12:42:00Z",
        "licensePlate": "99-QD-99",
        "location": "Lisboa",
        "startDateTime": "2015-11-05T12:33:00Z",
        "taxCode": "IVA23",
        "timeBooked": "486",
        "timeInUse": "0"
      },
      {
        "applicableAddon": "false",
        "applicablePromotion": "false",
        "bookingNumber": "BCTD15110240",
        "bookingType": "ADVANCE",
        "cost": "0.0000",
        "costWithTax": "0.00",
        "endDateTime": "2015-11-05T22:04:37.965Z",
        "licensePlate": "99-QD-99",
        "location": "Lisboa",
        "startDateTime": "2015-11-05T13:29:00Z",
        "taxCode": "IVA23",
        "timeBooked": "30900",
        "timeInUse": "0"
      }
    ]
  }
}
```

Name | Type | Description
--------- | ------- | -----------
applicableAddon | Boolean | Check if addon was applied.
applicablePromotion | Boolean | Check if promotion was applied.
bookingNumber | String | The booking number.
bookingType | Object | The booking type.
cost | BigDecimal | The booking cost.
costWithTax | BigDecimal | The booking cost with tax.
endDateTime | Date | The booking end date.
licensePlate | String | The car's license plate.
location | String | The car's end location.
startDateTime | Date | The booking start date.
taxCode | String | The tax code.
timeBooked | Integer | The time that the car was booked.
timeInUse | Integer | The time that the car was in use.