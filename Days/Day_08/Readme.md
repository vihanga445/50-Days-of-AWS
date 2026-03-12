# Day 08: Enabling EC2 Stop Protection 🛡️

## 📖 The Concept
**Stop Protection** (and its cousin, Termination Protection) is a safety mechanism to prevent accidental service disruption.

* **Human Error:** In a fast-paced DevOps environment, it is easy to accidentally select the wrong instance when performing maintenance.
* **The Safeguard:** By enabling Stop Protection, AWS prevents the instance from being shut down until an administrator explicitly disables the protection first. 

---

## 🏢 Business Scenario
The **Nautilus DevOps team** has identified `devops-ec2` as a critical component of their new infrastructure. To ensure "optimal resource availability" and prevent any accidental downtime during the migration phase, the team has mandated that Stop Protection be enabled. This adds a layer of operational security to the environment.

---

## 🛠️ Tasks Performed

1.  **Navigation:** Logged into the AWS Console and navigated to the **EC2 Instances** list in `us-east-1`.
2.  **Identification:** Located the target instance named `devops-ec2`.
3.  **Modification:** * Selected **Actions > Instance Settings > Change stop protection**.
    * Toggled the setting to **Enable**.
4.  **Verification:** Attempted to view the setting status to confirm the protection is now active.

---

## 📸 Screenshots

### Modifying Stop Protection
<img width="1156" height="772" alt="Screenshot 2026-03-12 130813" src="https://github.com/user-attachments/assets/c15d2208-f199-4d73-b889-7ab8b4399161" />

<img width="915" height="430" alt="Screenshot 2026-03-12 130848" src="https://github.com/user-attachments/assets/f7fa8407-6e45-479e-86fc-259a59369318" />

### Confirmation Message

<img width="1545" height="361" alt="Screenshot 2026-03-12 130904" src="https://github.com/user-attachments/assets/0d201f5d-75f7-41c7-8c7f-13c25270067a" />

<img width="984" height="344" alt="Screenshot 2026-03-12 131028" src="https://github.com/user-attachments/assets/491a8629-ab08-4993-99c2-963e14c23b78" />


To check if an instance has stop protection enabled using the terminal:

```bash
aws ec2 describe-instance-attribute --instance-id YOUR_INSTANCE_ID --attribute disableApiStop
