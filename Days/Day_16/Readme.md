# Day 16: Creating an IAM User 👤🔑

## 📖 The Concept
**IAM (Identity and Access Management)** is the framework of policies and technologies for ensuring that the right users have the appropriate access to technology resources.

* **Identity:** An IAM User represents a person or service that interacts with AWS.
* **Security Best Practice:** Never use the "Root" account for daily tasks. Instead, create individual IAM users for every team member.
* **Auditability:** By giving Jim his own account (`iamuser_jim`), we can track exactly what he does in the AWS CloudTrail logs.

---

## 🏢 Business Scenario
The **Nautilus DevOps team** is expanding, and a new engineer named Jim has joined the project. To maintain a secure environment, the team is following the standard onboarding process by creating a dedicated IAM entity for him. This ensures that Jim's actions are isolated and can be managed independently of other team members.

---

## 🛠️ Tasks Performed

1.  **Navigation:** Accessed the **IAM Dashboard** from the AWS Management Console.
2.  **User Creation:** * Initiated the "Create User" wizard.
    * Assigned the username: `iamuser_jim`.
3.  **Permissions:** Performed a "Clean Creation" by not attaching any initial policies, following the strategy of adding permissions only as needed (Least Privilege).
4.  **Verification:** Confirmed the user `iamuser_jim` appears in the IAM User list.

---

## 📸 Screenshots


### User Configuration

<img width="1900" height="872" alt="Screenshot 2026-03-21 234343" src="https://github.com/user-attachments/assets/5ba5bb0b-7804-49e9-a294-89a82a921d48" />


### Final User List

<img width="1919" height="855" alt="Screenshot 2026-03-21 234444" src="https://github.com/user-attachments/assets/b38dcc9a-c40b-4bcd-a395-81884874843b" />

---

To create a user via the terminal, use this simple command:

```bash
aws iam create-user --user-name iamuser_jim
