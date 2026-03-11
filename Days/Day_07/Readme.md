# Day 07: Resizing an EC2 Instance (Scaling) ⚖️

## 📖 The Concept
One of the greatest benefits of the cloud is **Elasticity**. You can change the hardware specifications of your server without having to rebuild it from scratch.

* **Vertical Scaling:** This is what we did today—changing the size of a single instance (from `t2.micro` to `t2.nano`).
* **t2.nano:** This is even smaller than a micro. It has less memory (RAM), which is perfect for very small tasks, saving the company money on underutilized resources.

---

## 🏢 Business Scenario
The **Nautilus DevOps team** noticed that the `nautilus-ec2` server was barely using its CPU and RAM. To optimize costs and ensure "optimal resource utilization," the team decided to "downsize" the instance. This ensures the company isn't paying for power it doesn't need.

---

## 🛠️ Tasks Performed

1.  **Health Check:** Verified that the `nautilus-ec2` instance had completed its initial **Status Checks** (2/2 passed).
2.  **Stopping the Service:** Gracefully shut down the instance to allow for hardware configuration changes.
3.  **Resizing:** Navigated to **Instance Settings > Change Instance Type** and successfully switched the type from `t2.micro` to `t2.nano`.
4.  **Restarting:** Powered the instance back on and verified its state returned to **Running**.

---





<img width="1908" height="808" alt="Screenshot 2026-03-11 102809" src="https://github.com/user-attachments/assets/b61795a4-fbb9-4d78-a600-eb0b8f1a69b2" />


<img width="376" height="259" alt="Screenshot 2026-03-11 102822" src="https://github.com/user-attachments/assets/18d074c7-543d-4a0a-b039-91e799bf4944" />

<img width="1845" height="728" alt="Screenshot 2026-03-11 102837" src="https://github.com/user-attachments/assets/240568d3-abd5-431a-b771-c2affcac05d3" />

---

To check the current size of your instance using the terminal:

```bash
aws ec2 describe-instances --filters "Name=tag:Name,Values=nautilus-ec2" --query "Reservations[*].Instances[*].InstanceType"
