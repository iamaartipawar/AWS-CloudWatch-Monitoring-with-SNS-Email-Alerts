# ☁️ AWS CloudWatch Monitoring with SNS Email Alerts

## 📌 Project Overview

This project demonstrates how to build a complete monitoring and alerting solution using Amazon CloudWatch, CloudWatch Agent, and Amazon SNS. The solution continuously monitors the health and performance of an Amazon EC2 instance by collecting both default AWS metrics and operating system-level metrics such as CPU, Memory, Disk, and Network utilization.

A custom CloudWatch Dashboard was created to visualize system performance in real time. CloudWatch Alarms were configured to detect high CPU utilization, and Amazon SNS was integrated to automatically send email notifications whenever the alarm threshold was exceeded. A CPU stress test was performed on the EC2 instance to validate the monitoring pipeline and ensure that alerts were triggered successfully.

## 🏗️ Architecture Overview

The monitoring workflow begins with an Amazon EC2 instance running the CloudWatch Agent. The agent collects operating system metrics and sends them to Amazon CloudWatch. A custom dashboard displays real-time metrics, while CloudWatch Alarms continuously monitor CPU utilization. When the configured threshold is exceeded during a stress test, the alarm changes to the ALARM state and automatically publishes a notification to an Amazon SNS topic. SNS then sends an email notification to the subscribed recipient, enabling immediate awareness of performance issues.

<p align="center">
  <img src="images/Architec.png" width="700">
</p>

## 🎯 Project Objectives
- Monitor Amazon EC2 performance using Amazon CloudWatch.
- Install and configure the CloudWatch Agent.
- Collect CPU, Memory, Disk, Network, and Disk I/O metrics.
- Create a custom CloudWatch Dashboard.
- Configure CloudWatch Alarms for CPU utilization.
- Integrate Amazon SNS for email notifications.
- Perform CPU stress testing to validate alarms.
- Enable proactive infrastructure monitoring.

## 🛠 AWS Services Used
- Amazon EC2
- Amazon CloudWatch
- Amazon CloudWatch Agent
- CloudWatch Dashboard
- CloudWatch Alarms
- Amazon SNS
- AWS Systems Manager Parameter Store
- IAM
- Amazon Linux 2023

## ⚙️ Implementation Steps

### Launch an Amazon EC2 instance running Amazon Linux.

<p align="center">
  <img src="images/1.png" width="700">
</p>

<p align="center">
  <img src="images/2.png" width="700">
</p>


### Navigate to Amazon SNS and create a new Standard topic named Global-Topic.

<p align="center">
  <img src="images/3.png" width="700">
</p>

### Create Subscription

<p align="center">
  <img src="images/4.png" width="700">
</p>

<p align="center">
  <img src="images/5.png" width="700">
</p>

<p align="center">
  <img src="images/6.png" width="700">
</p>

<p align="center">
  <img src="images/7.png" width="700">
</p>

<p align="center">
  <img src="images/8.png" width="700">
</p>

### Configure Global Topic

<p align="center">
  <img src="images/9.png" width="700">
</p>

<p align="center">
  <img src="images/10.png" width="700">
</p>

<p align="center">
  <img src="images/11.png" width="700">
</p>

### Create dashboard & Share your dashboard publically after you get the link copy that and paste it into browser

<p align="center">
  <img src="images/12.png" width="700">
</p>

<p align="center">
  <img src="images/13.png" width="700">
</p>

<p align="center">
  <img src="images/14.png" width="700">
</p>

<p align="center">
  <img src="images/16.png" width="700">
</p>

<p align="center">
  <img src="images/17.png" width="700">
</p>

<p align="center">
  <img src="images/18.png" width="700">
</p>

<p align="center">
  <img src="images/19.png" width="700">
</p>

<p align="center">
  <img src="images/20.png" width="700">
</p>

<p align="center">
  <img src="images/21.png" width="700">
</p>

<p align="center">
  <img src="images/22.png" width="700">
</p>

<p align="center">
  <img src="images/23.png" width="700">
</p>

<p align="center">
  <img src="images/24.png" width="700">
</p>

### Create Alarm and configure alarm settings
- when your alarm is triggerd then your EC2 instance is stop

<p align="center">
  <img src="images/25.png" width="700">
</p>

<p align="center">
  <img src="images/26.png" width="700">
