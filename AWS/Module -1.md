**

Client - Server model  - . The client makes a request to the server, and the server processes the request and sends back the response.

  

 AWS services

1. Amazon Virtual Private Cloud (Amazon VPC).
    
2. AWS Lambda.
    
3.  Amazon Simple Storage Service (Amazon S3)
    

##  What is Cloud Computing?

Definition:

Cloud computing =  
  On-demand delivery of IT resources  
  Over the internet  
  With pay-as-you-go pricing

Instead of owning physical servers, you rent computing resources from a cloud provider like Amazon Web Services.

Client-server model =

A client makes a request → a server responds to the request.

## Virtual Servers in AWS

In AWS:

- Servers are not physical machines you see.
    
- They are virtual servers running in AWS data centers.
    

Example service (you should know):

- Amazon EC2 (Elastic Compute Cloud)
    

  
  

## On-Premises vs Cloud 

## 🏢 On-Premises:

- You buy servers in advance
    
- Fixed capacity
    
- Hard to scale quickly
    
- You pay even if servers are idle
    

### ☁️ AWS Cloud:

- No upfront hardware purchase
    
- Instantly scale up or down
    
- Flexible
    
- No long-term commitment required
    

## Pay-As-You-Go Pricing (CORE AWS CONCEPT)

### Definition:

You only pay for the resources you use.  
When you stop using them → you stop paying.

### In AWS:

- Need more servers → provision more
    
- Traffic drops → deprovision
    
- Billing stops immediately when stopped
    

💡 Exam keywords:

- No upfront costs
    
- No long-term contracts
    
- Consumption-based pricing
    
- Operational expense (OpEx), not capital expense (CapEx)
    

  

##  Elasticity 

Elasticity =  
Ability to automatically increase or decrease resources based on demand.

Example:

- High demand → scale out
    
- Low demand → scale in
    

This prevents:

- Overprovisioning (too many servers, waste money)
    
- Underprovisioning (not enough servers, poor performance)
    

## Types of AWS Services

AWS provides services for:

- Compute
    
- Storage
    
- Databases
    
- Networking
    
- AI/ML
    
- Content Delivery
    
- Security
    

# How AWS Started 

### 🔹 Early 2000s

- Amazon.com was an ecommerce website (books, goods).
    
- Rapid growth → needed:  
      
    

- More servers
    
- More storage
    
- More compute  
      
    

- IT team built standardized, scalable infrastructure tools.
    

### 🔹 2003 – Big Idea

Amazon employees realized:

Other companies also struggle with infrastructure scaling.

Idea:

- Rent computing resources to businesses
    
- No need to buy hardware
    
- On-demand model
    

This became AWS.

# First AWS Services 

# 🔹 2004

First public AWS service:

- Amazon Simple Queue Service (SQS)
    

Purpose:

- Message queuing between applications
    

### 🔹 2006 (Major Year)

Two major launches:

1️⃣ Amazon Simple Storage Service (S3)

- Data storage service
    
- Object storage
    
- Highly scalable
    

2️⃣ Amazon Elastic Compute Cloud (EC2)

- Virtual servers
    
- Scalable compute capacity
    
- Core AWS service
    

# Who Used AWS First?

Initially:

- Startups
    
- Developers
    

Later:

- Large enterprises
    
- Governments
    
- Corporations
    
- Millions of global customers
    

Today:  
AWS powers a significant portion of the internet.

# What is a Data Center?

### Definition:

A data center =  
A physical building that contains:

- Servers
    
- Storage systems
    
- Networking equipment
    

Includes:

- Redundant power
    
- Cooling systems
    
- Physical security
    

### Traditional Model (Before AWS)

Companies:

- Built their own data centers
    
- Or co-located in shared facilities
    
- Managed hardware themselves
    
- Large upfront cost (CapEx)  
      
    

### Cloud Model (With AWS)

Companies:

- Run applications in AWS data centers
    
- Do NOT own infrastructure
    
- No hardware management
    
- Focus on innovation instead of maintenance
    

# Official Definition of Cloud Computing 

Cloud computing =

On-demand delivery of IT resources over the internet with pay-as-you-go pricing.

Breakdown:

### ✅ On-demand

- Use resources when needed
    
- No waiting
    
- No procurement process
    

Example:  
Need 2000 TB storage?  
→ Use S3 immediately

Delete files?  
→ Stop paying immediately

### ✅ Over the Internet

- Access via browser
    
- Remote management
    
- From anywhere with internet
    
- No physical presence required
    

  

### ✅ Pay-as-you-go

- No contracts required
    
- No upfront hardware investment
    
- Stop using → stop paying
    
- Consumption-based billing  
      
    

Important Services You Must Know So Far

|   |   |
|---|---|
|Service|Purpose|
|SQS|Message queuing|
|S3|Object storage|
|EC2|Virtual servers (compute)|

  
  
  
  

# Cloud deployment types

1. Cloud - flexibility to migrate your existing resources to the cloud,
    
2. On-premises - it is sometimes sought for its ability to provide dedicated resources and low latency.
    
3. Hybrid - cloud-based resources and on-premises infrastructure work together. a company might choose to retain certain regulated legacy applications on-premises while using cloud services for advanced data processing and analytics.
    

**