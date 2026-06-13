# 🛡️ Zero-Trust Automated Enterprise Infrastructure with AI

![Terraform](https://img.shields.io/badge/terraform-%235835CC.svg?style=for-the-badge&logo=terraform&logoColor=white)
![Ansible](https://img.shields.io/badge/ansible-%231A1918.svg?style=for-the-badge&logo=ansible&logoColor=white)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![pfSense](https://img.shields.io/badge/pfsense-000000.svg?style=for-the-badge&logo=pfsense&logoColor=white)
![Security](https://img.shields.io/badge/Zero_Trust-Enterprise_Grade-red?style=for-the-badge)

---

## 📖 Overview

This project presents a **real-world enterprise-grade infrastructure simulation** designed using **Zero-Trust architecture principles**, **Infrastructure as Code (IaC)**, and **AI-driven security monitoring**.

It replicates how modern organizations design secure environments where:
- No network zone is trusted by default
- Every access is verified and controlled
- Infrastructure is fully automated and reproducible
- Security monitoring is enhanced with machine learning

The system combines **network segmentation, automation, and AI-based anomaly detection** to create a self-defending infrastructure model.

---

## 🎯 Objectives

- Build a production-like **Zero Trust network architecture**
- Automate infrastructure deployment using **IaC principles**
- Implement centralized and secure **network segmentation**
- Apply **DevSecOps practices** in a virtual enterprise environment
- Integrate **AI-based intrusion/anomaly detection**
- Simulate real enterprise SOC behavior

---

## 🚀 Key Features

- 🔐 **Zero-Trust Architecture**
  - Strict VLAN segmentation (MGMT / SERVERS / USERS)
  - Default deny firewall policy
  - Controlled inter-zone communication

- ⚙️ **Infrastructure as Code (IaC)**
  - Fully automated provisioning using Terraform
  - Reproducible infrastructure deployments

- 🤖 **Configuration Automation**
  - Ansible-based system hardening
  - Automated firewall and server configuration

- 🧱 **Perimeter Security**
  - pfSense Next-Generation Firewall (NGFW)
  - Advanced routing, filtering, and NAT control

- 🧠 **AI-Powered Threat Detection**
  - Python-based log analyzer
  - Isolation Forest algorithm for anomaly detection
  - Detection of brute-force and abnormal access patterns

- 🖧 **Secure Management Layer**
  - Out-of-Band (OOB) isolated management network
  - SSH key-based authentication only

---

## 🏗️ Architecture Overview

The infrastructure is designed to isolate and protect critical assets through strict segmentation.

- WAN → Internet gateway (NAT)
- MGMT → Secure administration network
- SERVERS → Application and service layer
- USERS → End-user simulation environment

> Each zone is strictly controlled through firewall policies and monitored for anomalies.

![Architecture Diagram](./architecture.png)

---

## 🛠️ Technology Stack

| Layer | Technology |
|------|------------|
| Virtualization | Oracle VirtualBox |
| Firewall | pfSense CE (FreeBSD) |
| OS | Ubuntu Server 24.04 LTS |
| IaC | Terraform |
| Automation | Ansible |
| Containers | Docker |
| AI / ML | Python, Scikit-learn, Pandas |
| Monitoring | Log-based anomaly detection |

---

## 📦 Setup Guide

### 1. Network Topology Setup (pfSense)

- Configure interfaces:
  - WAN → NAT
  - LAN → MGMT
  - OPT1 → SERVERS
  - OPT2 → USERS

- Apply **Default Deny Policy**
- Allow only required inter-zone traffic

---

### 2. Management Server Deployment

- Install Ubuntu Server (MGMT zone)
- Enable SSH access with key authentication only
- Install Ansible for remote configuration control

---

### 3. Infrastructure as Code (Terraform)

```hcl
resource "docker_container" "web_server" {
  name  = "web_server_tf"
  image = "nginx:latest"

  ports {
    internal = 80
    external = 8080
  }
}
