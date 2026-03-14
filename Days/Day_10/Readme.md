# Day 10: Associating an Elastic IP (EIP) 🌐📍

## 📖 The Concept
An **Elastic IP (EIP)** is a reserved public IPv4 address that you can assign to any EC2 instance in a specific region.

* **Static Addressing:** Unlike standard public IPs, an Elastic IP does not change when an instance is stopped and started.
* **Masking Failures:** If your server fails, you can quickly "remap" the Elastic IP to a new, working server. Your users won't even notice because the IP address they use remains the same.

---

## 🏢 Business Scenario
The **Nautilus DevOps team** is moving a service that requires a consistent entry point for their users. By associating the `xfusion-ec2-eip` with the `xfusion-ec2` instance, they ensure that the application remains reachable at the same static IP address, regardless of server restarts or maintenance windows.

---

## 🛠️ Tasks Performed

1.  **Navigation:** Accessed the **EC2 Dashboard** and navigated to **Network & Security > Elastic IPs**.
2.  **Resource Check:** Located the pre-allocated Elastic IP named `xfusion-ec2-eip` and the target instance `xfusion-ec2`.
3.  **Association:** * Selected the EIP and chose **Actions > Associate Elastic IP address**.
    * Linked the EIP to the specific `xfusion-ec2` instance ID.
    * Selected the corresponding **Private IP address** for the mapping.
4.  **Verification:** Confirmed the association was successful and the instance now reflects the new static Public IP.

To associate an Elastic IP via the terminal, you would first get the Allocation ID and then run:

```bash
aws ec2 associate-address --instance-id YOUR_INSTANCE_ID --allocation-id eipalloc-YOUR_ALLOCATION_ID
