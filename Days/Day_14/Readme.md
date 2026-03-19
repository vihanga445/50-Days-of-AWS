# Day 14: Terminating an EC2 Instance 🗑️🛑

## 📖 The Concept
**Termination** is the final stage of an EC2 instance's life. It is the process of permanently deleting a virtual server and releasing its resources back to AWS.

* **Cost Management:** In DevOps, we follow the principle of "Pay for what you use." Terminating obsolete resources is essential to prevent unnecessary billing.
* **Permanence:** Unlike stopping an instance, termination is irreversible. By default, any data stored on the instance's root EBS volume is also deleted.
* **Lifecycle:** An instance goes from `Running` -> `Shutting-down` -> `Terminated`.

---

## 🏢 Business Scenario
The **Nautilus DevOps team** has successfully migrated their services to a new architecture. As a result, the older `devops-ec2` instance is no longer needed. To optimize cloud spend and clean up the infrastructure, the team is decommissioning this resource. This marks the successful completion of one phase of their incremental migration.

---

## 🛠️ Tasks Performed

1.  **Navigation:** Accessed the **EC2 Dashboard > Instances** in the `us-east-1` region.
2.  **Identification:** Located the obsolete instance named `devops-ec2`.
3.  **Decommissioning:** * Selected the instance and chose **Instance state > Terminate instance**.
    * Confirmed the action in the AWS dialogue box.
4.  **Verification:** Monitored the instance state until it successfully transitioned to **Terminated**.

---


### Initiating Termination

<img width="1590" height="378" alt="Screenshot 2026-03-20 011758" src="https://github.com/user-attachments/assets/e0dad0fc-cd47-498c-a199-2836b9edc03e" />

<img width="1550" height="707" alt="Screenshot 2026-03-20 011808" src="https://github.com/user-attachments/assets/37f0b703-d85d-47cc-a8f4-9e785ef2e989" />

### State: Terminated

<img width="1552" height="366" alt="image" src="https://github.com/user-attachments/assets/1900af8e-b906-48b0-a177-f568865ad6e5" />




---

To terminate an instance via the terminal, use the following command:

```bash
aws ec2 terminate-instances --instance-ids i-1234567890abcdef0
