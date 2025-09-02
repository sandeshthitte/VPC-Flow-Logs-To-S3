# VPC Flow Logs to Amazon S3 with IAM Role

## 📌 Overview
This project demonstrates how to enable **VPC Flow Logs** for a custom VPC in AWS and deliver the logs to an **Amazon S3 bucket** using an **IAM role** with the necessary permissions.  
These logs help in analyzing network traffic, troubleshooting connectivity issues, and enhancing security monitoring.

---

## 🛠️ Steps Performed

### 1. VPC Setup
- Created a new **VPC** (CIDR: `10.0.0.0/16`).
- Added a **public subnet** (CIDR: `10.0.1.0/24`).
- Attached an **Internet Gateway (IGW)** to the VPC.
- Updated the **Route Table**:
  - `10.0.0.0/16 → local`
  - `0.0.0.0/0 → igw-xxxxxxxx`

### 2. Security & NACL
- Security Group: Allowed **SSH (22)** and **HTTP (80)**.
- Network ACL: Allowed **Inbound SSH (22)** and **Outbound traffic**.

### 3. EC2 Instance
- Launched an EC2 instance inside the public subnet.
- Associated a **public IP** for external SSH access.
- Verified connectivity using SSH.

### 4. S3 Bucket for Flow Logs
- Created bucket: `vpc-flow-logs-bucket-<unique-id>`.
- Applied **bucket policy** to allow VPC Flow Logs service to write objects.
- Log storage path:
s3://vpc-flow-logs-bucket/<account-id>/<region>/<vpc-id>/

css
Copy code

### 5. IAM Role for VPC Flow Logs
- Created IAM role with **trust policy** for `vpc-flow-logs.amazonaws.com`.
- Attached permissions policy:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:PutObject",
      "Resource": "arn:aws:s3:::vpc-flow-logs-bucket-*/AWSLogs/*"
    }
  ]
}
6. Enable VPC Flow Logs
Destination: S3 bucket.

IAM Role: Attached the created role.

Traffic Type: ALL (Accept + Reject).

7. Verification
Generated traffic by SSH into EC2.

Verified logs in S3 bucket under:

php-template
Copy code
<account-id>/<region>/<vpc-id>/<year>/<month>/<day>/<log-file>
✅ Outcome
Successfully delivered VPC Flow Logs to S3.

Logs can be further analyzed using Athena, CloudWatch, or SIEM tools.

📷 Screenshots


![VPC Flow Logs Setup](screenshots/vpc-flow-logs-setup.png)
