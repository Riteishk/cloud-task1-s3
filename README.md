# cloud-task1-s3
# Task 1: Cloud Storage Setup using AWS S3

## 🎯 Objective
To create a cloud storage bucket using AWS S3, upload sample files, and configure access permissions (public and private).

---

## 🪜 Steps Followed

### ✅ 1. Created S3 Bucket
- **Name:** riteishk-storage-bucket 
- **Region:** Europe (eu-west-1)

### ✅ 2. Uploaded Files
- `hello.txt` – Public
- `image.jpg` – Public
- `info.json` – Private (Access Denied)

### ✅ 3. Configured Access
- Granted public read access to `.txt` and `.jpg` via ACL
- Ensured `.json` was private by default
- Applied Bucket Policy to **block `.json` public access**

### ✅ 4. Tested Public URLs
- ✔️ [hello.txt](https://riteishk-storage.s3.eu-north-1.amazonaws.com/hello.txt)
- ✔️ [image.jpg](https://riteishk-storage.s3.eu-north-1.amazonaws.com/image.jpg)
- ❌ [info.json](https://riteishk-storage.s3.eu-west-1.amazonaws.com/info.json) – Access Denied (as expected)

---

## 🔒 Security Measure

Added bucket policy to block public access for all `.json` files:
```json
{
  "Effect": "Deny",
  "Principal": "*",
  "Action": "s3:GetObject",
  "Resource": "arn:aws:s3:::your-bucket-name/*.json"
}
