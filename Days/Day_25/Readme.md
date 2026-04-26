# Day 31: Infrastructure Monitoring with CloudWatch Alarms 🛡️📈

## 📖 The Concept
Infrastructure monitoring ensures application reliability by detecting performance bottlenecks before they cause downtime. 

* **Amazon CloudWatch:** Acts as the monitoring "brain," tracking metrics like CPU, Memory, and Disk.
* **Amazon SNS:** Handles the communication, ensuring alerts reach the team instantly.
* **Threshold Logic:** We monitor for a **5-minute period** to ignore short, harmless CPU spikes and only alert on sustained, heavy usage.

---

## 🏢 Business Scenario
The **Nautilus DevOps team** is deploying the `devops-ec2` instance. Because this server handles critical workloads, the team must be notified if it hits a 90% CPU load for more than 5 minutes. This proactive approach allows the team to investigate potential issues (like inefficient code or traffic surges) before they impact end-users.

---

## 🛠️ Tasks Performed: Full Command Sequence

```bash
# 1. Discover the Instance ID
aws ec2 describe-instances --filters "Name=tag:Name,Values=devops-ec2" --query "Reservations[*].Instances[*].InstanceId" --output text

# 2. Create the CloudWatch Alarm via CLI
# Note: Replace YOUR_INSTANCE_ID with the ID found in step 1
aws cloudwatch put-metric-alarm \
    --alarm-name "devops-alarm" \
    --alarm-description "Alarm when CPU exceeds 90 percent" \
    --metric-name CPUUtilization \
    --namespace AWS/EC2 \
    --statistic Average \
    --period 300 \
    --threshold 90 \
    --comparison-operator GreaterThanOrEqualToThreshold \
    --dimensions Name=InstanceId,Value=YOUR_INSTANCE_ID \
    --evaluation-periods 1 \
    --alarm-actions arn:aws:sns:us-east-1:416452986212:devops-sns-topic \
    --unit Percent
