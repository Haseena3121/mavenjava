# **Part Maven pom.xml File — Theory and PurposeMaven’s core file is the POM (pom.xml), which defines a project’s structure, dependencies, build lifecycle, and plugins using a standardized, declarative model.
📘 What Maven Is
Maven is a build automation and dependency‑management tool for Java projects. Its theory is based on convention over configuration, meaning Maven expects projects to follow a standard layout so the configuration file stays simple.
.
 
 10: Working with Minikube and Nagios**

# **Part A — Minikube (Kubernetes)**

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
