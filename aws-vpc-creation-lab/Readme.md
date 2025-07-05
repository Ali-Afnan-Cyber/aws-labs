# Custom VPC Creation & CIDR Understanding

## Overview
This lab demonstrates how to create and customize a Virtual Private Cloud (VPC) in AWS using a custom CIDR block. It also covers the basics of CIDR notation and prepares the foundation for subnetting in cloud network design.

---

## Objectives
- Create a **custom VPC** with a specified IP range
- Understand and apply **CIDR** (/16) addressing
- Attach and configure an **Internet Gateway**
- Set up a **custom route table** for internet access
- Enable **DNS support** for instances within the VPC

---

## Configuration Summary

| Component         | Value                    |
|------------------|--------------------------|
| VPC Name         | `Custom-VPC-01`           |
| CIDR Block       | `10.0.0.0/16`            |
| DNS Hostnames    | Enabled                  |
| Internet Gateway | `Custom-IGW-01`           |
| Route Table      | `Custom-RT-01`            |
| Route            | `0.0.0.0/0` → IGW target |

---

## Step-by-Step Instructions

1. **Navigate to VPC Dashboard**  
   AWS Console → Services → VPC

![aws-vpc-dashboard](https://github.com/user-attachments/assets/4d309d25-b67f-4e1e-98af-1ec5c1709dc9)


3. **Create VPC**  
   - Name: `Custom-VPC-01`  
   - IPv4 CIDR: `10.0.0.0/16`  
   - IPv6: Not used

  ![creating-vpc-adding-cidr](https://github.com/user-attachments/assets/a3adffb0-19cb-42dd-b363-38aaa6c86952)

![vpc-successfully-created](https://github.com/user-attachments/assets/b71693e9-4c59-4dcc-8804-0db488d8e54a)


4. **Enable DNS Support**  
   - Edit VPC settings → Enable DNS Hostnames and DNS Resolution

![enabling-dns-hostnames-dns-support](https://github.com/user-attachments/assets/bb8ea9e5-648f-4f81-b07b-169b03d20622)

5. **Create and Attach Internet Gateway**  
   - Name: `Custom-IGW-01`  
   - Attach to `Custom-VPC-01`

![creating-custom-internet-gateway](https://github.com/user-attachments/assets/07ed1b29-c46e-43f8-a727-6f2b6e0d03bb)

![attaching-custom-igw-to-custom-vpc](https://github.com/user-attachments/assets/70420e53-dfb3-4526-bb00-0eaa9806472d)


6. **Create Route Table**  
   - Name: `Custom-RT-01`  
   - Associate with `Custom-VPC-01`  
   - Add route `0.0.0.0/0` → IGW

![created-custom-routetable-with-vpc](https://github.com/user-attachments/assets/504d2765-5db0-4822-9b11-69c7aa3601e4)


---

## 📍 Why Use `10.0.0.0/16` as the CIDR Block in a Custom VPC?

In this lab, we created a custom Virtual Private Cloud (VPC) using the CIDR block `10.0.0.0/16`. Here's why this range is chosen and what makes it ideal for AWS VPC design and subnetting.

---

### 🔹 What is `10.0.0.0/16`?

- `10.0.0.0/16` is a **Class A private IP range** from the **RFC 1918** private address space.
- It supports **65,536 IP addresses** (2¹⁶), ranging from `10.0.0.0` to `10.0.255.255`.
- This range is **non-routable on the public internet**, making it safe for internal use.

---

### 🔹 Why /16 Specifically?

| Reason                         | Explanation                                                                 |
|-------------------------------|-----------------------------------------------------------------------------|
| 🧩 **Flexibility in Subnetting** | Allows you to create up to **256 /24 subnets** or customize further (e.g., /20, /28). |
| 🏗 **Scalable Architecture**    | Supports future scaling – adding more availability zones, tiers, and services. |
| 🔐 **Isolation & Security**    | Lets you isolate environments (dev/test/prod) using different subnets.       |
| 📊 **Efficient IP Planning**   | You can assign IPs to public, private, and DB subnets without conflicts.     |

---

### 🔹 Why Not Smaller Ranges (e.g., /24)?

- A `/24` only provides **256 IP addresses** (with ~251 usable).
- In a large deployment (e.g., multiple AZs, load balancers, NAT gateways, RDS, ECS, etc.), `/24` is too restrictive.
- AWS reserves **5 IPs per subnet**, further reducing usable space in smaller blocks.

---

### 🔹 Why Not Larger Ranges (e.g., /8)?

- `/8` (16.7 million IPs) is **wasteful** and exceeds practical needs for most use cases.
- Can lead to **routing inefficiencies** and **IP management problems**.
- AWS VPC supports a maximum of **/16 for the primary CIDR**, unless additional CIDRs are added.

---

### 🔹 Summary

Using `10.0.0.0/16` offers the **ideal balance** between:

- **Scalability**
- **Subnetting flexibility**
- **Private addressing**
- **AWS best practices**

It enables clean, organized VPC design and future expansion while adhering to RFC standards and AWS limits.

---

### 🧠 Tip: Think Ahead

Always choose a CIDR block large enough to accommodate:
- Multi-tier app design (web/app/db)
- Multiple availability zones (AZs)
- Services like NAT, Load Balancers, Bastion, etc.

A well-planned CIDR = fewer headaches later.



---

## Screenshots
> Screenshots for each step are included in the `/screenshots` directory:
- VPC creation
- DNS settings
- IGW setup
- Route table config
- Default subnet overview

---

## Architecture (Basic)

![architectural-diagram](https://github.com/user-attachments/assets/01e1ec8e-6fe4-421c-b57c-12277bfa667d)


---

## Author
**Ali Afnan – AIOps | DevOps | Cloud | Cybersecurity**

---

## License
This lab is part of an educational series and intended for learning purposes.
