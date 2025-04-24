# Student Course Management System

A simple cloud-based MySQL project hosted on **AWS EC2 + RDS**, designed to manage students, courses, and enrollments using SQL via CLI.

<img width="1190" alt="Screenshot 2025-04-21 at 1 13 52 AM" src="https://github.com/user-attachments/assets/09e2bc2f-fa2b-4f5c-a953-a1b5ce75daa4" />

# Created Tables
<img width="1440" alt="Screenshot 2025-04-20 at 9 28 29 PM" src="https://github.com/user-attachments/assets/dc52001e-c9fc-4558-829a-5e31410a82cb" />

# Inserted Data into tables
<img width="722" alt="Screenshot 2025-04-20 at 9 32 56 PM" src="https://github.com/user-attachments/assets/6111b9db-447a-41ce-9297-c3abc71efad0" />

# Performing Joint operations
<img width="656" alt="Screenshot 2025-04-20 at 9 34 31 PM"    src="https://github.com/user-attachments/assets/34d1df56-69e6-4d99-b0fa-c63721809490" />
---

## 🚀 Project Architecture

- **AWS EC2**: Hosts the MySQL client for interaction.
- **AWS RDS (MySQL)**: Cloud-hosted managed database.
- **MySQL CLI**: Used for creating and querying the database.

---

## ✅ Step 1: Launch EC2 Instance

1. Navigate to **AWS Console > EC2 > Launch Instance**
2. Choose **Amazon Linux 2 AMI**
3. Select **t2.micro** (Free Tier eligible)
4. Configure network (VPC + Subnet) and **enable Auto-assign Public IP**
5. Create or use an existing **key pair**
6. Set up the **Security Group** to allow:
   - SSH (Port 22)
   - MySQL (Port 3306)
7. Launch your instance

---

## ✅ Step 2: Launch RDS MySQL Instance

1. Navigate to **AWS Console > RDS > Create Database**
2. Choose **Standard Create > MySQL**
3. Select default **engine version**
4. Choose **db.t3.micro** (Free Tier)
5. Set **DB name, master username, and password**
6. **Enable public access** if needed
7. Use the **same VPC as EC2**
8. In the **Security Group**, allow **MySQL/Aurora (3306)** inbound from EC2

---

## ✅ Step 3: Connect EC2 to RDS

### 🔐 SSH into your EC2:
```bash
ssh -i your-key.pem ec2-user@<EC2-Public-IP>

sudo dnf update -y
sudo dnf install mariadb105 mariadb105-server -y
sudo systemctl start mariadb
sudo systemctl enable mariadb

mysql -h <RDS-ENDPOINT> -u <master-username> -p
