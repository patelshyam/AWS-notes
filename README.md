# Table of contents
- [Cloud computing with AWS](#cloud-computing-with-aws)
  * [1. What is cloud?](#1-what-is-cloud-)
    + [1.1 The Six Benefits of Cloud Computing](#11-the-six-benefits-of-cloud-computing)
  * [2. AWS Global Infrastructure](#2-aws-global-infrastructure)
    + [2.1 Here are a few examples of Region codes:](#21-here-are-a-few-examples-of-region-codes-)
    + [2.2 Choose the Right AWS Region](#22-choose-the-right-aws-region)
  * [3. Availability Zones](#3-availability-zones)
  * [4. Interacting with AWS](#4-interacting-with-aws)
    + [4.1 The AWS Management Console](#41-the-aws-management-console)
    + [4.2 AWS Software Development Kits (SDKs)](#42-aws-software-development-kits--sdks-)
    + [4.3 The AWS Command Line Interface (CLI)](#43-the-aws-command-line-interface--cli-)
  * [5. Security and the AWS Shared Responsibility Model](#5-security-and-the-aws-shared-responsibility-model)
    + [5.1 What is AWS responsiable for?](#51-what-is-aws-responsiable-for-)
    + [5.2 What Is the Customer Responsible For?](#52-what-is-the-customer-responsible-for-)
  * [6. AWS Identity and Access Management (IAM)](#6-aws-identity-and-access-management--iam-)
    + [6.1 What Is an IAM User?](#61-what-is-an-iam-user-)
      - [6.1.1 IAM User Credentials](#611-iam-user-credentials)
      - [6.1.2 What Is an IAM Group?](#612-what-is-an-iam-group-)
    + [6.2 What Is an IAM Policy?](#62-what-is-an-iam-policy-)
  * [7. Role Based Access in AWS](#7-role-based-access-in-aws)
    + [7.1 Lock Down the AWS Root User](#71-lock-down-the-aws-root-user)
    + [7.2 Follow the Principle of Least Privilege](#72-follow-the-principle-of-least-privilege)
    + [7.3 Use IAM Appropriately](#73-use-iam-appropriately)
    + [7.4 Use IAM Roles When Possible](#74-use-iam-roles-when-possible)
    + [7.5 Consider Using an Identity Provider](#75-consider-using-an-identity-provider)
    + [7.6 Consider AWS SSO](#76-consider-aws-sso)
  * [8.  Networking on AWS](#8--networking-on-aws)
    + [8.1 What Are IP Addresses?](#81-what-are-ip-addresses-)
      - [8.1.1 What is IPV4 Notation?](#811-what-is-ipv4-notation-)
    + [8.2 Use CIDR Notation](#82-use-cidr-notation)
  * [9. VPC (Virtual private cloud)](#9-vpc--virtual-private-cloud-)
    + [9.1 Create subnet](#91-create-subnet)
    + [9.2 Gateways](#92-gateways)
    + [9.3 Amazon VPC Routing and Security](#93-amazon-vpc-routing-and-security)
# Cloud computing with AWS

## 1. What is cloud?
In the past, companies and organizations hosted and maintained hardware such as compute, storage, and networking equipment in their own data centers. They needed to allocate entire infrastructure departments to take care of them, resulting in a costly operation that made some workloads and experimentation impossible.

As internet usage became more widespread, the demand for compute, storage, and networking equipment increased. For some companies and organizations, the cost of maintaining a large physical presence was unsustainable. To solve this problem, cloud computing was created.

Cloud computing is the on-demand delivery of IT resources over the internet with pay-as-you-go pricing. You no longer have to manage and maintain your own hardware in your own data centers. Companies like AWS own and maintain these data centers and provide virtualized data center technologies and services to users over the internet.

### 1.1 The Six Benefits of Cloud Computing
**Pay as you go**. Instead of investing in data centers and hardware before you know how you are going to use them, you pay only when you use computing resources, and pay only for how much you use.

**Benefit from massive economies of scale**. By using cloud computing, you can achieve a lower cost than you can get on your own. Because usage from hundreds of thousands of customers is aggregated in the cloud, AWS can achieve higher economies of scale, which translates into lower pay as-you-go prices.
 
**Stop guessing capacity**. Eliminate guessing on your infrastructure capacity needs. When you make a capacity decision prior to deploying an application, you often end up either sitting on expensive idle resources or dealing with limited capacity. With cloud computing, these problems go away. You can access as much or as little capacity as you need, and scale up and down as required with only a few minutes notice.
 
**Increase speed and agility**. IT resources are only a click away, which means that you reduce the time to make those resources available to your developers from weeks to just minutes. This results in a dramatic increase in agility for the organization since the cost and time it takes to experiment and develop is significantly lower.
 
**Stop spending money running and maintaining data centers**. Focus on projects that differentiate your business, not the infrastructure. Cloud computing lets you focus on your customers, rather than on the heavy lifting of racking, stacking, and powering physical infrastructure. This is often referred to as undifferentiated heavy lifting.

**Go global in minutes**. Easily deploy your application in multiple Regions around the world with just a few clicks. This means you can provide lower latency and a better experience for your customers at a minimal cost.

## 2. AWS Global Infrastructure 
Regions are geographic locations worldwide where AWS hosts its data centers. AWS Regions are named after the location where they reside. For example, in the United States, there is a Region in Northern Virginia called the Northern Virginia Region and a Region in Oregon called the Oregon Region. There are Regions in Asia Pacific, Canada, Europe, the Middle East, and South America, and AWS continues to expand to meet the needs of its customers.

### 2.1 Here are a few examples of Region codes:

-   us-east-1: This is the first Region created in the east of the US. The geographical name for this Region is N. Virginia.
-   ap-northeast-1: The first Region created in the northeast of Asia Pacific. The geographical name for this Region is Tokyo.

AWS Regions are independent from one another. This means that your data is not replicated from one Region to another, without your explicit consent and authorization.

### 2.2 Choose the Right AWS Region

Consider four main aspects when deciding which AWS Region to host your applications and workloads: latency, price, service availability, and compliance.
 
**Latency.** If your application is sensitive to latency, choose a Region that is close to your user base. This helps prevent long wait times for your customers. Synchronous applications such as gaming, telephony, WebSockets, and IoT are significantly affected by higher latency, but even asynchronous workloads, such as ecommerce applications, can suffer from an impact on user connectivity.
 
**Price.** Due to the local economy and the physical nature of operating data centers, prices may vary from one Region to another. The pricing in a Region can be impacted by internet connectivity, prices of imported pieces of equipment, customs, real estate, and more. Instead of charging a flat rate worldwide, AWS charges based on the financial factors specific to the location.  
 
**Service availability.** Some services may not be available in some Regions. The AWS documentation provides a table containing the Regions and the available services within each one.
 
**Data compliance.** Enterprise companies often need to comply with regulations that require customer data to be stored in a specific geographic territory. If applicable, you should choose a Region that meets your compliance requirements.

## 3. Availability Zones
Inside every Region is a cluster of Availability Zones (AZ). An AZ consists of one or more data centers with redundant power, networking, and connectivity. These data centers operate in discrete facilities with undisclosed locations. They are connected using redundant high-speed and low-latency links.

AZs also have a code name. Since they’re located inside Regions, they can be addressed by appending a letter to the end of the Region code name. For example:

- us-east-1a: an AZ in us-east-1 (Northern Virginia Region)

- sa-east-1b: an AZ in sa-east-1 (São Paulo Region in South America)

If you see that a resource exists in us-east-1c, you know this resource is located in AZ c of the us-east-1 Region.

**3.1 Scope AWS Services**
Depending on the AWS Service you use, your resources are either deployed at the AZ, Region, or Global level. Each service is different, so you need to understand how the scope of a service may affect your application architecture. 

When you operate a Region-scoped service, you only need to select the Region you want to use. If you are not asked to specify an individual AZ to deploy the service in, this is an indicator that the service operates on a Region-scope level. For region-scoped services, AWS automatically performs actions to increase data durability and availability.

On the other hand, some services ask you to specify an AZ. With these services, you are often responsible for increasing the data durability and high availability of these resources.

![enter image description here](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/kTtu46zqSou7buOs6oqLew_b4777c328bdc4d1d8013e0560db9492a_GlobalINfra_4.jpeg?expiry=1636156800000&hmac=kWZRHloWXw-v9f_r8NiBHyWBklSP7NKui4nAU_SRPnk)


## 4. Interacting with AWS

Every action you make in AWS is an API call that is authenticated and authorized. In AWS, you can make API calls to services and resources through the AWS Management Console, the AWS Command Line Interface (CLI), or the AWS Software Development Kits (SDKs).

### 4.1 The AWS Management Console
One way to manage cloud resources is through the web-based console, where you log in and click on the desired service. This can be the easiest way to create and manage resources when you first begin working with the cloud. Below is a screenshot that shows the landing page when you first log into the AWS Management Console.

### 4.2 AWS Software Development Kits (SDKs)
API calls to AWS can also be performed by executing code with programming languages. You can do this by using AWS Software Development Kits (SDKs). SDKs are open-source and maintained by AWS for the most popular programming languages, such as C++, Go, Java, JavaScript, .NET, Node.js, PHP, Python, and Ruby.

### 4.3 The AWS Command Line Interface (CLI)
Consider the scenario where you run tens of servers on AWS for your application’s frontend. You want to run a report to collect data from all of these servers. You need to do this programmatically every day because the server details may change. Instead of manually logging into the AWS Management Console and copying/pasting information, you can schedule an AWS Command Line Interface (CLI) script with an API call to pull this data for you.

## 5. Security and the AWS Shared Responsibility Model
When you begin working with the AWS Cloud, managing security and compliance is a shared responsibility between AWS and you. To depict this shared responsibility, AWS created the shared responsibility model. This distinction of responsibility is commonly referred to as security of the cloud, versus security in the cloud.

### 5.1 What is AWS responsiable for?
AWS is responsible for security of the cloud. This means AWS is required to protect and secure the infrastructure that runs all the services offered in the AWS Cloud. AWS is responsible for:

-   Protecting and securing AWS Regions, Availability Zones, and data centers, down to the physical security of the buildings
    
-   Managing the hardware, software, and networking components that run AWS services, such as the physical server, host operating systems, virtualization layers, and AWS networking components

### 5.2 What Is the Customer Responsible For?
You’re responsible for security in the cloud. When using any AWS service, you’re responsible for properly configuring the service and your applications, as well as ensuring your data is secure. 

The level of responsibility you have depends on the AWS service. Some services require you to perform all the necessary security configuration and management tasks, while other more abstracted services require you to only manage the data and control access to your resources. Using the three categories of AWS services, you can determine your level of responsibility for each AWS service you use.

## 6. AWS Identity and Access Management (IAM)
IAM is a web service that enables you to manage access to your AWS account and resources. It also provides a centralized view of who and what are allowed inside your AWS account (authentication), and who and what have permissions to use and work with your AWS resources (authorization).
 
With IAM, you can share access to an AWS account and resources without having to share your set of access keys or password. You can also provide granular access to those working in your account, so that people and services only have permissions to the resources they need. For example, to provide a user of your AWS account with read-only access to a particular AWS service, you can granularly select which actions and which resources in that service they can access.

### 6.1 What Is an IAM User?

An IAM user represents a person or service that interacts with AWS. You define the user within your AWS account. And any activity done by that user is billed to your account. Once you create a user, that user can sign in to gain access to the AWS resources inside your account. 

You can also add more users to your account as needed. For example, for your cat photo application, you could create individual users in your AWS account that correspond to the people who are working on your application. Each person should have their own login credentials. Providing users with their own login credentials prevents sharing of credentials.

####  6.1.1 IAM User Credentials

An IAM user consists of a name and a set of credentials. When creating a user, you can choose to provide the user:
-   Access to the AWS Management Console
-   Programmatic access to the AWS Command Line Interface (AWS CLI) and AWS Application Programming Interface (AWS API)

#### 6.1.2 What Is an IAM Group?

An IAM group is a collection of users. All users in the group inherit the permissions assigned to the group. This makes it easy to give permissions to multiple users at once. It’s a more convenient and scalable way of managing permissions for users in your AWS account. This is why using IAM groups is a best practice.

If you have a an application that you’re trying to build and have multiple users in one account working on the application, you might decide to organize these users by job function. You might want IAM groups organized by developers, security, and admins. You would then place all of your IAM users in the respective group for their job function.

### 6.2 What Is an IAM Policy?

To manage access and provide permissions to AWS services and resources, you create IAM policies and attach them to IAM users, groups, and roles. Whenever a user or role makes a request, AWS evaluates the policies associated with them. For example, if you have a developer inside the developers group who makes a request to an AWS service, AWS evaluates any policies attached to the developers group and any policies attached to the developer user to determine if the request should be allowed or denied.

## 7. Role Based Access in AWS
**IAM best practices**. It’s helpful to have a brief summary of some of the most important IAM best practices you need to be familiar with before building out solutions on AWS.

### 7.1 Lock Down the AWS Root User
The root user is an all-powerful and all-knowing identity within your AWS account. If a malicious user were to gain control of root-user credentials, they would be able to access every resource within your account, including personal and billing information. To lock down the root user

-   Don’t share the credentials associated with the root user.
-   Consider deleting the root user access keys.
-   Enable MFA on the root account.

### 7.2 Follow the Principle of Least Privilege
Least privilege is a standard security principle that advises you to grant only the necessary permissions to do a particular job and nothing more. To implement least privilege for access control, start with the minimum set of permissions in an IAM policy and then grant additional permissions as necessary for a user, group, or role.

### 7.3 Use IAM Appropriately
IAM is used to secure access to your AWS account and resources. It simply provides a way to create and manage users, groups, and roles to access resources within a single AWS account. IAM is **not** used for website authentication and authorization, such as providing users of a website with sign-in and sign-up functionality. IAM also does **not** support security controls for protecting operating systems and networks.

### 7.4 Use IAM Roles When Possible
Maintaining roles is easier than maintaining users. When you assume a role, IAM dynamically provides temporary credentials that expire after a defined period of time, between 15 minutes and 36 hours. Users, on the other hand, have long-term credentials in the form of user name and password combinations or a set of access keys. 

User access keys only expire when you or the admin of your account rotates these keys. User login credentials expire if you have applied a password policy to your account that forces users to rotate their passwords.

### 7.5 Consider Using an Identity Provider
f you decide to make your cat photo application into a business and begin to have more than a handful of people working on it, consider managing employee identity information through an identity provider (IdP). Using an IdP, whether it be an AWS service such as AWS Single Sign-On (SSO) or a third-party identity provider, provides you a single source of truth for all identities in your organization.

You no longer have to create separate IAM users in AWS. You can instead use IAM roles to provide permissions to identities that are federated from your IdP.

### 7.6 Consider AWS SSO
If you have an organization that spans many employees and multiple AWS accounts, you may want your employees to sign in with a single credential. 

AWS SSO is an IdP that lets your users sign in to a user portal with a single set of credentials. It then provides them access to all their assigned accounts and applications in one central location.

AWS SSO is similar to IAM, in that it offers a directory where you can create users, organize them in groups, and set permissions across those groups, and grant access to AWS resources. However, AWS SSO has some advantages over IAM. For example, if you’re using a third-party IdP, you can sync your users and groups to AWS SSO.

This removes the burden of having to re-create users that already exist elsewhere, and it enables you to manage those users from your IdP. More importantly, AWS SSO separates the duties between your IdP and AWS, ensuring that your cloud access management is not inside or dependent on your IdP.

## 8.  Networking on AWS
Networking is how you connect computers around the world and allow them to communicate with one another. In this trail, you’ve already seen a few examples of networking. One is the AWS global infrastructure. AWS has created a network of resources using data centers, Availability Zones, and Regions.

### 8.1 What Are IP Addresses?
In order to properly route your messages to a location, you need an address. Just like each home has a mail address, each computer has an IP address. However, instead of using the combination of street, city, state, zip code, and country, the IP address uses a combination of bits, 0s and 1s.

Here is an example of a 32-bit address in binary format:
11000000 10101000 00000001 00011110

#### 8.1.1 What is IPV4 Notation?
Typically, you don’t see an IP address in this binary format. Instead, it’s converted into decimal format and noted as an Ipv4 address. 

the 32 bits are grouped into groups of 8 bits, also called octets. Each of these groups is converted into decimal format separated by a period.

11000000 10101000 00000001 00011110
192           . 168          . 1                . 30

In the end, this is what is called an Ipv4 address. This is important to know when trying to communicate to a single computer. But remember, you’re working with a network. This is where CIDR Notation comes in.


### 8.2 Use CIDR Notation
192.168.1.30 is a single IP address. If you wanted to express IP addresses between the range of 192.168.1.0 and 192.168.1.255, how can you do that?

One way is by using Classless Inter-Domain Routing (CIDR) notation. CIDR notation is a compressed way of specifying a range of IP addresses. Specifying a range determines how many IP addresses are available to you.  

CIDR notation looks like this: 192.168.1.0/24

32 total bits subtracted by 24 fixed bits leaves 8 flexible bits. Each of these flexible bits can be either 0 or 1, because they are binary. That means you have two choices for each of the 8 bits, providing 256 IP addresses in that IP range.

192.168.1 (Fixed) .0 (Flexiable)

The higher the number after the /, the smaller the number of IP addresses in your network. For example, a range of 192.168.1.0/24 is smaller than 192.168.1.0/16. 

When working with networks in the AWS Cloud, you choose your network size by using CIDR notation. In AWS, the smallest IP range you can have is /28, which provides you 16 IP addresses. The largest IP range you can have is a /16, which provides you with 65,536 IP addresses.

## 9. VPC (Virtual private cloud)

A VPC is an isolated network you create in the AWS cloud, similar to a traditional network in a data center. When you create a VPC, you need to choose three main things.

1.  The name of your VPC.
2.  A Region for your VPC to live in. Each VPC spans multiple Availability Zones within the Region you choose.
3.  A IP range for your VPC in CIDR notation. This determines the size of your network. Each VPC can have up to four /16 IP ranges.

### 9.1 Create subnet
After you create your VPC, you need to create subnets inside of this network. Think of subnets as smaller networks inside your base network—or virtual area networks (VLANs) in a traditional, on-premises network. In an on-premises network, the typical use case for subnets is to isolate or optimize network traffic. In AWS, subnets are used for high availability and providing different connectivity options for your resources.

The use of subnet is to provide diffrent access rules and provide a place to put an container
When you create a subnet, you need to choose three settings.
1.  The VPC you want your subnet to live in, in this case VPC (10.0.0.0/16).
2.  The Availability Zone you want your subnet to live in, in this case AZ1.
3.  A CIDR block for your subnet, which must be a subset of the VPC CIDR block, in this case 10.0.0.0/24.
    
When you launch an EC2 instance, you launch it inside a subnet, which will be located inside the Availability Zone you choose.

**Reserved IPs** For AWS to configure your VPC appropriately, AWS reserves five IP addresses in each subnet. These IP addresses are used for routing, Domain Name System (DNS), and network management. For example, consider a VPC with the IP range 10.0.0.0/22. The VPC includes 1,024 total IP addresses. This is divided into four equal-sized subnets, each with a /24 IP range with 256 IP addresses. Out of each of those IP ranges, there are only 251 IP addresses that can be used because AWS reserves five.

Since AWS reserves these five IP addresses, it can impact how you design your network. A common starting place for those who are new to the cloud is to create a VPC with a IP range of /16 and create subnets with a IP range of /24. This provides a large amount of IP addresses to work with at both the VPC and subnet level.

![enter image description here](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/2xyjkGLySbGco5Bi8lmxkw_ad3d1b2c0a774f0e94c9279fbb6a9a73_IntroVPC_3.jpeg?expiry=1636243200000&hmac=v93IgZ2TkZwBEra-iB6b19oZREQKjcnG60NKdteGYyY)

 ### 9.2 Gateways
 **Internet Gateway** To enable internet connectivity for your VPC, you need to create an internet gateway. Think of this gateway as similar to a modem. Just as a modem connects your computer to the internet, the internet gateway connects your VPC to the internet. Unlike your modem at home, which sometimes goes down or offline, an internet gateway is highly available and scalable. After you create an internet gateway, you then need to attach it to your VPC.

- Used for connecting internet to VPC

**Virtual Private Gateway** A virtual private gateway allows you to connect your AWS VPC to another private network. Once you create and attach a VGW to a VPC, the gateway acts as anchor on the AWS side of the connection. On the other side of the connection, you’ll need to connect a customer gateway to the other private network. A customer gateway device is a physical device or software application on your side of the connection. Once you have both gateways, you can then establish an encrypted VPN connection between the two sides.

- Used to connect on premice network to AWS VPC.

### 9.3 Amazon VPC Routing and Security
After creating IGW or VGW you need to specify route for access the particular resource otherwise by default the outside traffic will be not allowed for the internal resources to be used for that you need to create routes.

**The Main Route Table**
When you create a VPC, AWS creates a route table called the main route table. A route table contains a set of rules, called routes, that are used to determine where network traffic is directed. AWS assumes that when you create a new VPC with subnets, you want traffic to flow between them. Therefore, the default configuration of the main route table is to allow traffic between all subnets in the local network. Below is an example of a main route table:

There are two main parts to this route table.

- The destination, which is a range of IP addresses where you want your traffic to go. In the example of sending a letter, you need a destination to route the letter to the appropriate place. The same is true for routing traffic. In this case, the destination is the IP range of our VPC network.

- The target, which is the connection through which to send the traffic. In this case, the traffic is routed through the local VPC network.

**Custom route table**

While the main route table controls the routing for your VPC, you may want to be more granular about how you route your traffic for specific subnets. For example, your application may consist of a frontend and a database. You can create separate subnets for these resources and provide different routes for each of them. 

If you associate a custom route table with a subnet, the subnet will use it instead of the main route table. By default, each custom route table you create will have the local route already inside it, allowing communication to flow between all resources and subnets inside the VPC.

![enter image description here](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/69m1UQ52QS6ZtVEOdsEuvg_6d98f06359fd4ce9bd3233180011cf7d_Screen-Shot-2021-01-19-at-1.24.00-PM.png?expiry=1636243200000&hmac=SYNRUv9OiwWrAUUQpTCQyHR2ll6gSwGBFKZqoxbbmI4)

Any new VPC is isolated from the external traffic. Whenever we allow external traffic to our network, we need to create the traffic rules for internal security to keep the network secure.

There are two mechenicams to create security rules for the Instances.
1. **Network ACLs**
Think of a network ACL as a firewall at the subnet level. A network ACL enables you to control what kind of traffic is allowed to enter or leave your subnet. You can configure this by setting up rules that define what you want to filter. Here’s an example.
- Network ACL’s are considered stateless, so you need to include both the inbound and outbound ports used for the protocol. If you don’t include the outbound range, your server would respond but the traffic would never leave the subnet.

2.  **Security Groups**
The next layer of security is for your EC2 Instances. Here, you can create a firewall called a security group. The default configuration of a security group blocks all inbound traffic and allows all outbound traffic.
You might be wondering: “Wouldn’t this block all EC2 instances from receiving the response of any customer requests?” Well, security groups are stateful, meaning they will remember if a connection is originally initiated by the EC2 instance or from the outside and temporarily allow traffic to respond without having to modify the inbound rules.
If you want your EC2 instance to accept traffic from the internet, you’ll need to open up inbound ports. If you have a web server, you may need to accept HTTP and HTTPS requests to allow that type of traffic in through your security group. You can create an inbound rule that will allow port 80 (HTTP) and port 443 (HTTPS) .

You learned in a previous unit that subnets can be used to segregate traffic between computers in your network. Security groups can be used to do the same thing. A common design pattern is organizing your resources into different groups and creating security groups for each to control network communication between them.

![enter image description here](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/ZnKJspBYSOeyibKQWDjnYQ_6e94f0f1d04e4409a37ce7b5ada5c75b_SG2.jpeg?expiry=1636243200000&hmac=F-Pt67bQZt0rkRyfCwuG4tObWcs_mTyDnDgdsMP6QXM)

This example allows you to define three tiers and isolate each tier with the security group rules you define. In this case, you only allow internet traffic to the web tier over HTTPS, Web Tier to Application Tier over HTTP, and Application tier to Database tier over MySQL. This is different from traditional on-premises environments, in which you isolate groups of resources via VLAN configuration. In AWS, security groups allow you to achieve the same isolation without tying it to your network.
