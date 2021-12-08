# aws_vpc_nat_
# AWS networking
## VPC
### 2-tier architecture deployment

**AWS Networking**
- IP address
- CIDR block
- IPv4 and IPv6

**VPC and its resources**
![](/images/vpc_1.png)
- Route table rules
- SG rules
- subnets cidr blocks
- connectivity between app and db, and app nat db

**2-tier architecture deployment in our own VPC**
![](add a diagram)
- Should have all rules at all levels required

# The Blocker 07/12/2021
- Only one routing table which is public allowing internet access to both public and private subnetworks which includes the database.
- This is an inherent security issue, so needs to be swiftly corrected, as database is accessible from the public.
- Solution involved creation of a new routing table connected to a private network, and the association removal from the public routing table.

# The Blocker 08/12/2021
- Current database instance has a public IP address
- Current measures was to use the security guard to stop access, but still fundamental issue as vulnerability
- Solution involved generating new instance using same SG settings and then changing IP connections to use new database. Once the database is confirmed to be accessible from the nat instance, has access to the internet via nat and on npm launch the posts section is visible, the old database instance can be stopped/terminated.
