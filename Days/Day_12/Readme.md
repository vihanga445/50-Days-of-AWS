# Day 12: Attaching an EBS Volume to EC2 💾🔌

## 📖 The Concept
Attaching an **EBS (Elastic Block Store)** volume is the process of connecting a block-level storage device to a running or stopped EC2 instance.

* **Block Storage:** Unlike S3 (which is for files), EBS is "Block Storage," meaning it behaves like a physical hard drive where you can install databases or operating systems.
* **Device Mapping:** Using a device name like `/dev/sdb` tells the Linux kernel which "slot" the drive is plugged into.
* **Persistence:** If the EC2 instance is deleted, you can choose to keep this volume so your data is never lost.

---

## 🏢 Business Scenario
The **Nautilus DevOps team** is expanding the storage capacity of their primary development server. To handle an influx of data during the migration, they are attaching a secondary 2GB volume (`devops-volume`) to the `devops-ec2` instance. By mapping it to `/dev/sdb`, they are following their internal standard for secondary data drives.

---

## 🛠️ Tasks Performed

1.  **Navigation:** Accessed the **EC2 Dashboard** and navigated to **Elastic Block Store > Volumes**.
2.  **Volume Identification:** Located the `devops-volume` in an `Available` state.
3.  **Attachment:** * Selected **Actions > Attach volume**.
    * Target Instance: `devops-ec2`.
    * Device Name: Specified `/dev/sdb` as per requirements.
4.  **Verification:** Confirmed the volume status changed to `In-use` and is successfully mapped to the instance.

---

## 📸 Screenshots

### Volume Attachment Settings


<img width="1896" height="745" alt="Screenshot 2026-03-17 001830" src="https://github.com/user-attachments/assets/ce83a791-c3c9-43a5-9528-a97b5066ad53" />


### Confirmation: Volume In-Use

<img width="1601" height="443" alt="Screenshot 2026-03-17 001838" src="https://github.com/user-attachments/assets/2e06b537-84cc-4551-8c30-a3bf159080ca" />

  

To attach a volume via the terminal, use this command:

```bash
aws ec2 attach-volume --volume-id vol-12345678 --instance-id i-12345678 --device /dev/sdb
