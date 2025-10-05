# Ron Lerner — AWS Cloud & Cyber Demo ☁️

This project demonstrates a basic **cloud + security** setup on AWS:
- **EC2** instance running **NGINX** with a custom landing page
- **IAM** user with **least-privilege** policy (`AmazonS3ReadOnlyAccess`)
- **S3** bucket for storing demo objects
- **Security Group** hardened: SSH restricted to *My IP*; HTTP open for web access

---

## 🧩 Architecture
```
Client (Browser)
     │  HTTP :80
     ▼
AWS EC2 (Amazon Linux 2 + NGINX)
     │
     ├─ IAM (user with AmazonS3ReadOnlyAccess)
     │
     └─ S3 bucket (demo object)
```
*You can also include an architecture diagram image if you want.*

---

## 🚀 Steps Performed (Console / GUI)
1. **Launched EC2** (`t3.micro`, Amazon Linux 2, Free Tier eligible).
2. Created **Key Pair** and **Security Group**:
   - SSH (22) → *My IP only*
   - HTTP (80) → *Anywhere*
3. **Connected via SSH** (from local machine).
4. **Installed NGINX** and deployed `index.html` (this repo).
5. Created **S3 bucket** and uploaded demo file.
6. Created **IAM user** `ron-student-user` and attached `AmazonS3ReadOnlyAccess`.
7. Verified website via the instance **Public IPv4 / DNS**.

> Replace with your current public endpoint (optional):  
> `http://YOUR-PUBLIC-IP`  or  `http://YOUR-PUBLIC-DNS`

---

## 🔐 Security Notes
- Followed **least privilege** for IAM.
- **SSH restricted** to my IP only (no 0.0.0.0/0).
- Avoid storing secrets/keys in code or screenshots.
- Terminate resources when done to avoid costs.

---

## 📸 Screenshots
EC2 instance (running, public IP/DNS):  
![EC2](screenshots/ec2-instance.png)

Custom NGINX landing page:  
![NGINX Page](screenshots/nginx-page.png)

S3 bucket with object:  
![S3](screenshots/s3-bucket.png)

IAM user with read-only S3 policy:  
![IAM](screenshots/iam-user.png)

---

## 🧼 Cleanup (avoid charges)
When you’re done:
1. **Terminate** the EC2 instance.
2. **Delete** S3 objects and the bucket.
3. **Remove** IAM user or detach policies.

---

## 🎯 What I Learned
- Provisioning & securing EC2
- Serving a static site with NGINX
- Managing IAM identities and permissions
- Working with S3 storage
- Cloud security fundamentals relevant to SOC/Cloud roles
