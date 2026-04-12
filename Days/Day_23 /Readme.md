# Day 30: Implementing an Application Load Balancer (ALB) ⚖️🌐

## 📖 The Concept
An **Application Load Balancer (ALB)** serves as the single point of contact for clients. It distributes incoming application traffic across multiple targets, such as EC2 instances, in multiple Availability Zones.

* **Target Group:** A logical grouping of instances that receive traffic from the Load Balancer.
* **Listeners:** Rules that check for connection requests based on the protocol and port configured.
* **High Availability:** If one instance fails, the ALB automatically routes traffic to the remaining healthy instances.

---

## 🏢 Business Scenario
The **Nautilus DevOps team** is preparing to go live with their application. To ensure the app can handle high traffic and remain available even if a server fails, they are placing an ALB (`xfusion-alb`) in front of the `xfusion-ec2` server. This setup allows them to scale horizontally in the future by simply adding more instances to the `xfusion-tg` target group.

---

## 🛠️ Tasks Performed

1.  **Security Configuration:** Created `xfusion-sg` to allow public HTTP traffic on Port 80.
2.  **Targeting:** Provisioned `xfusion-tg` and registered the `xfusion-ec2` instance as a healthy target.
3.  **ALB Deployment:** Launched `xfusion-alb`, configured with listeners to forward traffic from the public-facing port to the internal target group.
4.  **Network Hardening:** Modified the default EC2 security group to allow inbound traffic strictly from the ALB's security group, following the "Least Privilege" model.

---

To check the health of your instance within the target group:

```bash
aws elbv2 describe-target-health --target-group-arn YOUR_TARGET_GROUP_ARN
