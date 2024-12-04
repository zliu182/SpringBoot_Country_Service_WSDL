## Select "Request 1"

<img width="284" alt="Screenshot 2024-12-03 at 11 24 24 PM" src="https://github.com/user-attachments/assets/591ebad4-1751-4555-929f-f97f20c77548">

<img width="590" alt="Screenshot 2024-12-03 at 11 24 36 PM" src="https://github.com/user-attachments/assets/b0abf0a6-2b4b-4993-b780-af50f2e8f083">

<br /><br />

## Copy the request.xml:

Link: https://spring.io/guides/gs/producing-web-service

<br />

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/"
				  xmlns:gs="http://spring.io/guides/gs-producing-web-service">
   <soapenv:Header/>
   <soapenv:Body>
      <gs:getCountryRequest>
         <gs:name>Spain</gs:name>
      </gs:getCountryRequest>
   </soapenv:Body>
</soapenv:Envelope>
```

<br />

## Paste them to the SOAP:

Get 404:

<img width="658" alt="Screenshot 2024-12-03 at 11 28 56 PM" src="https://github.com/user-attachments/assets/639c2154-cd33-4318-bea5-53241ba7e250">

<br /><br />

Modify:
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/"
				  xmlns:gs="http://spring.io/guides/producingwebservice">
   <soapenv:Header/>
   <soapenv:Body>
      <gs:getCountryRequest>
         <gs:name>Spain</gs:name>
      </gs:getCountryRequest>
   </soapenv:Body>
</soapenv:Envelope>
```

<br />

Run again:

<img width="1039" alt="Screenshot 2024-12-03 at 11 30 03 PM" src="https://github.com/user-attachments/assets/37f5d114-85b5-4936-bf20-072f33d2b0a0">





