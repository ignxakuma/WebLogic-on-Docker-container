# WebLogic-on-Docker-container
Running webLogic App server in docker container in easiest way possible

REQUIREMENTS:
  1. Account on https://container-registry.oracle.com/ with Middleware and weblogic container license accepted.
  2. Docker installed and running and tested.
  
Steps:
  1. Login to oracle registry with docker using your oracle email and password.
    $ docker login container-registry.oracle.com
    Enter your email and password, you will get login succeed message.
   
  2. Create new directory on host operating system to keep the domain.properties file with weblogic admin credentials and to mount that directory to container.
      for eg.- /opt/docker/weblogic
        create file name "domain.properties" in it with below content
        username=weblogic
        password=weblogic123
        
  3. Now to run the weblogic contaioner by pulling the image from oracle registry
  
      $ docker container run -d -p 7000:7001 -p 9001:9002 -it –-name WlsContNode1 -v /opt/docker/weblogic:/u01/oracle/properties container-registry.oracle.com/middleware/weblogic:12.2.1.4-ol8-230119
      
      NOTE: You should have accepted the license for weblogic in middleware using oracle container registry site from browser before running the container.
  4. Once you get server state changed to running, check the console using public IP of server or localhost.
  eg. - https://localhost:9001/console
  
  login with the given username and password
