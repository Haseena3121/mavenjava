# **Part Maven pom.xml File — Theory and PurposeMaven’s core file is the POM (pom.xml), which defines a project’s structure, dependencies, build lifecycle, and plugins using a standardized, declarative model.
📘 What Maven Is
Maven is a build automation and dependency‑management tool for Java projects. Its theory is based on convention over configuration, meaning Maven expects projects to follow a standard layout so the configuration file stays simple.
.
 
 10: Working with Minikube and Nagios**

# **Part A — Minikube (Kubernetes)**
```
minikube start
kubectl get nodes
kubectl create deployment nginx --image=nginx
kubectl get pods
kubectl scale deployment nginx --replicas=3
kubectl get pods
kubectl delete deployment nginx
minikube stop
```
```
docker pull nginx
docker run -d --name nginx-server -p 8080:80 nginx
docker ps
http://localhost:8080
docker stop nginx-server
```
```
docker pull jasonrivers/nagios
docker run -d --name nagios -p 8080:80 jasonrivers/nagios
docker ps
docker logs nagios
```
## **Step 1: Start Minikube**

Open CMD or PowerShell:

```
minikube start
```


```
minikube status
```

Expected: Minikube components should show `Running`.

## **Step 2: Create Nginx deployment**

```
kubectl create deployment mynginx --image=nginx
```

This creates a Deployment named `mynginx` using the Nginx image.

## **Step 3: Check deployment**

```
kubectl get deployments
```

Expected output:

```
NAME       READY   UP-TO-DATE   AVAILABLE   AGE
mynginx   1/1     1            1          10s
```

## **Step 4: Check Pods**

```
kubectl get pods
```

Expected:

```
NAME                        READY   STATUS    RESTARTS   AGE
mynginx-xxxxxxxxxx-xxxxx    1/1     Running   0          20s
```

Important output to show examiner: `STATUS = Running` and `READY = 1/1`

## **Step 5: Describe the Pod**

```
kubectl describe pods
```

This displays detailed information about the Pod, such as:

- Pod name
- Namespace
- Node
- Status
- IP address
- Events

Expected: Pod details are displayed, and you should see it is running without errors.

## **Step 6: Expose Nginx as a Service**

```
kubectl expose deployment mynginx --type=NodePort --port=80 --target-port=80
```

This exposes the deployment as a Service.

Check the Service:

```
kubectl get services
```

Expected output similar to:

```
NAME       TYPE       CLUSTER-IP      PORT(S)        AGE
mynginx    NodePort   10.x.x.x       80:xxxxx/TCP   10s
```

The IP and NodePort values will be different on your system.

## **Step 7: Scale the deployment to 4 Pods**

This is a very important step for your external.

```
kubectl scale deployment mynginx --replicas=4
```

Now check:

```
kubectl get pods
```

Expected:

```
NAME                         READY   STATUS
mynginx-xxxx-1                1/1     Running
mynginx-xxxx-2                1/1     Running
mynginx-xxxx-3                1/1     Running
mynginx-xxxx-4                1/1     Running
```

Check deployment:

```
kubectl get deployments
```

Expected:

```
NAME       READY   UP-TO-DATE   AVAILABLE
mynginx    4/4     4            4
```

Your scaling output should show 4/4

This means Kubernetes is managing four replicas of your Nginx deployment.

## **Step 8: Access Nginx in your browser**

Your manual gives this port-forwarding method:

```
kubectl port-forward svc/mynginx 8081:80
```

Keep this terminal open while testing.

Now open:

