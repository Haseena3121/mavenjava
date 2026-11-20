# Maven Java Project

This project is used for Jenkins CI/CD and GitHub Webhook testing.

## Jenkins CI Test

This change is being used to test automatic Jenkins builds through a GitHub webhook.
# Maven Java Project





Q1.Docker Compose – Online Boutique Store (25 Marks)
An online boutique store wants to launch an e-commerce website. The application consists of a mysql backend and an tomcat web server. Create a Docker Compose file to run both applications in separate containers, exposing the mysql backend on port 3306 and tomcat on port 8080.
Tasks:
1.	Create a Docker Compose YAML file.
2.	Configure appropriate port mappings and persistent volumes.
3.	Start both containers using docker compose
4.	Verify running containers using docker compose command.
5.	Access the tomcat server through a web browser.
Scenario based Questions:
1.	Your Online Boutique Store application runs on Tomcat using port 8080, and MySQL uses port 3306. You want to access Tomcat through the browser and allow the application to communicate with MySQL. How do you configure port mappings and a custom Docker network in Docker Compose?
2.	You are running an Online Boutique Store using Tomcat and MySQL containers. After removing and recreating the MySQL container, you notice that all customer registration and product details are lost. Why does this happen, and how can you configure Docker Compose volumes to preserve database data?
3.	Your Online Boutique Store is deployed using Tomcat and MySQL containers. When you access the application through http://localhost:8080, you receive a Connection Refused error. How do you identify whether the Tomcat container is running, check its logs, verify port mappings, troubleshoot the database connection, and safely stop and remove the containers?
Q2. Jenkins Pipeline for a Maven Web Project with web hooks	[25 Marks]	
The Online Boutique Store development team frequently pushes code changes to GitHub. The company wants to trigger the Jenkins Scripted Pipeline automatically whenever developers commit and push changes to the repository. Configure a GitHub webhook and the appropriate Jenkins build trigger to automatically execute the pipeline. The pipeline should perform GitHub clone, Maven clean, build, test, and package operations.
Tasks:

