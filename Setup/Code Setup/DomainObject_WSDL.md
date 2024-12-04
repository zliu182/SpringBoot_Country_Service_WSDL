## Generate Domain Objects Based on a WSDL

Link: https://spring.io/guides/gs/consuming-web-service

The interface to a SOAP web service is captured in WSDL. JAXB provides a way to generate Java classes from WSDL (or rather, the XSD contained in the `<Types/>` section of the WSDL). 

Find the WSDL for the country service at: http://localhost:8080/ws/countries.wsdl

<br/>

Update this part of file in the `pom.xml`:

```xml
<plugin>
	<groupId>com.sun.xml.ws</groupId>
	<artifactId>jaxws-maven-plugin</artifactId>
	<version>3.0.0</version>
	<executions>
		<execution>
			<goals>
				<goal>wsimport</goal>
			</goals>
		</execution>
	</executions>
	<configuration>
		<packageName>com.example.consumingwebservice.wsdl</packageName>
		<wsdlUrls>
			<wsdlUrl>http://localhost:8080/ws/countries.wsdl</wsdlUrl>
		</wsdlUrls>
		<sourceDestDir>${sourcesDir}</sourceDestDir>
		<destDir>${classesDir}</destDir>
		<extension>true</extension>
	</configuration>
</plugin>
```
