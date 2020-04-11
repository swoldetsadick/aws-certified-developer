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

**Load balancers** are servers that **forward internet traffic to multiple servers** downstream

![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/20.PNG)

It **spreads network traffic load** across multiple downstream instances and **exposes only a single point of access** (DNS).
It serves to **handle instance failure seamlessly** by doing **regular health check** of instances.
It also enforces **stickiness with cookies** as well as provide **SSL termination** for HTTPS.
It can provide **high availability across zones** and **separate public from private** network **traffic**.

**Elastic Load Balancer (ELB)** is an EC2 instance that is a **managed load balancer**. Managed means that:
    
    1. AWS guarantees it works
    2. AWS takes care of upgrades, maintenance and high availability
    3. AWS provide easy configuration via UI

the advantage over self-made load balancers being that it will **generate less maintenance** costs even if more expensive to setup and it **integrates well with other** compute and monitoring **services**.
There exists **3 ELB types**:
    
    1. Classic Load Balancer (v1) - 2009
    2, Application Load Balancer (v2) - 2016
    3. Network Load Balancer (v2) - 2017
    
recommendation is to **use v2** load balancers
One can set **internal (private) and an external (public) ELBs**

#### Health Check

Health checks are crucial to load balancers because they **enable the LB to know if** **instances are healthy and can receive traffic**
Heath check is done usually on specific **port and route (usually /health)**

#### Application Load Balancer (ALB)

* ALB allows to:
   1. Load balancing to multiple HTTP application across machines (Target Groups) [Layer 7 HTTP]
   2. Load balancing to multiple applications on same machine (ex: Containers...)
   3. Load balancing can be done **on route in URL**
   4. Load balancing can be done **on hostname in URL**

* Great for micro-services and container based applications (ex: ECS)
* Has a port mapping feature to re-direct to a dynamic port that allow it to load balancing to multiple applications on same machine
(in comparison an CLB would need to be as many as application while of ALB you would need just one)

![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/21.PNG)

~~Resume:~~

* Stickiness can be enabled at target group level meaning same req goes to same instances and stickiness is directly generated by the ALB
* ALB supports HTTP/HTTPS and Websockets protocol 
* The application server does not see the client IP directly, it is rather inserted in the header X-Forwarder-For, X-Forwarder-Port for port and X-Forwarder-Proto for proto

#### Network Load Balancer (NLB)

* NLB allows to:
   1. forwards TCP/TLS/UDP traffic to your instances (Target Groups) [Layer 4 TCP]
   2. Handles millions of requests per seconds - High availability
   3. supports static or Elastic IP
   4. Less latency approx. 100ms ( vs 400 ms for ALB)
* Used for high performance and should not be the default go to

![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/22.PNG)

~~Resume:~~

* **CLB are deprecated** use **ALB for HTTP/HTTPS** and websockets and **NLB for TCP/TLS/UDP**
* **CLB and ALB support SSL certification** and provide SSL termination
* All LBs have **health check capabilities**
* ALB can **route** based **on hostname / route**
* **ALB** are **great for ECS**
* CLB, ALB and NLB **all have static hostname** **do not use underlying IP**
* **LBs** can **scale** but **not instantaneously**
* **NLB** can **directly see the client IP**
* **4xx** errors are **client** induced **errors**
* **5xx** are **application** induced **errors** ( - Load balancer error **503** means **at capacity or no registered target**) 

```
Lab VII

* on the left pane find "Load balancer" option under "load balancing"
* click on "create load balancer" button
* in "Application load balancer" column click create
* give instance a name and choose "internet facing" (for public ELB and choose "internal" for private)
   -> IP adress type (IPv4 or dualstack)
   -> in "Listeners" list all protocol-port pair we want ELB t listen on
   -> "avail. zone" use all 3 zones for high avail.
   -> VPC (?)
   -> add at least "Name" tag
* pass configure security settings to configure security groups and go to create security group.
   -> give name and description
   -> give type (protocol, port, source)
* create target group for instance and heath check can be done in advanced settings
* ON "register targets" "add to registered" instances of choice
* then click "review" for review and then "create"
* Navigate back to "Load balancers" page and wait for state to be "provisioned"
* now you can connect both via IP and DNS of the LB so resctrict access via IP via security group of instance by
reducing its security group's inbound rule source for http 80 to be only coming from LB

```

