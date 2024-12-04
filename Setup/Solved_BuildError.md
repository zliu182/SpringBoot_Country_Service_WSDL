## Run the command to build:

```shell
./mvnw spring-boot:run
```

<br />

## Display the error message:

```
[INFO] Scanning for projects...
[ERROR] [ERROR] Some problems were encountered while processing the POMs:
[ERROR] Malformed POM /Users/vivianliu/Desktop/Terms/Autumn_2024/WSA_500/Week_10/producingwebservice/producingwebservice/pom.xml: Unrecognised tag: 'plugin' (position: START_TAG seen ...</plugins>\n\t\t<plugin>... @64:11)  @ /Users/vivianliu/Desktop/Terms/Autumn_2024/WSA_500/Week_10/producingwebservice/producingwebservice/pom.xml, line 64, column 11
 @ 
[ERROR] The build could not read 1 project -> [Help 1]
[ERROR]   
[ERROR]   The project com.example:producingwebservice:0.0.1-SNAPSHOT (/Users/vivianliu/Desktop/Terms/Autumn_2024/WSA_500/Week_10/producingwebservice/producingwebservice/pom.xml) has 1 error
[ERROR]     Malformed POM /Users/vivianliu/Desktop/Terms/Autumn_2024/WSA_500/Week_10/producingwebservice/producingwebservice/pom.xml: Unrecognised tag: 'plugin' (position: START_TAG seen ...</plugins>\n\t\t<plugin>... @64:11)  @ /Users/vivianliu/Desktop/Terms/Autumn_2024/WSA_500/Week_10/producingwebservice/producingwebservice/pom.xml, line 64, column 11 -> [Help 2]
[ERROR] 
[ERROR] To see the full stack trace of the errors, re-run Maven with the -e switch.
[ERROR] Re-run Maven using the -X switch to enable full debug logging.
[ERROR] 
[ERROR] For more information about the errors and possible solutions, please read the following articles:
[ERROR] [Help 1] http://cwiki.apache.org/confluence/display/MAVEN/ProjectBuildingException
[ERROR] [Help 2] http://cwiki.apache.org/confluence/display/MAVEN/ModelParseException
```

<br />

## Why happened?

The compile error is likely due to the placement and syntax issues in your `pom.xml`, especially around the JAXB plugin.

```xml
<build>
  <plugins>
    <plugin>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-maven-plugin</artifactId>
    </plugin>
  </plugins>
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
</build>
```

<br />

## Corrected `pom.xml`
```xml
<?xml version="1.0" encoding="UTF-8" ?>
<project
  xmlns="http://maven.apache.org/POM/4.0.0"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>3.4.0</version>
		<relativePath /> <!-- lookup parent from repository -->
	</parent>
	<groupId>com.example</groupId>
	<artifactId>producingwebservice</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<name>producingwebservice</name>
	<description>Demo project for Spring Boot</description>
	<url />
	<licenses>
		<license />
	</licenses>
	<developers>
		<developer />
	</developers>
	<scm>
		<connection />
		<developerConnection />
		<tag />
		<url />
	</scm>
	<properties>
		<java.version>17</java.version>
	</properties>
	<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web-services</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
		</dependency>
		<dependency>
			<groupId>wsdl4j</groupId>
			<artifactId>wsdl4j</artifactId>
		</dependency>
	</dependencies>

	<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
			</plugin>
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
		</plugins>
	</build>
</project>
```
