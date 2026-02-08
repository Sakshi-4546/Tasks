# AWS Assignment

## Task 1: Application

- Simple frontend + backend app

- Use one database (MySQL/MongoDB/Influx DB)

- App must connect to the database successfully

## Objective

 Using docker build a simple application with a frontend and backend that successfully connects to a database (MySQL) to store and retrieve data.

## Steps :-

- Launch one instance and inside instance create following structure

![](./Img/Task%201structure.png)

- Write code inside all files and run docker compose file using following command:-

  command:

         docker-compose up -d

![](./Img/Task%201run%20docker-compose%20file.png)         

- Access app using instance public ip
- Fill the form and click Submit

![](./Img/Task1access%20app%20using%20ip.png)

- frontend successfully connected to backend and data stored in database

![](./Img/Task%201record%20insertrd%20in%20database.png)

- Go inside db container 

  command:

         docker exec -it <db-container-name> bin/bash


![](./Img/Task1go%20inside%20db%20container.png)

- Check record inserted in database

![](./Img/Task%201check%20record.png)
           
## Conclusion :- 

The Dockerized application with a frontend, backend, and MySQL database was successfully implemented. The frontend communicates with the backend, and data is stored and retrieved from the database as expected. This demonstrates a simple full-stack application running in containers, making it easy to deploy and manage.




---

## Task 2: Docker
- Create Docker file(s)

- Run app using Docker containers

- Expose required ports

- Ensure containers auto-start on reboot

## Objective:

This task focuses on containerizing the application using Docker, exposing required ports, and ensuring containers auto-start on reboot.


## Steps: 
- Launch Ec2 Instance (Ubuntu): SSH to local host and install docker

  command:

         sudo apt update -y

         sudo apt-get install docker.io -y
- Create a dockerfile:

![](./Img/Task%202create%20docker%20file.png)

- Add index.html page

![](./Img/Task%202index.html.png)

  A dockerfile was created to define the application and dependencies.


![](./Img/Task%202dockerfile.png)

- Build the Docker image using the Dockerfile:

![](./Img/Task%202%20build%20image.png)

- Expose Required Port:
  
  Port 80 was exposed to allow access from a browser.

![](./Img/Task%20add%20port%20in%20sg.png)

- Run application using Docker container:
  
  Start the application inside a Docker container using the built image

- Enable Auto-Start on System Reboot:
  
  The --restart=always flag ensures the container restarts automatically after a system reboot
   
   command :

      docker run -d --name nginx_container -p 80:80 --restart=always nginx-app  

![](./Img/Task%202run%20container.png)

## Conclusion:
   
   This task successfully demonstrates containerization of an application using Docker. The application runs in a container, is accessible via the exposed port, and is configured to automatically start on system reboot.

   ---

## Task 3: AWS EC2 Deployment

- Launch EC2 (cost-optimized: t2.micro / t3.micro)

- Install Docker

- Run containers on EC2

## Objective:
The objective of this task is to provision a cost-efficient EC2 instance on AWS, install Docker, and deploy the containerized application, ensuring it runs reliably and is accessible externally..

## Steps:

- Launch EC2 Instance:
  Choose a cost-optimized instance type (t2.micro / t3.micro).

![](./Img/Task%203launch%20ec2.png)

- Connect to EC2 Instance

![](./Img/Task%203login.png)

- Update packages
command:

         sudo apt update -y


![](./Img/Task%203update%20package.png)

- Install Docker on EC2  
  command:

      sudo apt-get install docker.io -y
      sudo systemctl enable docker
      sudo systemctl start docker

![](./Img/Task%203install%20docker.png)

- Pull docker image

![](./Img/Task%203pull%20image.png)

- Create and run Container on EC2

![](./Img/Task%203create%20container.png)  

- Access Application via Public IP:
  
  The application was accessed using the EC2 Public IP


![](./Img/Task%203access%20on%20browser.png)

## Conclusion:
   
   This task demonstrates the successful deployment of a Dockerized application on AWS EC2 using a cost-effective instance. The application runs reliably in a container and is accessible externally via the EC2 Public IP.

 ---

## Task 4: Application Access

- Access app via:

- Elastic IP or

- EC2 Public IP

- (Optional) Route 53 domain

## Objective:

Provide secure and reliable access to the deployed application using AWS networking option such as EC2 Public IP, Elastic IP.

## Steps:

- Launch EC2 Instance:

![](./Img/Task%204launch%20ec2.png)

- Connect to instance and inside the instance install nginx 

![](./Img/Task%204install%20nginx%20on%20ec2.png)

- Add port 80 to the instance security group to allow HTTP traffic

![](./Img/Task%20add%20port%20in%20sg.png)

- Access Using EC2 Public IP

![](./Img/Task%204acces%20app%20using%20public%20ip.png)

