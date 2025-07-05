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

2. **Create VPC**  
   - Name: `CustomVPC-01`  
   - IPv4 CIDR: `10.0.0.0/16`  
   - IPv6: Not used

3. **Enable DNS Support**  
   - Edit VPC settings → Enable DNS Hostnames and DNS Resolution

4. **Create and Attach Internet Gateway**  
   - Name: `CustomIGW-01`  
   - Attach to `CustomVPC-01`

5. **Create Route Table**  
   - Name: `CustomRT-01`  
   - Associate with `CustomVPC-01`  
   - Add route `0.0.0.0/0` → IGW

6. **Review Default Subnets**  
   - Navigate to Subnets section  
   - Note: Do **not** use default subnets in this lab

---

## CIDR Breakdown

- **CIDR Notation**: `10.0.0.0/16`  
- **Explanation**:  
  - 16 bits for network, 16 bits for hosts  
  - IP range: `10.0.0.0` – `10.0.255.255`  
  - Total IPs: 65,536  
- **Use Case**: Ideal for large-scale subnetting and flexible IP allocation

---

## Screenshots
> Screenshots for each step are included in the `/screenshots` directory:
- VPC creation
- DNS settings
- IGW setup
- Route table config
- Default subnet overview

---

## Author
**Ali – AIOps | DevOps | Cloud | Cybersecurity**

---

## License
This lab is part of an educational series and intended for learning purposes.
