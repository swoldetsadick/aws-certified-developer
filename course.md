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

How SSH works

![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/10.PNG)

EC2 will allow SSH only if:
1. activated the public IP option
2. if you set the right firewall rule (security group) for it


```
Lab II

1. Navigate to instance overview page, find instance and click on it
2. Get to IPv4 public IP and copy the IP adress xx.xx.xxx.xxx
3. Get over to inbound rules on same page and see if port22 is open by security group
4. Find the key pair you created for the instance in lab I (ex: ~/.ssh/EC2.pem

chmod 0400 ~/.ssh/EC2.pem
ssh -i ~/.ssh/EC2.pem ec2-user@xx.xx.xxx.xxx

DEBUG:

1. When downloding it the private key file is permissio 0644 which can throw "uprotected key file" error when doing SSH
Resolution: chmod 0400 ~/.ssh/EC2.pem

2. If you get connection timeout error it means that you have a security group issue or corporate firewall issues.

3. Connection refused means that whether that instance is down or SSH utility is not installed on it
```

**EC2 connect** is a **browser based SSH connection utility** that can be launched from "instances" page.

#### Introduction to security groups

**Security groups** is **fundamental to network security** in AWS.

![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/11.PNG)

They **control traffic allowed** into and out of EC2 and act like a **firewall** for EC2 instance.

A security group :

1. can be attached to multiple instances
2. is locked to a region / VPC combo
3. lives outside EC2 instance (so traffic is filtered before reaching EC2)
4. misconfiguration is always the reason of of SSH timeout issues
5. allows by default all inbound traffic and blocks all outbound traffic

![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/12.PNG)

Security groups regulate:

1. access to ports
2. authorized IP ranges both IPV4 and IPV6
3. Inbound network
4. outbound network

**Referencing other security groups**

![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/13.PNG)

Referencing security groups from other security groups serves to allow all traffic from instances that have attached
security in the allowed list whatever the IP range is.

```
Lab III

1. Navigate to "instances" page and choose the right instance and click on the security group of your instance
2. on security groups page, select the right security group
3. Below one can see Details, Inbound rules, Outbound rules and Tags buttons
4. Edit all Inbound and outbound rules to see changes
```

#### Private vs Public vs Elastic IP

1. **Public IP**
    i. public IP means **machine** will be **identified on the internet**
    
    ii. IP is **unique across the internet**
    
    iii. **can be geo-located**

2. **Private IP**

    i. private IP machine can **only be identified within the private network** only
    
    ii. IP must be **unique only across the private network**
    
    iii. but **2 different machines** on **separate private networks** can have the **same IP**
    
    iv. machines on private network usually **access** then **internet via** an **internet gateway (proxy)**
    
    v. only a **specific IP range can be used as private IP**
    
3. **Elastic IP**

    i. when **stopping and starting** an **EC2** instance it can **change public IP**
    
    ii. if you **don't want it to change public IP** one can **use elastic IP**
    
    iii. an elastic IP is **a public IPv4 IP you own as long as you don't delete it**
    
    iv. it can only be **attached to one instance at a time**
    
    v. you can of course hide failure of software by re-assigning IP of failed instances
    
    vi. AWS allows up to 5 elastic IPs but the limit can be raised
    
    vii. Avoid using elastic IPs
    
      a. best use random public IP then assign a registered DNS to it
    
      b. or use a load balancer and not use public at all

```
Lab IV

1. Navigate to "instances" page and choose the right instance 
2. on "Description" tab find both private and public IP
3. find green running and right-click on it
4. find "instance state" in the dropdwon wherestop and then start back instance again
5. on "Description" tab find both private and public IP observe that public IP has changed but not the private IP
6. on the left panel find "Elastic IPs" under "Network & Security" button and click it
7. click on allocate Elastic IP adress and then allocate button
8. you can now select the new Elastic IP and on "tags" tab associate key called 'Name' to a name for the Elastic IP
9. click on "Actions" button then "Associate Elastic IP address"
 a. Ressource Type: choose instance
 b. Instance: choose the ID of EC2 instance
 c. Private IP address: Choose elastic IP
and press "asscoiate" button and on "Elastic IP address" page you can see the elastic IP has been associated to your EC2 instance
10. go to "instances" page find and click your instance and on "description" tab see that üublic IP has changed and that elastic IP fields is filled too with same IP
11. check you can ssh to test and then stop and re-start your instance to see that public IP did not change
12. right click on your instance agai "Dissociate Elastic IP address" option under "netwroking" once you stpped your instance
13. restart your instance and see that elastic IP has gone and public IP has changed again
14. Go to "Elastic IPs" page choose the Elatic IP you created click on "Actions" button and choose "Release Elastic IP"

```

#### Install Apache Server

```
Lab V

sudo su
yum update -y
curl -sL https://rpm.nodesource.com/setup_12.x | sudo bash -
yum install nodejs
npm install -g @angular/cli @angular/core
ng new test
npm run build --prefix /home/ec2-user/test
yum install -y httpd.x86_64
systemctl start httpd.service
systemctl enable httpd.service
cp test/dist/test/* /var/www/html/
curl localhost:80

update inbound rules for security groups of the insatnce to have an additional rule to allow http from anywhere via port 80
in a broswer entre http://xx.xxx.xxx.xxx:80 where xx.xxx.xxx.xxx is the public IP of your instance you shuld see a page

```

#### EC2 User data

```
Lab VI

* Start a new instance from scratch following Lab I but when you get to "user data option" pass it the text below with option text selected

#!/bin/bash
yum update -y
curl -sL https://rpm.nodesource.com/setup_12.x | sudo bash -
yum install -y nodejs
npm install -g @angular/cli @angular/core
ng new test --routing=true --style=css --commit=false
npm run build --prefix /home/ec2-user/test
yum install -y httpd.x86_64
systemctl start httpd.service
systemctl enable httpd.service
cp test/dist/test/* /var/www/html/

* attach existing security group one created in previous lab
* attach existing key pair from previous lab
* wait the instance to finish initializing and and get the public IP then navigate to http://xxx.xxx.xxx.xxx:80

```

#### EC2 Instances Launch types

![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/14.PNG)
![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/15.PNG)
![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/16.PNG)
![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/17.PNG)
![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/18.PNG)
![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/19.PNG)

#### EC2 pricing

1. Pricing is given per hour and depends on:

    - Region you are in
    
    - Instance type
    
    - Pricing Model (spot/on demand/reserved/scheduled/convertible/dedicated/dedicated host)
    
    - operating system
    
2. Billed by second with threshold of 60 seconds up

3. Additional cost for things like (Storage, data transfer, fixed IP...)

4. You do not pay if instance is stopped

#### AMI

We have a bunch of images that come with AWS, and we can use "User Data" to bootstrap but if you want to do it all the time use AMIs.

You can use your own "custom AMI" for both Linux and Windows and can also share it or use other people's AMI

AMI built are AWS Region specific

#### EC2 Types

EC2 types are specific combination of:
1. RAM (Type, amount, generation)
2. CPU (type, make, frequency, generation, core numbers)
3. I/O (disk performance, EBS Optimization)
4. Network (bandwidth, network latency)
5. GPU

M type has balanced these features and type are specialized in one or two of above components.
T2/T3 are burstable types with accumulated CPU credits even though we have seen T2 unlimited.

#### Resume

To Know:

1. How to SSH to EC2 with 0644 problem
2. Properly use security groups
3. Difference between private vs public vs elastic IPs
4. User Data
5. how AMIs enhance your OS
6. EC2 instances are billed by the second above threshold of 60 seconds and prices are given in hour.

### V. ELB, ASG and EBS volumes
