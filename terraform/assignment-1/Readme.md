# 📘 Assignment 1: Launch EC2 in Default Subnet (Ohio Region)

---

## 📌 Objective

Create and launch an EC2 instance in the **default subnet** of the AWS **Ohio region (`us-east-2`)** using Terraform.

---

## 📚 What You'll Learn

- Provider configuration for AWS
- Launching EC2 instance in default VPC/subnet
- Managing AMI, instance type via variables
- Viewing EC2 Public IP via Terraform output

---

## 🧠 Prerequisites

- Terraform installed (`terraform -v`)
- AWS CLI configured with access keys
- IAM user with EC2 full access
- Basic understanding of AWS EC2

---

## 📁 File Structure

terraform-assignment-1/
├── main.tf
├── provider.tf
├── variables.tf
├── terraform.tfvars
├── outputs.tf
└── README.md



---

## 📂 Terraform Files with Code

### 🧾 `provider.tf`

```hcl
provider "aws" {
  region = "us-east-2"  # Ohio Region
}


🧾 main.tf
hcl
Copy
Edit
resource "aws_instance" "example" {
  ami           = var.ami_id
  instance_type = var.instance_type

  tags = {
    Name = "Terraform-EC2"
  }
}
_____________________________________________________________________________________________________________



🧾 variables.tf.



variable "ami_id" {
  description = "AMI ID for EC2"
  type        = string
}

variable "instance_type" {
  description = "Instance type for EC2"
  type        = string
}

-------------------------------------------------------------------------------------------------------

🧾 terraform.tfvars
ami_id        = "ami-0ddda618e961f2270"  # Amazon Linux 2 in us-east-2
instance_type = "t2.micro"

--------------------------------------------------------------------------------------------------------


🧾 outputs.tf
output "ec2_public_ip" {
  description = "Public IP of the EC2 instance"
  value       = aws_instance.example.public_ip
}

-------------------------------------------------------------------------------------------------------------
⚙️ How to Run


terraform init        # Initialize the working directory
terraform plan        # Preview the changes
terraform apply       # Apply the changes

-------------------------------------------------------------------------------------------------------------

🧼 How to Destroy the Infrastructure


terraform destroy

----------------------------------------------------------------------------------------------------------------

✅ Output Example


Apply complete! Resources: 1 added.
Outputs:

ec2_public_ip = "3.21.58.133"
-------------------------------------------------------------------------------------------------------------------

🧠 Summary
We successfully created an EC2 instance in the Ohio region

Used Terraform variables for flexibility

Displayed the public IP using outputs

Used default AWS networking (VPC/subnet)


--------------------------------------------------------------------------------------------------------------------------





