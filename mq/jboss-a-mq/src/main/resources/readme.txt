JBoss A-MQ
----------

Configuration
-------------
The default broker is defined in: 
 ./etc/org.fusesource.mq.fabric.server-default.cfg
The xml configuration is:
 ./etc/activemq.xml

Security Prerequisites
----------------------
By default, no users are defined for the container. You can run the container in the
foreground in this case, but you will not be able to access the container remotely and you will
not be able to run it in the background.

To enable remote access to the container, you must create at least one user in
the ./etc/users.properties file.
It is recommended that you create at least one user with the admin role by adding
a line with the following syntax:

<Username>=<Password>,admin

The admin role grants full administration privileges to the user.

To make the ActiveMQ shell command line tools accessible, add the following lines to the
./etc/system.properties file, using the credentials of one of the users from the
users.properties file:

activemq.jmx.user=<Username>
activemq.jmx.password=<Password>

To make the ActiveMQ Web console accessible, add the following lines to the
./etc/org.apache.activemq.webconsole.cfg file, using the credentials of one of the users from the
users.properties file:

webconsole.jmx.user=<Username>
webconsole.jmx.password=<Password>
webconsole.jms.user=<Username>
webconsole.jms.password=<Password>


Quick Start
-----------
To start JBoss A-MQ in the background, type 'bin/start' on Linux/Unix or 'bin\start.bat' on Windows.

Note: Be sure to use the appropriate username and password in the following examples.
To display the log using the remote console, type:

[Linux/Unix]
    ./bin/client -u <Username> -p <Password> log:display
[Windows]
    .\bin\client.bat -u <Username> -p <Password> log:display

To display the current broker statistics using the remote console, type:
   
[Linux/Unix]
    ./bin/client -u <Username> -p <Password> activemq:bstat
[Windows]
    .\bin\client.bat -u <Username> -p <Password> activemq:bstat

To validate the installation with a simple JMS producer and consumer, type:

    java -jar extras/mq-client.jar producer --user <Username> --password <Password>
    java -jar extras/mq-client.jar consumer --user <Username> --password <Password>

View the webconsole at http://localhost:8181/activemqweb

Documentation
-------------
You can find documentation online at:
http://www.redhat.com/products/jbossenterprisemiddleware/amq/

