# Day 26: Automated Web Server Deployment with User Data 🚀🌐

## 📖 The Concept
Manual configuration is the enemy of scaling. To ensure consistency across environments, we use **User Data scripts (Cloud-Init)** to automate the initial setup of our instances.

* **Bootstrapping:** The process of automatically installing software and starting services at the first boot of a server.
* **Security Groups:** Acting as a virtual firewall, we specifically opened Port 80 to allow the public to reach our Nginx web server.

---

## 🏢 Business Scenario
The **Nautilus DevOps Team** is preparing for a major application launch. To speed up the deployment of web nodes, the team is using User Data to provision Nginx automatically. This ensures that every `datacenter-ec2` instance created is identical and ready to serve traffic the moment it finishes booting.

---

## 🛠️ Tasks Performed: Full Command Sequence

### The User Data Script
The following shell script was injected into the instance metadata to handle the automated installation:

```bash
#!/bin/bash
apt-get update -y
apt-get install nginx -y
systemctl start nginx
systemctl enable nginx
