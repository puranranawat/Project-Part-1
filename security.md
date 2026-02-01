# Security
This section gives a cyber security risk assessment for the company and recommended security controls.

[Risk Assessment](#risk-assessment) | [Security Controls](#security-controls) | [Plan](./plan.md) | [Network Design](./network.md) | [Cloud Services](./cloud.md) | [Ethics](./ethics.md) | [Reflection](./reflection.md) | [Return to index](./README.md)

---

## Risk Assessment

A mini cyber security risk assessment was conducted using the risk assessment template provided in the unit. Due to limited organisational detail, a subset of a full risk assessment process was applied, focusing on identifying key assets, threats, vulnerabilities, and associated risks relevant to the proposed network and cloud-based infrastructure for Truelec.

The assessment considers:
- Assets from **all asset types** (data, software, hardware, and people)
- **Five data assets**, exceeding the minimum requirement:
  - Customer Personal Data  
  - Employee HR Records  
  - Financial and Accounting Data  
  - Booking Application Database  
  - Access Control Logs (RFID & CCTV)
- **More than eight information security threats**, including data breach, malware and ransomware, phishing and social engineering, denial of service, insider misuse, privilege abuse, misconfiguration, physical theft, and loss of availability

Risk levels were evaluated using a qualitative scale:
- **Likelihood:** 1 (Low) to 3 (High)  
- **Impact:** 1 (Low) to 3 (High)

The completed risk register spreadsheet is provided below:

[View risk assessment spreadsheet](./risk_assessment_HD.xlsx)

---

### TVA Matrix Summary

The TVA Matrix Summary below provides a consolidated view of assets, threats, likelihood, impact, and resulting risk levels. The matrix clearly identifies the highest-risk assets within the organisation.

**TVA Matrix Screenshot – Part 1**

![TVA Matrix Summary Part 1](./security/TVA_Matrix_1.png)

**TVA Matrix Screenshot – Part 2**

![TVA Matrix Summary Part 2](./security/TVA_Matrix_2.png)

Based on the TVA Matrix, **Customer Personal Data** is identified as the **highest-risk data asset**, with a **High risk rating** resulting from a combination of high likelihood and high impact associated with unauthorised access and data breaches.

---

## Security Controls

Based on the risk assessment results, the following three security controls are recommended to reduce the risk to **Customer Personal Data**. These controls align with the unit content and relevant controls from **NIST SP 800-53**.

---

### 1. Strong Access Control and Multi-Factor Authentication (MFA)

**Description**  
Access control ensures that only authorised users can access customer personal data. Multi-Factor Authentication (MFA) requires users to verify their identity using an additional factor beyond a password.

**How this control reduces risk**  
This control significantly reduces the likelihood of unauthorised access caused by credential compromise, phishing, or weak passwords. Role-based access control further limits insider misuse by ensuring users can only access data required for their job role.

**Implementation in the project scenario**  
- Enforce MFA on all cloud virtual machines hosting the booking application and customer databases  
- Restrict administrative access to authorised ICT administrators only  
- Apply role-based access for staff accessing customer data from headquarters and branch offices  
- Regularly review and revoke access for staff who change roles or leave the organisation  

This control directly applies to the cloud servers and user access paths defined in the network design.

**Disadvantages for users**  
- Slightly longer login times  
- Training required for staff unfamiliar with MFA  
- Temporary access issues if authentication devices are unavailable  

---

### 2. Encryption of Data at Rest and in Transit

**Description**  
Encryption protects data by converting it into an unreadable format unless decrypted using authorised cryptographic keys. This applies to both stored data and data transmitted across networks.

**How this control reduces risk**  
Encryption reduces the impact of a data breach by ensuring that even if customer personal data is accessed without authorisation, it cannot be easily read or misused.

**Implementation in the project scenario**  
- Enable disk encryption on all cloud virtual machine storage containing customer data  
- Use HTTPS/TLS encryption for all access to the booking application  
- Encrypt backups stored in cloud storage services  
- Encrypt data transmitted between headquarters and branch offices  

This control protects data across WAN links, cloud infrastructure, and internal network connections shown in the network design.

**Disadvantages for users**  
- Minor performance overhead  
- Increased complexity in encryption key management  
- Additional configuration effort for ICT administrators  

---

### 3. Centralised Logging, Monitoring, and Incident Detection

**Description**  
Centralised logging and monitoring involve collecting and analysing system and network logs to detect suspicious or malicious activity.

**How this control reduces risk**  
This control reduces both the likelihood and duration of security incidents by enabling early detection of unauthorised access, abnormal login behaviour, and potential data exfiltration involving customer personal data.

**Implementation in the project scenario**  
- Enable detailed access logging on cloud virtual machines and databases  
- Collect logs from routers, firewalls, and application servers into a central monitoring system  
- Configure alerts for unusual access to customer personal data  
- Regularly review logs as part of incident response procedures  

This control directly relates to the cloud services and network security devices defined in the network design.

**Disadvantages for users**  
- Increased monitoring may raise staff privacy concerns  
- ICT staff must manage and review large volumes of log data  
- Possible additional cost for cloud-based monitoring services  

---

### Summary

The combination of strong access control with MFA, encryption, and centralised logging provides layered protection for customer personal data. These controls significantly reduce the likelihood of unauthorised access, minimise the impact of potential breaches, and improve incident detection and response. Although these controls introduce some usability and administrative overhead, they are justified given the high risk associated with this critical data asset.