- Access Using Elastic IP
  
  - Allocated an Elastic IP from AWS EC2 console
  - Associated Elastic IP with running EC2 instance
  

![](./Img/Task%204create%20elastic%20ip.png)

- Verified application accessibility using Elastic IP

![](./Img/Task%204access%20using%20elastic%20ip.png)


## Conclusion:

  This task successfully enables multiple methods to access the deployed application, ensuring flexibility, reliability, and production-ready networking using AWS best practices.

  ---

## Task 5: Load Balancer & auto scaling

- Configure Application Load Balancer (ALB)

- Attach Auto Scaling Group (ASG)

- Scale based on CPU utilization

## Objective
This task focuses on configuring ALB and Auto Scaling to distribute traffic and automatically scale instances based on CPU load.

## Steps:

- Create Application Load Balancer (ALB)

![](./Img/Task%205ALB.png)

- Create launch template 

   A launch template was created to define the instance configuration for the Auto Scaling Group.

![](./Img/Task%205create%20one%20launch%20template.png)

- Create Auto Scaling group and attach template    

   The ASG manages EC2 instances dynamically based on load, attaching the launch template for configuration.

![](./Img/Task%205create%20ASG%20and%20attach%20launch%20template.png)

![](./Img/Task%206AsG%20created.png)

- Scale Up Instances  
   The ASG launched 2 instances initially to handle incoming traffic.

![](./Img/Task%205ASG%20launch%20two%20server.png)

- Scale Down Instances  
   When traffic decreases, the ASG automatically terminates one instance to optimize cost.

![](./Img/Task%205ASG%20remove%201.png)

- Check into ASG  
   Checked the ASG and confirmed dynamic scaling works as expected.

![](./Img/Task%205proof.png)

## Conclusion:
This task successfully demonstrates the use of an Application Load Balancer and Auto Scaling Group to manage traffic and dynamically scale EC2 instances based on CPU utilization, ensuring availability and cost-efficiency



## Task 6: Cost Optimization

- Use free-tier eligible instances

- Minimal resources

- Auto Scaling to avoid over-provisioning

## Objective
Reduce AWS costs by using free-tier resources, minimal infrastructure, and Auto Scaling to ensure efficient performance without over-provisioning.

## Steps:

 - Use Free-Tier Eligible Instances:
   
   Use AWS resources that are included in the free tier

![](./Img/Task%206launch%20free%20tier%20instance.png)

![](./Img/Task%206ec2%20details.png)

- Create Auto Scaling Group (ASG)   
   Configured an ASG to dynamically manage EC2 instances based on traffic


![](./Img/Task%206create%20auto%20scaling%20group.png)

- Auto Scaling to avoid Over-Provisioning:
    
  The ASG automatically adjusts the number of instances based on traffic, ensuring minimal resource usage and cost-efficiency.

![](./Img/Task%206AsG%20created.png)

- ASG Launched Instances to Handle Load

![](./Img/Task%206ASG%20launch%202%20instance.png)
   
-ASG Scaled Down When Traffic Decreased

![](./Img/Task%206Asg%20remove%20instance.png)

- Verified ASG Instances and Scaling Behavior

![](./Img/Task%206check.png)

## Conclusion:

This task successfully demonstrates cost optimization in AWS by using free-tier eligible EC2 instances and implementing Auto Scaling. The ASG automatically scales the number of instances based on traffic demand, ensuring minimal resource usage while maintaining performance.

---

## Task 7: Troubleshooting (Explain) 
- App not accessible

- Container running but port not reachable

- ALB health check failures

## Steps:
 ### - App not accessible
 
 1. Check EC2 Instance Status:
    
    In EC2 - Instances - ensure system status check and instance status check.
    

 2. Verify Security Group Rules:
    
    Check Inbound Rules - Ensure required ports are open (HTTP:80)
    Source should be: 0.0.0.0/0 (All IP'S)

 3. Check Application Process:
    
    SSH into EC2
    Verify app or container is running or not
  
###  - Container running but port not reachable

  1. Verify Port Mapping:

     Check docker port mapping

  2. Check Application Port Inside Container

     - Inside the Container

       cmd: docker exec -it <cont_id>    

     - Verify app is listening on correct port:

       cmd: netstat -tuln  

  3. Verified dockerfile Configuration

     Ensure Dockerfile has correct port          
     
    Run container using correct port, image name:
    cmd: docker run -p 80:3000 image_name  

### - ALB health check failures

  1. Check target group health
     
     Go to target groups - Target

     If status shows Unhealthy, click reason

   2. Verify health Check Path

   3. Verify target Group port

      Ensure target group port matches app port:

        If app run on 3000

        Target group must also use 3000     

  4. Check security group for ALB

## Conclusion:

  Application access issues can be resolved by checking EC2 health, security group rules, Docker port mappings, and ALB health check configurations. A systematic troubleshooting approach ensures reliable connectivity and stable application deployment.
