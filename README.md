# AWS-Networkfirewall-VPC

**Template File:** [NAT_vpc_anfw_2az.yml](NAT_vpc_anfw_2az.yml)

we deploy AWS Network Firewall into each VPC which requires protection. Each VPC is protected individually and blast radius is reduced through VPC isolation. Each VPC does not require connectivity to any other VPC or AWS Transit Gateway. Each AWS Network Firewall can have its own firewall policy or share a policy through common rule groups (reusable collections of rules) across multiple firewalls. This allows each AWS Network Firewall to be managed independently, which reduces the possibility of misconfiguration and limits the scope of impact.


* Spoke VPC. Spoke VPC consists of three subnets in each AZ:
  * Private subnet for application/client.
  * Public subnet for NAT Gateway.
  * Firewall subnet for firewall endpoint.


For return traffic, Ingress Route Table is associated with Internet Gateway to ensure the traffic is forwarded to firewall endpoint within the same AZ. This route tables has public subnet route pointing towards firewall endpoint in the same AZ.

![AWS-Networkfirewall on AWS](designer.png)
