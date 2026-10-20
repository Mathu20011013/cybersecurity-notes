

- Governance - managing/ directing organization to meet objectives
- Regulation - rules enforced by the governing the body
- Compliance - Adhering to those rule

# Information security governance process

strategy --> policies --> risk management --> performance measurement --> compliance 

**Key Regulations**

| Regulation | Domain                   |
| ---------- | ------------------------ |
| GDPR       | Data Privacy (EU)        |
| HIPAA      | Healthcare (US)          |
| PCI-DSS    | Financial/Payment Cards  |
| GLBA       | Financial/NPI protection |

# Benefits of Governance
- strong security
- stakeholders trust
- avoid penalties
- business alignment
- competitive edge

# Framework Document type

- Policy -  Formal document that outline the goals and principles to achieve the objectives
- Standards - specific requirements  for the particular process, product / services
- Guidelines - provide the recommendations and best practices for achieving specific goals or objectives
- Procedures - Set of specific steps 
- Baseline - Minimum security requirements

# Steps to develop Governance document

1. Identify the scope & purpose 
2. Research 7 review
3. Draft 
4. Review & approval
5. Implement & communicate
6. Review & update

# GRC

GRC = Governance + Risk + Compliance
integrated approach to  align security with org goals

|Component|What it does|Example|
|---|---|---|
|**Governance**|Sets direction via policies & strategy|Security steering committee|
|**Risk Management**|Identify → Assess → Mitigate risks|Fix weak access controls|
|**Compliance**|Meet legal/industry obligations|Follow PCI-DSS, HIPAA|


## **7 Steps to Build a GRC Program**

1. Define scope & objectives _(e.g. reduce risk by 50% in 12 months)_
2. Risk assessment _(find vulnerabilities)_
3. Policies & procedures _(e.g. password policy)_
4. Governance processes _(e.g. security committee)_
5. Implement controls _(firewall, IDS, IPS, SIEM)_
6. Monitor & measure _(track KPIs)_
7. Continuously improve _(post-incident review)_

Final Simple Understanding

- **Governance** → “What rules should we follow?”
- **Risk Management** → “What can go wrong?”
- **Compliance** → “Are we following laws?”


Easy Real-Life  example 

Think of a **bank security system**:

- Governance → Bank sets security policies
- Risk → Bank identifies fraud risks
- Compliance → Bank follows financial laws

# Privacy and Data Protection

PII = Personally Identifiable Information
	Core focus of ALL privacy regulations

Key points of the law 
-  **Prior approval** must be obtained before collecting any personal data.
-  Personal data should be kept to a **minimum** and only collected when necessary.
-  **Adequate measures** are to be adopted to protect stored personal data.


**GDPR** - General Data Protection Regulation _(EU, May 2018)_

| Key Rule     | Detail                                       |
| ------------ | -------------------------------------------- |
| Consent      | Must get approval **before** collecting data |
| Minimization | Collect only what's necessary                |
| Protection   | Adequate security measures required          |
| Applies to   | Any business handling EU residents' data     |

**GDPR Penalties**

- **Tier 1** _(severe — e.g. unauthorized data sharing)_ → **4%** revenue or **€20M**
- **Tier 2** _(less severe — e.g. breach notification failures)_ → **2%** revenue or **€10M**

**PCI DSS** - Payment Card Industry Data Security Standard _(Payment Card Industry)_

- Created by **Visa, MasterCard, American Express**
- Protects **card transactions** from theft & fraud
- Requires → access control + monitoring + **WAF** + **encryption**
- Used mainly by **online businesses**

CHD - cardHolder Data

# NIST  special publications

**NIST 800-53** = "Security & Privacy Controls for Info Systems"
	Made by NIST (US)  
	Protects CIA triad 
	20 control families


**4 Compliance Best Practices**

**Discover → Map → Manage → Monitor**

- **Discover & Classify** sensitive data
- **Map** data and permissions
- **Manage** access control
- **Monitor** data, file activity, user behavior


**4 Control Categories** 

|Type|Examples|
|---|---|
|**Administrative**|Audit (AU), Incident Response (IR), Risk Assessment (RA)|
|**Technical**|Access Control (AC), Authentication (IA), System Integrity (SI)|
|**Physical**|Personnel Security (PS), Media Protection (MP)|
|**Strategic**|Planning (PL)|