</p>

<p align="center">
  <img src="images/27.png" width="700">
</p>

<p align="center">
  <img src="images/28.png" width="700">
</p>

<p align="center">
  <img src="images/29.png" width="700">
</p>

<p align="center">
  <img src="images/30.png" width="700">
</p>

<p align="center">
  <img src="images/31.png" width="700">
</p>

<p align="center">
  <img src="images/32.png" width="700">
</p>

<p align="center">
  <img src="images/33.png" width="700">
</p>

<p align="center">
  <img src="images/34.png" width="700">
</p>

<p align="center">
  <img src="images/35.png" width="700">
</p>

<p align="center">
  <img src="images/36.png" width="700">
</p>

<p align="center">
  <img src="images/37.png" width="700">
</p>

<p align="center">
  <img src="images/38.png" width="700">
</p>

### Connect to your EC2 instance
```bash
sudo yum install stress -y
sudo yum install htop -y
htop
stress --cpu 80 --io 4 --vm 2 --vm-bytes 128M --timeout 10m &
stress: info: [27190] dispatching hogs: 80 cpu, 4 io, 2 vm, 0 hdd
jobs
```
<p align="center">
  <img src="images/39.png" width="700">
</p>

<p align="center">
  <img src="images/40.png" width="700">
</p>

<p align="center">
  <img src="images/41.png" width="700">
</p>

<p align="center">
  <img src="images/42.png" width="700">
</p>

<p align="center">
  <img src="images/43.png" width="700">
</p>

<p align="center">
  <img src="images/44.png" width="700">
</p>

<p align="center">
  <img src="images/45.png" width="700">
</p>

### Access your Dashboard and refresh dashboard & you see your instance load was increases

<p align="center">
  <img src="images/46.png" width="700">
</p>

<p align="center">
  <img src="images/47.png" width="700">
</p>

### When your alarm is trigger then you get mail from SNS

<p align="center">
  <img src="images/48.png" width="700">
</p>

<p align="center">
  <img src="images/49.png" width="700">
</p>

### Again create another global topic

<p align="center">
  <img src="images/50.png" width="700">
</p>

<p align="center">
  <img src="images/51.png" width="700">
</p>

<p align="center">
  <img src="images/52.png" width="700">
</p>

### Create Subscription and confirm it from email

<p align="center">
  <img src="images/53.png" width="700">
</p>

<p align="center">
  <img src="images/54.png" width="700">
</p>

<p align="center">
  <img src="images/55.png" width="700">
</p>

<p align="center">
  <img src="images/56.png" width="700">
</p>

<p align="center">
  <img src="images/57.png" width="700">
</p>

<p align="center">
  <img src="images/58.png" width="700">
</p>

### Publish message (Monsoon Sale)

<p align="center">
  <img src="images/59.png" width="700">
</p>

<p align="center">
  <img src="images/60.png" width="700">
</p>

<p align="center">
  <img src="images/61.png" width="700">
</p>

<p align="center">
  <img src="images/62.png" width="700">
</p>

<p align="center">
  <img src="images/63.png" width="700">
</p>

### After that you get monsoon sale notification on email

<p align="center">
  <img src="images/64.png" width="700">
</p>

## 📊 Features
- Real-time EC2 monitoring
- CloudWatch Agent configuration
- Custom Dashboard visualization
- CPU utilization monitoring
- Memory and Disk monitoring
- Network traffic monitoring
- Automated CloudWatch Alarms
- SNS Email Notifications
- CPU Stress Testing
- End-to-end monitoring validation

## 📸 Project Workflow
- Launch Amazon EC2
- Configure IAM Role
- Install CloudWatch Agent
- Configure Systems Manager Parameter Store
- Publish EC2 Metrics
- Create CloudWatch Dashboard
- Configure CloudWatch Alarm
- Create SNS Topic
- Confirm Email Subscription
- Execute CPU Stress Test
- Trigger Alarm
- Receive Email Notification

## ✅ Project Outcome

Successfully implemented a complete AWS monitoring and alerting solution capable of collecting detailed EC2 performance metrics, visualizing infrastructure health through CloudWatch Dashboards, detecting abnormal CPU usage using CloudWatch Alarms, and automatically notifying administrators through Amazon SNS email alerts. This project demonstrates real-world cloud monitoring practices used in production environments.