### ASG

* The goal of an ASG is to:
    1. scale out (add EC2 instances) to match increment in load
    2. scale-in (reduce EC2 instance) to match reduce in load
    3. Ensure we have a min and ma machines running (min, max and desired)
    4. automatically register new instance to load balancer

![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/23.PNG)
![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/24.PNG)

#### Attributes
1. A launch configuration (AMI + instance type, EC2 user data, EBS volumes, security groups, SSH key pairs...)
2. Min/ Max / Desired capacity
3. Network + subnet information
4. Load balancer information

#### Alerts
1. Possible to scale an ASG based on Cloudwatch alarms
2. An alarm monitors a metric (such as number of users)
3. Metric are calculated overall ASG instances
4. Based on the alarms one can create:
    a. scale-out policies
    b. scale-in policies

#### Auto-Scaling new rules
1. Possible to define better auto-scaling rules that are directly managed by EC2:
    a. avg. CPU usage
    b. Number of requests on the ELB per instances
    c. avg. network in
    d. avg. network out
2. rules easier to setup and more intuitive to understand

#### Auto-Scaling with custom metrics
1. sends custom metric from application (in EC2) to Cloudwatch (put metric API)
2. create Cloudwatch alarms to react to low / high values
3. use Cloudwatch alarms as the scaling policy for ASG

#### ~~Resume~~
* scaling policies can be on (CPU, network...) and can even be on custom metrics or schedule
* ASG use launch configuration and you update an ASG by providing a new launch configuration
* IAM roles attached get transferred from ASG to instances
* ASG are free
* If instances are killed by accident ASG can reboots them (so extra safety)
* ASG kills automatically instances marked as unhealthy  by ASG

```
Lab VIII - ASG
```

#### EBS Volumes
* An EC2 machine loses its root volume (main drive) when it is terminated, if you need data persistence across shutdown then use EBS volumes.
* Elastic Block Store is a network drive you can attach to your instance while they run
* it allows EC2 to perists data
* it is a network drive (not a physical drive)
    1. it uses network to communicate (so a bit latency)
    2. can be detached from instance and re-attached to new one
* Locked to an AZ (moved across via snapshots)
* Have provisioned capacity (size in GBs and IOPS) and billed for all provisioned capa
* EBS volumes are 4 types:
    1. GP2 (SSD) Balance price and performance
    2. IOI (SSD) for databases
    3. STI (HDD) Big data (hot storage)
    4. SCI (HDD) Big data (cold storage)
* EBS characterized by size | throughput | IOPS
* EBS can be resized (size and IOPSonly for IOI)
* After re-size you need to re-partition 
* EBS can be backed-up using snapshots
* snapshots only take the actual space of the block on the volume

#### EBS Encryption

1. Data is encrypted at rest via KMS (AES-256) keys
2. Data is encrypted at flight between EBS and instances via TLS
3. All snapshots are encrypted too
4. volumes created from encrypted snapshots are also encrypted

* Encryption and decryption handled transparently (nothing to do for user)
* Has minimum impact on latency

#### EBS instance store
* some instances do not come with root EBS volume but an instance store instead
* an instances store is physically attached to the machine
    pro: Better I/O perforamce
    cons: on termination instance store is lost, not re-sizable, backups are hard to manipulate
* EBS- backed instances should be the norm

#### ~~Resume~~

* EBS can be attached to only one instance at a time
* EBS are locked at the AZ level
* Migrating an EBS volume across AZ means first backing it up (snapshot) then re-creating it in the other AZ
* EBS backups use I/O and you should not run them while app is handling traffic
* Root EBS volumes of instances get terminated by default if the EC2 instances get terminated

