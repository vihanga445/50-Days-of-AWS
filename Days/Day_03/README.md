# Day 03: Creating a Subnet 🌐

## 📖 The Concept
A **Subnet** (short for "sub-network") is a logical slice of a **VPC**. 

Think of it like an **Office Floor** inside a building:
* **VPC:** The entire Office Building.
* **Subnet:** A specific floor (e.g., the 2nd Floor for the IT Department).
* **IP Addresses:** The room numbers on that floor.

By creating subnets, the Nautilus team can group their resources together and control how traffic flows between different parts of their cloud "building."

---

## 🏢 Business Scenario
As part of the incremental migration, the **Nautilus DevOps team** needs a specific place to launch their new application servers. By creating the `nautilus-subnet`, they are preparing the foundation. This subnet will live inside the **Default VPC**, providing the network addresses required for their virtual machines to communicate.

---

## 🛠️ Tasks Performed

1.  **Region Selection:** Confirmed the working region as **us-east-1**.
2.  **Navigation:** Accessed the **VPC Dashboard** and selected the **Subnets** section.
3.  **Subnet Creation:** Initiated the creation of a new subnet with these details:
    * **Name Tag:** `nautilus-subnet`
    * **VPC:** Associated it with the **Default VPC**.
    * **Availability Zone:** Selected an available zone in us-east-1.
    * **IPv4 CIDR block:** Assigned a specific IP range (e.g., `172.31.100.0/24`).

---

## 📸 Screenshots
*Replace the placeholder links below with your uploaded image paths.*

### Subnet Creation Settings


<img width="1894" height="881" alt="Screenshot 2026-03-06 222115" src="https://github.com/user-attachments/assets/58cfb58a-185f-4170-b79e-476c0eb0bd77" />

<img width="1823" height="669" alt="Screenshot 2026-03-06 222643" src="https://github.com/user-attachments/assets/76779dbf-7b2e-4ab8-aab4-e87b231315a0" />

---

## 💻 The Engineer's Way (CLI)
To verify that the subnet was created and see its details

```bash
aws ec2 describe-subnets --filters "Name=tag:Name,Values=nautilus-subnet"
