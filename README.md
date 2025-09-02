📖 Overview

This project demonstrates the complete process of capturing VPC Flow Logs in Amazon Web Services (AWS) and storing them in an Amazon S3 bucket for monitoring, troubleshooting, and security analysis.

VPC Flow Logs are a powerful AWS feature that record detailed metadata about network traffic flowing into and out of your Virtual Private Cloud (VPC). By delivering these logs to an S3 bucket, you can centralize network visibility and analyze traffic patterns for auditing, performance tuning, or threat detection.

Unlike other implementations that require an IAM role for delivery permissions, this project configures logging directly through the S3 bucket policy, making the setup simpler while maintaining security.

⚡ Project Goals

Enable network visibility in a custom VPC.

Store VPC Flow Logs in a secure S3 bucket.

Validate log delivery and demonstrate real-world use cases.

Learn how permissions and policies control AWS service interactions.

🛠️ Project Workflow
1️⃣ Create a Custom VPC & EC2 Instance

Designed a custom VPC with subnets, route tables, and internet gateway.

Launched an EC2 instance inside the VPC to generate traffic for logs.

Configured security groups to allow inbound/outbound traffic.

2️⃣ Create an S3 Bucket for Logs

Provisioned a new S3 bucket dedicated for log storage.

Updated the bucket policy to allow the VPC Flow Logs service (delivery.logs.amazonaws.com) to write objects into the bucket.

Enforced least-privilege access to ensure only flow logs could be delivered.

3️⃣ Enable VPC Flow Logs

Configured flow logs at the VPC level to capture traffic from all resources.

Selected All traffic (Accepted + Rejected) to maximize visibility.

Chose Amazon S3 as the log destination and specified the bucket.

4️⃣ Generate Traffic

Connected to the EC2 instance to simulate inbound/outbound network traffic.

Performed actions like pings, SSH connections, and outbound web requests to ensure logs would be generated.

5️⃣ Validate Log Delivery

Navigated to the S3 bucket and verified that compressed log files (.log.gz) were successfully delivered.

Downloaded and extracted logs to confirm they contained:

Source/Destination IPs

Ports and Protocols

Action (ACCEPT/REJECT)

Traffic direction (ingress/egress)



🔍 Key Outcomes & Learnings

✅ Hands-on experience with VPC networking and logging.

✅ Practical knowledge of S3 bucket policies and service permissions.

✅ Learned how to enable and validate VPC Flow Logs.

✅ Understood how logs can be used for security monitoring and traffic analysis.

✅ Improved troubleshooting skills by generating and analyzing network flow data.

📊 Real-World Use Cases

Security Analysis → Detect unauthorized traffic or suspicious patterns.

Compliance → Store logs for audits and regulatory requirements.

Troubleshooting → Diagnose dropped packets, connectivity failures, and firewall misconfigurations.

Optimization → Analyze network usage and optimize costs/resources.

📌 About 

End-to-end project demonstrating VPC Flow Logs setup in AWS. Created a custom VPC and EC2, configured S3 bucket policies for log delivery, enabled logging at the VPC level, and validated logs for monitoring, troubleshooting, and security analysis.
