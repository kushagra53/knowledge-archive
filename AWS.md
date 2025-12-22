# AWS DevSecOps Learning Notes

Hey, these are my quick notes from the past few days diving into AWS for the **terraform-devsecops** project. Focused only on what I'm actually using: EC2, S3, Terraform setup, and TFSEC scanning. No fluff—just the hands-on stuff to get the pipeline running by Dec 25. [memory:1][memory:3][conversation_history:5]

## Core AWS Services in Project

- **S3 Bucket**: Object storage for files/datasets (like NSL-KDD data). Define in Terraform as `resource "aws_s3_bucket" "mybucket" { bucket = "kushagra-demo" }`. Start public for demo, then lock down with private/encryption policies. Free tier safe. [conversation_history:11][conversation_history:10]
- **EC2 Instance**: Virtual server to run models/code. Terraform spins it up with `resource "aws_instance" "web" { ami = "ami-0abcdef1234567890" instance_type = "t2.micro" }`. Ties to anomaly detection—upload data to S3, process on EC2. [conversation_history:11][conversation_history:10]

## Terraform Basics (IaC Tool)

Terraform defines AWS infra as code (**.tf files**) instead of console clicks. Workflow:  
**write config** → `terraform init` (downloads AWS provider) → `plan` (preview) → `apply` (deploy).  

Tracks state in **tfstate file** to avoid drift. Used for repeatable S3/EC2 setups across envs. [conversation_history:6][memory:2]

## Credential Setup Fixes

**Error**: `"No valid credential sources found"` = missing AWS keys. **Fix**:

1. Create IAM user in AWS console → Access Key/Secret Key (**wait 24h if new account**)
2. Set as env vars:  
export AWS_ACCESS_KEY_ID=...
export AWS_SECRET_ACCESS_KEY=...

text
*(never commit!)*
3. Or hardcode temporarily in provider block for local tests:
provider "aws" {
region = "us-east-1"
access_key = "..."
secret_key = "..."
}
4. Then: `terraform init -upgrade`. **Enable MFA on IAM ASAP**. [conversation_history:5][memory:1]

## TFSEC Security Scanning

**TFSEC** scans .tf files for vulns (e.g., public S3, open ports) **before deploy**.  

**In GitHub Actions**:
name: Security scan
run: tfsec . --format sarif

text

**Fails CI on high-risk**—fix code (`acl = "private"`) → re-push → **green pipeline**.  
**Demo**: vulnerable config fails → secure one deploys. [conversation_history:11]

## Local Setup on Windows

1. **Download** terraform.exe ZIP → extract to `C:\terraform`
2. **Add to PATH**:  
$env:Path += ";C:\terraform"
[Environment]::SetEnvironmentVariable("Path", $env:Path, "Machine")

text
3. **Restart PowerShell** → test: `terraform version`
4. **In repo**:  
cd aws-terraform-devsecops-tfsec-demo
terraform init

text

**Choco alt**: `choco install terraform` [conversation_history:7][conversation_history:8][conversation_history:9]

## Project Workflow

Push main.tf (S3/EC2) to GitHub
↓

GitHub Actions:
checkout → terraform init/plan → tfsec scan → if pass, terraform apply
↓

Secure AWS infra auto-deploys

text

**Links to NSL-KDD**: store data in S3, run RF model on EC2. **Internship gold**—shows DevSecOps, not just manual deploys. [conversation_history:11][memory:3]

---

*Dec 22, 2025 - Kushagra (3rd year CSE) | For aws-terraform-devsecops-tfsec-demo repo*
