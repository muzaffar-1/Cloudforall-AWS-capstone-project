# 🌩️ Cloudforall AWS Capstone Project  
### Multi-Tier, Highly Available & Highly Scalable Architecture on AWS

This project demonstrates how to design and deploy a **production-grade multi-tier architecture** on AWS.  
It includes a VPC, public/private subnets, load balancer, Auto Scaling Group, RDS, S3, CloudFront, IAM, SSM and security best practices.

---

# 📌 Architecture Overview

The goal was to create a **secure, scalable, fault-tolerant** AWS environment:

- **VPC with 2 AZs**  
- **Public Subnets** → ALB, NAT Gateway  
- **Private Subnets** → EC2 Web Tier + RDS MySQL  
- **Auto Scaling Group** with Launch Template  
- **Application Load Balancer** for web traffic  
- **S3 bucket** for static content  
- **CloudFront CDN** for low-latency delivery  
- **Systems Manager (SSM)** for EC2 access (no SSH)  
- **CloudWatch** for monitoring and scaling  

---

# 📁 AWS Resources (with Screenshots)

### **1️⃣ VPC & Subnets**
| Component | Screenshot |
|----------|------------|
| VPC List | ![VPC](screenshots/vpc.png) |
| Subnets | ![Subnets](screenshots/subnets.png) |

---

### **2️⃣ Internet Gateway & Route Tables**
| IGW | Route Table |
|-----|-------------|
| ![IGW](screenshots/igw.png) | ![Route Table](screenshots/public-rt.png) |

---

### **3️⃣ NAT Gateway & Private Route Table**
| NAT Gateway | Private RT |
|-------------|------------|
| ![NAT](screenshots/nat-gw.png) | ![Private RT](screenshots/private-rt.png) |

---

### **4️⃣ Security Groups & EC2 Instances**
| Security Groups | EC2 Instances |
|-----------------|---------------|
| ![SG](screenshots/security-groups.png) | ![Instances](screenshots/ec2.png) |

---

### **5️⃣ Systems Manager (SSM) Access**
| Fleet Manager | SSM IAM Role |
|---------------|--------------|
| ![Fleet](screenshots/fleet-manager.png) | ![SSM Role](screenshots/ssm-role.png) |

---

### **6️⃣ Target Group & Launch Template**
| Target Group | Launch Template |
|--------------|-----------------|
| ![TG](screenshots/target-group.png) | ![LT](screenshots/launch-template.png) |

---

### **7️⃣ Auto Scaling Group**
| ASG Overview | ASG Activity |
|--------------|--------------|
| ![ASG](screenshots/asg.png) | ![ASG Activity](screenshots/asg-activity.png) |

---

### **8️⃣ CloudFront CDN**
| CloudFront Distribution |
|-------------------------|
| ![CloudFront](screenshots/cloudfront.png) |

---

# 🏗️ Project Summary

### **✔️ VPC Design**
- CIDR: `10.0.0.0/16`
- **Public Subnets:** For ALB and NAT  
- **Private Subnets:** For EC2 + RDS  
- Route Tables:  
  - Public RT → IGW  
  - Private RT → NAT Gateway  

### **✔️ Web Tier**
- EC2 Amazon Linux 2023
- Auto Scaling Group (Min 2, Max 4)
- Launch Template with User Data
- Application code served on NGINX

### **✔️ Load Balancer**
- Application Load Balancer  
- Health checks on port 80  
- Forwarding to Target Group (EC2 instances)

### **✔️ Database Tier**
- Amazon RDS MySQL  
- Private subnet only  
- Security Group allows DB access **only** from WebApp-SG  

### **✔️ Storage + CDN**
- S3 bucket for images  
- CloudFront for low-latency global delivery  
- Bucket locked down using **OAC**  

### **✔️ Security**
- No SSH access  
- EC2 access via **Systems Manager**  
- SGs follow least-privilege  
- Private subnets for compute + DB  

### **✔️ Monitoring**
- CloudWatch CPU alarms  
- ASG scaling policies  
- CloudWatch logs for EC2  

---

# 🚀 How to Run This Project

1. Create VPC in 2 AZs  
2. Create public and private subnets  
3. Attach Internet Gateway  
4. Create Public & Private Route Tables  
5. Create NAT Gateway  
6. Launch EC2 in private subnets  
7. Attach IAM role for SSM  
8. Configure ALB + Target Group  
9. Create Launch Template  
10. Create Auto Scaling Group  
11. Create RDS in private subnets  
12. Create S3 bucket  
13. Create CloudFront Distribution (OAC recommended)  

---

# 📝 Author  
**Md Muzaffar Qureshi**  
Capstone Project – Cloud & DevOps  

---

