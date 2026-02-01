# Cloud Services
This section gives pricing for a cloud setup for the company.

[Cloud VM Provider Comparison](#cloud-vm-provider-comparison) | [Total Cost](#total-cost-of-cloud-vms) | [Plan](./plan.md) | [Network Design](./network.md) | [Security](./security.md) | [Ethics](./ethics.md) | [Reflection](./reflection.md) | [Return to index](./README.md)

---

## Cloud VM Provider Comparison

Truelec currently operates its booking application on on-premise Dell PowerEdge tower servers that are approximately five years old. To evaluate whether cloud services are better suited for future operations, cloud virtual machines from two providers were analysed using **official pricing calculators**.

The booking application requires:
- **3 servers at headquarters**
- **1 server per branch office**
- **Total: 7 virtual machines**
- Continuous operation (**24/7, 730 hours per month**)

To ensure a fair comparison, equivalent specifications were used across providers.

### Selected Virtual Machine Specifications

| Specification | Value |
|--------------|-------|
| Operating System | Linux |
| vCPU | 2 |
| RAM | 8 GB |
| Storage | 100 GB SSD |
| Availability | 24/7 (730 hours/month) |
| Pricing Model | On-Demand / Pay-as-you-go |

### Amazon Web Services (AWS)

The AWS estimate was generated using the **official AWS Pricing Calculator**.

- Service: Amazon EC2
- Region: Asia Pacific (Sydney)
- Instance type: t3.large
- Operating system: Linux
- Storage: 100 GB EBS (SSD)
- Pricing model: On-Demand

**Cost (per VM):**
- Monthly: USD 86.69  
- Annual: USD 1,040.28  

### Microsoft Azure

The Azure estimate was generated using the **official Azure Pricing Calculator**.

- Service: Azure Virtual Machines
- Region: Australia East
- VM size: B2ms (2 vCPU, 8 GB RAM)
- Operating system: Linux
- Storage: 100 GB Premium SSD
- Pricing model: Pay-as-you-go

**Cost (per VM):**
- Monthly: USD 135.92  
- Annual: USD 1,631.04  

### Currency Conversion

Cloud provider calculators present pricing in USD. For reporting purposes, costs are converted to AUD using an approximate exchange rate of:

**1 USD = 1.50 AUD**

This conversion is applied consistently to both providers to ensure comparability.

### Cost Summary (Per VM, AUD)

| Provider | Monthly Cost (AUD) | Annual Cost (AUD) |
|--------|--------------------|-------------------|
| AWS | ≈ AUD 130.04 | ≈ AUD 1,560.42 |
| Azure | ≈ AUD 203.88 | ≈ AUD 2,446.56 |

Links to cloud provider export files:
- [AWS](./cloud/aws-ec2-ondemand-estimate.csv)
- [Azure](./cloud/azure-vm-ondemand-estimate.xlsx)

---

## Total Cost of Cloud VMs

The total cost of replacing all existing on-premise servers with cloud virtual machines was calculated over a **5-year period**, aligned with the typical physical server replacement cycle.

### AWS – Total Cost (7 VMs)

| Item | Cost (AUD) |
|----|-----------|
| Monthly cost (1 VM) | AUD 130.04 |
| Monthly cost (7 VMs) | AUD 910.28 |
| Annual cost (7 VMs) | AUD 10,923.36 |
| **5-year total cost** | **AUD 54,616.80** |

### Azure – Total Cost (7 VMs)

| Item | Cost (AUD) |
|----|-----------|
| Monthly cost (1 VM) | AUD 203.88 |
| Monthly cost (7 VMs) | AUD 1,427.16 |
| Annual cost (7 VMs) | AUD 17,125.92 |
| **5-year total cost** | **AUD 85,629.60** |

### Comparison and Discussion

AWS is significantly more cost-effective than Azure over the 5-year period for equivalent specifications, resulting in a saving of approximately **AUD 31,000**.

#### Advantages of Cloud Virtual Machines
- No upfront capital expenditure
- High availability and built-in redundancy
- Easy scalability as new branch offices are added
- Reduced hardware maintenance responsibility

#### Disadvantages of Cloud Virtual Machines
- Ongoing operational expenditure
- Dependence on internet connectivity
- Reduced physical control over infrastructure

Compared to purchasing new on-premise servers, cloud virtual machines provide greater flexibility, faster scalability, and reduced operational overhead for an organisation with multiple geographically distributed offices.

### Recommendation

Based on the cost analysis and operational considerations, **Amazon Web Services (AWS)** is recommended as the preferred cloud provider for Truelec. AWS offers the lowest total cost over five years while meeting availability, performance, and scalability requirements for the booking application.