**Program Management Key Sub-controls** 

	 Risk strategy · Insider threat program · Privacy policies · Data governance body · Data integrity board · Threat intelligence sharing


**NIST 800-63B** = Digital Identity & Authentication

- Focuses on **verifying who accesses systems**
- Covers → **passwords + biometrics + tokens**
- Different **assurance levels** (basic → high)

# NIST 800-53 Compliance 

- Identify and classify **assets, systems, and risks**
- Map **security controls** to identified risks
- Establish **governance structure** (roles, policies, responsibilities)
- Implement **technical and administrative controls**
- Perform **continuous monitoring** (logs, activities, compliance status)
- Conduct **regular audits and improvements**

_Example:_ If there is a risk of unauthorized access → implement access control + monitor login activity

# NIST 800-63B 
- Focuses on **digital identity and authentication**
- Defines **levels of assurance** (low to high)
- Recommends:
    - Strong passwords
    - Multi-factor authentication (MFA)
    - Secure credential management

# Program Management (NIST 800-53) 

- Establish **organization-wide security program**
- Define **roles and responsibilities**
- Align security with **business objectives**
- Monitor **program performance**
- Ensure **continuous improvement**

| Control Type          | Control Families                                                                                                                                                            |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Management Controls   | PM (Program Management), RA (Risk Assessment), PL (Planning), CA (Assessment, Authorization)                                                                                |
| Operational Controls  | AT (Awareness & Training), AU (Audit & Accountability), IR (Incident Response), MA (Maintenance), MP (Media Protection), PS (Personnel Security), CP (Contingency Planning) |
| Technical Controls    | AC (Access Control), IA (Identification & Authentication), SC (System & Communications Protection), SI (System & Information Integrity), CM (Configuration Management)      |
| Physical Controls     | PE (Physical & Environmental Protection)                                                                                                                                    |
| Supply Chain Controls | SR (Supply Chain Risk Management)                                                                                                                                           |



# Short Note 

**Information Security (IS) Management**  
Protects information from unauthorized access, use, or damage through:

- Risk assessment
- Security controls
- Incident response
- Awareness training

**Compliance**  
Following laws, regulations, and standards related to information security.


## ISO/IEC 27001

- Global standard for **Information Security Management System (ISMS)**
- Focus: **Build, implement, maintain, improve security system**
- Key elements:
    - Scope
    - Security policy
    - Risk assessment & treatment
    - Statement of Applicability (SoA)
    - Internal audit & management review

	 Goal: **Manage risks and protect information systematically**



## SOC 2

- Audit framework by AICPA
- Focus: **Effectiveness of security controls**
- Based on **CIA Triad**:
    - Confidentiality
    - Integrity
    - Availability

	 Goal: **Prove to customers that data is secure**


- **IS Management = Protect & manage security internally**
- **Compliance = Follow external rules & standards**
- **ISO 27001 → Build and run a security system (ISMS)**
- **SOC 2 → Prove your security works (Audit report)**
- **ISO = Process-focused (management system)**
- **SOC 2 = Audit-focused (trust & assurance)**
- **Both together = Strong security + customer trust**


## steps in a SOC 2 Audit

1. **Define Scope**  
    Decide which systems, processes, and data will be audited.
2. **Select Auditor**  
    Choose an independent auditor (usually from AICPA standards).
3. **Plan the Audit**  
    Set timeline, scope, and criteria with the auditor.
4. **Prepare for Audit**  
    Review policies, controls, and fix gaps.
5. **Conduct Audit**  
    Auditor tests controls (interviews, documents, system checks).
6. **Audit Report**  
    Get final report with findings and recommendations.

**S S P P C R**  
	 _Scope → Select → Plan → Prepare → Conduct → Report_

## ISO/IEC 27001

Key Components

- **Scope** – Defines boundaries of ISMS
- **Information Security Policy** – Overall security direction
- **Risk Assessment** – Identify & evaluate risks
- **Risk Treatment** – Apply controls to reduce risks
- **Statement of Applicability (SoA)** – Selected controls list
- **Internal Audit** – Check ISMS effectiveness
- **Management Review** – Regular performance review

 Benefits

- Protects **confidentiality, integrity, availability** of data
- Improves **risk management**
- Ensures **legal & regulatory compliance**
- Builds **customer trust**
- Supports **continuous improvement**
- Enhances **overall security posture**