## Add the Spring-WS dependency

The project needs to include `spring-ws-core` and `wsdl4j` as dependencies in your build file.

The following example shows the changes you need to make to the `pom.xml` file if you use Maven:

<br />

```xml
<dependency>
	<groupId>wsdl4j</groupId>
	<artifactId>wsdl4j</artifactId>
</dependency>
```

<br />

## Create an XML Schema to Define the Domain

The web service domain is defined in an XML schema file (XSD) that Spring-WS will automatically export as a WSDL.

Create an XSD file with operations to return a country’s `name`, `population`, `capital`, and `currency`. 

<br />

Create a file named `countries.xsd` in such path: `src/main/resources/countries.xsd)`

```xsd
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:tns="http://spring.io/guides/gs-producing-web-service"
           targetNamespace="http://spring.io/guides/gs-producing-web-service" elementFormDefault="qualified">

    <xs:element name="getCountryRequest">
        <xs:complexType>
            <xs:sequence>
                <xs:element name="name" type="xs:string"/>
            </xs:sequence>
        </xs:complexType>
    </xs:element>

    <xs:element name="getCountryResponse">
        <xs:complexType>
            <xs:sequence>
                <xs:element name="country" type="tns:country"/>
            </xs:sequence>
        </xs:complexType>
    </xs:element>

    <xs:complexType name="country">
        <xs:sequence>
            <xs:element name="name" type="xs:string"/>
            <xs:element name="population" type="xs:int"/>
            <xs:element name="capital" type="xs:string"/>
            <xs:element name="currency" type="tns:currency"/>
        </xs:sequence>
    </xs:complexType>

    <xs:simpleType name="currency">
        <xs:restriction base="xs:string">
            <xs:enumeration value="GBP"/>
            <xs:enumeration value="EUR"/>
            <xs:enumeration value="PLN"/>
        </xs:restriction>
    </xs:simpleType>
</xs:schema>
```

<br />

## Generate Domain Classes Based on an XML Schema

Update these code into the `pom.xml` file:

```xml
<plugin>
	<groupId>org.codehaus.mojo</groupId>
	<artifactId>jaxb2-maven-plugin</artifactId>
	<version>3.1.0</version>
	<executions>
		<execution>
			<id>xjc</id>
			<goals>
				<goal>xjc</goal>
			</goals>
		</execution>
	</executions>
	<configuration>
		<sources>
			<source>${project.basedir}/src/main/resources/countries.xsd</source>
		</sources>
	</configuration>
</plugin>
```

<br />

Synchronize the Java class/configuration:

<img width="451" alt="Screenshot 2024-12-03 at 8 38 36 PM" src="https://github.com/user-attachments/assets/f9042bdf-858b-430c-ba06-a4bf0b43542c">