### Route 53
* Route 53 is a managed DNS
* DNS is a collection of rules and records which helps clients understand how to reach a server thorough a URL
* AWS most common URLs:
    1. A URL to IPv4AWSRDS
    2. AAAA URL to IPv6
    3. CNAME URL to URL
    4. Alias URL to AWS resource

![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/25.PNG)

* Route 53 can use **public domain** and **private domain** (resolvable only within VPC)
* Route 53 is used as **LB through DNS** (or Client LB) can make **health checks** and handles **routing policy**.
* Prefer Alias over CNAME for AWS resources

### RDS
* Relational database service is a managed DB services for DB that use SQL
* Create DB in the clod managed by AWS (postgres, oracle, mysql, MariaDB, MySQL, Aurora...)
* Managed services meaning: OS patching, continuous backup, monitoring, read replicas, multi AZ setup for DR...
* But cannot ssh directly to them

#### RDS Replicas for read scaling
![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/26.PNG)
1. upto 5 replicas
2. with AZ, cross AZ or Region
3. Replication is async
4. each replica can become its own db
5. one needs to update connection string to leverage read replicas

#### RDS multi AZ - disaster recovery
![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/27.PNG)
1. sync replication
2. one DNS name so no manual intervention in app to update connection string
3. increase of avail.
4. Failover in case of loss of AZ
5. Not used for scaling

#### RDS encryption
1. Encryption at rest via AWS KMS that leverages AES 256 encryption
2. SSL certificates to encrypt data in RDS in flight
3. to enforce SSL
    a. postgresql rds.force.ssl=1
    b. mysql GRANT USAGE ON *.* TO 'user'@'@'% REQUIRE SSL
4. to connect using SSL
    a. Download SSL on AWS website
    b. provide SSL options when connecting to DB

#### RDS Security
1. usually deplyoed within private VPC and not avail. from public but can be
2. RDS security works via security groups
3. IAm policy helps control who can manage AWS RDS
4. Traditional username and password can be used to login to the DB
5. IAM users can also be used too

#### RDS vs Aurora
![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/28.PNG)

### AWS Elasticache
1. Elasticache is a AWS managed service for inmem Ds
2. caches are in-mem DBs with high performance and low latency
3. they help reduce load from RDS for read intensive application
4. helps makes applications stateless  (by storing states)
5. write scaling by using sharding
6. read scaling by using read replicas
7. multi AZ with failover
8. AWS takes care of maintenance, backup, recovery...

#### Solution Architecture - As RDS intermediary
![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/29.PNG)

1. application queries elasticache if not avail. gets query from RDS and writes it to cache (cache hit - cache miss)
2. helps relieve load from RDS
3. apps must have built-in invalidation strategies

#### Solution Architecture - As RDS intermediary
![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/30.PNG)

#### REDIS
1. REDIS is an in-mem key-value store
2. super low latency (below ms.)
3. cache survives reboots by default (persistency)
4. Great to host:
    a. user sessions
    b. leaderboards
    c. distributed states
    d. relieve pressure from RDS
    e. pub/sub for messaging
* supports read replicas
* multi AZ failover

#### Memcached
* memcached is an im-mem object store
* cache does not survive reboot
* use cases:
    a. quick retrieval of objects
    b.caching often accessed objects
* prefer REDIS

### Elasticache Strategies
1. Elastic cache is excellent for read intensive application
2. Elastic cache is excellent for compute intensive workloads
3. There are 2 patterns (caching strategies) for elasticache:
    a. Lazy loading
    b. Write through
4. use different architecture based on the kind of application

#### Lazy loading
![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/31.PNG)

pros:
    1. only requested data is cached
    2. node failure are not fatal
cons:
    1. cache miss penalty results in 3 round trips
    2. stale data can happen (so implement TTL)

#### write through
![alt text](https://github.com/swoldetsadick/aws-certified-developer/blob/master/images/32.PNG)

pros:
    1. data in cache is never stale
    2. write penalty costs 2 round trips but no read penalties
cons:
    1. data can be miss until added or updated in DB (mitigate by implementing also LL)
    2. cache burn as not all data in cache in needed

### AWS VPC

