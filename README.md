Red Hat JBoss A-MQ Quickstarts
==============================
Summary: The quickstarts demonstrate Red Hat JBoss A-MQ. They provide small, specific, working examples that can be used as a reference for your own project.  

Introduction
------------

These quickstarts use Red Hat JBoss A-MQ 6 or later. 

Be sure to read this entire document before you attempt to work with the quickstarts. It contains the following information:

* [Available Quickstarts](#available-quickstarts): List of the available quickstarts and details about each one.

* [Suggested Approach to the Quickstarts](#suggested-approach-to-the-quickstarts): A suggested approach on how to work with the quickstarts.

* [System Requirements](#system-requirements): List of software required to run the quickstarts.

* [Configure Maven](https://github.com/jboss-developer/jboss-developer-shared-resources/blob/master/guides/CONFIGURE_MAVEN_JBOSS_EAP7.md#configure-maven-to-build-and-deploy-the-quickstarts): How to configure the Maven repository for use by the quickstarts.

Use of AMQ_HOME Variable
------------------------
The quickstart README files use the *replaceable* value `AMQ_HOME` to denote the path to the JBoss A-MQ installation. When you encounter this value in a README file, be sure to replace it with the actual path to your JBoss A-MQ installation. 


Suggested Approach to the Quickstarts
-------------------------------------

We suggest you approach the quickstarts as follows:

* Regardless of your level of expertise, we suggest you start with the **helloworld-jms** quickstart. It is the simplest example and is an easy way to prove your server is configured and started correctly.
* If you are a beginner or new to JBoss, start with the quickstarts labeled **Beginner**, then try those marked as **Intermediate**. When you are comfortable with those, move on to the **Advanced** quickstarts.


System Requirements
-------------------

The applications these projects produce are designed to be run against Red Hat JBoss A-MQ 6.2 or later. 

All you need to build these projects is Java 8.0 (Java SDK 1.8) or later and Maven 3.1.1 or later.

You can also use [JBoss Developer Studio or Eclipse](#use-jboss-developer-studio-or-eclipse-to-run-the-quickstarts) to run the quickstarts. 


Run the Quickstarts
-------------------

The root folder of each individual quickstart contains a README file with specific details on how to build and run the example. In most cases you do the following:

* [Start the JBoss A-MQ Server](#start-the-jboss-a-mq-server)
* [Build the quickstarts](#build-the-quickstarts)

           
### Start the JBoss A-MQ Server

1. Open a command prompt and navigate to the root of the JBoss A-MQ directory.
2. The following shows the command line to start the server in the foregound with a command shell.

        For Linux:   AMQ_HOME/bin/amq
        For Windows: AMQ_HOME\bin\amq


### Build the Quickstarts

See the README file in each individual quickstart folder for specific details and information on how to run and access the example. 

In most cases, you can use the following steps to build the application to test for compile errors. See the specific quickstart README file for complete details.

1. Open a command prompt and navigate to the root directory of the quickstart you want to build.
2. Use this command to build the archive.

            mvn clean package

3. Use this command to execute the example.

            mvn java:exec


Use JBoss Developer Studio or Eclipse to Run the Quickstarts
------------------------------------------------------------

You can also run the quickstarts from Eclipse using JBoss tools. For more information on how to set up Maven and the JBoss tools, see [Get Started with JBoss Developer Studio](http://www.jboss.org/products/devstudio/get-started/ "Get Started with JBoss Developer Studio").


