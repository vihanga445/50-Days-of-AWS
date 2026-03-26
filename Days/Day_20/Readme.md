# Day 20: Creating an IAM Role for AWS Services 🎭🛠️

## 📖 The Concept
An **IAM Role** is an IAM identity that you can create in your account that has specific permissions. Unlike a user, a role does not have a password or access keys.

* **Temporary Credentials:** When a service like EC2 "assumes" a role, AWS provides it with temporary security credentials.
* **Service-to-Service Access:** Roles are the most secure way to allow one AWS service (like a server) to interact with another AWS service (like a database or storage bucket) without hardcoding credentials.
* **Trust Policy:** This defines *who* is allowed to wear the role (in this case, the EC2 service).

---

## 🏢 Business Scenario
The **Nautilus DevOps team** is setting up an automated backup script that will run on an EC2 instance. This script needs to interact with other AWS resources securely. Instead of storing sensitive access keys on the server, the team is creating `iamrole_kirsty`. By attaching the `iampolicy_kirsty` to this role and assigning it to the instance, they ensure the server has the exact permissions needed to perform its tasks safely.

---

## 🛠️ Tasks Performed

1.  **Navigation:** Accessed the **IAM Dashboard > Roles** section.
2.  **Trust Configuration:** * Selected **AWS Service** as the trusted entity.
    * Chose **EC2** as the primary use case.
3.  **Policy Attachment:** Linked the pre-existing custom policy `iampolicy_kirsty` to the role.
4.  **Naming:** Assigned the unique role name `iamrole_kirsty`.
5.  **Verification:** Confirmed the role was created and the trust relationship correctly points to `ec2.amazonaws.com`.

---

## 📸 Screenshots

### Role Use Case Selection

<img width="1897" height="806" alt="Screenshot 2026-03-26 202823" src="https://github.com/user-attachments/assets/855a40aa-6261-4f1f-9311-9606c30719e3" />

<img width="1889" height="858" alt="Screenshot 2026-03-26 202937" src="https://github.com/user-attachments/assets/ca299db1-2f9f-4476-bb82-055cc204c299" />

### Attaching the Policy

<img width="1893" height="812" alt="Screenshot 2026-03-26 203129" src="https://github.com/user-attachments/assets/918199c5-c3be-4696-9447-89a8980b5891" />

<img width="1891" height="877" alt="Screenshot 2026-03-26 203144" src="https://github.com/user-attachments/assets/3b7dc224-00ad-45c6-ae0d-d121e5ea0a7c" />

---

To create a role via the terminal, you first create a trust policy JSON file (e.g., `trust.json`) and then run:

```bash
# Create the role with the trust policy
aws iam create-role --role-name iamrole_kirsty --assume-role-policy-document file://trust.json

# Attach the permission policy
aws iam attach-role-policy --role-name iamrole_kirsty --policy-arn arn:aws:iam::ACCOUNT_ID:policy/iampolicy_kirsty
