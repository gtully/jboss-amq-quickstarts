helloworld-jms: Helloworld JMS Example
======================
Author: AMQ Team  
Level: Beginner  
Technologies: JMS  
Summary: The `helloworld-jms` quickstart demonstrates the use of the Java Messaging Service API with JBoss A-MQ.  
Target Product: JBoss A-MQ  
Source: <https://github.com/jboss-developer/jboss-amq-quickstarts/>  

What is it?
-----------

The `helloworld-jms` quickstart demonstrates the use of the JMS API with Red Hat JBoss A-MQ.

It contains a single main line with a message producer that sends a message to a queue named `queue` and a consumer that receives that message.

System requirements
-------------------

The application this project produces is designed to be run against Red Hat JBoss A-MQ 6.2 or later. 

All you need to build this project is Java 8.0 (Java SDK 1.8) or later and Maven 3.1.1 or later. 


Use of AMQ_HOME
---------------

In the following instructions, replace `AMQ_HOME` with the actual path to your JBoss A-MQ installation.   


Start the JBoss A-MQ Server
--------------------------

1. Open a command prompt and navigate to the root of the JBoss A-MQ directory.
2. The following shows the command line to start the server in the foregound with a command shell. 

        For Linux:   AMQ_HOME/bin/amq
        For Windows: AMQ_HOME\bin\amq


Add an Application User
-----------------------

This quickstart uses secured interfaces and requires that you create the following application user to allow access to the A-MQ server. 

| **UserName** | **Password** | **Roles** |
|:-------------|:-------------|:----------|
| admin        | admin        | admin     |

To add the application user, in the A-MQ shell, type the following command:

        amq:create-admin-user --new-user admin --new-user-password admin --new-user-role admin


Build and Execute the Quickstart
-------------------------

To run the quickstart from the command line:

1. Make sure you have started the JBoss A-MQ server. See the instructions in the previous section.

2. Open a command prompt and navigate to the root of the helloworld-jms quickstart directory:

        cd PATH_TO_QUICKSTARTS/helloworld-jms

3. Type the following command to compile the quickstart:

        mvn clean package

4. Type the following command to execute the quickstart:

        mvn exec:java

 
Investigate the Console Output
-------------------------

If the Maven command is successful, you will see output similar to this:
        Hello world!
        
Investigate the destination statistics on the JBoss A-MQ console
-------------------------
Using the JBoss A-MQ shell you can note the enqueue and dequeue count using the destination statistics (dstat) command. 
In the A-MQ shell, type the following command:

        activemq:dstat queues


Run the Quickstart in Red Hat JBoss Developer Studio or Eclipse
-------------------------------------
You can also run the quickstarts from Eclipse using JBoss tools. For general information about how to import, build and deploy a quickstart, see [Use JBoss Developer Studio or Eclipse to Run the Quickstarts](https://github.com/jboss-developer/jboss-developer-shared-resources/blob/master/guides/USE_JBDS.md#use-jboss-developer-studio-or-eclipse-to-run-the-quickstarts) 

1. In JBoss Developer Studio, right-click and choose `Run As` --> `Java Application`.  In the `Select Java Application` window, choose `HellowWorld - org.jboss.amq.quickstarts.jms` and click `OK`. The client output displays in the `Console` window.
The output messages appear in the `Console` window.

Debug the Application
------------------------------------

If you want to debug the source code of any library in the project, run the following command to pull the source into your local repository. The IDE should then detect it.

        mvn dependency:sources


 