[http://localhost:8081](http://localhost:8081?utm_source=chatgpt.com)

Expected browser output:

[Exploring Microsoft Radius Application Platform - The New Stack](https://images.openai.com/static-rsc-4/TVh8NxOjrWasvQG3Ae95i_dL5bEu1nzCiftb6WYyr_LjVr4xiLzAtNVMkOMzC6ltoVuIbgWdRjISZ7WqIkfxo7zjjKHoeRP3LtK6wQOdnmlLpvhqERsg61q_SmMtQ8oMgSVNPldOcUffitxZS8h-BHqaUXWQmQKL24qPYpJdOz0?purpose=inline)

You should see:

**Welcome to nginx!**

This means the Nginx web server is successfully running.

If it doesn't work, your manual also mentions trying the Minikube tunnel:

```
minikube tunnel
```

And retrieving the service URL:

```
minikube service mynginx --url
```

The URL returned by Minikube can be opened in the browser.



SE_record_final (1)(1).pdf

SE_record_final (1)(1).pdf



# **Part B — Nagios Monitoring using Docker**

Nagios is a monitoring tool used to monitor **servers, network devices, applications, and services**. It alerts administrators when problems occur.&#x20;

SE_record_final (1)(1).pdf



## **Step 1: Pull the Nagios image**

Open a **new CMD terminal** (you can keep the Minikube port-forward terminal open).

```
docker pull jasonrivers/nagios:latest
```

Expected output:

```
latest: Pulling from jasonrivers/nagios
...
Status: Downloaded newer image
```

Image downloaded successfully.

## **Step 2: Run Nagios container**

```
docker run --name nagiosdemo -p 8888:80 jasonrivers/nagios:latest
```

This command:

- `docker run` → creates and runs the container
- `--name nagiosdemo` → names the container
- `-p 8888:80` → maps your computer's port 8888 to the container's port 80
- `jasonrivers/nagios:latest` → Nagios image

Wait for the container startup logs.

You should see startup messages in the terminal, indicating that the Nagios services are starting.

## **Step 3: Open Nagios dashboard**

Open your browser:

[http://localhost:8888](http://localhost:8888?utm_source=chatgpt.com)

You should get the Nagios login page.

[Use this Nagios monitoring tutorial for proactive IT monitoring | TechTarget](https://images.openai.com/static-rsc-4/HG38HGF8Vsz7FBy2ngR8CflhEwxkabu6MwwDcYYdKrSULgRlQ-ID-ZkjA47B50QvSPQBjvw6EiPGNHKvXuxylja7xtcuMnM25FhggIXbzHhQzliK9Uuh5BqdBNEaDWD7iu-3AyYl_UrYbA8k2KRGhRVQUNxkrnfMgTh4syXDI0o?purpose=inline)

[\[5 Mins Docker\] Install Open Source Monitoring System - Nagios Core - NetSec](https://images.openai.com/static-rsc-4/oxghDackJTNit0xRpKBjvkhfxb-ZUPEFRhQ6v7-kLZc2X3CzqamkV2YxxECN03j_8uWuVqtKr4TFr3nw7VGACHaQOP4vKWd9fdKul3ZmpWXER5NCy02gdj6rSxX7Y-HHo7JhnwqA8g6O2pDqbaPPqWGFvdTrTq1vsRrP-10LWl4?purpose=inline)

[How to Install Nagios Core by Docker on Ubuntu 21.04 | LinuxHelp Tutorials](https://images.openai.com/static-rsc-4/N-8EO_UytK6lQFQHX8Y9gHXKq8epao9lha7FC9uAl1NEMRTec_1bKXQcwuikBGitIjjCNl6lXGMJBg4EZiey_WhECrqkVWFO08p9MZe5k0-KcZ2vZxZ6sQe33-8xARfh8erbcwCwqMt4EXJ7l9uRVorasRYJhtxticjtYZWL1Qc?purpose=inline)

5

Log in using the credentials configured for the image/manual setup.

If you reach the dashboard, Nagios is running successfully.

## **Step 4: What output should you show?**

## **Nagios expected practical output**

[Ubuntu 14.04 LTS : Nagios : Notification Setting : Server World](https://images.openai.com/static-rsc-4/9cg7K788CVwDtmALMEFl_6yIRJHXIeFSjSIV1xRyKsUZYPaTIxQB8tVUsC8Q4ybVcsHViJh-08D4295xhp-dPHVaCvJJBjxyIksFljApWK7M9Cew3a4uyNKW4xhgW-a5db8Z8VbBSX4UB_eWoC0QWR4RFWklJEUtZ_THnPGLytI?purpose=inline)

**Nagios Web Dashboard**

Dashboard visible in browser

Monitoring interface opens at localhost:8888

For your practical screenshot, capture:

1. Docker image downloaded.
2. Nagios container running.
3. Nagios web interface/login page.
4. Nagios dashboard after login, if you can reach it.

The **browser dashboard is the main visible output** of the Nagios task.

## **Step 5: Login to Nagios**

Your lab manual gives these credentials:

**Nagios login credentials**

| Field    | Value         |
| -------- | ------------- |
| Username | `nagiosadmin` |
| Password | `nagios`      |

After login, explore these sections:

- **Hosts** — view monitored systems.
- **Services** — view monitored services.
- **Alerts** — view recent notifications.

LAB RECORD_5F6 (1)(1).docx

### **Is reaching the sign-in page enough?**

**Yes, it is a valid output for the Nagios installation/startup portion.** But for the best external demonstration, try to log in and show the dashboard as well. Your manual specifically asks you to explore Hosts, Services, and Alerts.

If you only reach the login screen, show your examiner:

- Docker container running
- Port mapping `8888:80`
- Nagios login page at `localhost:8888`

# **Part C — Stop and clean up**

### **Stop Minikube**

```
minikube stop
```

Optional deletion:

```
minikube delete
```

### **Stop Nagios**

Open another terminal:

```
docker stop nagiosdemo
```

Remove the container:

```
docker rm nagiosdemo
```

Optional — remove the image:

```
docker images
docker rmi jasonrivers/nagios:latest
```



SE_record_final (1)(1).pdf

LAB RECORD_5F6 (1)(1).docx



# **Final outputs to show in the external**

## **Minikube output checklist**

- `minikube status` — cluster running
- `kubectl get deployments` — Nginx deployment visible
- `kubectl get pods` — Pod in Running status
- `kubectl describe pods` — details shown
- `kubectl get services` — Nginx service visible
- `kubectl scale ... --replicas=4` — 4 Pods
- `localhost:8081` — Nginx Welcome page

## **Nagios output checklist**

- Docker image pulled
- Nagios container started
- `docker ps` shows Nagios running
- `localhost:8888` opens Nagios login page
- Login with `nagiosadmin` / `nagios`
- Dashboard/Hosts/Services visible

## **The easiest way to remember Experiment 10**

Minikube → Deploy Nginx → Check Pods → Expose Service → Scale to 4 → Open Browser → Nagios Docker → Login

If you are preparing on your Windows laptop, I can also give you **Experiment 10 in a copy-paste command sequence, one command at a time, with exactly what output you should expect after each command**.


12) AWS
    # 1. Update Ubuntu
sudo apt update

# 2. Install Docker
sudo apt install docker.io -y

# 3. Install Git
sudo apt install git -y

# 4. Start Docker
sudo systemctl start docker

# 5. Enable Docker
sudo systemctl enable docker

# 6. Clone GitHub project
git clone https://github.com/username/project.git

# 7. Enter project directory
cd project

# 8. Create Dockerfile
nano Dockerfile

# 9. Build Docker image
sudo docker build -t maven-web-app .

# 10. Check images
sudo docker images

# 11. Run container
sudo docker run -d -p 8080:8080 --name maven-web maven-web-app

# 12. Check running containers
sudo docker ps




7)Docker
Sure bro. This time I checked **Experiment 7 – Creating Multi-Containerization Using Docker Compose**, from pages 89 to 103 of your record, including the practical tasks and scenario questions.

I'll give you the full experiment in the record's order:

- Docker Compose introduction and file structure
- Basic Compose commands
- All 5 practical tasks
- Expected outputs
- All 10 scenario-based questions with answers

This experiment is different from Experiment 6: here you manage multiple services together using a `docker-compose.yml` file.&#x20;

SE_record_final.pdf



# **EXPERIMENT 7**

## **Creating Multi-Containerization Using Docker Compose**

## **1. What is Docker Compose?**

Docker Compose is a tool used to define and run multi-container Docker applications.

It allows us to define multiple services, networks, and volumes in a single configuration file.

For example, an application may require:

- Nginx web server
- PostgreSQL database
- Redis cache

Instead of starting each container separately, we can define them in one `docker-compose.yml` file and start them together.

## **2. Structure of a Docker Compose file**

A Docker Compose file is written in YAML.

The file commonly contains the following components:

### **1. Version**

The manual shows an example:

```
version: '3.8'
```

This identifies the Compose file format version used in the example.

### **2. Services**

The `services` section defines the containers required for the application.

Each service can contain:

- `image` – Docker image to use
- `ports` – host and container port mapping
- `environment` – environment variables
- `depends_on` – service dependency

Example from the record:

```
services:
  web:
    image: nginx
    ports:
      - "8060:80"

  db:
    image: tomee
    ports:
      - "8050:8080"
```

### **3. Networks**

Networks allow different services to communicate with each other.

Docker Compose automatically creates a default network if one is not specified.

### **4. Volumes**

Volumes provide persistent storage.

They allow data to remain available even after a container is stopped or removed.

## **3. Example Docker Compose file – WordPress and MySQL**

The record gives an example of running WordPress and MySQL together.

Create a file named:

`docker-compose.yml`

Add:

```
version: '3.8'

services:
  wordpress:
    image: wordpress:latest
    ports:
      - "8080:80"
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpress
      WORDPRESS_DB_NAME: wordpress
    depends_on:
      - db

  db:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: rootpassword
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpress
```

### **How to run it**

Save the file as either:

```
docker-compose.yml
```

or

```
docker-compose.yaml
```

Start the services:

```
docker-compose up -d
```

Stop and remove the Compose containers:

```
docker-compose down
```

Scale a service:

```
docker-compose up --scale SERVICE_NAME=2 -d
```

Replace `SERVICE_NAME` with the service name you want to scale.

# **Practical 1: Define and run multiple interdependent services**

### **Task**

Create a new folder named `compose-lab`.

Inside it, create a file named `docker-compose.yml`.

The file should contain an Nginx web service and a PostgreSQL database service.

## **Step 1: Create the folder**

In VS Code:

1. Click **File → Open Folder**.
2. Create or select a folder named `compose-lab`.
3. Open the folder.

You can also create it from the terminal:

```
mkdir compose-lab
cd compose-lab
```

## **Step 2: Create the Compose file**

Inside the `compose-lab` folder, create:

```
docker-compose.yml
```

Add the following content:

```
version: "3.9"

services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"

  db:
    image: postgres:15
    environment:
      POSTGRES_USER: demo
      POSTGRES_PASSWORD: demo
      POSTGRES_DB: demo_db
```

Save the file.

## **Step 3: Run the setup**

Open the terminal in the `compose-lab` folder and run:

```
docker compose up -d
```

This command:

- Downloads the required images if they are not already present.
- Creates the web and database containers.
- Starts both containers in the background.

## **Step 4: Open the browser**

Visit:

[http://localhost:8080](http://localhost:8080?utm_source=chatgpt.com)

## **Expected output**

- The Nginx welcome page is displayed.
- The PostgreSQL database container runs in the background.

## **Step 5: Check the services**

```
docker compose ps
```

This shows the services and their status.

# **Practical 2: Write and interpret docker-compose.yml files**

### **Task**

Modify `docker-compose.yml` to add a Redis cache and configure the web service to depend on Redis.

## **Step 1: Add the Redis service**

Open your existing `docker-compose.yml`.

Add the Redis service under `services`:

```
  redis:
    image: redis:alpine
```

Now your file contains the `web`, `db`, and `redis` services.

## **Step 2: Add depends_on to the web service**

The record asks to add `depends_on` so the web service waits for Redis.

Update the `web` service:

```
  web:
    image: nginx:latest
    ports:
      - "8080:80"
    depends_on:
      - redis
```

Your complete Compose file should now look like this:

```
version: "3.9"

services:
  redis:
    image: redis:alpine

  web:
    image: nginx:latest
    ports:
      - "8080:80"
    depends_on:
      - redis

  db:
    image: postgres:15
    environment:
      POSTGRES_USER: demo
      POSTGRES_PASSWORD: demo
      POSTGRES_DB: demo_db
```

## **Step 3: Restart the setup**

Run:

```
docker compose up -d
```

## **Step 4: Check the services**

```
docker compose ps
```

## **Expected output**

Three services should be listed:

- `web`
- `db`
- `redis`

They should be running.

**Note:** `depends_on` controls the startup order, but it does not guarantee that Redis is fully ready to accept connections before the web service starts.

# **Practical 3: Deploy across different machines**

### **Task**

Deploy the same Compose setup on another computer without manually configuring each container.

## **Step 1: Zip the compose-lab folder**

Your folder should contain:

```
compose-lab/
    docker-compose.yml
```

Right-click the `compose-lab` folder and select:

**Send to → Compressed (zipped) folder**

## **Step 2: Transfer the ZIP file**

Transfer the ZIP file to another computer.

That computer should have Docker and Docker Compose installed.

## **Step 3: Extract the ZIP file**

Extract the folder on the other computer.

Open the extracted `compose-lab` folder in VS Code or terminal.

## **Step 4: Run the setup**

Run:

```
docker compose up -d
```

Docker Compose downloads the required images and creates the services.

## **Step 5: Check the services**

Run:

```
docker compose ps
```

## **Expected output**

The same services should run on the new machine without changing the Compose configuration.

# **Practical 4: Networking and persistent storage**

### **Task**

Update `docker-compose.yml` to add:

- A custom network
- A persistent volume for PostgreSQL

## **Step 1: Update the Compose file**

Replace your current Compose file with this complete configuration:

```
version: "3.9"

networks:
  app-net:

volumes:
  db-data:

services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"
    networks:
      - app-net
    depends_on:
      - db

  db:
    image: postgres:15
    environment:
      POSTGRES_USER: demo
      POSTGRES_PASSWORD: demo
      POSTGRES_DB: demo_db
    volumes:
      - db-data:/var/lib/postgresql/data
    networks:
      - app-net
```

### **Explanation**

`networks` defines a custom network named `app-net`.

`volumes` defines a persistent volume named `db-data`.

The web and database services are connected to the same network.

The database stores its data in:

```
/var/lib/postgresql/data
```

inside the PostgreSQL container, backed by the Docker volume `db-data`.

## **Step 2: Run the services**

```
docker compose up -d
```

## **Step 3: Insert data into PostgreSQL**

The record says this step is optional and can be done using `psql`.

You can enter the PostgreSQL container using:

```
docker compose exec db psql -U demo -d demo_db
```

Inside PostgreSQL, create a table:

```
CREATE TABLE students (
    id SERIAL PRIMARY KEY,
    name VARCHAR(50)
);
```

Insert a record:

```
INSERT INTO students (name)
VALUES ('Alice');
```

Check the data:

```
SELECT * FROM students;
```

Exit PostgreSQL:

```
\q
```

## **Step 4: Remove the containers**

```
docker compose down
```

This removes the Compose containers and network, but the named volume is retained unless you explicitly remove it.

## **Step 5: Start the services again**

```
docker compose up -d
```

## **Step 6: Check whether data persists**

Enter PostgreSQL again:

```
docker compose exec db psql -U demo -d demo_db
```

Run:

```
SELECT * FROM students;
```

## **Expected output**

- The inserted database data remains after the containers are removed and recreated.
- The services communicate through the `app-net` network using their service names.

# **Practical 5: Faster iteration during development**

### **Task**

Create a simple Flask application, build a Docker image, and run it using Docker Compose.

## **Step 1: Create app.py**

Inside your `compose-lab` folder, create:

```
app.py
```

Add the following code:

```
from flask import Flaskapp = Flask(__name__)@app.route("/")def home():    return "Hello from Flask + Docker!"if __name__ == "__main__":    app.run(host="0.0.0.0", port=5000)
```

### **Explanation**

- `Flask(__name__)` creates the Flask application.
- `@app.route("/")` defines the home page.
- `return` sends the message to the browser.
- `0.0.0.0` allows the application to accept connections from outside the container.
- `5000` is the port on which Flask runs.

## **Step 2: Create a Dockerfile**

Create a file named:

```
Dockerfile
```

Add:

```
FROM python:3.10-slim

WORKDIR /app

COPY app.py /app/

RUN pip install flask

CMD ["python", "app.py"]
```

### **Explanation**

- `FROM python:3.10-slim` uses a Python base image.
- `WORKDIR /app` sets the working directory.
- `COPY app.py /app/` copies the Python file into the image.
- `RUN pip install flask` installs Flask.
- `CMD` starts the Flask application when the container runs.

## **Step 3: Update docker-compose.yml**

Replace the `web` service with this configuration:

```
services:
  web:
    build: .
    ports:
      - "5000:5000"
    depends_on:
      - db
```

Keep the `db` service in the Compose file as well.

Your `web` service uses `build: .` instead of `image: nginx:latest`, because Docker Compose will build the Flask image from the Dockerfile in the current folder.

## **Step 4: Run the application**

Run:

```
docker compose up --build
```

The `--build` option tells Docker Compose to build the image before starting the service.

## **Step 5: Open the browser**

Visit:

[http://localhost:5000](http://localhost:5000?utm_source=chatgpt.com)

Expected message:

```
Hello from Flask + Docker!
```

## **Step 6: Change the application message**

Open `app.py`.

Change:

```
return "Hello from Flask + Docker!"
```

to:

```
return "Hello Docker Compose!"
```

Save the file.

## **Step 7: Rebuild the application**

Run:

```
docker compose up --build
```

Visit the same URL again:

[http://localhost:5000](http://localhost:5000?utm_source=chatgpt.com)

## **Expected output**

The new message appears after rebuilding the image and restarting the service.

# **Part D: Scenario-based questions**

Your record has **10 scenario-based questions** after the five practical tasks.

The questions below follow the manual. The answers are practical explanations to help you perform them.

## **Scenario 1**

**Question:** You have two applications — a Node.js backend and a Python script that handles scheduled jobs. You're considering running both inside the same container. Should you run multiple applications in the same Docker container?

**Answer:**

It is generally recommended to run each application or service in a separate container.

For example:

- Node.js backend runs in one container.
- Python scheduled job runs in another container.

Docker Compose can manage both containers together.

This makes the applications easier to maintain, restart, and scale independently.

## **Scenario 2**

**Question:** You have a Flask API and an Nginx server. You want to run both containers on the same host and expose them on ports 5000 and 80 respectively. How can you expose both applications from different containers?

**Answer:**

Use Docker port mapping.

```
docker run -d --name flask-api -p 5000:5000 flask-image
```

```
docker run -d --name nginx-server -p 80:80 nginx
```

Now:

- Flask API is accessible on host port 5000.
- Nginx is accessible on host port 80.

## **Scenario 3**

**Question:** You want to run a React frontend, an Express.js backend and MongoDB – all together. How do you run and manage all three together?

**Answer:**

Use Docker Compose.

Create a `docker-compose.yml` file with three services:

```
services:
  frontend:
    image: react-image
    ports:
      - "3000:3000"

  backend:
    image: express-image
    ports:
      - "5000:5000"
    depends_on:
      - mongodb

  mongodb:
    image: mongo:latest
    ports:
      - "27017:27017"
```

Run all services:

```
docker compose up -d
```

Docker Compose manages all three containers together.

## **Scenario 4**

**Question:** You try to run two containers that both expose port 8080 on the host. What happens, and how can you run both apps?

**Answer:**

Both containers cannot use the same host port at the same time.

The second container may fail with a port allocation error.

Use different host ports:

```
docker run -d -p 8080:80 nginx
```

```
docker run -d -p 8081:80 nginx
```

Now both containers can run:

- First app: `localhost:8080`
- Second app: `localhost:8081`

## **Scenario 5**

**Question:** You updated some code and want to restart your frontend, backend, and database containers quickly. What is the easiest way to restart all services?

**Answer:**

Use:

```
docker compose restart
```

This restarts all services defined in the Compose file.

## **Scenario 6**

**Question:** Your frontend has a new release, but you don't want to restart the backend or database. How can you update and rebuild only the frontend container?

**Answer:**

Rebuild only the frontend service:

```
docker compose build frontend
```

Then recreate and start only the frontend:

```
docker compose up -d --no-deps frontend
```

This avoids restarting the backend and database services.

## **Scenario 7**

**Question:** Tomcat is listening on port 8080, but you get a "Connection Refused" error in the browser. Why?

**Answer:**

Possible reasons include:

1. The Tomcat container is not running.
2. The container stopped or crashed.
3. The host port is not mapped correctly.
4. Tomcat is not actually listening on port 8080.
5. A firewall or network rule is blocking the connection.

Check the container:

```
docker ps
```

Check the port mapping:

```
docker ps
```

Look at the `PORTS` column.

Check the logs:

```
docker logs CONTAINER_NAME
```

## **Scenario 8**

**Question:** You're not sure which container is using port 3000. How do you check?

**Answer from the record:**

```
docker ps
```

Check the `PORTS` column to identify which running container is using port 3000.

## **Scenario 9**

**Question:** How do you stop and clean up your running Tomcat container and image?

**Answer:**

First, stop the container:

```
docker stop tomcat
```

Remove the container:

```
docker rm tomcat
```

Remove the image:

```
docker rmi tomcat
```

Replace `tomcat` with the actual container or image name if you used a different name.

## **Scenario 10**

**Question:** You want to share your app with a teammate. What do you do with the Docker image?

**Answer:**

Upload the image to Docker Hub.

Login:

```
docker login
```

Tag the image with your Docker Hub username:

```
docker tag myapp YOUR_USERNAME/myapp
```

Push the image:

```
docker push YOUR_USERNAME/myapp
```

Your teammate can download it using:

```
docker pull YOUR_USERNAME/myapp
```

Then they can run it:

```
docker run -d --name myapp YOUR_USERNAME/myapp
```

# **Conclusion**

Docker Compose simplifies multi-container application management by allowing developers to define, configure, and run multiple services in a single YAML file.

It helps to:

- Run multiple containers together.
- Configure service dependencies.
- Set up networks and persistent volumes.
- Deploy the same application across different machines.
- Rebuild and update services during development.

This completes the practical tasks and scenario questions for **Experiment 7 – Creating Multi-Containerization Using Docker Compose**, following your record.&#x20;

SE_record_final.pdf



## **Before you start performing it**

For the practical, you need:

1. Docker Desktop running.
2. VS Code.
3. A folder named `compose-lab`.
4. A `docker-compose.yml` file.

Start with **Practical 1**, create the Nginx and PostgreSQL services, and run:

```
docker compose up -d
```

Then continue with Practical 2, 3, 4, and 5 in the order above.
