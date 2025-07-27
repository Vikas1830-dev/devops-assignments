# 📘 Assignment 2: Destroy Previous Deployment & Create EC2 with Elastic IP

---

## 📌 Objective

1. Destroy the EC2 instance created in Assignment 1.
2. Launch a **new EC2 instance** in the Ohio region (`us-east-2`) with a **permanently attached Elastic IP** using Terraform.

---

## 📚 What You'll Learn

- How to destroy existing Terraform-managed infrastructure
- How to provision an EC2 instance
- How to allocate and associate an **Elastic IP (EIP)** to EC2
- How to use Terraform dependencies to ensure correct order of resource creation

---

## 🧠 Prerequisites

- Terraform installed (`terraform -v`)
- AWS CLI configured with access keys
- IAM user with EC2 and EIP privileges

---

## 📁 File Structure

terraform-assignment-2/
├── main.tf
├── provider.tf
├── variables.tf
├── terraform.tfvars
├── outputs.tf
└── README.md

---

## 🔥 Step 1: Destroy Previous EC2

If you have completed Assignment 1, go to its folder and run:

```bash
terraform destroy
Confirm with yes to delete the previous EC2 instance and free up resources.
.


🛠️ Step 2: Full Terraform Code for Assignment 2

-----------------------------------------------------------------------------
🧾 provider.tf

provider "aws" {
  region = "us-east-2"  # Ohio
}
-------------------------------------------------------------------------------------------

🧾 main.tf
resource "aws_instance" "example" {
  ami           = var.ami_id
  instance_type = var.instance_type

  tags = {
    Name = "EC2-With-EIP"
  }
}

resource "aws_eip" "eip" {
  vpc = true
}

resource "aws_eip_association" "eip_assoc" {
  instance_id   = aws_instance.example.id
  allocation_id = aws_eip.eip.id
}
-------------------------------------------------------------------------------------------------------------------------------------------
🧾 variables.tf

variable "ami_id" {
  description = "AMI ID for EC2"
  type        = string
}

variable "instance_type" {
  description = "EC2 instance type"
  type        = string
}
 terraform.tfvars
ami_id        = "ami-0ddda618e961f2270"  # Amazon Linux 2 (Ohio region)
instance_type = "t2.micro"

----------------------------------------------------------------------------------------------------------------------------------------
🧾 outputs.tf
output "ec2_public_ip" {
  description = "Elastic IP associated with EC2"
  value       = aws_eip.eip.public_ip
}
-----------------------------------------------------------------------------------------------------------------------------------
⚙️ How to Run
Go to the terraform-assignment-2/ directory
-------------------------------------------------------------------------------------------------------------------------------
Run the following:

terraform init
terraform plan
terraform apply
-----------------------------------------------------------------------------------------------------------------------------------
🧼 How to Destroy
terraform destroy

---------------------------------------------------------------------------------------------------------------------------------
🔍 Explanation
aws_instance: Launches EC2 instance

aws_eip: Allocates a new static IP

aws_eip_association: Binds the EIP to the EC2 instance using dependency chaining
---------------------------------------------------------------------------------------------------------------------------
🧠 Summary
You destroyed your old EC2 instance ✅

Created a fresh EC2 instance ✅

Attached an Elastic IP ✅

Learned how to manage multi-resource dependencies in Terraform ✅
