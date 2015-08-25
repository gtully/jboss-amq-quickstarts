helloworld-jms-amqp: Helloworld JMS Example
======================
Author: AMQ Team  
Level: Beginner  
Technologies: JMS, AMQP
Summary: The `helloworld-jms-amqp` quickstart demonstrates the use of the Java Messaging Service API with AMQP and JBoss A-MQ.
Target Product: JBoss A-MQ  
Source: <https://github.com/jboss-developer/jboss-amq-quickstarts/>  

What is it?
-----------

The `helloworld-jms-amqp` quickstart demonstrates the use of the JMS API with AMQP and Red Hat JBoss A-MQ.

This quickstart has no code! It reuses the code from the `helloworld-jms` quickstart. 
It contains a single jndi properties file that directs the InitialContext lookup in the code from the
'helloworld-jms' example to use the QPID JMS ConnectionFactory and the AMQP transport.
It is proof that the JMS APIs are protocol agnostic. 

Note the pom.xml dependency on the `helloworld-jms` quickstart jar. Be sure to `mvn install` the helloworld-jms quick start before attempting this one.

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
2. The following shows the command line to start the server in the foreground with a command shell.

        For Linux:   AMQ_HOME/bin/amq
        For Windows: AMQ_HOME\bin\amq

3. Verify the AMQP protocol listener is active on JBoss A-MQ. From the A-MQ shell type the following command:

        activemq:query -QBroker=* --view TransportConnectors

If port 5672 is not in the list proceed to [Add AMQP transport to A-MQ]


Add AMQP transport to A-MQ
--------------------------
Using a text editor you will modify the JBoss A-MQ xml configuration to add an AMQP transport connector.

1. Open a command prompt and navigate to the root of the JBoss A-MQ installation.

2. Open AMQ_HOME/etc/activemq.xml

3. Navigate to the element called <transportConnectors>, note the existing transportConnector named openwire.
   Add a new transportConnector using the amqp protocol scheme and using a name of "amqp" as follows.

        <transportConnectors>
            <transportConnector name="openwire" uri="tcp://0.0.0.0:0?maximumConnections=1000"/>
            <transportConnector name="amqp" uri="amqp://0.0.0.0:5672"/>
        </transportConnectors>

4. Restart JBoss A-MQ
   Note: a simple way to trigger an automatic restart is to 'UNIX touch' the file AMQ_HOME/etc/io.fabric8.mq.fabric.server-broker.cfg

5. Verify the AMQP protocol listener is active on JBoss A-MQ.
   From the A-MQ shell type the following command:

        activemq:query -QBroker=* --view TransportConnectors



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

2. Install the helloworld-jms quickstart. This is necessary because this quickstart has no code, just configuration.
   Open a command prompt and navigate to the root of the `helloworld-jms` quickstart directory:

        cd PATH_TO_QUICKSTARTS/helloworld-jms
        
3. Type the following command to install the required dependency in your local maven repository.        
        
        mvn install

4. Package this quickstart. Navigate back to the root of the `helloworld-jms-amqp` quickstart directory:
        
        cd PATH_TO_QUICKSTARTS/helloworld-jms-amqp

5. Type the following command to package the jndi.properties file.        

        mvn clean package

6. Type the following command to execute the quickstart:

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


 
