# Day 18: Creating a Custom IAM Policy 📜🔍

## 📖 The Concept
An **IAM Policy** is an object in AWS that, when associated with an identity (User or Group), defines its permissions. 

* **JSON Format:** Policies are written in JSON, using a "Statement" that includes:
    * **Effect:** (Allow or Deny)
    * **Action:** (What can they do? e.g., `ec2:DescribeInstances`)
    * **Resource:** (What can they touch? e.g., `*` for everything)
* **Read-Only:** This specific policy provides "visibility without power," allowing users to audit resources without the risk of changing or deleting them.

---

## 🏢 Business Scenario
The **Nautilus DevOps team** is implementing a security auditing process. They need a way for external auditors or junior members to view the status of the migration without granting them the ability to interfere with running instances. By creating `iampolicy_james`, the team is enforcing the "Principle of Least Privilege" by providing exactly the level of access required for observation and nothing more.

---

## 🛠️ Tasks Performed

1.  **Navigation:** Accessed the **IAM Dashboard > Policies** section.
2.  **Policy Definition:** Used the Visual Editor to create a custom policy with:
    * **Service:** `EC2`
    * **Actions:** Enabled all `Read` level access (Describe actions).
    * **Resources:** Set to `All resources` (`*`).
3.  **Naming:** Assigned the unique name `iampolicy_james`.
4.  **Verification:** Confirmed the policy was created and appears in the "Customer managed" policy list.

---

<img width="1896" height="774" alt="Screenshot 2026-03-23 193708" src="https://github.com/user-attachments/assets/b1ff24a4-e8aa-42d2-befe-2cebdb7d6d91" />

<img width="1507" height="685" alt="Screenshot 2026-03-23 195133" src="https://github.com/user-attachments/assets/735928f5-a116-46eb-901b-2b4968fd13e2" />

<img width="1652" height="509" alt="Screenshot 2026-03-23 195147" src="https://github.com/user-attachments/assets/f6fa58f8-e452-4623-8ecb-c33d7015e2a0" />

To create a policy via the terminal, you first save your JSON to a file (e.g., `policy.json`) and then run:

```bash
aws iam create-policy --policy-name iampolicy_james --policy-document file://policy.json
