# AWS CloudWatch Monitoring & Alerts – EC2 CPU Utilization

This project demonstrates how to monitor an EC2 instance’s CPU usage using Amazon CloudWatch and receive email alerts via Amazon SNS when usage exceeds a set threshold.

---

## 🔧 Tools & Services Used

- *Amazon EC2* (Ubuntu 22.04, t2.micro)
- *Amazon CloudWatch* (metrics and alarms)
- *Amazon SNS* (email notifications)
- *Ubuntu Terminal + stress utility*
- *Git Bash (SSH)*

---

## 🎯 Project Objective

- Launch an EC2 instance in a public subnet
- Monitor CPU utilization using CloudWatch
- Trigger an SNS email alert when CPU > 10%
- Simulate high CPU usage using stress

---

## 🛠️ Steps Performed

### ✅ 1. EC2 Setup
- Launched an Ubuntu instance in a public subnet with public IP
- Enabled SSH access from 0.0.0.0/0

### ✅ 2. Installed CPU Load Generator
SSH into instance:
```bash
sudo apt update
sudo apt install stress -y
```

### ✅ 3. Created SNS Topic & Email Subscription
- **SNS Topic:** `ec2-cpu-alerts`
- **Subscription:**  
  - Protocol: Email  
  - Endpoint: `chandanu000@gmail.com`
- Confirmed the subscription via AWS email

### ✅ 4. Created CloudWatch Alarm
- **Metric:** EC2 → CPUUtilization
- **Condition:** CPU > 10% for 5 minutes
- **Datapoints to alarm:** 1 out of 1
- **Notification:** SNS topic `ec2-cpu-alerts`
- **Alarm name:** `High-CPU-Alarm-EC2`

### ✅ 5. Simulated High CPU
Ran the following:
```bash
stress --cpu 4 --timeout 300
```

### ✅ 6. Received SNS Email Alert
- CloudWatch detected the threshold breach, transitioned the alarm to ALARM, and sent a confirmation email.

-------------------
## 📸 Attached Screenshots

CloudWatch alarm in OK → ALARM state

Email alert from AWS SNS

Terminal showing stress running

SNS topic + confirmed email subscription



---

##🧹 Cleanup

Stopped EC2 instance to avoid charges

Confirmed no unattached volumes

Alarm and SNS left in place for demo purposes


---

📌 Author

Chandan Upadhyay

[LinkedIn](https://www.linkedin.com/in/chandan-upadhyay-813077141?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=android_app)

[GitHub](https://github.com/itschandan2024)
