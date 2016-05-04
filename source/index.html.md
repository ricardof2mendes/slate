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

Welcome to the Mobiag API! You can use our API to

# Authentication

> To authorize, use this header:

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
Host: mobics.mobiag.com
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

# Find Cars

## Find Cars Immediate

This page contains the description of the process to Find Cars.
This process is the start of the booking flow and you can do the search using the services getCarOnRadius, searchCars and getCarsByLicensePlate from web services with SOAP or REST.

![Find Cars Immediate Diagram](/images/FindCarsImmediate.png)

You also can get all the cars of the car club with getFleet.

## getCarOnRadius

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

## searchCars

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

<aside class="notice">
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

## getCarsByLicensePlate

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

<aside class="notice">
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

## getFleet

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

## getCarsForAdvanceBooking

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

## getNextAvailableCarForAdvanceBooking

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

## getCarsInLocationByCarClubCodeAndLocationCode

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

## getCarsInLocationByCarClubCode

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

## getFleet

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