# Day 06: Launching an EC2 Instance 🚀

## 📖 The Concept
An **EC2 (Elastic Compute Cloud)** instance is a virtual server in the Amazon cloud. 

Think of it as **Renting a Computer**:
* **The Hardware:** The `t2.micro` instance type defines how much "power" your virtual computer has.
* **The OS:** The **AMI** (Amazon Machine Image) acts as the pre-installed Operating System (Amazon Linux).
* **The Keys:** The **Key Pair** (`nautilus-kp`) is your digital identity used to log in securely without a password.
* **The Guard:** The **Security Group** acts as the firewall for this specific server.

---

## 🏢 Business Scenario
The **Nautilus DevOps team** is ready to move their first application component to the cloud. Following their incremental strategy, they are starting by launching a single, scalable virtual server. By using `t2.micro` and Amazon Linux, they are establishing a cost-effective environment for testing their migration.

---

## 🛠️ Tasks Performed

1.  **Navigation:** Accessed the **EC2 Dashboard** and initiated the **Launch Instance** wizard.
2.  **OS Selection:** Chose the **Amazon Linux AMI** as the base image for the server.
3.  **Sizing:** Selected the **t2.micro** instance type.
4.  **Security Setup:** * Created a new RSA key pair named `nautilus-kp` for secure SSH access.
    * Attached the **default** security group to define network access rules.
5.  **Deployment:** Named the instance `nautilus-ec2` and launched it into the `us-east-1` region.

---

## 📸 Screenshots

<img width="1894" height="863" alt="Screenshot 2026-03-10 234640" src="https://github.com/user-attachments/assets/fb077ca6-4dbe-4f75-94da-fd0838c97e8f" />


<img width="1895" height="288" alt="Screenshot 2026-03-10 234747" src="https://github.com/user-attachments/assets/25312d23-0e19-4902-ab43-1d2febb35a5f" />


<img width="1895" height="288" alt="Screenshot 2026-03-10 234747" src="https://github.com/user-attachments/assets/57901cfc-5e9d-4fe3-bf91-c4d0cb536588" />


To check the status of your instance and find its IP address via the terminal:

```bash
aws ec2 describe-instances --filters "Name=tag:Name,Values=nautilus-ec2" --query "Reservations[*].Instances[*].{ID:InstanceId,State:State.Name,IP:PublicIpAddress}"
