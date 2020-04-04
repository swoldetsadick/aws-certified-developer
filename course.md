# Section 1: Introduction

### Exam guide
[link](https://github.com/swoldetsadick/aws-certified-developer/blob/master/AWS_Certified_Developer_Associate-Exam_Guide_EN_1.4.pdf)

1. Create AWS Account
2. Set AWS Budget
3. AWS Technologies Review

    a. Fundamentals for 3-tier web apps
    
    ![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/1.PNG)
    
    b. developer tools
    
    ![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/2.PNG)
    
    c. CI / CD with Monitoring and Infrastructure as Code
    
    ![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/3.PNG)
    
    d. Application decoupling & integration
    
    ![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/4.PNG)
    
    e. serverless paradigm
    
    ![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/5.PNG)
    
    f. always secure
    
    ![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/6.PNG)
    
    g. other services
    
    ![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/7.PNG)

# Section 2: Slides

[link](https://lbs-application.s3.eu-central-1.amazonaws.com/AWS+Certified+Developer+Slides+2.0.pdf)

# Section 3: AWS Fundamentals ( IAM - EC2 )

### I. AWS Regions

**AWS regions** are **geographical locations all around the world**, with each having at least 3 **availability zones (AZ)**
which are **physical data centers** with **redundancy** creating **disaster safety**.

**AWS console** is generally **scoped to a region**, **except for IAM and S3**.

### II. IAM (Identity and Access Management)
  
 Main components of IAM are **Users**, **groups** and **Roles** is **scoped globally** and is **center of AWS security.**
 
 * **Root users** have the **most power** and are **never to be used except for initial setup**
 * A **user** should **represent** one and only one **physical person**
 * **User** must be created with proper **permissions**
 * **MFA** is possible for all users
 * **permissions** are **governed via policies**
 * **policies** are written in **JSON**
 * IAM has **predefined "managed policies"**
 * **prefer** to attach permissions to users via **groups rather than directly attaching policies** to users
 * A **group** **defined by certain policy** is a **set of users** that **inherit permission from group policy**
 * A **role** represents one **specific application** and also has associated permissions
 * For big companies AWS also had **IAM federation** that helps them integrate their own user repository such as AD groups so user can login with corporate password and this uses SAML standard
 
 * The philosophy is to **give users/roles minimum amount of permission to perform their jobs (least privilege principle)**
    
### III. Lab

 a. Delete root access key
 
 b. Activate MFA
 
 c. create a user with admin policy attached directly
 
 d. create group assign admin policy to it and add user to this group, erase directly attached policy
 
 e. add password policy (how often should it be changed? How should password look like)
 
 (optional): customize IAM users sign-in link
 
### IV. EC2
