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
 
 ![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/8.PNG)
 
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

**EC2** is **central in understanding the cloud paradigm** and is a AWS service that is **region scoped**.

EC2 mainly consists of the capabilities of:
1. **renting virtual machine** online via **Elastic Compute Cloud (EC2)**
2. **storing data on virtual drives** online via **Elastic Block Store (EBS)**
3. **distributing loads across multiple machines** via **Elastic Load Balancer (ELB)**
4. **scaling services** via **Auto-Scaling Groups (ASG)**

`Elastic Compute Cloud (EC2)` is a web service that provides secure, resizable compute capacity in the cloud.

`Elastic Block Store (EBS)` is an easy to use, high performance block storage service.

`Elastic Load Balancer (ELB)` automatically distributes incoming application traffic across multiple targets.

`Auto-Scaling Groups (ASG)` an Auto Scaling group contains a collection of Amazon EC2 instances that are treated as a
logical grouping for the purposes of automatic scaling and management.

```
Lab I
Goal: Launch virtual server in AWS Console

1. Navigate to EC2 service page where one can find an overview of all resources
2. Choose the nearest region
3. Navigate then to "Instances" page where one can find a list of EC2 instances details
4. Click on "Launch Instance"

    A. Choose an Amazon Machine Image (AMI)

    B. Choose an Instance Type
        i. "Family" is a purpose driven grouping of EC2 types 
            a. "General purpose" instances provide a balance of compute, memory and networking resources,
            and can be used for a variety of diverse workloads. These instances are ideal for applications that use these
            resources in equal proportions such as web servers and code repositories.
            b. "Compute optimized" instances are ideal for compute bound applications that benefit from high performance
            processors. Instances belonging to this family are well suited for batch processing workloads, media
            transcoding, high performance web servers, high performance computing (HPC), scientific modeling, dedicated
            gaming servers and ad server engines, machine learning inference and other compute intensive applications.
            c. "GPU instances" or "Accelerated Computing" instances use hardware accelerators, or co-processors, to
            perform functions, such as floating point number calculations, graphics processing, or data pattern matching,
            more efficiently than is possible in software running on CPUs.
            d. "Memory Optimized" instances are designed to deliver fast performance for workloads that process large
            data sets in memory.
            e. "Storage Optimized" instances are designed for workloads that require high, sequential read and write
            access to very large data sets on local storage. They are optimized to deliver tens of thousands of low-latency,
            random I/O operations per second (IOPS) to applications.
        ii. "Type" Instance types comprise varying combinations of CPU, memory, storage, and networking capacity and
        give you the flexibility to choose the appropriate mix of resources for your applications. Each instance type
        includes one or more instance sizes
        iii. "virtual CPU" is the number of virtual CPUs
        iv. "memory" is size of storage in megabytes
        v. "instance storage" is the local instance store volumes that are available to the instance. The data in an
        instance store is not permanent - it persists only during the lifetime of the instance.
        vi. "EBS-optimized available" Indicates whether the instance type supports EBS optimization. An EBS-optimized
        instance provides additional, dedicated throughput for Amazon EBS I/O.
        vii. "Network performance" describes rate of data transfer
        viii. "IPv6" Indicates whether the instance type supports IPv6 Addresses

    C. Configure Instance Details
        i. "Number of instances" is just the number of instances spinned up
        ii. "Purchase option" if you need to request spot instances
        iii. "Network" ?
        iv. "Subnet" to assign specific availibility zone (AZ)
        v. "Auto-assign Public IP" enabled fo accessing instance from outisde world disable if not
        vi. "Placement" ?
        vii. "Capcity reservation" ?
        viii. "IAM role" ?
        ix. "Shutdown behavior" should a shutdown 'stop' or 'terminate' a EC2 instance
        x. "Stop - Hibernate behavior" ?
        xi. "Enable termination protection" ?
        xii. "Monitoring" ?
        xiii. "Tenancy" ?
        xiv. "T2/T3 Unlimited" ?
        xv. "File systems" ?
        xvi. "Metadata accessible" ?
        xvii. "Metadata version" ?
        xviii. "Metadata token response hop limit" ?
        xix. "User data" ?

    D. Add Storage
    
    E. Tags
        Tags are a key - value pairs for identification and classification of instances. (ex: Name)
    
    F. Security Groups
        A security group is a set of firewall rules that control the traffic for your instance. On this page, you can add
    rules to allow specific traffic to reach your instance. 
    
    G. Review and Launch
        Review parameters

    H. Launch
        Create a key pair. A key pair is credentails that helps you ssh into your instance one can create a new one or
        import and existing one.
    
    I. View Instance
        In instance overview find your instance through Name tag and find green running. right-click on it and find
        "instance state" in the dropdwon where you can [start, stop, stop-hibernte, reboot or terminate] the instance
```

#### SSH Overview
![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/9.PNG)