1. Clone Git Hub repository.( https://github.com/haleema91/LAB-INTERNAL-II-OBS.git)

2. Configure Tomcat web server.
3. Deploy the application on the Web Server
4. Create the Pipeline View using Jenkins and show how code changes triggers jenkins using webhooks.
Scenario based Questions:
1.	Your project manager asks you to remove previously generated build files before building the Online Boutique Store Maven Java Web Application. Which Maven command should you use in the pipeline?
2.	Your Online Boutique Store source code is available in a private GitHub repository. Where should you provide the repository URL in the Jenkins pipeline?
3.	Your Online Boutique Store application is building successfully, but the WAR file is not generated. Which Maven command should you execute in pipeline code?

Q3. Kubernetes – Container Deployment and Auto Scaling and monitoring 
                                                                                                 [25 MARKS]
During festival seasons, discount sales, and special promotional offers, thousands of customers access the Online Boutique Store simultaneously to browse products, check prices, and place orders. The company wants to deploy multiple application replicas using Kubernetes to handle increased customer traffic and ensure automatic recovery when application containers fail and monitor application availability using Nagios.
Tasks:
1.	Start a Kubernetes cluster using Minikube.
2.	Create a Kubernetes Deployment nginx with two replicas.
3.	Expose the nginx using a Kubernetes Service of type NodePort at port 7070.
4.	Scale the deployment from two to five replicas to handle increased customer traffic.
5.	Verify the deployment, pods, services using appropriate Kubernetes commands.
6.	Install and configure Nagios Core using Docker to monitor the Online Boutique Store application.

Scenario based Questions:
1.	Your Online Boutique Store is running successfully inside Minikube, but customers cannot access it through a web browser. How will you expose the application externally using a NodePort Service and access it through the Minikube service URL?The boutique store administrator wants to confirm whether Nagios is running properly and monitoring the application server. Which commands will you execute to verify Nagios service status and configuration?
2.	During a festival sale, you scale the Online Boutique Store deployment from two to five replicas. However, some Pods remain in the Pending state. What could be the possible reasons, and how would you troubleshoot them?

Q4. AWS EC2 Deployment – Online Boutique Store     [25 Marks]
An online boutique company wants to launch its website on AWS. Create an Ubuntu EC2 instance, connect to it using SSH, install Docker, and deploy the website's index.html file using an Nginx Docker container. Verify the website using the EC2 public IPv4 address.
Task: Deploy the online boutique store on EC2 instance.
Scenario based Questions:
1.	The Online Boutique Store administrator has successfully launched an Ubuntu EC2 instance but needs to access it remotely to configure the website. How will you connect to the EC2 instance from your local machine using an SSH key pair? What steps will you follow if the SSH connection fails?
2.	An online boutique company wants to launch its shopping website on AWS. The administrator needs a Linux server to host the website. How will you launch an Ubuntu EC2 instance, select an appropriate instance type, configure a key pair, and create a Security Group to allow SSH and HTTP traffic?
3.	The Online Boutique Store Docker container is running successfully on the AWS EC2 instance, but customers are unable to access the website through a browser. How will you identify the network issue, configure the EC2 Security Group to allow inbound HTTP traffic on port 80, and verify the website using the EC2 public IPv4 address?
		
		
		
		
		
		







































;






Q3. Kubernetes – Container Deployment, Auto Scaling and Monitoring (25 Marks)
1. Start a Kubernetes cluster using Minikube
Step 1: Start Minikube
Open the terminal and execute:
bash
minikube start
Step 2: Verify the cluster status
bash
minikube status
Step 3: Check the Kubernetes nodes
bash
kubectl get nodes
Expected output:
text
NAME       STATUS   ROLES           AGE   VERSION
minikube   Ready    control-plane   1m    v1.xx.x
2. Create a Kubernetes Deployment with two replicas
Create a deployment named nginx with two replicas.
bash
kubectl create deployment nginx --image=nginx --replicas=2
Verify the deployment:
bash
kubectl get deployments
Expected output:
text
NAME    READY   UP-TO-DATE   AVAILABLE
nginx   2/2     2            2
Check the running Pods:
bash
kubectl get pods
Two Nginx Pods should be displayed with the status Running.
3. Expose Nginx using a NodePort Service at port 7070
Create a NodePort Service:
bash
kubectl expose deployment nginx \
--type=NodePort \
--port=7070 \
--target-port=80
Here:
•	--type=NodePort: Exposes the application outside the cluster.
•	--port=7070: Service port.
•	--target-port=80: Port on which Nginx listens inside the container.
Verify the Service:
bash
kubectl get services
To get the assigned NodePort:
bash
kubectl describe service nginx
The NodePort is automatically assigned from the default NodePort range (30000–32767).
Access the application:
bash
minikube service nginx --url
Copy the generated URL and open it in a web browser.
You should see the Nginx welcome page.
4. Scale the deployment from two to five replicas
During festival sales, customer traffic increases. Kubernetes allows us to increase the number of replicas.
Execute:
bash
kubectl scale deployment nginx --replicas=5
Verify scaling:
bash
kubectl get deployments
Expected output:
text
NAME    READY   UP-TO-DATE   AVAILABLE
nginx   5/5     5            5
Check the Pods:
bash
kubectl get pods
Five Nginx Pods should be running.
Explanation: Scaling increases the number of application instances, helping Kubernetes distribute incoming traffic across multiple Pods through the Service.
5. Verify deployment, Pods and Services
Execute the following Kubernetes commands:
Command	Purpose
kubectl get nodes	Check cluster nodes
kubectl get deployments	Check deployments
kubectl get pods	Check Pod status
kubectl get services	Check Services
kubectl describe deployment nginx	Get deployment details
kubectl describe pods	Get Pod details
kubectl describe service nginx	Get Service details
kubectl get pods -o wide	Display Pod IP addresses and nodes
kubectl logs <pod-name>	View container logs
To continuously monitor Pods:
bash
kubectl get pods -w
6. Install and configure Nagios Core using Docker
Nagios Core is an open-source monitoring tool used to monitor server availability, network services and application health.
 
techtarget.com
Step 1: Verify Docker installation
bash
docker --version
Step 2: Pull a Nagios Docker image
For example, use the Nagios Core image:
bash
docker pull jasonrivers/nagios:latest
Step 3: Run the Nagios container
bash
docker run --name nagios \
-d \
-p 8080:80 \
jasonrivers/nagios:latest
This command:
•	Creates a container named nagios.
•	Runs it in detached mode.
•	Maps host port 8080 to container port 80.
Step 4: Check the Nagios container
bash
docker ps
Step 5: Access the Nagios web interface
Open a browser and enter:
text
http://localhost:8080/nagios
Use the credentials configured by the selected Docker image.
Step 6: Configure application monitoring
Nagios can monitor the availability of the Online Boutique Store using HTTP checks.
For example, add a service configuration:
text
define service {
    use                     generic-service
    host_name               boutique-server
    service_description     Boutique Website
    check_command           check_http
}
Configure the corresponding host and ensure that the HTTP check plugin is installed.
Nagios can monitor:
•	Application availability.
•	HTTP response status.
•	Server availability.
•	CPU and memory utilization (using suitable monitoring plugins).
•	Application downtime.
Step 7: Restart Nagios after configuration changes
bash
docker restart nagios
Scenario-Based Questions
1. Application running in Minikube, but customers cannot access it through a browser. How will you expose it externally?
Answer:
We can expose the application using a Kubernetes NodePort Service.
Step 1: Create a NodePort Service
bash
kubectl expose deployment nginx \
--type=NodePort \
--port=7070 \
--target-port=80
Step 2: Verify the Service
bash
kubectl get svc
Step 3: Get the Minikube Service URL
bash
minikube service nginx --url
This command generates a URL that can be accessed through a web browser.
Step 4: Open the generated URL
For example:
text
http://192.168.49.2:30080
The actual URL and port depend on the Minikube environment.
 
medium.com
Step 5: Troubleshooting if the application is not accessible
Execute:
bash
kubectl get pods
kubectl get svc
kubectl describe svc nginx
kubectl get endpoints nginx
minikube status
Check that:
•	Pods are in the Running state.
•	Service selectors match Pod labels.
•	Service endpoints are available.
•	The NodePort is correctly assigned.
•	Minikube is running.
Conclusion: NodePort exposes the application outside the Kubernetes cluster, and minikube service nginx --url provides the URL to access the application.
2. Which commands will you execute to verify Nagios service status and configuration?
Answer:
We can use Docker and Nagios commands to verify whether Nagios is running properly.
Step 1: Check whether the Nagios container is running
bash
docker ps
Step 2: Check the Nagios container status
bash
docker inspect nagios
Step 3: View Nagios container logs
bash
docker logs nagios
Step 4: Access the container shell
bash
docker exec -it nagios bash
Step 5: Verify Nagios service status
Inside the container, execute:
bash
service nagios status
Depending on the Docker image, the service may instead be managed by its startup process or another service manager.
Step 6: Verify Nagios configuration
bash
nagios -v /opt/nagios/etc/nagios.cfg
This checks the Nagios configuration for errors. The configuration path may vary depending on the Docker image.
Step 7: Restart Nagios
bash
docker restart nagios
Step 8: Verify through the browser
text
http://localhost:8080/nagios
If the Nagios dashboard opens and displays the configured hosts and services, we can verify that the monitoring interface is accessible.
3. During a festival sale, deployment is scaled from two to five replicas, but some Pods remain in Pending state. What are the possible reasons and how would you troubleshoot them?
Answer:
A Pending state means Kubernetes has not yet successfully scheduled the Pod onto a suitable node or completed its setup.
Possible reasons
1.	Insufficient CPU resources: The Minikube node does not have enough CPU to run additional Pods.
2.	Insufficient memory: Available RAM is insufficient for the new Pods.
3.	Resource limits: Pod resource requests are higher than the available node capacity.
4.	Node problems: The Kubernetes node may be NotReady or unavailable.
5.	Persistent Volume problems: Required storage volumes may not be available.
6.	Scheduling constraints: Node selectors, taints, tolerations or affinity rules may prevent Pods from being scheduled.
Troubleshooting steps
Step 1: Check Pod status
bash
kubectl get pods
Identify the Pods in Pending state.
Step 2: Describe the Pending Pod
bash
kubectl describe pod <pod-name>
Check the Events section for errors such as:
text
Insufficient cpu
Insufficient memory
FailedScheduling
Step 3: Check node status
bash
kubectl get nodes
Step 4: Check node resource availability
bash
kubectl describe node minikube
Check the Allocatable and Allocated resources sections.
Step 5: Check cluster events
bash
kubectl get events --sort-by=.metadata.creationTimestamp
This displays recent Kubernetes events and scheduling errors.
Step 6: Increase Minikube resources if required
Stop Minikube:
bash
minikube stop
Restart with more CPU and memory:
bash
minikube start --cpus=4 --memory=8192
The host machine must have sufficient available resources.
Step 7: Check the deployment again
bash
kubectl get deployments
kubectl get pods
Step 8: Verify all five replicas are running
bash
kubectl get pods -o wide
Expected result:
text
NAME                     READY   STATUS
nginx-xxxxxxxxxx-aaaaa   1/1     Running
nginx-xxxxxxxxxx-bbbbb   1/1     Running
nginx-xxxxxxxxxx-ccccc   1/1     Running
nginx-xxxxxxxxxx-ddddd   1/1     Running
nginx-xxxxxxxxxx-eeeee   1/1     Running
Conclusion: Pending Pods are generally caused by insufficient resources, node problems, storage issues or scheduling constraints. Using kubectl describe pod, kubectl describe node and kubectl get events helps identify the issue. Increasing Minikube resources or correcting scheduling constraints can resolve it.
Important commands for practical examination
Task	Command
Start Minikube	minikube start
Check cluster	minikube status
Create deployment	kubectl create deployment nginx --image=nginx --replicas=2
Expose application	kubectl expose deployment nginx --type=NodePort --port=7070 --target-port=80
Scale deployment	kubectl scale deployment nginx --replicas=5
Check Pods	kubectl get pods
Check Services	kubectl get svc
Access application	minikube service nginx --url
Check events	kubectl get events
Describe Pod	kubectl describe pod <pod-name>
Check Docker	docker ps
Check Nagios logs	docker logs nagios
Restart Nagios	docker restart nagios
Final conclusion: Kubernetes helps the Online Boutique Store handle high customer traffic through multiple replicas, NodePort provides external application access, and Nagios Core monitors application and server availability. Together, these technologies improve scalability, reliability and monitoring during festival sales and promotional events.


Q2. Jenkins Pipeline for a Maven Web Project with Webhooks (25 Marks)
1. Clone GitHub Repository
1.	Open Jenkins Dashboard.
2.	Go to New Item.
3.	Enter the name Online-Boutique-Pipeline.
4.	Select Pipeline and click OK.
5.	In the Pipeline section, select Pipeline script.
6.	Use the following Scripted Pipeline:
groovy
node {
    // Clone GitHub Repository
    stage('Git Clone') {
        git 'https://github.com/haleema91/LAB-INTERNAL-II-OBS.git'
    }

    // Maven Clean
    stage('Clean') {
        sh 'mvn clean'
    }

    // Maven Build
    stage('Build') {
        sh 'mvn compile'
    }

    // Maven Test
    stage('Test') {
        sh 'mvn test'
    }

    // Maven Package
    stage('Package') {
        sh 'mvn package'
    }

    // Deploy to Tomcat
    stage('Deploy') {
        sh 'cp target/*.war /opt/tomcat/webapps/'
    }
}
Click Save and then Build Now.
2. Configure Tomcat Web Server
1.	Install Apache Tomcat on the server.
2.	Start the Tomcat server.
3.	Configure the Tomcat username and password in tomcat-users.xml.
4.	Start Tomcat using:
bash
sudo systemctl start tomcat
5. Access Tomcat using:
text
http://localhost:8080
3. Deploy Application on Web Server
1. Generate the WAR file using Maven:
bash
mvn clean package
2. Copy the WAR file into Tomcat's webapps directory:
bash
cp target/*.war /opt/tomcat/webapps/
3. Restart Tomcat:
bash
sudo systemctl restart tomcat
4. Access the deployed application:
text
http://localhost:8080/OBS
4. Create Pipeline View and Configure GitHub Webhook
Step 1: Create Pipeline View
1.	Open Jenkins Dashboard.
2.	Click the + icon to add a new view.
3.	Enter Online-Boutique-View.
4.	Select Build Pipeline View.
5.	Click OK and select the pipeline job.
6.	Click Save.
Step 2: Configure GitHub Webhook
1.	Open your GitHub repository.
2.	Go to Settings → Webhooks → Add webhook.
3.	Enter the Jenkins webhook URL:
text
http://<JENKINS-IP>:8080/github-webhook/
4.	Set Content type to application/json.
5.	Select Just the push event.
6.	Click Add webhook.
Step 3: Configure Jenkins Build Trigger
1.	Open the Jenkins pipeline job.
2.	Click Configure.
3.	Go to Build Triggers.
4.	Enable GitHub hook trigger for GITScm polling.
5.	Click Save.
Step 4: Test Webhook
1.	Make a code change in the GitHub repository.
2.	Commit and push the changes.
3.	GitHub sends a webhook notification to Jenkins.
4.	Jenkins automatically triggers the pipeline.
5.	Check the Build History and Pipeline View to verify execution.
Scenario-Based Questions
1. Which Maven command removes previously generated build files?
bash
mvn clean
2. Where should you provide the GitHub repository URL in the Jenkins pipeline?
In the git command inside the Git Clone stage.
groovy
git 'https://github.com/haleema91/LAB-INTERNAL-II-OBS.git'
3. Which Maven command should you execute to generate the WAR file?
bash
mvn package

Q1. Docker Compose – Online Boutique Store (25 Marks)
1. Create a Docker Compose YAML file
Docker Compose is used to define and run multiple Docker containers using a single YAML configuration file.
For the Online Boutique Store, we need two services:
•	MySQL: Database backend running on port 3306.
•	Tomcat: Web server running on port 8080.
Create a file named docker-compose.yml.
Docker Compose YAML file:
yaml

services:
  mysql:
    image: mysql:8.0
    container_name: boutique-mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: root123
      MYSQL_DATABASE: boutique
      MYSQL_USER: boutiqueuser
      MYSQL_PASSWORD: boutique123
    ports:
      - "3306:3306"
    volumes:
      - mysql_data:/var/lib/mysql
    networks:
      - boutique-network

  tomcat:
    image: tomcat:9.0
    container_name: boutique-tomcat
    restart: always
    ports:
      - "8080:8080"
    depends_on:
      - mysql
    networks:
      - boutique-network

volumes:
  mysql_data:

networks:
  boutique-network:
    driver: bridge
2. Configure port mappings and persistent volumes
Port mappings:
Service	Container Port	Host Port
MySQL	3306	3306
Tomcat	8080	8080
•	3306:3306 exposes MySQL on port 3306.
•	8080:8080 exposes Tomcat on port 8080.
Persistent volume:
yaml
volumes:
  - mysql_data:/var/lib/mysql
This stores MySQL database files in a Docker-managed volume so that data remains available even if the MySQL container is removed and recreated.
Custom network:
yaml
networks:
  boutique-network:
    driver: bridge
Both containers are connected to the same custom network. Tomcat can communicate with MySQL using the hostname mysql and port 3306.
3. Start both containers using Docker Compose
Open the terminal in the directory containing docker-compose.yml.
Step 1: Start the containers
bash
docker compose up -d
The -d option runs containers in detached mode (background).
Step 2: Download images if required
Docker Compose automatically downloads the required images if they are not already available locally.
Step 3: Check the services
bash
docker compose ps
4. Verify running containers using Docker Compose
Execute:
bash
docker compose ps
Expected output (illustrative):
text
NAME              IMAGE        STATUS
boutique-mysql    mysql:8.0    Up
boutique-tomcat   tomcat:9.0   Up
To view container logs:
bash
docker compose logs
To view logs of a particular service:
bash
docker compose logs mysql
docker compose logs tomcat
5. Access Tomcat server through a web browser
1.	Open Google Chrome or any web browser.
2.	Enter the following URL:
text
http://localhost:8080
3. The Apache Tomcat welcome page should appear if Tomcat is running correctly.
 
Expected result Tomcat server is accessible through port 8080.
Scenario-Based Questions
Scenario 1: Configure port mappings and a custom Docker network
Question: How do you configure port mappings and a custom Docker network to access Tomcat through a browser and allow communication with MySQL?
Answer:
We configure both services in the Docker Compose file.
1. Port mapping configuration:
yaml
ports:
  - "8080:8080"
This allows users to access Tomcat through:
text
http://localhost:8080
For MySQL:
yaml
ports:
  - "3306:3306"
This exposes MySQL on the host's port 3306.
2. Create a custom Docker network:
yaml
networks:
  boutique-network:
    driver: bridge
3. Connect both containers to the network:
yaml
services:
  mysql:
    image: mysql:8.0
    networks:
      - boutique-network

  tomcat:
    image: tomcat:9.0
    networks:
      - boutique-network
4. Configure database connectivity:
The Tomcat application should use the following MySQL connection details:
Parameter	Value
Database hostname	mysql
Port	3306
Database name	boutique
Username	boutiqueuser
Password	boutique123
Example JDBC URL:
text
jdbc:mysql://mysql:3306/boutique
Result:
•	Users can access Tomcat using http://localhost:8080.
•	Tomcat can communicate with MySQL using mysql:3306.
•	Both containers communicate securely through the custom Docker network.
Scenario 2: MySQL data lost after removing and recreating the container
Question: Why does this happen, and how can Docker Compose volumes preserve database data?
Answer:
Reason for data loss:
When a MySQL container is removed, the data stored inside its writable container filesystem is also removed.
If persistent storage is not configured, customer registration details and product information may be lost.
Solution: Use Docker volumes.
Add the following configuration to the Docker Compose file:
yaml
services:
  mysql:
    image: mysql:8.0
    container_name: boutique-mysql
    environment:
      MYSQL_ROOT_PASSWORD: root123
      MYSQL_DATABASE: boutique
    volumes:
      - mysql_data:/var/lib/mysql

volumes:
  mysql_data:
Explanation:
•	mysql_data is a named Docker volume.
•	/var/lib/mysql is the directory where MySQL stores database files.
•	The volume stores database data independently of the container.
•	Even if the container is deleted and recreated, the database data remains in the volume.
Commands to verify persistent storage:
Check available volumes:
bash
docker volume ls
Inspect the volume:
bash
docker volume inspect mysql_data
Recreate containers:
bash
docker compose down
docker compose up -d
The existing database data will be reused.
Result Customer registration and product information remain محفوظ (preserved) even after container recreation, provided the named volume is not deleted.
Important: Avoid using docker compose down -v because it deletes the Compose-managed named volumes as well.
Scenario 3: Tomcat Connection Refused error
Question: When accessing http://localhost:8080, you receive a Connection Refused error. How do you troubleshoot the problem?
Answer:
Follow these troubleshooting steps.
Step 1: Check whether the Tomcat container is running
Execute:
bash
docker compose ps
If Tomcat is stopped, start it:
bash
docker compose up -d
You can also check all running containers:
bash
docker ps
Step 2: Check Tomcat container logs
Execute:
bash
docker compose logs tomcat
To continuously monitor logs:
bash
docker compose logs -f tomcat
Check for errors such as:
•	Port binding errors.
•	Application deployment failures.
•	Java configuration errors.
•	Database connection failures.
Step 3: Verify port mappings
Execute:
bash
docker port boutique-tomcat
Expected output:
text
8080/tcp -> 0.0.0.0:8080
If the port mapping is incorrect, verify the Compose configuration:
yaml
ports:
  - "8080:8080"
Restart the containers:
bash
docker compose up -d
Step 4: Troubleshoot MySQL database connection
Check whether MySQL is running:
bash
docker compose ps
Check MySQL logs:
bash
docker compose logs mysql
Check whether MySQL is ready:
bash
docker compose exec mysql mysqladmin ping -h localhost -u root -p
Verify that the Tomcat application uses the correct database hostname:
text
mysql
The JDBC connection URL should be:
text
jdbc:mysql://mysql:3306/boutique
Important: Inside the Tomcat container, use mysql as the hostname instead of localhost. The hostname localhost refers to the Tomcat container itself.
Also verify that:
•	Both containers belong to the same Docker network.
•	MySQL username and password are correct.
•	The MySQL database has been initialized.
•	The application has the required MySQL JDBC driver.
Step 5: Test Tomcat in the browser
Open:
text
http://localhost:8080
If Tomcat is running and the port is correctly mapped, the Tomcat welcome page should appear.
Step 6: Safely stop and remove containers
To stop the containers:
bash
docker compose stop
To stop and remove containers and the Compose network:
bash
docker compose down
To remove containers, networks, and named volumes (only when intentionally deleting database data):
bash
docker compose down -v
Warning: Do not use -v if you want to preserve MySQL data.
Important Docker Compose commands – Quick Revision
Command	Purpose
docker compose up -d	Start containers in background
docker compose ps	List Compose containers
docker compose logs	Display container logs
docker compose logs -f	Follow logs continuously
docker compose stop	Stop containers
docker compose start	Start stopped containers
docker compose restart	Restart containers
docker compose down	Stop and remove containers and network
docker volume ls	List Docker volumes
docker network ls	List Docker networks
docker ps	Display running containers
Final Conclusion
Docker Compose simplifies the deployment of multi-container applications. In the Online Boutique Store:
1.	MySQL provides database services on port 3306.
2.	Tomcat provides web services on port 8080.
3.	A custom bridge network enables communication between containers.
4.	Persistent Docker volumes protect database information from container deletion.
5.	Docker Compose commands help start, stop, monitor, and troubleshoot containers.
Thus, Docker Compose provides an easy and reliable way to deploy and manage the Online Boutique Store application.






Testing Jenkins CI using GitHub Webhook.


I'll use `SE 19-11-26.zip`**&#x20;(SET–1 to SET–9)**, the same collection we used for SET–7, SET–8 and SET–9. Below are only the required code files and commands, grouped by set. I'm leaving out explanations and viva answers.

# **SET–1 – E-Ticketing**

**Repository**

```
git clone https://github.com/ssvkotamraju/E-ticketing.git
cd E-ticketing
```

### **1. Docker – WordPress + MySQL**

```
docker pull mysql:8.0
docker pull wordpress:latest

docker network create eticket-net

docker volume create eticket-db-data

docker run -d `
  --name eticket-db `
  --network eticket-net `
  -e MYSQL_ROOT_PASSWORD=root123 `
  -e MYSQL_DATABASE=eticket `
  -e MYSQL_USER=eticketuser `
  -e MYSQL_PASSWORD=eticketpass `
  -v eticket-db-data:/var/lib/mysql `
  mysql:8.0

docker run -d `
  --name eticket-web `
  --network eticket-net `
  -p 80:80 `
  -e WORDPRESS_DB_HOST=eticket-db:3306 `
  -e WORDPRESS_DB_USER=eticketuser `
  -e WORDPRESS_DB_PASSWORD=eticketpass `
  -e WORDPRESS_DB_NAME=eticket `
  wordpress:latest

docker ps
docker logs eticket-db
docker logs eticket-web
```

Open `http://localhost`.

Recovery test:

```
docker stop eticket-db
docker start eticket-db
docker ps
```

### **2. Jenkins – Maven CI**

Repository URL:

```
https://github.com/ssvkotamraju/E-ticketing.git
```

Jenkinsfile (Windows agent):

```
node {
    stage('Checkout') {
        git branch: 'main',
            url: 'https://github.com/ssvkotamraju/E-ticketing.git'
    }

    stage('Build') {
        bat 'mvn clean package'
    }

    stage('Test') {
        bat 'mvn test'
    }

    stage('Archive') {
        archiveArtifacts artifacts: '**/target/*.war, **/target/*.jar',
                         allowEmptyArchive: true
    }
}
```

Build trigger: configure GitHub webhook or Poll SCM:

```
H/5 * * * *
```

### **3. Kubernetes – Minikube**

```
minikube start --driver=docker
kubectl get nodes
```

`deployment.yaml`:

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: eticket-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: eticket
  template:
    metadata:
      labels:
        app: eticket
    spec:
      containers:
      - name: eticket
        image: eticket-app:v1
        ports:
        - containerPort: 8080
```

`service.yaml`:

```
apiVersion: v1
kind: Service
metadata:
  name: eticket-service
spec:
  type: NodePort
  selector:
    app: eticket
  ports:
  - port: 8080
    targetPort: 8080
    nodePort: 30080
```

Commands:

```
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get deployments
kubectl get pods
kubectl get services

kubectl scale deployment eticket-deployment --replicas=5

kubectl delete pod POD_NAME
kubectl get pods

kubectl set image deployment/eticket-deployment eticket=eticket-app:v2
kubectl rollout status deployment/eticket-deployment
kubectl rollout undo deployment/eticket-deployment

minikube service eticket-service
```

### **4. Nagios**

```
docker pull jasonrivers/nagios:latest

docker run -d `
  --name nagios `
  -p 8082:80 `
  jasonrivers/nagios:latest

docker ps
docker logs nagios
```

Open:

```
http://localhost:8082/nagios
```

### **5. AWS EC2**

Ubuntu commands:

```
sudo apt update
sudo apt upgrade -y
sudo apt install docker.io git openjdk-17-jdk maven -y

sudo systemctl start docker
sudo systemctl enable docker

git clone https://github.com/ssvkotamraju/E-ticketing.git
cd E-ticketing

mvn clean package
```

Docker deployment, assuming the project produces a WAR:

`Dockerfile`:

```
FROM tomcat:10.1-jdk17
RUN rm -rf /usr/local/tomcat/webapps/*
COPY target/*.war /usr/local/tomcat/webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh", "run"]
```

```
sudo docker build -t eticket-app .
sudo docker run -d --name eticket-container -p 80:8080 eticket-app
sudo docker ps
sudo docker logs eticket-container
```

Open:

```
http://EC2-PUBLIC-IP
```

# **SET–2 – Hospital Management System**

**Repository**

```
git clone https://github.com/ssvkotamraju/HMS.git
cd HMS
```

### **1. Docker – HMS + PostgreSQL**

```
docker pull postgres:15
docker network create hms-net
docker volume create hms-db-data

docker run -d `
  --name hms-db `
  --network hms-net `
  -e POSTGRES_DB=hms `
  -e POSTGRES_USER=hmsuser `
  -e POSTGRES_PASSWORD=hms123 `
  -v hms-db-data:/var/lib/postgresql/data `
  postgres:15
```

If the project has a Dockerfile for its web backend:

```
docker build -t hms-app .
docker run -d `
  --name hms-web `
  --network hms-net `
  -p 8080:8080 `
  -e DB_HOST=hms-db `
  -e DB_PORT=5432 `
  -e DB_NAME=hms `
  -e DB_USER=hmsuser `
  -e DB_PASSWORD=hms123 `
  hms-app

docker ps
docker logs hms-web
docker logs hms-db
```

### **2. Jenkins – Maven CI**

Repository URL:

```
https://github.com/ssvkotamraju/HMS.git
```

Jenkinsfile:

```
node {
    stage('Checkout') {
        git branch: 'main',
            url: 'https://github.com/ssvkotamraju/HMS.git'
    }

    stage('Clean') {
        bat 'mvn clean'
    }

    stage('Install and Test') {
        bat 'mvn install'
    }

    stage('Package') {
        bat 'mvn package'
    }

    stage('Archive') {
        archiveArtifacts artifacts: '**/target/*.war',
                         allowEmptyArchive: true
    }
}
```

### **3. Kubernetes – HMS**

```
minikube start --driver=docker
docker build -t hms-app:v1 .
minikube image load hms-app:v1
```

`deployment.yaml`:

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: hms-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: hms
  template:
    metadata:
      labels:
        app: hms
    spec:
      containers:
      - name: hms
        image: hms-app:v1
        imagePullPolicy: IfNotPresent
        ports:
        - containerPort: 8080
```

`service.yaml`:

```
apiVersion: v1
kind: Service
metadata:
  name: hms-service
spec:
  type: NodePort
  selector:
    app: hms
  ports:
  - port: 8080
    targetPort: 8080
    nodePort: 30080
```

```
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get pods
kubectl get services

kubectl scale deployment hms-deployment --replicas=5
kubectl delete pod POD_NAME

kubectl set image deployment/hms-deployment hms=hms-app:v2
kubectl rollout status deployment/hms-deployment
kubectl rollout undo deployment/hms-deployment

minikube service hms-service
```

### **4. Nagios**

```
docker pull jasonrivers/nagios:latest
docker run -d --name nagios -p 8082:80 jasonrivers/nagios:latest
docker ps
docker logs nagios
```

### **5. AWS EC2**

```
sudo apt update
sudo apt upgrade -y
sudo apt install openjdk-17-jdk maven git tomcat10 -y

git clone https://github.com/ssvkotamraju/HMS.git
cd HMS

mvn clean install
```

Deploy WAR:

```
sudo cp target/*.war /var/lib/tomcat10/webapps/
sudo systemctl enable tomcat10
sudo systemctl restart tomcat10
sudo systemctl status tomcat10
```

CloudWatch Agent installation, if required:

```
sudo apt install amazon-cloudwatch-agent -y
```

# **SET–3 – Online Recruitment System**

**Repository**

```
git clone https://github.com/ssvkotamraju/ORS.git
cd ORS
```

### **1. Docker – MySQL + Java application**

```
docker pull mysql:8.0
docker network create ors-net
docker volume create ors-db-data

docker run -d `
  --name ors-db `
  --network ors-net `
  -e MYSQL_ROOT_PASSWORD=root123 `
  -e MYSQL_DATABASE=ors `
  -e MYSQL_USER=orsuser `
  -e MYSQL_PASSWORD=orspass `
  -v ors-db-data:/var/lib/mysql `
  mysql:8.0
```

If the application has a Dockerfile:

```
docker build -t ors-app .
docker run -d `
  --name ors-web `
  --network ors-net `
  -p 8080:8080 `
  -e DB_HOST=ors-db `
  -e DB_NAME=ors `
  -e DB_USER=orsuser `
  -e DB_PASSWORD=orspass `
  ors-app

docker ps
docker logs ors-db
docker logs ors-web
```

### **2. Jenkins**

```
node {
    stage('Checkout') {
        git branch: 'main',
            url: 'https://github.com/ssvkotamraju/ORS.git'
    }

    stage('Clean') {
        bat 'mvn clean'
    }

    stage('Test') {
        bat 'mvn test'
    }

    stage('Package') {
        bat 'mvn package'
    }

    stage('Archive') {
        archiveArtifacts artifacts: '**/target/*.war, **/target/*.jar',
                         allowEmptyArchive: true
    }
}
```

### **3. Kubernetes**

```
minikube start --driver=docker
docker build -t ors-app:v1 .
minikube image load ors-app:v1
```

`deployment.yaml`:

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: ors-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: ors
  template:
    metadata:
      labels:
        app: ors
    spec:
      containers:
      - name: ors
        image: ors-app:v1
        imagePullPolicy: IfNotPresent
        ports:
        - containerPort: 8080
```

`service.yaml`:

```
apiVersion: v1
kind: Service
metadata:
  name: ors-service
spec:
  type: NodePort
  selector:
    app: ors
  ports:
  - port: 8080
    targetPort: 8080
    nodePort: 30080
```

```
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl scale deployment ors-deployment --replicas=5
kubectl get pods
kubectl get services
kubectl delete pod POD_NAME
kubectl set image deployment/ors-deployment ors=ors-app:v2
kubectl rollout undo deployment/ors-deployment
minikube service ors-service
```

### **4. Nagios**

```
docker pull jasonrivers/nagios:latest
docker run -d --name nagios -p 8082:80 jasonrivers/nagios:latest
docker ps
docker logs nagios
```

### **5. AWS EC2**

```
sudo apt update
sudo apt install openjdk-17-jdk maven git tomcat10 -y

git clone https://github.com/ssvkotamraju/ORS.git
cd ORS

mvn clean test package

sudo cp target/*.war /var/lib/tomcat10/webapps/
sudo systemctl enable tomcat10
sudo systemctl restart tomcat10
```

# **SET–4 – Online Shopping Application**

**Repository**

```
git clone https://github.com/nikithamoturi/OnlineShoppingApp.git
cd OnlineShoppingApp
```

### **1. Docker – WordPress + MySQL**

```
docker pull wordpress:latest
docker pull mysql:8.0

docker network create shopping-net
docker volume create shopping-db-data

docker run -d `
  --name shopping-db `
  --network shopping-net `
  -e MYSQL_ROOT_PASSWORD=root123 `
  -e MYSQL_DATABASE=shopping `
  -e MYSQL_USER=shopuser `
  -e MYSQL_PASSWORD=shop123 `
  -v shopping-db-data:/var/lib/mysql `
  mysql:8.0

docker run -d `
  --name shopping-wordpress `
  --network shopping-net `
  -p 8080:80 `
  -e WORDPRESS_DB_HOST=shopping-db:3306 `
  -e WORDPRESS_DB_USER=shopuser `
  -e WORDPRESS_DB_PASSWORD=shop123 `
  -e WORDPRESS_DB_NAME=shopping `
  wordpress:latest

docker ps
docker logs shopping-db
docker logs shopping-wordpress
```

Open `http://localhost:8080`.

### **2. Jenkins – Freestyle Project**

Repository URL:

```
https://github.com/nikithamoturi/OnlineShoppingApp.git
```

Jenkins Freestyle configuration:

```
Source Code Management → Git
Repository URL → https://github.com/nikithamoturi/OnlineShoppingApp.git
Branch Specifier → */main
Build Triggers → Poll SCM
Schedule → H/5 * * * *
Build → Invoke top-level Maven targets
Goals → clean test package
Post-build Actions → Archive the artifacts
Files to archive → **/target/*.war
```

### **3. Kubernetes – 3 to 5 replicas**

```
minikube start --driver=docker
docker build -t shopping-app:v1 .
minikube image load shopping-app:v1
```

`deployment.yaml`:

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: shopping-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: shopping
  template:
    metadata:
      labels:
        app: shopping
    spec:
      containers:
      - name: shopping
        image: shopping-app:v1
        imagePullPolicy: IfNotPresent
        ports:
        - containerPort: 8080
```

`service.yaml`:

```
apiVersion: v1
kind: Service
metadata:
  name: shopping-service
spec:
  type: NodePort
  selector:
    app: shopping
  ports:
  - port: 8080
    targetPort: 8080
    nodePort: 30080
```

```
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get pods
kubectl get services

kubectl scale deployment shopping-deployment --replicas=5
kubectl get deployments
kubectl get pods

kubectl delete pod POD_NAME
kubectl get pods

minikube service shopping-service
```

### **4. Nagios**

```
docker pull jasonrivers/nagios:latest
docker run -d --name nagios -p 8082:80 jasonrivers/nagios:latest
docker ps
docker logs nagios
```

### **5. AWS EC2**

```
sudo apt update
sudo apt install openjdk-17-jdk maven git tomcat10 -y

git clone https://github.com/nikithamoturi/OnlineShoppingApp.git
cd OnlineShoppingApp

mvn clean test package

sudo cp target/*.war /var/lib/tomcat10/webapps/
sudo systemctl enable tomcat10
sudo systemctl restart tomcat10
sudo systemctl status tomcat10
```

# **SET–5 – Gym Membership Management System**

**Repository**

```
git clone https://github.com/nikithamoturi/GymManagementSystem.git
cd GymManagementSystem
```

### **1. Docker – WordPress + MySQL**

```
docker pull wordpress:latest
docker pull mysql:8.0

docker network create gym-net
docker volume create gym-db-data

docker run -d `
  --name gym-db `
  --network gym-net `
  -e MYSQL_ROOT_PASSWORD=root123 `
  -e MYSQL_DATABASE=gym `
  -e MYSQL_USER=gymuser `
  -e MYSQL_PASSWORD=gym123 `
  -v gym-db-data:/var/lib/mysql `
  mysql:8.0

docker run -d `
  --name gym-wordpress `
  --network gym-net `
  -p 8080:80 `
  -e WORDPRESS_DB_HOST=gym-db:3306 `
  -e WORDPRESS_DB_USER=gymuser `
  -e WORDPRESS_DB_PASSWORD=gym123 `
  -e WORDPRESS_DB_NAME=gym `
  wordpress:latest

docker ps
docker logs gym-db
docker logs gym-wordpress
```

Open `http://localhost:8080`.

### **2. Jenkins – Freestyle Project**

Repository URL:

```
https://github.com/nikithamoturi/GymManagementSystem.git
```

```
New Item → Freestyle Project
Source Code Management → Git
Repository URL → https://github.com/nikithamoturi/GymManagementSystem.git
Branch → */main
Build Triggers → Poll SCM
Schedule → H/5 * * * *
Build Steps → Invoke top-level Maven targets
Goals → clean test package
Post-build Actions → Archive the artifacts
Files to archive → **/target/*.war
```

### **3. Kubernetes – 2 to 5 replicas**

```
minikube start --driver=docker
docker build -t gym-app:v1 .
minikube image load gym-app:v1
```

`deployment.yaml`:

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: gym-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: gym
  template:
    metadata:
      labels:
        app: gym
    spec:
      containers:
      - name: gym
        image: gym-app:v1
        imagePullPolicy: IfNotPresent
        ports:
        - containerPort: 8080
```

`service.yaml`:

```
apiVersion: v1
kind: Service
metadata:
  name: gym-service
spec:
  type: NodePort
  selector:
    app: gym
  ports:
  - port: 8080
    targetPort: 8080
    nodePort: 30080
```

```
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml

kubectl get pods
kubectl get services

kubectl scale deployment gym-deployment --replicas=5
kubectl get deployments

kubectl delete pod POD_NAME
kubectl get pods

minikube service gym-service
```

### **4. Nagios**

```
docker pull jasonrivers/nagios:latest
docker run -d --name nagios -p 8082:80 jasonrivers/nagios:latest
docker ps
docker logs nagios
```

### **5. AWS EC2**

```
sudo apt update
sudo apt install openjdk-17-jdk maven git tomcat10 -y

git clone https://github.com/nikithamoturi/GymManagementSystem.git
cd GymManagementSystem

mvn clean test package

sudo cp target/*.war /var/lib/tomcat10/webapps/
sudo systemctl enable tomcat10
sudo systemctl restart tomcat10
sudo systemctl status tomcat10
```

# **SET–6 – Vehicle Rental Management System**

**Repository**

```
git clone https://github.com/nikithamoturi/VehicleRentalManagementSystem.git
cd VehicleRentalManagementSystem
```

### **1. Docker – WordPress + MySQL**

```
docker pull wordpress:latest
docker pull mysql:8.0

docker network create rental-net
docker volume create rental-db-data

docker run -d `
  --name rental-db `
  --network rental-net `
  -e MYSQL_ROOT_PASSWORD=root123 `
  -e MYSQL_DATABASE=rental `
  -e MYSQL_USER=rentaluser `
  -e MYSQL_PASSWORD=rental123 `
  -v rental-db-data:/var/lib/mysql `
  mysql:8.0

docker run -d `
  --name rental-wordpress `
  --network rental-net `
  -p 8080:80 `
  -e WORDPRESS_DB_HOST=rental-db:3306 `
  -e WORDPRESS_DB_USER=rentaluser `
  -e WORDPRESS_DB_PASSWORD=rental123 `
  -e WORDPRESS_DB_NAME=rental `
  wordpress:latest

docker ps
docker logs rental-db
docker logs rental-wordpress
```

Open `http://localhost:8080`.

### **2. Jenkins – Freestyle Project**

Repository URL:

```
https://github.com/nikithamoturi/VehicleRentalManagementSystem.git
```

```
New Item → Freestyle Project
Source Code Management → Git
Repository URL → https://github.com/nikithamoturi/VehicleRentalManagementSystem.git
Branch → */main
Build Triggers → Poll SCM
Schedule → H/5 * * * *
Build Steps → Invoke top-level Maven targets
Goals → clean test package
Post-build Actions → Archive the artifacts
Files to archive → **/target/*.war
```

### **3. Kubernetes – 2 to 4 replicas**

```
minikube start --driver=docker
docker build -t rental-app:v1 .
minikube image load rental-app:v1
```

`deployment.yaml`:

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: rental-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: rental
  template:
    metadata:
      labels:
        app: rental
    spec:
      containers:
      - name: rental
        image: rental-app:v1
        imagePullPolicy: IfNotPresent
        ports:
        - containerPort: 8080
```

`service.yaml`:

```
apiVersion: v1
kind: Service
metadata:
  name: rental-service
spec:
  type: NodePort
  selector:
    app: rental
  ports:
  - port: 8080
    targetPort: 8080
    nodePort: 30080
```

```
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml

kubectl get pods
kubectl get services

kubectl scale deployment rental-deployment --replicas=4
kubectl get pods

kubectl delete pod POD_NAME
kubectl get pods

minikube service rental-service
```

### **4. Nagios**

```
docker pull jasonrivers/nagios:latest
docker run -d --name nagios -p 8082:80 jasonrivers/nagios:latest
docker ps
docker logs nagios
```

### **5. AWS EC2**

```
sudo apt update
sudo apt install openjdk-17-jdk maven git tomcat10 -y

git clone https://github.com/nikithamoturi/VehicleRentalManagementSystem.git
cd VehicleRentalManagementSystem

mvn clean test package

sudo cp target/*.war /var/lib/tomcat10/webapps/
sudo systemctl enable tomcat10
sudo systemctl restart tomcat10
sudo systemctl status tomcat10
```

# **SET–7 – SportSystem**

**Repository**

```
git clone https://github.com/sarasrija/SportSystem.git
cd SportSystem
```

### **1. Jenkins – Scripted Pipeline**

Jenkins tools: configure JDK and Maven under `Manage Jenkins → Tools`.

Jenkinsfile for Windows:

```
node {
    stage('Clean Workspace') {
        cleanWs()
    }

    stage('Clone') {
        git branch: 'main',
            url: 'https://github.com/sarasrija/SportSystem.git'
    }

    stage('Clean') {
        def mvn = tool 'Maven3'
        bat "\"${mvn}\\bin\\mvn\" clean"
    }

    stage('Compile') {
        def mvn = tool 'Maven3'
        bat "\"${mvn}\\bin\\mvn\" compile"
    }

    stage('Test') {
        def mvn = tool 'Maven3'
        bat "\"${mvn}\\bin\\mvn\" test"
    }

    stage('Package') {
        def mvn = tool 'Maven3'
        bat "\"${mvn}\\bin\\mvn\" package"
    }

    stage('Archive') {
        archiveArtifacts artifacts: '**/target/*.war',
                         allowEmptyArchive: true
    }
}
```

Build trigger Poll SCM:

```
H/5 * * * *
```

GitHub webhook URL:

```
https://YOUR-NGROK-URL/github-webhook/
```

Start ngrok:

```
ngrok http 8080
```

### **2. AWS EC2 – Docker + Tomcat**

```
sudo apt update
sudo apt upgrade -y
sudo apt install docker.io git openjdk-17-jdk maven -y

sudo systemctl start docker
sudo systemctl enable docker

git clone https://github.com/sarasrija/SportSystem.git
cd SportSystem

mvn clean package
```

`Dockerfile`:

```
FROM tomcat:10.1-jdk17
RUN rm -rf /usr/local/tomcat/webapps/*
COPY target/*.war /usr/local/tomcat/webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh", "run"]
```

```
sudo docker build -t sports-app .
sudo docker run -d --name sports-container -p 8090:8080 sports-app

sudo docker ps
sudo docker logs sports-container
```

Open:

```
http://EC2-PUBLIC-IP:8090
```

### **3. Kubernetes + Nagios**

```
minikube start --driver=docker
docker build -t sports-app:v1 .
minikube image load sports-app:v1
```

`deployment.yaml`:

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: sports-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: sports
  template:
    metadata:
      labels:
        app: sports
    spec:
      containers:
      - name: sports
        image: sports-app:v1
        imagePullPolicy: IfNotPresent
        ports:
        - containerPort: 8080
```

`service.yaml`:

```
apiVersion: v1
kind: Service
metadata:
  name: sports-service
spec:
  type: NodePort
  selector:
    app: sports
  ports:
  - port: 8080
    targetPort: 8080
    nodePort: 30080
```

```
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get pods
kubectl get services
kubectl scale deployment sports-deployment --replicas=5
kubectl describe pod POD_NAME
kubectl logs POD_NAME
kubectl rollout undo deployment/sports-deployment
minikube service sports-service
```

Nagios:

```
docker pull jasonrivers/nagios:latest
docker run -d --name nagios -p 8082:80 jasonrivers/nagios:latest
docker ps
docker logs nagios
```

### **4. Docker Compose – Flask + PostgreSQL + Redis**

Create `docker-compose.yml`:

```
services:
  web:
    build: ./web
    container_name: sports-web
    ports:
      - "5000:5000"
    depends_on:
      - db
      - redis
    networks:
      - sports-network

  db:
    image: postgres:15
    container_name: sports-db
    environment:
      POSTGRES_DB: sportsdb
      POSTGRES_USER: sportsuser
      POSTGRES_PASSWORD: sports123
    volumes:
      - sports-data:/var/lib/postgresql/data
    networks:
      - sports-network

  redis:
    image: redis:latest
    container_name: sports-redis
    networks:
      - sports-network

networks:
  sports-network:
    driver: bridge

volumes:
  sports-data:
```

`web/Dockerfile`:

```
FROM python:3.11
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
EXPOSE 5000
CMD ["python", "app.py"]
```

`web/requirements.txt`:

```
Flask
psycopg2-binary
redis
```

`web/app.py`:

```
from flask import Flaskapp = Flask(__name__)@app.route("/")def home():    return "Sports Management System is running"if __name__ == "__main__":    app.run(host="0.0.0.0", port=5000)
```

Commands:

```
docker compose up -d --build
docker compose ps
docker compose logs
docker compose stop
docker compose start
docker compose down
docker compose down -v
docker compose up -d --scale web=3
```

# **SET–8 – Blood Bank System**

**Repository**

```
git clone https://github.com/sarasrija/BloodBanksystem.git
cd BloodBanksystem
```

### **1. Jenkins – Scripted Pipeline**

```
node {
    stage('Clean Workspace') {
        cleanWs()
    }

    stage('Clone') {
        git branch: 'main',
            url: 'https://github.com/sarasrija/BloodBanksystem.git'
    }

    stage('Clean') {
        def mvn = tool 'Maven3'
        bat "\"${mvn}\\bin\\mvn\" clean"
    }

    stage('Install') {
        def mvn = tool 'Maven3'
        bat "\"${mvn}\\bin\\mvn\" install -DskipTests"
    }

    stage('Test') {
        def mvn = tool 'Maven3'
        bat "\"${mvn}\\bin\\mvn\" test"
    }

    stage('Package') {
        def mvn = tool 'Maven3'
        bat "\"${mvn}\\bin\\mvn\" package"
    }

    stage('Archive') {
        archiveArtifacts artifacts: '**/target/*.war',
                         allowEmptyArchive: true
    }
}
```

Build trigger:

```
H/5 * * * *
```

### **2. AWS EC2 – Static website**

```
sudo apt update
sudo apt upgrade -y
sudo apt install apache2 git -y

sudo systemctl start apache2
sudo systemctl enable apache2

git clone https://github.com/sarasrija/BloodBanksystem.git
cd BloodBanksystem
```

Deploy a static `index.html`:

```
sudo cp index.html /var/www/html/
sudo chmod 644 /var/www/html/index.html
sudo systemctl restart apache2
```

Check:

```
curl localhost
sudo systemctl status apache2
```

For a Maven WAR application:

```
sudo apt install openjdk-17-jdk maven tomcat10 -y
mvn clean package
sudo cp target/*.war /var/lib/tomcat10/webapps/
sudo systemctl restart tomcat10
```

### **3. Kubernetes + Nagios**

```
minikube start --driver=docker
docker build -t bloodbank-app:v1 .
minikube image load bloodbank-app:v1
```

`deployment.yaml`:

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: bloodbank-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: bloodbank
  template:
    metadata:
      labels:
        app: bloodbank
    spec:
      containers:
      - name: bloodbank
        image: bloodbank-app:v1
        imagePullPolicy: IfNotPresent
        ports:
        - containerPort: 8080
```

`service.yaml`:

```
apiVersion: v1
kind: Service
metadata:
  name: bloodbank-service
spec:
  type: NodePort
  selector:
    app: bloodbank
  ports:
  - port: 8080
    targetPort: 8080
    nodePort: 30080
```

```
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get pods
kubectl get services

kubectl scale deployment bloodbank-deployment --replicas=4
kubectl describe pod POD_NAME
kubectl logs POD_NAME
kubectl rollout undo deployment/bloodbank-deployment

minikube service bloodbank-service
```

Nagios:

```
docker pull jasonrivers/nagios:latest
docker run -d --name nagios -p 8082:80 jasonrivers/nagios:latest
docker ps
docker logs nagios
```

### **4. Docker Compose – Nginx + PostgreSQL 15**

Create `docker-compose.yml`:

```
version: "3.9"

services:
  web:
    image: nginx:latest
    container_name: bloodbank-web
    ports:
      - "8080:80"
    depends_on:
      - db
    networks:
      - bloodbank-network

  db:
    image: postgres:15
    container_name: bloodbank-db
    environment:
      POSTGRES_DB: bloodbank
      POSTGRES_USER: blooduser
      POSTGRES_PASSWORD: blood123
    volumes:
      - bloodbank-data:/var/lib/postgresql/data
    networks:
      - bloodbank-network

networks:
  bloodbank-network:
    driver: bridge

volumes:
  bloodbank-data:
```

Commands:

```
docker compose up -d
docker compose ps
docker compose logs
docker exec -it bloodbank-db psql -U blooduser -d bloodbank
docker compose stop
docker compose start
docker compose down
docker compose down -v
docker compose up -d --build
```

# **SET–9 – Apartment Management System**

**Repository**

```
git clone https://github.com/sarasrija/ApartmentSystem.git
cd ApartmentSystem
```

### **1. Jenkins – Scripted Pipeline + GitHub Webhook + Tomcat**

Start ngrok:

```
ngrok http 8080
```

GitHub webhook URL:

```
https://YOUR-NGROK-URL/github-webhook/
```

Jenkinsfile:

```
node {
    stage('Clean Workspace') {
        cleanWs()
    }

    stage('Clone') {
        git branch: 'main',
            url: 'https://github.com/sarasrija/ApartmentSystem.git'
    }

    stage('Clean') {
        def mvn = tool 'Maven3'
        bat "\"${mvn}\\bin\\mvn\" clean"
    }

    stage('Compile') {
        def mvn = tool 'Maven3'
        bat "\"${mvn}\\bin\\mvn\" compile"
    }

    stage('Test') {
        def mvn = tool 'Maven3'
        bat "\"${mvn}\\bin\\mvn\" test"
    }

    stage('Package') {
        def mvn = tool 'Maven3'
        bat "\"${mvn}\\bin\\mvn\" package"
    }

    stage('Archive') {
        archiveArtifacts artifacts: '**/target/*.war',
                         allowEmptyArchive: false
    }
}
```

GitHub webhook trigger:

```
GitHub hook trigger for GITScm polling
```

Pipeline View: create a new view → select **Pipeline View** → choose `ApartmentSystem` job.

Tomcat deployment, assuming WAR output:

```
mvn clean package
```

Copy the generated WAR into Tomcat's `webapps` folder, then restart Tomcat.

### **2. AWS EC2 – Docker + Tomcat**

Connect:

```
ssh -i "your-key.pem" ubuntu@EC2-PUBLIC-IP
```

Ubuntu commands:

```
sudo apt update
sudo apt upgrade -y
sudo apt install docker.io git openjdk-17-jdk maven -y

sudo systemctl start docker
sudo systemctl enable docker

git clone https://github.com/sarasrija/ApartmentSystem.git
cd ApartmentSystem

mvn clean package
```

`Dockerfile`:

```
FROM tomcat:10.1-jdk17

RUN rm -rf /usr/local/tomcat/webapps/*

COPY target/*.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080

CMD ["catalina.sh", "run"]
```

Build and run:

```
sudo docker build -t apartment-app .
sudo docker run -d --name apartment-container -p 8090:8080 apartment-app

sudo docker ps
sudo docker logs apartment-container
```

Open:

```
http://EC2-PUBLIC-IP:8090
```

### **3. Kubernetes – 4 replicas + Nagios**

```
minikube start --driver=docker
docker build -t apartment-app:v1 .
minikube image load apartment-app:v1
```

`deployment.yaml`:

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: apartment-deployment
spec:
  replicas: 4
  selector:
    matchLabels:
      app: apartment
  template:
    metadata:
      labels:
        app: apartment
    spec:
      containers:
      - name: apartment
        image: apartment-app:v1
        imagePullPolicy: IfNotPresent
        ports:
        - containerPort: 8080
```

`service.yaml`:

```
apiVersion: v1
kind: Service
metadata:
  name: apartment-service
spec:
  type: NodePort
  selector:
    app: apartment
  ports:
  - port: 8080
    targetPort: 8080
    nodePort: 30080
```

Commands:

```
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml

kubectl get deployments
kubectl get pods
kubectl get services

kubectl scale deployment apartment-deployment --replicas=6

kubectl describe pod POD_NAME
kubectl logs POD_NAME
kubectl top nodes
kubectl top pods

kubectl port-forward service/apartment-service 8081:8080
```

Open:

```
http://localhost:8081
```

Nagios:

```
docker pull jasonrivers/nagios:latest

docker run -d `
  --name nagios `
  -p 8082:80 `
  jasonrivers/nagios:latest

docker ps
docker logs nagios
```

Open:

```
http://localhost:8082/nagios
```

### **4. Docker Compose – Nginx + PostgreSQL 15**

Create folder:

```
mkdir compose-lab
cd compose-lab
```

Create `index.html`:

```
<!DOCTYPE html>
<html>
<head>
    <title>Apartment Management System</title>
</head>
<body>
    <h1>Apartment Management System</h1>
    <p>Docker Compose is working!</p>
</body>
</html>
```

Create `docker-compose.yml`:

```
version: "3.9"

services:
  web:
    image: nginx:latest
    container_name: apartment-web
    ports:
      - "8080:80"
    volumes:
      - ./index.html:/usr/share/nginx/html/index.html:ro
    depends_on:
      - db
    networks:
      - apartment-network

  db:
    image: postgres:15
    container_name: apartment-db
    restart: always
    environment:
      POSTGRES_DB: apartmentdb
      POSTGRES_USER: admin
      POSTGRES_PASSWORD: admin123
    volumes:
      - postgres-data:/var/lib/postgresql/data
    networks:
      - apartment-network

networks:
  apartment-network:
    driver: bridge

volumes:
  postgres-data:
```

Run and verify:

```
docker compose up -d
docker compose ps
docker compose logs
```

Open:

```
http://localhost:8080
```

PostgreSQL:

```
docker exec -it apartment-db psql -U admin -d apartmentdb
```

SQL commands:

```
CREATE TABLE residents (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    apartment_no VARCHAR(20)
);

INSERT INTO residents (name, apartment_no)
VALUES ('Rahul', 'A101');

SELECT * FROM residents;

\q
```

Lifecycle commands:

```
docker compose stop
docker compose start
docker compose down
docker compose up -d --build
docker compose down -v
```

## **Common commands used across the sets**

**Docker**

```
docker images
docker ps
docker ps -a
docker logs CONTAINER_NAME
docker stop CONTAINER_NAME
docker start CONTAINER_NAME
docker restart CONTAINER_NAME
docker rm -f CONTAINER_NAME
docker network ls
docker volume ls
docker compose up -d
docker compose down
```

**Jenkins / Maven**

```
mvn clean
mvn compile
mvn test
mvn install
mvn package
mvn clean test package
```

**Kubernetes**

```
minikube start --driver=docker
minikube status
kubectl get nodes
kubectl get deployments
kubectl get pods
kubectl get services
kubectl describe pod POD_NAME
kubectl logs POD_NAME
kubectl delete pod POD_NAME
kubectl scale deployment DEPLOYMENT_NAME --replicas=5
kubectl rollout status deployment/DEPLOYMENT_NAME
kubectl rollout undo deployment/DEPLOYMENT_NAME
kubectl port-forward service/SERVICE_NAME 8081:8080
minikube service SERVICE_NAME
```

**AWS / Ubuntu**

```
sudo apt update
sudo apt upgrade -y
sudo apt install docker.io git -y
sudo systemctl start docker
sudo systemctl enable docker
sudo systemctl status docker
sudo docker ps
sudo docker logs CONTAINER_NAME
```

**Note:** For Sets 1–9, replace example image names such as `eticket-app:v1`, `hms-app:v1`, and `apartment-app:v1` with the actual image you build. Maven, WAR, Tomcat and Dockerfile commands apply only if the repository contains the corresponding Maven web application and produces a compatible WAR.





# **Software Engineering Lab Internal II – All 9 Sets Cheat Sheet**

Exam revision format

**Only practical steps, commands and required code.** Follow the steps in order. This is based on `SE 19-11-26.zip`, SET–1 to SET–9.

## **First: Commands common to the practical exam**

Open PowerShell for Docker, Jenkins and Minikube commands. Use the Ubuntu terminal for EC2 commands.

**Check software**

```
docker --version
docker compose version
kubectl version --client
minikube version
git --version
mvn -version
```

**Start Docker Desktop**, then start Minikube:

```
minikube start --driver=docker
kubectl get nodes
```

**Important:** For the GitHub Java projects, first check whether `pom.xml` exists. Maven commands and WAR deployment are applicable only when the repository is actually a Maven web application.

# **SET–1 – E-Ticketing System**

Repository: [https://github.com/ssvkotamraju/E-ticketing.git](https://github.com/ssvkotamraju/E-ticketing.git?utm_source=chatgpt.com)

## **1. Docker – WordPress + MySQL**

**Step 1:** Open Docker Desktop.

**Step 2:** Pull images.

```
docker pull mysql:8.0
docker pull wordpress:latest
```

**Step 3:** Create network and volume.

```
docker network create eticket-net
docker volume create eticket-db-data
```

**Step 4:** Run MySQL.

```
docker run -d --name eticket-db --network eticket-net `
-e MYSQL_ROOT_PASSWORD=root123 `
-e MYSQL_DATABASE=eticket `
-e MYSQL_USER=eticketuser `
-e MYSQL_PASSWORD=eticketpass `
-v eticket-db-data:/var/lib/mysql mysql:8.0
```

**Step 5:** Run WordPress.

```
docker run -d --name eticket-web --network eticket-net `
-p 80:80 `
-e WORDPRESS_DB_HOST=eticket-db:3306 `
-e WORDPRESS_DB_USER=eticketuser `
-e WORDPRESS_DB_PASSWORD=eticketpass `
-e WORDPRESS_DB_NAME=eticket wordpress:latest
```

**Step 6:** Check containers.

```
docker ps
docker logs eticket-db
docker logs eticket-web
```

**Step 7:** Open browser.

```
http://localhost
```

Complete WordPress installation and publish sample ticket information.

**Step 8:** Test recovery.

```
docker stop eticket-db
docker start eticket-db
docker ps
```

## **2. Jenkins – Maven CI Pipeline**

**Step 1:** Open Jenkins.

```
http://localhost:8080
```

**Step 2:** Install Git, Pipeline, Maven Integration and JUnit plugins.

**Step 3:** Configure JDK and Maven:

`Manage Jenkins → Tools`

Example names:

```
JDK17
Maven3
```

**Step 4:** Create job.

`New Item → ETicketing → Pipeline → OK`

**Step 5:** Paste this pipeline in Pipeline Script.

```
node {
    stage('Checkout') {
        git branch: 'main',
        url: 'https://github.com/ssvkotamraju/E-ticketing.git'
    }

    stage('Clean') {
        bat 'mvn clean'
    }

    stage('Compile and Test') {
        bat 'mvn test'
    }

    stage('Package') {
        bat 'mvn package'
    }

    stage('Archive') {
        archiveArtifacts artifacts: '**/target/*.war, **/target/*.jar',
                         allowEmptyArchive: true
    }
}
```

**Step 6:** Configure Poll SCM.

```
H/5 * * * *
```

**Step 7:** Click Build Now.

**Step 8:** Open Console Output and check build status.

- Green: Success.
- Red: Failed.

**Step 9:** Check the WAR/JAR under Build Artifacts.

## **3. Kubernetes – 2 to 5 replicas**

**Step 1:**

```
minikube start --driver=docker
```

**Step 2:** Build and load application image if the repository has a Dockerfile.

```
git clone https://github.com/ssvkotamraju/E-ticketing.git
cd E-ticketing
docker build -t eticket-app:v1 .
minikube image load eticket-app:v1
```

**Step 3:** Create `deployment.yaml`.

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: eticket-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: eticket
  template:
    metadata:
      labels:
        app: eticket
    spec:
      containers:
      - name: eticket
        image: eticket-app:v1
        imagePullPolicy: IfNotPresent
        ports:
        - containerPort: 8080
```

**Step 4:** Create `service.yaml`.

```
apiVersion: v1
kind: Service
metadata:
  name: eticket-service
spec:
  type: NodePort
  selector:
    app: eticket
  ports:
  - port: 8080
    targetPort: 8080
    nodePort: 30080
```

**Step 5:**

```
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get pods
kubectl get services
```

**Step 6: Scale from 2 to 5.**

```
kubectl scale deployment eticket-deployment --replicas=5
kubectl get pods
```

**Step 7: Delete a pod.**

```
kubectl get pods
kubectl delete pod POD_NAME
kubectl get pods
```

**Step 8: Update and rollback.**

```
kubectl set image deployment/eticket-deployment eticket=eticket-app:v2
kubectl rollout status deployment/eticket-deployment
kubectl rollout undo deployment/eticket-deployment
```

**Step 9: Open application.**

```
minikube service eticket-service
```

## **4. Nagios – Monitoring**

**Step 1:**

```
docker pull jasonrivers/nagios:latest
```

**Step 2:**

```
docker run -d --name nagios -p 8082:80 jasonrivers/nagios:latest
```

**Step 3:**

```
docker ps
docker logs nagios
```

**Step 4:** Open:

```
http://localhost:8082/nagios
```

Common image login:

```
Username: nagiosadmin
Password: nagios
```

**Step 5:** Configure host and service checks for:

- CPU
- Memory
- Disk
- Uptime
- HTTP
- MySQL TCP port

A running Nagios container alone does not configure all these checks. Add the required host/service definitions and monitoring plugins.

## **5. AWS EC2**

**Step 1:** AWS Console → EC2 → Launch Instance.

- Select Ubuntu.
- Select `t2.micro` if available.
- Create/download `.pem` key.
- Security Group: SSH 22 from My IP; HTTP 80 from required users.

**Step 2:** Connect from PowerShell.

```
ssh -i "your-key.pem" ubuntu@EC2-PUBLIC-IP
```

**Step 3:** Install Docker and Git.

```
sudo apt update
sudo apt upgrade -y
sudo apt install docker.io git -y
sudo systemctl start docker
sudo systemctl enable docker
```

**Step 4:** Clone repository.

```
git clone https://github.com/ssvkotamraju/E-ticketing.git
cd E-ticketing
```

**Step 5:** Pull the image from Docker Hub.

```
sudo docker pull YOUR-USERNAME/eticket-app:latest
```

**Step 6:** Run application image containing Tomcat.

```
sudo docker run -d --name eticket-app -p 80:8080 YOUR-USERNAME/eticket-app:latest
```

**Step 7:**

```
sudo docker ps
sudo docker logs eticket-app
```

Open:

```
http://EC2-PUBLIC-IP
```

# **SET–2 – Hospital Management System**

Repository: [https://github.com/ssvkotamraju/HMS.git](https://github.com/ssvkotamraju/HMS.git?utm_source=chatgpt.com)

## **1. Docker – HMS + Database**

The question allows PostgreSQL/MySQL. Use PostgreSQL for this example.

**Step 1:**

```
docker pull postgres:15
```

**Step 2:**

```
docker network create hms-net
docker volume create hms-db-data
```

**Step 3:**

```
docker run -d --name hms-db --network hms-net `
-e POSTGRES_DB=hms `
-e POSTGRES_USER=hmsuser `
-e POSTGRES_PASSWORD=hms123 `
-v hms-db-data:/var/lib/postgresql/data postgres:15
```

**Step 4:** If the HMS backend has a Dockerfile:

```
docker build -t hms-app .
docker run -d --name hms-web --network hms-net `
-p 8080:8080 `
-e DB_HOST=hms-db `
-e DB_PORT=5432 `
-e DB_NAME=hms `
-e DB_USER=hmsuser `
-e DB_PASSWORD=hms123 hms-app
```

**Step 5:**

```
docker ps
docker logs hms-db
docker logs hms-web
```

Open:

```
http://localhost:8080
```

## **2. Jenkins – Maven CI**

**Step 1:** Open Jenkins → New Item → `HMS` → Pipeline.

**Step 2:** Configure Git and Maven plugins and JDK/Maven tools.

**Step 3:** Use this pipeline:

```
node {
    stage('Checkout') {
        git branch: 'main',
        url: 'https://github.com/ssvkotamraju/HMS.git'
    }

    stage('Clean') {
        bat 'mvn clean'
    }

    stage('Install and Test') {
        bat 'mvn install'
    }

    stage('Package') {
        bat 'mvn package'
    }

    stage('Archive') {
        archiveArtifacts artifacts: '**/target/*.war',
                         allowEmptyArchive: true
    }
}
```

**Step 4:** Configure GitHub webhook or Poll SCM.

```
H/5 * * * *
```

**Step 5:** Build Now → Console Output → Artifacts.

## **3. Kubernetes – 2 to 5 replicas**

**Step 1:**

```
minikube start --driver=docker
```

**Step 2:**

```
docker build -t hms-app:v1 .
minikube image load hms-app:v1
```

**Step 3:** Create `deployment.yaml`.

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: hms-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: hms
  template:
    metadata:
      labels:
        app: hms
    spec:
      containers:
      - name: hms
        image: hms-app:v1
        imagePullPolicy: IfNotPresent
        ports:
        - containerPort: 8080
```

**Step 4:** Create `service.yaml`.

```
apiVersion: v1
kind: Service
metadata:
  name: hms-service
spec:
  type: NodePort
  selector:
    app: hms
  ports:
  - port: 8080
    targetPort: 8080
    nodePort: 30080
```

**Step 5:**

```
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get pods
kubectl get services
```

**Step 6:**

```
kubectl scale deployment hms-deployment --replicas=5
kubectl get pods
```

**Step 7:**

```
kubectl delete pod POD_NAME
kubectl get pods
```

**Step 8:**

```
kubectl set image deployment/hms-deployment hms=hms-app:v2
kubectl rollout status deployment/hms-deployment
kubectl rollout undo deployment/hms-deployment
```

**Step 9:**

```
minikube service hms-service
```

## **4. Nagios**

```
docker pull jasonrivers/nagios:latest
docker run -d --name nagios -p 8082:80 jasonrivers/nagios:latest
docker ps
docker logs nagios
```

Open:

```
http://localhost:8082/nagios
```

Configure host/service checks for CPU, memory, disk, uptime, HTTP and database connectivity.

## **5. AWS EC2 – Java + Maven + Tomcat**

**Step 1:** Launch Ubuntu EC2 and configure SSH 22, HTTP 80 and Tomcat 8080 as required.

**Step 2:** Connect:

```
ssh -i "your-key.pem" ubuntu@EC2-PUBLIC-IP
```

**Step 3:**

```
sudo apt update
sudo apt upgrade -y
sudo apt install openjdk-17-jdk maven git tomcat10 -y
```

**Step 4:**

```
git clone https://github.com/ssvkotamraju/HMS.git
cd HMS
```

**Step 5:**

```
mvn clean install
```

**Step 6:**

```
sudo cp target/*.war /var/lib/tomcat10/webapps/
sudo systemctl enable tomcat10
sudo systemctl restart tomcat10
sudo systemctl status tomcat10
```

**Step 7:** Open the application using:

```
http://EC2-PUBLIC-IP:8080/war-filename
```

# **SET–3 – Online Recruitment System**

Repository: [https://github.com/ssvkotamraju/ORS.git](https://github.com/ssvkotamraju/ORS.git?utm_source=chatgpt.com)

## **1. Docker – MySQL + Java Application**

**Step 1:**

```
docker pull mysql:8.0
```

**Step 2:**

```
docker network create ors-net
docker volume create ors-db-data
```

**Step 3:**

```
docker run -d --name ors-db --network ors-net `
-e MYSQL_ROOT_PASSWORD=root123 `
-e MYSQL_DATABASE=ors `
-e MYSQL_USER=orsuser `
-e MYSQL_PASSWORD=orspass `
-v ors-db-data:/var/lib/mysql mysql:8.0
```

**Step 4:** If the Java application has a Dockerfile:

```
docker build -t ors-app .
docker run -d --name ors-web --network ors-net `
-p 8080:8080 `
-e DB_HOST=ors-db `
-e DB_NAME=ors `
-e DB_USER=orsuser `
-e DB_PASSWORD=orspass ors-app
```

**Step 5:**

```
docker ps
docker logs ors-db
docker logs ors-web
```

Open:

```
http://localhost:8080
```

## **2. Jenkins – Maven CI**

**Step 1:** Jenkins → New Item → ORS → Pipeline.

**Step 2:** Configure Git/Maven plugins, JDK and Maven.

**Step 3:** Pipeline:

```
node {
    stage('Checkout') {
        git branch: 'main',
        url: 'https://github.com/ssvkotamraju/ORS.git'
    }

    stage('Clean') {
        bat 'mvn clean'
    }

    stage('Test') {
        bat 'mvn test'
    }

    stage('Package') {
        bat 'mvn package'
    }

    stage('Archive') {
        archiveArtifacts artifacts: '**/target/*.war, **/target/*.jar',
                         allowEmptyArchive: true
    }
}
```

**Step 4:** Poll SCM:

```
H/5 * * * *
```

**Step 5:** Build Now → Console Output → Artifacts.

## **3. Kubernetes – 2 to 5 replicas**

**Step 1:**

```
minikube start --driver=docker
docker build -t ors-app:v1 .
minikube image load ors-app:v1
```

**Step 2:** Create `deployment.yaml`.

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: ors-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: ors
  template:
    metadata:
      labels:
        app: ors
    spec:
      containers:
      - name: ors
        image: ors-app:v1
        imagePullPolicy: IfNotPresent
        ports:
        - containerPort: 8080
```

**Step 3:** Create `service.yaml`.

```
apiVersion: v1
kind: Service
metadata:
  name: ors-service
spec:
  type: NodePort
  selector:
    app: ors
  ports:
  - port: 8080
    targetPort: 8080
    nodePort: 30080
```

**Step 4:**

```
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get pods
kubectl get services
```

**Step 5:**

```
kubectl scale deployment ors-deployment --replicas=5
kubectl get pods
```

**Step 6:**

```
kubectl delete pod POD_NAME
kubectl get pods
```

**Step 7:**

```
kubectl rollout undo deployment/ors-deployment
minikube service ors-service
```

## **4. Nagios**

```
docker pull jasonrivers/nagios:latest
docker run -d --name nagios -p 8082:80 jasonrivers/nagios:latest
docker ps
docker logs nagios
```

Open:

```
http://localhost:8082/nagios
```

Configure host and HTTP/MySQL service checks.

## **5. AWS EC2**

**Step 1:** Launch Ubuntu EC2, download `.pem` key and configure Security Group.

**Step 2:**

```
ssh -i "your-key.pem" ubuntu@EC2-PUBLIC-IP
```

**Step 3:**

```
sudo apt update
sudo apt install openjdk-17-jdk maven git tomcat10 -y
```

**Step 4:**

```
git clone https://github.com/ssvkotamraju/ORS.git
cd ORS
```

**Step 5:**

```
mvn clean test package
```

**Step 6:**

```
sudo cp target/*.war /var/lib/tomcat10/webapps/
sudo systemctl enable tomcat10
sudo systemctl restart tomcat10
```

**Step 7:** Open:

```
http://EC2-PUBLIC-IP:8080/war-filename
```

# **SET–4 – Online Shopping Application**

Repository: [https://github.com/nikithamoturi/OnlineShoppingApp.git](https://github.com/nikithamoturi/OnlineShoppingApp.git?utm_source=chatgpt.com)

## **1. Docker – WordPress + MySQL**

This WordPress task is separate from the Online Shopping GitHub application.

**Step 1:**

```
docker pull wordpress:latest
docker pull mysql:8.0
```

**Step 2:**

```
docker network create shopping-net
docker volume create shopping-db-data
```

**Step 3:**

```
docker run -d --name shopping-db --network shopping-net `
-e MYSQL_ROOT_PASSWORD=root123 `
-e MYSQL_DATABASE=shopping `
-e MYSQL_USER=shopuser `
-e MYSQL_PASSWORD=shop123 `
-v shopping-db-data:/var/lib/mysql mysql:8.0
```

**Step 4:**

```
docker run -d --name shopping-web --network shopping-net `
-p 8080:80 `
-e WORDPRESS_DB_HOST=shopping-db:3306 `
-e WORDPRESS_DB_USER=shopuser `
-e WORDPRESS_DB_PASSWORD=shop123 `
-e WORDPRESS_DB_NAME=shopping wordpress:latest
```

**Step 5:**

```
docker ps
docker logs shopping-db
docker logs shopping-web
```

Open:

```
http://localhost:8080
```

Complete WordPress setup and add sample products.

## **2. Jenkins – Freestyle Project**

**Step 1:** Jenkins → New Item → `OnlineShopping` → Freestyle Project.

**Step 2:** Source Code Management → Git.

Repository:

```
https://github.com/nikithamoturi/OnlineShoppingApp.git
```

Branch:

```
*/main
```

**Step 3:** Build Triggers → Poll SCM.

```
H/5 * * * *
```

**Step 4:** Build Environment/Build Steps → Invoke top-level Maven targets.

Goals:

```
clean test package
```

**Step 5:** Post-build Actions → Archive the artifacts.

```
**/target/*.war
```

**Step 6:** Save → Build Now.

**Step 7:** Check Console Output, Test Result and Build Artifacts.

## **3. Kubernetes – 3 to 5 replicas**

**Step 1:**

```
minikube start --driver=docker
```

**Step 2:** Build and load application image if Dockerfile exists.

```
docker build -t shopping-app:v1 .
minikube image load shopping-app:v1
```

**Step 3:** Create `deployment.yaml`.

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: shopping-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: shopping
  template:
    metadata:
      labels:
        app: shopping
    spec:
      containers:
      - name: shopping
        image: shopping-app:v1
        imagePullPolicy: IfNotPresent
        ports:
        - containerPort: 8080
```

**Step 4:** Create `service.yaml`.

```
apiVersion: v1
kind: Service
metadata:
  name: shopping-service
spec:
  type: NodePort
  selector:
    app: shopping
  ports:
  - port: 8080
    targetPort: 8080
    nodePort: 30080
```

**Step 5:**

```
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get pods
kubectl get services
```

**Step 6: Scale 3 to 5.**

```
kubectl scale deployment shopping-deployment --replicas=5
kubectl get pods
```

**Step 7:**

```
kubectl delete pod POD_NAME
kubectl get pods
```

**Step 8:**

```
kubectl rollout undo deployment/shopping-deployment
minikube service shopping-service
```

## **4. Nagios**

```
docker pull jasonrivers/nagios:latest
docker run -d --name nagios -p 8082:80 jasonrivers/nagios:latest
docker ps
docker logs nagios
```

Open:

```
http://localhost:8082/nagios
```

Configure HTTP and MySQL checks, CPU, memory, disk and uptime.

## **5. AWS EC2 – Online Shopping**

**Step 1:** Launch Ubuntu EC2.

**Step 2:** Security Group: SSH 22 from My IP; HTTP 80 and Tomcat 8080 as required.

**Step 3:**

```
ssh -i "your-key.pem" ubuntu@EC2-PUBLIC-IP
```

**Step 4:**

```
sudo apt update
sudo apt upgrade -y
sudo apt install openjdk-17-jdk maven git tomcat10 -y
```

**Step 5:**

```
git clone https://github.com/nikithamoturi/OnlineShoppingApp.git
cd OnlineShoppingApp
```

**Step 6:**

```
mvn clean package
```

**Step 7:**

```
sudo cp target/*.war /var/lib/tomcat10/webapps/
sudo systemctl enable tomcat10
sudo systemctl restart tomcat10
```

**Step 8:** Open:

```
http://EC2-PUBLIC-IP:8080/war-filename
```

# **SET–5 – Gym Management System**

Repository: [https://github.com/nikithamoturi/GymManagementSystem.git](https://github.com/nikithamoturi/GymManagementSystem.git?utm_source=chatgpt.com)

## **1. Docker – WordPress + MySQL**

This is a separate WordPress portal exercise.

**Step 1:**

```
docker pull wordpress:latest
docker pull mysql:8.0
```

**Step 2:**

```
docker network create gym-net
docker volume create gym-db-data
```

**Step 3:**

```
docker run -d --name gym-db --network gym-net `
-e MYSQL_ROOT_PASSWORD=root123 `
-e MYSQL_DATABASE=gym `
-e MYSQL_USER=gymuser `
-e MYSQL_PASSWORD=gym123 `
-v gym-db-data:/var/lib/mysql mysql:8.0
```

**Step 4:**

```
docker run -d --name gym-web --network gym-net `
-p 8080:80 `
-e WORDPRESS_DB_HOST=gym-db:3306 `
-e WORDPRESS_DB_USER=gymuser `
-e WORDPRESS_DB_PASSWORD=gym123 `
-e WORDPRESS_DB_NAME=gym wordpress:latest
```

**Step 5:**

```
docker ps
docker logs gym-db
docker logs gym-web
```

Open:

```
http://localhost:8080
```

Complete WordPress setup and add gym information.

## **2. Jenkins – Freestyle Project**

**Step 1:** Jenkins → New Item → `GymManagement` → Freestyle Project.

**Step 2:** Source Code Management → Git.

```
https://github.com/nikithamoturi/GymManagementSystem.git
```

Branch:

```
*/main
```

**Step 3:** Build Triggers → Poll SCM.

```
H/5 * * * *
```

**Step 4:** Build Steps → Invoke top-level Maven targets.

```
clean test package
```

**Step 5:** Post-build Actions → Archive artifacts.

```
**/target/*.war
```

**Step 6:** Save → Build Now → Console Output.

## **3. Kubernetes – 2 to 5 replicas**

**Step 1:**

```
minikube start --driver=docker
docker build -t gym-app:v1 .
minikube image load gym-app:v1
```

**Step 2:** Create `deployment.yaml`.

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: gym-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: gym
  template:
    metadata:
      labels:
        app: gym
    spec:
      containers:
      - name: gym
        image: gym-app:v1
        imagePullPolicy: IfNotPresent
        ports:
        - containerPort: 8080
```

**Step 3:** Create `service.yaml`.

```
apiVersion: v1
kind: Service
metadata:
  name: gym-service
spec:
  type: NodePort
  selector:
    app: gym
  ports:
  - port: 8080
    targetPort: 8080
    nodePort: 30080
```

**Step 4:**

```
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get pods
kubectl get services
```

**Step 5:**

```
kubectl scale deployment gym-deployment --replicas=5
kubectl get pods
```

**Step 6:**

```
kubectl delete pod POD_NAME
kubectl get pods
```

**Step 7:**

```
kubectl rollout undo deployment/gym-deployment
minikube service gym-service
```

## **4. Nagios**

```
docker pull jasonrivers/nagios:latest
docker run -d --name nagios -p 8082:80 jasonrivers/nagios:latest
docker ps
docker logs nagios
```

Open:

```
http://localhost:8082/nagios
```

Configure CPU, memory, disk, uptime, HTTP and MySQL checks.

## **5. AWS EC2**

**Step 1:** Launch Ubuntu EC2 and configure Security Group.

**Step 2:**

```
ssh -i "your-key.pem" ubuntu@EC2-PUBLIC-IP
```

**Step 3:**

```
sudo apt update
sudo apt install openjdk-17-jdk maven git tomcat10 -y
```

**Step 4:**

```
git clone https://github.com/nikithamoturi/GymManagementSystem.git
cd GymManagementSystem
```

**Step 5:**

```
mvn clean package
```

**Step 6:**

```
sudo cp target/*.war /var/lib/tomcat10/webapps/
sudo systemctl enable tomcat10
sudo systemctl restart tomcat10
```

**Step 7:**

```
http://EC2-PUBLIC-IP:8080/war-filename
```

# **SET–6 – Vehicle Rental Management System**

Repository: [https://github.com/nikithamoturi/VehicleRentalManagementSystem.git](https://github.com/nikithamoturi/VehicleRentalManagementSystem.git?utm_source=chatgpt.com)

## **1. Docker – WordPress + MySQL**

**Step 1:**

```
docker pull wordpress:latest
docker pull mysql:8.0
```

**Step 2:**

```
docker network create rental-net
docker volume create rental-db-data
```

**Step 3:**

```
docker run -d --name rental-db --network rental-net `
-e MYSQL_ROOT_PASSWORD=root123 `
-e MYSQL_DATABASE=rental `
-e MYSQL_USER=rentaluser `
-e MYSQL_PASSWORD=rental123 `
-v rental-db-data:/var/lib/mysql mysql:8.0
```

**Step 4:**

```
docker run -d --name rental-web --network rental-net `
-p 8080:80 `
-e WORDPRESS_DB_HOST=rental-db:3306 `
-e WORDPRESS_DB_USER=rentaluser `
-e WORDPRESS_DB_PASSWORD=rental123 `
-e WORDPRESS_DB_NAME=rental wordpress:latest
```

**Step 5:**

```
docker ps
docker logs rental-db
docker logs rental-web
```

Open:

```
http://localhost:8080
```

Complete WordPress setup and add sample rental information.

## **2. Jenkins – Freestyle Project**

**Step 1:** Jenkins → New Item → `VehicleRental` → Freestyle Project.

**Step 2:** Source Code Management → Git.

```
https://github.com/nikithamoturi/VehicleRentalManagementSystem.git
```

Branch:

```
*/main
```

**Step 3:** Build Triggers → Poll SCM.

```
H/5 * * * *
```

**Step 4:** Build Steps → Invoke top-level Maven targets.

```
clean test package
```

**Step 5:** Post-build Actions → Archive artifacts.

```
**/target/*.war
```

**Step 6:** Save → Build Now → Console Output → Test Result → Artifacts.

## **3. Kubernetes – 2 to 4 replicas**

**Step 1:**

```
minikube start --driver=docker
docker build -t rental-app:v1 .
minikube image load rental-app:v1
```

**Step 2:** Create `deployment.yaml`.

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: rental-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: rental
  template:
    metadata:
      labels:
        app: rental
    spec:
      containers:
      - name: rental
        image: rental-app:v1
        imagePullPolicy: IfNotPresent
        ports:
        - containerPort: 8080
```

**Step 3:** Create `service.yaml`.

```
apiVersion: v1
kind: Service
metadata:
  name: rental-service
spec:
  type: NodePort
  selector:
    app: rental
  ports:
  - port: 8080
    targetPort: 8080
    nodePort: 30080
```

**Step 4:**

```
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get pods
kubectl get services
```

**Step 5:**

```
kubectl scale deployment rental-deployment --replicas=4
kubectl get pods
```

**Step 6:**

```
kubectl delete pod POD_NAME
kubectl get pods
```

**Step 7:**

```
kubectl rollout undo deployment/rental-deployment
minikube service rental-service
```

## **4. Nagios**

```
docker pull jasonrivers/nagios:latest
docker run -d --name nagios -p 8082:80 jasonrivers/nagios:latest
docker ps
docker logs nagios
```

Open:

```
http://localhost:8082/nagios
```

Configure host, HTTP, MySQL/TCP, CPU, memory, disk and uptime checks.

## **5. AWS EC2**

**Step 1:** Launch Ubuntu EC2 and configure SSH, HTTP and application ports.

**Step 2:**

```
ssh -i "your-key.pem" ubuntu@EC2-PUBLIC-IP
```

**Step 3:**

```
sudo apt update
sudo apt install openjdk-17-jdk maven git tomcat10 -y
```

**Step 4:**

```
git clone https://github.com/nikithamoturi/VehicleRentalManagementSystem.git
cd VehicleRentalManagementSystem
```

**Step 5:**

```
mvn clean package
```

**Step 6:**

```
sudo cp target/*.war /var/lib/tomcat10/webapps/
sudo systemctl enable tomcat10
sudo systemctl restart tomcat10
```

**Step 7:**

```
http://EC2-PUBLIC-IP:8080/war-filename
```

# **SET–7 – SportSystem**

Repository: [https://github.com/sarasrija/SportSystem.git](https://github.com/sarasrija/SportSystem.git?utm_source=chatgpt.com)

## **1. Jenkins – Scripted Pipeline**

**Step 1:** Open Jenkins → Manage Jenkins → Tools.

Configure Maven with name:

```
Maven3
```

**Step 2:** New Item → `SportSystem` → Pipeline.

**Step 3:** Paste this Scripted Pipeline (Windows agent):

```
node {
    stage('Clean Workspace') {
        cleanWs()
    }

    stage('Clone') {
        git branch: 'main',
        url: 'https://github.com/sarasrija/SportSystem.git'
    }

    stage('Clean') {
        def mvn = tool 'Maven3'
        bat "\"${mvn}\\bin\\mvn\" clean"
    }

    stage('Compile') {
        def mvn = tool 'Maven3'
        bat "\"${mvn}\\bin\\mvn\" compile"
    }

    stage('Package') {
        def mvn = tool 'Maven3'
        bat "\"${mvn}\\bin\\mvn\" package"
    }

    stage('Archive') {
        archiveArtifacts artifacts: '**/target/*.war'
    }
}
```

**Step 4:** Configure GitHub trigger or Poll SCM.

```
H/5 * * * *
```

**Step 5:** Build Now → Console Output.

## **2. AWS EC2 – Maven + Tomcat**

**Step 1:** Launch Ubuntu EC2. Configure SSH 22 and Tomcat 8080.

**Step 2:**

```
ssh -i "your-key.pem" ubuntu@EC2-PUBLIC-IP
```

**Step 3:**

```
sudo apt update
sudo apt install openjdk-17-jdk git maven tomcat10 -y
```

**Step 4:**

```
git clone https://github.com/sarasrija/SportSystem.git
cd SportSystem
```

**Step 5:**

```
mvn clean package
```

**Step 6:**

```
sudo cp target/*.war /var/lib/tomcat10/webapps/
sudo systemctl enable tomcat10
sudo systemctl restart tomcat10
```

**Step 7:** Open:

```
http://EC2-PUBLIC-IP:8080/war-filename
```

For a stable public IP, allocate and associate an Elastic IP.

## **3. Kubernetes + Nagios**

**Step 1:**

```
minikube start --driver=docker
docker build -t sports-app:v1 .
minikube image load sports-app:v1
```

**Step 2:** Create `deployment.yaml`.

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: sports-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: sports
  template:
    metadata:
      labels:
        app: sports
    spec:
      containers:
      - name: sports
        image: sports-app:v1
        imagePullPolicy: IfNotPresent
        ports:
        - containerPort: 8080
```

**Step 3:** Create `service.yaml`.

```
apiVersion: v1
kind: Service
metadata:
  name: sports-service
spec:
  type: NodePort
  selector:
    app: sports
  ports:
  - port: 8080
    targetPort: 8080
    nodePort: 30080
```

**Step 4:**

```
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get pods
kubectl get services
```

**Step 5:**

```
kubectl scale deployment sports-deployment --replicas=5
kubectl get pods
```

**Step 6:**

```
kubectl describe pod POD_NAME
kubectl logs POD_NAME
kubectl get events
```

**Step 7:**

```
kubectl rollout undo deployment/sports-deployment
minikube service sports-service
```

**Step 8:** Start Nagios.

```
docker pull jasonrivers/nagios:latest
docker run -d --name nagios -p 8082:80 jasonrivers/nagios:latest
docker ps
docker logs nagios
```

Open:

```
http://localhost:8082/nagios
```

## **4. Docker Compose – Flask + PostgreSQL + Redis**

**Step 1:** Create folder.

```
mkdir SportsCompose
cd SportsCompose
mkdir web
```

**Step 2:** Create `docker-compose.yml`.

```
services:
  web:
    build: ./web
    container_name: sports-web
    ports:
      - "5000:5000"
    depends_on:
      - db
      - redis
    networks:
      - sports-network

  db:
    image: postgres:15
    container_name: sports-db
    environment:
      POSTGRES_DB: sportsdb
      POSTGRES_USER: sportsuser
      POSTGRES_PASSWORD: sports123
    volumes:
      - sports-data:/var/lib/postgresql/data
    networks:
      - sports-network

  redis:
    image: redis:latest
    container_name: sports-redis
    networks:
      - sports-network

networks:
  sports-network:
    driver: bridge

volumes:
  sports-data:
```

**Step 3:** Inside `web`, create `requirements.txt`.

```
Flask
psycopg2-binary
redis
```

**Step 4:** Create `web/Dockerfile`.

```
FROM python:3.11
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
EXPOSE 5000
CMD ["python", "app.py"]
```

**Step 5:** Create `web/app.py`.

```
from flask import Flaskapp = Flask(__name__)@app.route("/")def home():    return "Sports Management System is running"if __name__ == "__main__":    app.run(host="0.0.0.0", port=5000)
```

**Step 6:** Run Compose.

```
docker compose up -d --build
```

**Step 7:** Check.

```
docker compose ps
docker compose logs
```

Open:

```
http://localhost:5000
```

**Step 8:** Scale web.

```
docker compose up -d --scale web=3
```

**Step 9:** Stop and remove.

```
docker compose stop
docker compose start
docker compose down
```

# **SET–8 – Blood Bank System**

Repository: [https://github.com/sarasrija/BloodBanksystem.git](https://github.com/sarasrija/BloodBanksystem.git?utm_source=chatgpt.com)

## **1. Jenkins – Scripted Pipeline**

**Step 1:** Configure Maven in Jenkins Tools with name `Maven3`.

**Step 2:** New Item → `BloodBank` → Pipeline.

**Step 3:** Paste:

```
node {
    stage('Clean Workspace') {
        cleanWs()
    }

    stage('Clone') {
        git branch: 'main',
        url: 'https://github.com/sarasrija/BloodBanksystem.git'
    }

    stage('Clean') {
        def mvn = tool 'Maven3'
        bat "\"${mvn}\\bin\\mvn\" clean"
    }

    stage('Install') {
        def mvn = tool 'Maven3'
        bat "\"${mvn}\\bin\\mvn\" install -DskipTests"
    }

    stage('Test') {
        def mvn = tool 'Maven3'
        bat "\"${mvn}\\bin\\mvn\" test"
    }

    stage('Package') {
        def mvn = tool 'Maven3'
        bat "\"${mvn}\\bin\\mvn\" package"
    }

    stage('Archive') {
        archiveArtifacts artifacts: '**/target/*.war',
                         allowEmptyArchive: true
    }
}
```

**Step 4:** Build Now → Console Output.

## **2. AWS EC2 – Static Website / Java Application**

**Step 1:** Launch Ubuntu EC2 and configure HTTP 80 and SSH 22.

**Step 2:**

```
ssh -i "your-key.pem" ubuntu@EC2-PUBLIC-IP
```

**Step 3:** Install Apache.

```
sudo apt update
sudo apt install apache2 git -y
sudo systemctl start apache2
sudo systemctl enable apache2
```

**Step 4:** Clone repository.

```
git clone https://github.com/sarasrija/BloodBanksystem.git
cd BloodBanksystem
```

**Step 5:** For static website deployment, copy `index.html`.

```
sudo cp index.html /var/www/html/
sudo chmod 644 /var/www/html/index.html
sudo systemctl restart apache2
```

**Step 6:** Test.

```
curl localhost
sudo systemctl status apache2
```

Open:

```
http://EC2-PUBLIC-IP
```

**For Maven WAR application instead:**

```
sudo apt install openjdk-17-jdk maven tomcat10 -y
mvn clean package
sudo cp target/*.war /var/lib/tomcat10/webapps/
sudo systemctl restart tomcat10
```

## **3. Kubernetes + Nagios**

**Step 1:**

```
minikube start --driver=docker
docker build -t bloodbank-app:v1 .
minikube image load bloodbank-app:v1
```

**Step 2:** Create `deployment.yaml`.

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: bloodbank-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: bloodbank
  template:
    metadata:
      labels:
        app: bloodbank
    spec:
      containers:
      - name: bloodbank
        image: bloodbank-app:v1
        imagePullPolicy: IfNotPresent
        ports:
        - containerPort: 8080
```

**Step 3:** Create `service.yaml`.

```
apiVersion: v1
kind: Service
metadata:
  name: bloodbank-service
spec:
  type: NodePort
  selector:
    app: bloodbank
  ports:
  - port: 8080
    targetPort: 8080
    nodePort: 30080
```

**Step 4:**

```
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get pods
kubectl get services
```

**Step 5:**

```
kubectl scale deployment bloodbank-deployment --replicas=4
kubectl get pods
```

**Step 6:**

```
kubectl get events
kubectl describe pod POD_NAME
kubectl logs POD_NAME
kubectl rollout undo deployment/bloodbank-deployment
```

**Step 7:** Start Nagios.

```
docker pull jasonrivers/nagios:latest
docker run -d --name nagios -p 8082:80 jasonrivers/nagios:latest
docker ps
docker logs nagios
```

Open:

```
http://localhost:8082/nagios
```

## **4. Docker Compose – Nginx + PostgreSQL 15**

**Step 1:** Create folder.

```
mkdir BloodBankCompose
cd BloodBankCompose
```

**Step 2:** Create `docker-compose.yml`.

```
services:
  web:
    image: nginx:latest
    container_name: bloodbank-web
    ports:
      - "8080:80"
    depends_on:
      - db
    networks:
      - bloodbank-network

  db:
    image: postgres:15
    container_name: bloodbank-db
    environment:
      POSTGRES_DB: bloodbank
      POSTGRES_USER: blooduser
      POSTGRES_PASSWORD: blood123
    volumes:
      - bloodbank-data:/var/lib/postgresql/data
    networks:
      - bloodbank-network

networks:
  bloodbank-network:
    driver: bridge

volumes:
  bloodbank-data:
```

**Step 3:** Run.

```
docker compose up -d
```

**Step 4:** Verify.

```
docker compose ps
docker compose logs
```

**Step 5:** Access Nginx.

```
http://localhost:8080
```

**Step 6:** Connect to PostgreSQL.

```
docker exec -it bloodbank-db psql -U blooduser -d bloodbank
```

**Step 7:** Create a table.

```
CREATE TABLE donors (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    blood_group VARCHAR(10)
);

INSERT INTO donors(name, blood_group)
VALUES ('Rahul', 'O+');

SELECT * FROM donors;

\q
```

**Step 8:** Stop/start/remove.

```
docker compose stop
docker compose start
docker compose down
```

The named volume remains after `docker compose down`.

To delete volume too:

```
docker compose down -v
```

# **SET–9 – Apartment Management System**

Repository: [https://github.com/sarasrija/ApartmentSystem.git](https://github.com/sarasrija/ApartmentSystem.git?utm_source=chatgpt.com)

## **1. Jenkins – GitHub Webhook + ngrok + Tomcat**

**Step 1:** Start Jenkins.

```
http://localhost:8080
```

**Step 2:** Start ngrok in PowerShell.

```
ngrok http 8080
```

Copy the HTTPS forwarding URL.

**Step 3:** GitHub → Repository → Settings → Webhooks → Add Webhook.

Payload URL:

```
https://YOUR-NGROK-URL/github-webhook/
```

Content type:

```
application/json
```

Select:

```
Just the push event
```

**Step 4:** Configure Jenkins plugins: Git, GitHub Integration, Pipeline and Pipeline Stage View.

**Step 5:** Configure Maven in:

`Manage Jenkins → Tools`

Name:

```
Maven3
```

**Step 6:** New Item → `ApartmentSystem` → Pipeline.

**Step 7:** Paste Jenkinsfile.

```
node {
    stage('Clean Workspace') {
        cleanWs()
    }

    stage('Clone') {
        git branch: 'main',
        url: 'https://github.com/sarasrija/ApartmentSystem.git'
    }

    stage('Clean') {
        def mvn = tool 'Maven3'
        bat "\"${mvn}\\bin\\mvn\" clean"
    }

    stage('Compile') {
        def mvn = tool 'Maven3'
        bat "\"${mvn}\\bin\\mvn\" compile"
    }

    stage('Test') {
        def mvn = tool 'Maven3'
        bat "\"${mvn}\\bin\\mvn\" test"
    }

    stage('Package') {
        def mvn = tool 'Maven3'
        bat "\"${mvn}\\bin\\mvn\" package"
    }

    stage('Archive') {
        archiveArtifacts artifacts: '**/target/*.war'
    }
}
```

**Step 8:** Under Build Triggers, select:

```
GitHub hook trigger for GITScm polling
```

Save.

**Step 9:** Test GitHub push.

```
git add .
git commit -m "Test webhook"
git push origin main
```

**Step 10:** Check Jenkins Build History and Console Output.

**Step 11:** Create Pipeline View.

- Dashboard → New View.
- Name: `ApartmentPipeline`.
- Select Pipeline View.
- Select `ApartmentSystem` as initial job.
- Save.

**Step 12:** Deploy WAR to Tomcat.

Copy generated WAR from:

```
target/
```

Into Tomcat's:

```
webapps/
```

Restart Tomcat and open the deployed application URL.

## **2. AWS EC2 – Docker + Tomcat**

**Step 1:** Launch Ubuntu EC2 (`t2.micro` if eligible).

**Step 2:** Configure Security Group:

| Type       | Port | Source           |
| ---------- | ---- | ---------------- |
| SSH        | 22   | My IP            |
| Custom TCP | 8090 | Required clients |

**Step 3:** Connect.

```
ssh -i "your-key.pem" ubuntu@EC2-PUBLIC-IP
```

**Step 4:** Install Docker and Git.

```
sudo apt update
sudo apt upgrade -y
sudo apt install docker.io git openjdk-17-jdk maven -y

sudo systemctl start docker
sudo systemctl enable docker
```

**Step 5:** Clone repository.

```
git clone https://github.com/sarasrija/ApartmentSystem.git
cd ApartmentSystem
```

**Step 6:** Build Maven WAR.

```
mvn clean package
```

**Step 7:** Create `Dockerfile`.

```
FROM tomcat:10.1-jdk17

RUN rm -rf /usr/local/tomcat/webapps/*

COPY target/*.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080

CMD ["catalina.sh", "run"]
```

**Step 8:** Build image.

```
sudo docker build -t apartment-app .
```

**Step 9:** Run container.

```
sudo docker run -d --name apartment-container -p 8090:8080 apartment-app
```

**Step 10:** Check.

```
sudo docker ps
sudo docker logs apartment-container
```

**Step 11:** Open:

```
http://EC2-PUBLIC-IP:8090
```

## **3. Kubernetes – 4 replicas + Nagios**

**Step 1:**

```
minikube start --driver=docker
docker build -t apartment-app:v1 .
minikube image load apartment-app:v1
```

**Step 2:** Create `deployment.yaml`.

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: apartment-deployment
spec:
  replicas: 4
  selector:
    matchLabels:
      app: apartment
  template:
    metadata:
      labels:
        app: apartment
    spec:
      containers:
      - name: apartment
        image: apartment-app:v1
        imagePullPolicy: IfNotPresent
        ports:
        - containerPort: 8080
```

**Step 3:** Create `service.yaml`.

```
apiVersion: v1
kind: Service
metadata:
  name: apartment-service
spec:
  type: NodePort
  selector:
    app: apartment
  ports:
  - port: 8080
    targetPort: 8080
    nodePort: 30080
```

**Step 4:**

```
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```

**Step 5:** Check four replicas.

```
kubectl get deployments
kubectl get pods
kubectl get services
```

**Step 6:** Scale.

```
kubectl scale deployment apartment-deployment --replicas=6
kubectl get pods
```

**Step 7:** Test pod recovery.

```
kubectl delete pod POD_NAME
kubectl get pods
```

**Step 8:** Test local access.

```
kubectl port-forward service/apartment-service 8081:8080
```

Open:

```
http://localhost:8081
```

**Step 9:** Run Nagios.

```
docker pull jasonrivers/nagios:latest
docker run -d --name nagios -p 8082:80 jasonrivers/nagios:latest
docker ps
docker logs nagios
```

Open:

```
http://localhost:8082/nagios
```

Resource metrics, where Metrics Server is installed:

```
kubectl top nodes
kubectl top pods
```

Configure Nagios host/service checks for CPU, memory, disk, uptime and HTTP application availability.

## **4. Docker Compose – Nginx + PostgreSQL 15**

**Step 1:** Create folder.

```
mkdir compose-lab
cd compose-lab
```

**Step 2:** Create `index.html`.

```
<!DOCTYPE html>
<html>
<head>
    <title>Apartment Management</title>
</head>
<body>
    <h1>Apartment Management System</h1>
    <p>Docker Compose is working!</p>
</body>
</html>
```

**Step 3:** Create `docker-compose.yml`.

```
version: "3.9"

services:
  web:
    image: nginx:latest
    container_name: apartment-web
    ports:
      - "8080:80"
    volumes:
      - ./index.html:/usr/share/nginx/html/index.html:ro
    depends_on:
      - db
    networks:
      - apartment-network

  db:
    image: postgres:15
    container_name: apartment-db
    restart: always
    environment:
      POSTGRES_DB: apartmentdb
      POSTGRES_USER: admin
      POSTGRES_PASSWORD: admin123
    volumes:
      - postgres-data:/var/lib/postgresql/data
    networks:
      - apartment-network

networks:
  apartment-network:
    driver: bridge

volumes:
  postgres-data:
```

**Step 4:** Start containers.

```
docker compose up -d
```

**Step 5:** Verify.

```
docker compose ps
docker compose logs
```

**Step 6:** Open browser.

```
http://localhost:8080
```

**Step 7:** Connect to PostgreSQL.

```
docker exec -it apartment-db psql -U admin -d apartmentdb
```

**Step 8:** Create table.

```
CREATE TABLE residents (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    apartment_no VARCHAR(20)
);

INSERT INTO residents(name, apartment_no)
VALUES ('Rahul', 'A101');

SELECT * FROM residents;

\q
```

**Step 9:** Lifecycle commands.

```
docker compose stop
docker compose start
docker compose down
docker compose up -d --build
```

**Step 10:** Remove volume only if data deletion is intended.

```
docker compose down -v
```

# **Final quick command sheet – memorize these**

## **Docker**

| Task                    | Command                           |
| ----------------------- | --------------------------------- |
| Pull image              | `docker pull IMAGE`               |
| List images             | `docker images`                   |
| Run container           | `docker run -d --name NAME IMAGE` |
| List running containers | `docker ps`                       |
| List all containers     | `docker ps -a`                    |
| View logs               | `docker logs NAME`                |
| Stop                    | `docker stop NAME`                |
| Start                   | `docker start NAME`               |
| Restart                 | `docker restart NAME`             |
| Remove                  | `docker rm -f NAME`               |
| Create network          | `docker network create NAME`      |
| Create volume           | `docker volume create NAME`       |

## **Jenkins**

| Task                | Where / Command              |
| ------------------- | ---------------------------- |
| New job             | New Item                     |
| Maven configuration | Manage Jenkins → Tools       |
| Git repository      | Source Code Management → Git |
| Maven goals         | `clean test package`         |
| Poll SCM            | `H/5 * * * *`                |
| Archive WAR         | `**/target/*.war`            |
| Build               | Build Now                    |
| Logs                | Console Output               |

## **Kubernetes**

| Task                  | Command                                       |
| --------------------- | --------------------------------------------- |
| Start cluster         | `minikube start --driver=docker`              |
| Apply YAML            | `kubectl apply -f deployment.yaml`            |
| View pods             | `kubectl get pods`                            |
| View services         | `kubectl get services`                        |
| Describe pod          | `kubectl describe pod POD_NAME`               |
| View logs             | `kubectl logs POD_NAME`                       |
| Scale                 | `kubectl scale deployment NAME --replicas=5`  |
| Delete pod            | `kubectl delete pod POD_NAME`                 |
| Rollback              | `kubectl rollout undo deployment/NAME`        |
| Port forwarding       | `kubectl port-forward service/NAME 8081:8080` |
| Open Minikube service | `minikube service SERVICE_NAME`               |
| Resource metrics      | `kubectl top pods`                            |

## **AWS Ubuntu**

```
sudo apt update
sudo apt upgrade -y
sudo apt install docker.io git openjdk-17-jdk maven -y
sudo systemctl start docker
sudo systemctl enable docker
sudo docker ps
sudo docker logs CONTAINER_NAME
```

## **Important corrections to remember during the exam**

1. **Sets 1–3:** Docker application tasks are separate from Jenkins Maven CI. Use the actual database and application image specified in your paper.
2. **Sets 4–6:** Docker task is a standalone WordPress + MySQL portal; it does not use the GitHub Java project.
3. **Sets 4–6:** Jenkins is a Freestyle Project, not a Scripted Pipeline.
4. **Sets 7–9:** Jenkins uses Scripted Pipeline; Sets 7 and 8 also have AWS, Kubernetes/Nagios and Docker Compose.
5. **Set 9:** Initial Kubernetes replicas must be 4.
6. **Set 4:** Initial Kubernetes replicas must be 3.
7. **Set 6:** Initial Kubernetes replicas must be 2 and scaled to 4.
8. **Set 8:** PostgreSQL version must be 15.
9. **Set 9:** PostgreSQL version must be 15.

**Very important:** Image names such as `apartment-app:v1` and `sports-app:v1` are examples that you build locally. The original question papers do not provide prebuilt images or confirm that every GitHub repository has a Dockerfile, Maven `pom.xml` or WAR output. Check the repository files before executing the corresponding build command.
