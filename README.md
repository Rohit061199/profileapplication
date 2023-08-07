# devopsproject-PAAS & SAAS
This is a PAAS project to host an application using AWS Coud. In the IAAS version, VMs are launched to host different services i.e. RabbitMQ, Memcache, Maria DB &amp; Tomcat 9.

However, using PAAS and SAAS services, we do not provision any infrastructure ourselves. Instead, we use the services provided by the cloud provider (AWS in this case).

1. AmazonMQ for RabbitMQ ->Used for Messaging Que
2. Elasticache for Memcache -> To cache
3. RDS for MySQL DB -> Used for Database operations

Below is the architecture followed for the application:

![image](https://github.com/Rohit061199/profileapplication/assets/73810251/5681d798-2f9b-4caf-a867-7aa61f78c6ab)

Separate Security group is created for the above services( mentioned as backend services here on) and rules are established to fecilitate communication between the services.

Elastic Beanstalk is used as the gateway to deploy the application. Once the Beanstalk is deployed for the application, the artifacts are built using VS code and are deployed in the beanstalk.

Using beanstalk relieves us from the burden of provisioning the infrastructure ourselves. Once our artifacts are deployed, we can access the web application using the URL.

In the DNS, a new CNAME record is created with the beanstalk's endpoint for SSL secure connection

For Autoscaling, a new launch configuration is created and an Autoscaling group is set up as per the load by Elastic Beanstalk itself.

Source Code can be downloaded from: https://github.com/hkhcoder/vprofile-project/
