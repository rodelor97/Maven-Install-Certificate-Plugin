# Maven-Install-Certificate-Plugin
A plugin to create a java JKS certificate for use in Tomcat

Usage:



<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<project xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://maven.apache.org/POM/4.0.0"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
...    
	<plugin>
		<groupId>org.rodelor.maven.plugin</groupId>
		<artifactId>installcert-maven-plugin</artifactId>
		<version>0.0.14</version>
		<configuration>
			<goalPrefix>installcert</goalPrefix>
			<certdomainhost>${remote.hostname}</certdomainhost>
			<certdomainport>${remote.port}</certdomainport>
			<certpassword>${sslstore.password}</certpassword>
			<certalias>${sslstore.alias}</certalias>
			<certstorelocation>${sslstore.location}</certstorelocation>
		</configuration>
	</plugin>
...             
    <profiles>        
        <profile>
            <id>server1234_cert</id>
            <properties>
            	<remote.hostname>server1234</remote.hostname>
            	<remote.port>443</remote.port>
            	<sslstore.password>changeit</sslstore.password>
                <remote.profile>dev-server</remote.profile>
                <remote.protocol>https</remote.protocol>
                <sslstore.alias>server1234</sslstore.alias>
                <sslstore.location>${basedir}/sslstore/jssecerts</sslstore.location>
                
                
            </properties>
        </profile>
    </profiles>
</project>

Maven call:
mvn -P server1234_cert installcert