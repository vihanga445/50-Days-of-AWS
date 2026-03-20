# Day 15: Creating an EBS Snapshot 📸💾

## 📖 The Concept
An **EBS Snapshot** is a point-in-time backup of an EBS volume. 

* **Point-in-Time:** It captures the exact state of the data at the moment of creation.
* **Durability:** Snapshots are stored in Amazon S3 automatically, making them highly reliable and protected against hardware failure.
* **Restoration:** You can use a snapshot to create a brand new EBS volume in any Availability Zone within the same region.

---

## 🏢 Business Scenario
The **Nautilus DevOps team** is implementing a disaster recovery strategy. To protect against data corruption or accidental loss during their incremental migration, they are taking manual snapshots of critical volumes. By creating `devops-vol-ss`, the team ensures they have a "safety net" they can return to if future migration steps go wrong.

---

## 🛠️ Tasks Performed

1.  **Navigation:** Accessed the **EC2 Dashboard > Elastic Block Store > Volumes**.
2.  **Resource Selection:** Identified the target volume `devops-vol` in the `us-east-1` region.
3.  **Snapshot Initiation:** * Selected the volume and chose **Actions > Create snapshot**.
    * Provided the required description: `devops Snapshot`.
    * Tagged the resource with the Name: `devops-vol-ss`.
4.  **Monitoring:** Navigated to the **Snapshots** section and monitored the progress.
5.  **Verification:** Confirmed the snapshot reached the **completed** state.

---

## 📸 Screenshots

### Creating the Snapshot
<img width="1919" height="640" alt="Screenshot 2026-03-20 232617" src="https://github.com/user-attachments/assets/476de837-5de4-439d-a8b1-f37d901f6007" />
<img width="1895" height="808" alt="Screenshot 2026-03-20 232628" src="https://github.com/user-attachments/assets/9418cfa3-bc4e-44d9-a383-fd00655f3502" />

### Snapshot Status: Completed

<img width="1919" height="755" alt="Screenshot 2026-03-20 232745" src="https://github.com/user-attachments/assets/6fa671fc-62d2-49f6-89bc-3d09a5fdd2f2" />


To create a snapshot and check its progress via the terminal:

```bash
# Create the snapshot
aws ec2 create-snapshot --volume-id vol-12345678 --description "devops Snapshot" --tag-specifications 'ResourceType=snapshot,Tags=[{Key=Name,Value=devops-vol-ss}]'

# Check status
aws ec2 describe-snapshots --snapshot-ids snap-12345678 --query "Snapshots[*].State"
