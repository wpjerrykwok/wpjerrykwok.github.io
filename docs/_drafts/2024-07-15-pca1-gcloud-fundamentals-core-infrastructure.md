---
title: "Google Cloud Fundamentals: Core Infrastructure"
tags: [Study Notes, PCA, Google Cloud]
style: fill
color: success
description: Study notes for Google Cloud Certification - Professional Cloud Architect
asset_path: /assets/images/blog/2024-07-15/
---

In this post, I will share with you the notes from the course [Google Cloud Fundamentals: Core Infrastructure](https://www.cloudskillsboost.google/course_templates/60), in preparation for [Google Cloud Certification - Professional Cloud Architect](https://cloud.google.com/learn/certification/cloud-architect).

![Image created with Microsoft Designer]({{ page.asset_path }}my_image.jpeg)

## Introducing Google Cloud

### 1. Cloud computing overview

- Cloud computing is a method of utilizing information technology (IT) that involves five key characteristics:
  - On-demand self-service
    - Users can access computing resources like processing power, storage, and networking through a web interface without human intervention.
  - Internet access
    - Resources are accessible from anywhere with an internet connection.
  - Resource pooling
    - Cloud providers manage a large pool of resources and allocate them to users as needed, offering cost savings through bulk purchasing.
  - Elasticity
    - Resources can be quickly scaled up or down to meet changing demands.
  - Pay-per-use
    - Users pay only for the resources they consume.
- The cloud model has become increasingly attractive due to several factors.
  - Initially, colocation emerged as a way to rent physical space in data centers, reducing real estate costs.
  - Subsequently, virtualized data centers offered greater flexibility but still required user management.
  - Google pioneered a third wave of cloud computing using container-based architecture, which is fully automated and elastic.
- This model, now available to Google customers through Google Cloud, enables rapid innovation and scalability.
- The future of business will increasingly revolve around technology, particularly software, and high-quality data.
- This means that every company is or will become a data company.

### 2. IaaS and PaaS

- IaaS (Infrastructure as a Service)
  - Provides on-demand access to computing resources (compute, storage, network).
  - Similar to a physical data center but virtualized.
  - Example: Compute Engine
  - Customers pay for allocated resources.
- PaaS (Platform as a Service)
  - Offers a platform for developing, running, and managing applications.
  - Focuses on application logic, not infrastructure.
  - Example: App Engine
  - Customers pay for resource usage.
- Shift towards Managed Services
  - Increasing focus on managed infrastructure and services.
  - Allows businesses to concentrate on core competencies.
  - Enables faster and more reliable delivery of products/services.
- Serverless
  - Eliminates infrastructure management for developers.
  - Focus on code, not server configuration.
  - Examples: Cloud Functions, Cloud Run
  - Pay-per-use model.
- SaaS (Software as a Service)
  - Delivers complete cloud-based applications.
  - Accessed through a web browser.
  - Examples: Gmail, Docs, Drive
  - Not installed locally.

### 3. The Google Cloud Network

- Global Network
  - Largest of its kind, designed for high throughput and low latency.
  - Content caching nodes in 100+ locations for faster access.
- Geographic Locations
  - 5 major regions (North America, South America, Europe, Asia, Australia).
- Regions
  - Independent geographic areas, composed of zones.
- Zones
  - Areas where resources are deployed (e.g., Compute Engine VMs).
  - Can run resources in different regions for user proximity and redundancy.
- Multi-region Support
  - Replicates data across multiple regions for low-latency reads (e.g., Spanner).
- Total Zones
  - 121+ across 40+ regions (continually growing).

### 4. Environmental Impact

- Data centers consume significant energy (approx. 2% of global electricity).
- Google prioritizes energy efficiency in data centers.
- Aligns with customer environmental goals.
- First data centers to achieve ISO 14001 certification; a framework for an organization to enhance its environmental performance through improving resource efficiency and reducing waste.
- Innovative cooling methods (e.g., seawater in Hamina, Finland).
- Achieved carbon neutrality and 100% renewable energy milestones.
- Goal: Carbon-free operations by 2030.

### 5. Security

- Focus on security throughout infrastructure (design, hardware, software, operations).
- Layers of security:
  - Hardware infrastructure:
    - Custom-designed hardware & chips
    - Secure boot stack; such as cryptographic signatures over the BIOS, bootloader, kernel, and base operating system image
    - Physical security (own data centers, limited access)
  - Service deployment:
    - Encrypted communication between services (RPC: remote procedure call)
  - User identity:
    - Multi-factor authentication (password + additional checks, U2F)
  - Storage services:
    - Encryption at rest (centrally managed keys)
    - Hardware encryption support
  - Internet communication:
    - Encrypted connections (TLS, certificates)
    - Denial-of-service (DoS) protection (infrastructure scale & multi-layered)
  - Operational security:
    - Intrusion detection & Red Team exercises
    - Limited & monitored employee access
    - Employee U2F security keys
    - Stringent software development practices (code review, security libraries, vulnerability rewards program)

### 6. Open source ecosystems

- Some organizations fear vendor lock-in with cloud providers.
- Google offers options for customers to move workloads to other providers.
- Google uses open source licenses for technology (e.g., TensorFlow).
- Google provides interoperability between different cloud platforms.
- Kubernetes and Google Cloud Observability support multi-cloud environments.

### 7. Pricing and billing

- Per-second billing
  - Offered for Compute Engine, Kubernetes Engine, Dataproc, and App Engine flexible environment VMs.
- Sustained-use discounts
  - Automatic discounts for running VMs for a significant portion of the billing month (over 25%).
- Custom VM types
  - Fine-tune VMs with optimal CPU and memory for your workloads.
- Pricing calculator
  - Estimate costs at cloud.google.com/products/calculator.
- Cost Management
  - Budgets:
    - Define spending limits at billing account or project level.
  - Alerts:
    - Get notified when costs approach budget limits (e.g., 90% of a $20,000 budget).
  - Reports:
    - Monitor expenditure by project or service in the Google Cloud Console.
- Quotas
  - Designed to prevent resource over-consumption (errors or attacks).
  - Two types:
    - Rate quotas:
      - Reset after a specific time (e.g., GKE API calls).
    - Allocation quotas:
      - Govern resource limits per project (e.g., VPC networks).
  - Some quotas can be increased by contacting Google Cloud Support.

---

## Resources and Access in the Cloud

### 1. Google Cloud resource hierarchy

- Four levels:
  - Resources (VMs, buckets, tables, etc.)
  - Projects (organize resources, billing, collaboration)
  - Folders (organize projects, apply policies)
  - Organization node (top level, contains all resources)
- Policies:
  - Applied at project, folder, and organization levels (some services allow resource-level policies).
  - Inherited downward (folder policies apply to contained projects).
- Projects:
  - Separate entities within an organization.
  - Have unique ID (immutable), name, and number.
  - Managed through Resource Manager API.
- Folders:
  - Organize projects and other folders.
  - Enable policy inheritance and delegation.
- Organization node:
  - Top-level container for all resources.
  - Special roles (organization policy admin, project creator).
  - Created automatically with Google Workspace or through Cloud Identity.

### 2. Identity and Access Management (IAM)

- Purpose
  - Control who can access and what they can do with Google Cloud resources.
- Components
  - Principals:
    - Entities that can access resources (Google accounts, groups, service accounts, Cloud Identity domains).
  - Roles:
    - Collections of permissions defining actions a principal can perform.
  - Policies:
    - Define who (principal) can do what (role) on which resources.
- Policy Inheritance
  - Policies applied to higher levels in the resource hierarchy (folder, organization) inherit to lower levels (projects, resources).
- Deny Rules
  - Prevent specific principals from using certain permissions, overriding allow policies.
- Role Types:
  - Basic roles:
    - Broad permissions (owner, editor, viewer, billing administrator).
  - Predefined roles:
    - Specific permissions for certain services (e.g., Compute Engine instanceAdmin).
  - Custom roles:
    - Define exact permissions for specific needs (least privilege principle - each person is given the minimal amount of privilege needed to do their job).
- Custom Role Considerations:
  - Require permission management.
  - Can only be applied at project or organization level.

### 3. Service accounts

- Purpose
  - Grant permissions to virtual machines instead of individuals.
- Authentication
  - Uses cryptographic keys instead of passwords.
- Roles
  - Can be assigned IAM roles (e.g., Compute Engine Instance Admin) to control resource access.
- Management
  - Treated as resources themselves, with IAM policies for controlling access (e.g., editor, viewer roles).

### 4. Cloud Identity

- Problem
  - Using Gmail accounts for Google Cloud access leads to management difficulties (e.g., user leaving the organization).
- Solution
  - Cloud Identity provides centralized user and group management.
- Benefits
  - Integration with existing Active Directory or LDAP systems.
  - Easier user management (adding, removing, modifying permissions).
  - Improved security through centralized control.
- Availability
  - Free and premium editions.
- Integration
  - Included in Google Workspace.

### 5. Interacting with Google Cloud

- Google Cloud Console
  - Web-based GUI for managing resources, budgets, and searching/connecting to instances.
- Cloud SDK & Cloud Shell
  - Cloud SDK:
    - Set of tools including gcloud CLI (main command-line interface) and bq (BigQuery CLI).
  - Cloud Shell:
    - Browser-based Debian VM with persistent storage for managing projects and resources (gcloud pre-installed).
- APIs & Client Libraries
  - APIs:
    - programmatic control of Google Cloud services.
  - Cloud Client Libraries & Google API Client Libraries:
    - pre-built libraries in various languages (Java, Python, PHP, etc.) to simplify interacting with APIs.
- Google Cloud App
  - Mobile app for managing Compute Engine instances, Cloud SQL, App Engine deployments, billing, and monitoring.

### 6. Google Cloud Fundamentals: Getting Started with Cloud Marketplace

#### Overview

In this lab, you use Google Cloud Marketplace to quickly and easily deploy a LAMP stack on a Compute Engine instance.

The Bitnami LAMP Stack provides a complete web development environment for Linux that can be launched in one click.

Component|Role
---|---
Linux|Operating system
Apache HTTP Server|Web server
MySQL|Relational database
PHP|Web application framework
phpMyAdmin|PHP administration tool

You can learn more about the Bitnami LAMP stack from the Bitnami Documentation article Google Cloud Platform.

#### Objectives

In this lab, you learn how to launch a solution using Cloud Marketplace.

#### Task 1. Sign in to the Google Cloud Console

Sign in to Qwiklabs using an **incognito window** with lab credentials (**Username** and **Password**).

#### Task 2. Use Cloud Marketplace to deploy a LAMP stack

In the Google Cloud Console, on the **Navigation menu**, click **Marketplace**.

In the search bar, type `LAMP` and then press **ENTER**.

In the search results, click **Bitnami package for LAMP**.

On the LAMP page, click **GET STARTED**.

On the Agreements page, check the box for **Terms and agreements**, and click **AGREE**.

On the **Successfully agreed to terms** pop up, click **DEPLOY**.

> If this is your first time using Compute Engine, the **Compute Engine API** must be initialized before you can continue.

For **Zone**, select the deployment zone to `ZONE` .

For **Machine Type**, select **E2** as the **Series** and **e2-medium** as the **Machine Type**.

Leave the remaining settings as their defaults.

Click **Deploy**.

If a **Welcome to Deployment Manager** message appears, click **Close** to dismiss it.

The status of the deployment appears in the console window: **lampstack-1 is being deployed**. When the deployment of the infrastructure is complete, the status changes to **lampstack-1 has been deployed**.

After the software is installed, a summary of the details for the instance, including the site address, is displayed.

#### Task 3. Verify your deployment

When the deployment is complete, click the **Site address** link in the right pane. (If the website is not responding, wait 30 seconds and try again.) If you see a redirection notice, click on that link to view your new site.

Alternatively, you can click **Visit the site** in the **Get started with Bitnami package for LAMP** section of the page. A new browser tab displays a congratulations message. This page confirms that, as part of the LAMP stack, the Apache HTTP Server is running.

#### Congratulations

In this lab, you deployed a LAMP stack to a Compute Engine instance.

---

## Virtual Machines and Networks in the Cloud

### 1. Virtual Private Cloud Networking

- VPC (Virtual Private Cloud)
  - Isolated private cloud environment within Google Cloud.
- VPC Networks
  - Connect resources within a VPC and to the internet.
- Subnets
  - Segmented portions of a VPC network, can span multiple regions.
- Global VPC Networks
  - Can have subnets in different regions.
- Subnet Expansion
  - Increase subnet size without affecting existing VMs.
- Example
  - VMs in different regions can communicate as if on the same network.

### 2. Compute Engine

- IaaS offering
  - Allows creation and running of virtual machines on Google infrastructure.
- No upfront costs
  - Pay-as-you-go model.
- Customizable VMs
  - Define CPU, memory, storage, and operating system.
- Creation methods
  - Google Cloud Console, Cloud CLI, Compute Engine API.
- Operating systems
  - Linux, Windows Server, custom images.
- Cloud Marketplace
  - Pre-configured solutions for faster deployment.
- Pricing and billing
  - Per-second billing with one-minute minimum.
  - Sustained-use discounts for longer running VMs.
  - Committed-use discounts for predictable workloads.
  - Preemptible and Spot VMs for cost savings (potential interruptions).
- Storage
  - High throughput between processing and persistent disks included.
- Custom machine types
  - Choose specific CPU and memory configurations.

### 3. Scaling virtual machines

- Predefined vs. Custom
  - Choose from pre-defined machine types or create custom configurations.
- Scaling
  - Autoscaling:
    - Add/remove VMs based on load metrics.
  - Load Balancing:
    - Distribute traffic across VMs using Google VPC.
- Scaling Out vs. Up
  - Most users start with horizontal scaling (more VMs) rather than vertical scaling (bigger VMs).
- Limits
  - Maximum CPUs per VM depends on machine family and user quota (zone-specific).

### 4. Important VPC compatibilities

- Built-in Routing
  - Automatically manages traffic forwarding between instances and subnets without external router.
- Global Distributed Firewall
  - Controls incoming and outgoing traffic through firewall rules.
- Network Tags
  - Simplify firewall rule management by applying rules based on instance tags.
- VPC Peering
  - Connect VPCs in different projects for traffic exchange.
- Shared VPC
  - Share VPC across multiple projects with granular access control using IAM.

### 5. Cloud Load Balancing

- Distributes traffic across multiple instances of an application.
- Improves performance by reducing load on individual instances.
- Fully managed service
  - No need to scale or manage load balancers.
- Supports various traffic types
  - HTTP(S), TCP, SSL, UDP.
- Global and regional options
  - Global HTTP(S) load balancer:
    - Cross-region load balancing with automatic failover.
  - Global SSL Proxy load balancer, Global TCP Proxy load balancer:
    - For SSL and TCP traffic (specific ports).
  - Regional External Passthrough Network load balancer:
    - For UDP and any port traffic.
  - Regional External Application load balancer, Proxy Network load balancer:
    - Additional options for external traffic.
  - Regional Internal load balancer:
    - For internal traffic within a project (Proxy Network, Passthrough Network, Application load balancer).
  - Google Cloud Cross-region Internal load balancer:
    - Layer 7 load balancer for globally distributed traffic.
- No pre-warming required
  - Automatically handles traffic spikes.

### 6. Cloud DNS and Cloud CDN

- Public DNS Service
  - 8.8.8.8 is a free public DNS service provided by Google.
- Cloud DNS
  - Managed DNS service for Google Cloud applications.
  - High availability, low latency, cost-effective.
  - Global distribution of DNS information.
  - Programmable via console, CLI, or API.
- Cloud CDN
  - Content Delivery Network for accelerating content delivery. Edge caching refers to the use of caching servers to store content closer to end users.
  - Reduces latency, load on origins, and costs.
  - Easily enabled with HTTP(S) Load Balancing.
  - Integrates with other CDNs through partner program.

### 7. Connecting networks to Google VPC

- Cloud VPN
  - Creates a secure tunnel over the internet using Cloud Router for dynamic routing.
  - Exchange route information over the VPN using the Border Gateway Protocol
  - security concerns or bandwidth reliability
- Direct Peering
  - Establishes a direct connection between your network and Google's network in a public data center as a Google point of presence.
  - isn’t covered by a Google Service Level Agreement
- Carrier Peering
  - Connects to Google through a service provider's network.
  - isn’t covered by a Google Service Level Agreement
- Dedicated Interconnect
  - Provides a direct, private connection to Google with higher SLAs.
  - covered by an SLA of up to 99.99%
  - can be backed up by a VPN
- Partner Interconnect
  - Connects through a supported service provider for less demanding workloads.
- Cross-Cloud Interconnect
  - Connects to other cloud providers with high bandwidth and dedicated connectivity.
  - a dedicated physical connection
  - an integrated multicloud strategy

### 8. Getting Started with VPC Networking and Google Compute Engine

#### Overview

Google Cloud Virtual Private Cloud (VPC) provides networking functionality to Compute Engine virtual machine (VM) instances, Kubernetes Engine containers, and App Engine flexible environment.

In other words, without a VPC network you cannot create VM instances, containers, or App Engine applications.

Therefore, each Google Cloud project has a **default** network to get you started.

You can think of a VPC network as similar to a physical network, except that it is virtualized within Google Cloud.

A VPC network is a global resource that consists of a list of regional virtual subnetworks (subnets) in data centers, all connected by a global wide area network (WAN).

VPC networks are logically isolated from each other in Google Cloud.

In this lab, you create an auto mode VPC network with firewall rules and two VM instances. Then, you explore the connectivity for the VM instances.

##### Objectives

In this lab, you learn how to perform the following tasks:

- Explore the default VPC network
- Create an auto mode network with firewall rules
- Create VM instances using Compute Engine
- Explore the connectivity for VM instances

#### Task 1. Explore the default network

Each Google Cloud project has a **default** network with subnets, routes, and firewall rules.

##### View the subnets

The **default** network has a subnet in each Google Cloud region.

In the Cloud Console, on the **Navigation menu**, click **VPC network** > **VPC networks**.

Click **default**.

Click **Subnets**.

Notice the **default** network with its subnets.

Each subnet is associated with a Google Cloud region and a private RFC 1918 CIDR block for its internal **IP addresses range** and a **gateway**.

##### View the routes

Routes tell VM instances and the VPC network how to send traffic from an instance to a destination, either inside the network or outside Google Cloud.

Each VPC network comes with some default routes to route traffic among its subnets and send traffic from eligible instances to the internet.

In the left pane, click **Routes**.

In **Effective Routes** click **Network**, and then select **default**.

Click **Region** and select the Lab Region assigned to you by Qwiklabs.

Click **View**.

Notice that there is a route for each subnet.

These routes are managed for you, but you can create custom static routes to direct some packets to specific destinations.

For example, you can create a route that sends all outbound traffic to an instance configured as a NAT gateway.

##### View the Firewall rules

Each VPC network implements a distributed virtual firewall that you can configure.

Firewall rules allow you to control which packets are allowed to travel to which destinations.

Every VPC network has two implied firewall rules that block all incoming connections and allow all outgoing connections.

In the left pane, click **Firewall**.

Notice that there are 4 **Ingress** firewall rules for the **default** network:

- default-allow-icmp
- default-allow-rdp
- default-allow-ssh
- default-allow-internal

> Note: These firewall rules allow **ICMP**, **RDP**, and **SSH** ingress traffic from anywhere (0.0.0.0/0) and all **TCP**, **UDP**, and **ICMP** traffic within the network (10.128.0.0/9).
> The **Targets**, **Filters**, **Protocols/ports**, and **Action** columns explain these rules.

##### Delete the Firewall rules

Select all of the default network firewall rules.

Click **Delete**.

Click **Delete** to confirm the deletion of the firewall rules.

##### Delete the default network

In the Cloud Console, on the **Navigation menu**, click **VPC network** > **VPC networks**.

Select the **default** network.

Click **Delete VPC network**.

Click **Delete** to confirm the deletion of the **default** network. Wait for the network to be deleted before continuing.

In the left pane, click **Routes**. Notice that there are no routes.

In the left pane, click **Firewall**. Notice that there are no firewall rules.

> Note: Without a VPC network, there are no routes and no firewall rules!

##### Try to create a VM instance

Verify that you cannot create a VM instance without a VPC network.

On the **Navigation menu**, click **Compute Engine** > **VM instances**.

Click **Create instance**.

Accept the default values and click **Create**. Notice the error.

Click **Go to Issues**.

In **Network Interfaces**, notice the no more networks and no network available errors.

Click **Cancel**.

> Note: As expected, you cannot create a VM instance without a VPC network!

#### Task 2. Create a VPC network and VM instances

Create a VPC network so that you can create VM instances.

##### Create an auto mode VPC network with Firewall rules

Replicate the **default** network by creating an auto mode network.

On the **Navigation menu**, click **VPC network** > **VPC networks**.

Click **Create VPC network**.

For **Name**, type **mynetwork**.

For **Subnet creation mode**, click **Automatic**. Auto mode networks create subnets in each region automatically.

For **Firewall**, select all available rules.

> These are the same standard firewall rules that the default network had. The **deny-all-ingress** and **allow-all-egress** rules are also displayed, but you cannot check or uncheck them because they are *implied*. These two rules have a lower **Priority** (higher integers indicate lower priorities) so that the allow ICMP, custom, RDP and SSH rules are considered first.

Click **Create**.

> When the new network is ready, notice that a subnet was created for each region.

Explore the IP address range for the subnets in Region 1 and Region 2.

> Note: If you ever delete the default network, you can quickly re-create it by creating an auto mode network as you just did. After recreating the network, allow-internal changes to allow-custom firewall rule.

##### Create a VM instance in Region

Create a VM instance in the Region region.

Selecting a region and zone determines the subnet and assigns the internal IP address from the subnet's IP address range.

On the **Navigation menu**, click **Compute Engine** > **VM instances**.

Click **Create instance**.

Specify the following, and leave the remaining settings as their defaults:

Property | Value
--- | ---
Name | mynet-us-vm
Region | Region 1
Zone | Zone 1
Series | E2
Machine type | e2-micro (2 vCPU, 1 GB memory)

Click **Create**.

##### Create a VM instance in Region 2

Create a VM instance in the Region 2 region.

Click **Create instance**.

Specify the following, and leave the remaining settings as their defaults:

Property | Value (type value or select option as specified)
--- | ---
Name | mynet-eu-vm
Region | Region 2
Zone | Zone 2
Series | E2
Machine type | e2-micro (2 vCPU, 1 GB memory)

Click **Create**.

> Note: The **External IP addresses** for both VM instances are ephemeral. If an instance is stopped, any ephemeral external IP addresses assigned to the instance are released back into the general Compute Engine pool and become available for use by other projects.
> When a stopped instance is started again, a new ephemeral external IP address is assigned to the instance. Alternatively, you can reserve a static external IP address, which assigns the address to your project indefinitely until you explicitly release it.

#### Task 3. Explore the connectivity for VM instances

Explore the connectivity for the VM instances.

Specifically, try to SSH to your VM instances using tcp:22, and ping both the internal and external IP addresses of your VM instances using ICMP.

Then explore the effects of the firewall rules on connectivity by removing the firewall rules individually.

#### Verify connectivity for the VM instances

The firewall rules that you created with **mynetwork** allow ingress SSH and ICMP traffic from within **mynetwork** (internal IP) and outside that network (external IP).

On the **Navigation menu**, click **Compute Engine** > **VM instances**. Note the external and internal IP addresses for **mynet-eu-vm**.

For **mynet-us-vm**, click **SSH** to launch a terminal and connect.

If an **Authorize** popup appears, click on **Authorize**

> Note: You can SSH because of the **allow-ssh** firewall rule, which allows incoming traffic from anywhere (0.0.0.0/0) for **tcp:22**.
>
> The SSH connection works seamlessly because Compute Engine generates an SSH key for you and stores it in one of the following locations:
>
> - By default, Compute Engine adds the generated key to project or instance metadata.
> - If your account is configured to use OS Login, Compute Engine stores the generated key with your user account.
>
> Alternatively, you can control access to Linux instances by creating SSH keys and editing public SSH key metadata.

To test connectivity to **mynet-eu-vm**'s internal IP, run the following command, replacing **mynet-eu-vm**'s internal IP:

```bash
ping -c 3 <Enter mynet-eu-vm's internal IP here>
```

You can ping **mynet-eu-vm**'s internal IP because of the **allow-custom** firewall rule.

To test connectivity to mynet-eu-vm's external IP, run the following command, replacing mynet-eu-vm's external IP:

```bash
ping -c 3 <Enter mynet-eu-vm's external IP here>
```

> Note: You can SSH to **mynet-us-vm** and ping **mynet-eu-vm**'s internal and external IP address as expected. Alternatively, you can SSH to **mynet-eu-vm** and ping **mynet-us-vm**'s internal and external IP address, which also works.

##### Remove the allow-icmp firewall rules

Remove the **allow-icmp** firewall rule and try to ping the internal and external IP address of **mynet-eu-vm**.

On the **Navigation menu**, click **VPC network** > **Firewall**.

Select the **mynetwork-allow-icmp** rule.

Click **Delete**.

Click **Delete** to confirm the deletion. Wait for the firewall rule to be deleted.

Return to the **mynet-us-vm** SSH terminal.

To test connectivity to **mynet-eu-vm**'s internal IP, run the following command, replacing **mynet-eu-vm**'s internal IP:

```bash
ping -c 3 <Enter mynet-eu-vm's internal IP here>
```

You can ping **mynet-eu-vm**'s internal IP because of the **allow-custom** firewall rule.

To test connectivity to **mynet-eu-vm**'s external IP, run the following command, replacing **mynet-eu-vm**'s external IP:

```bash
ping -c 3 <Enter mynet-eu-vm's external IP here>
```

> Note: The **100% packet loss** indicates that you cannot ping **mynet-eu-vm**'s external IP. This is expected because you deleted the **allow-icmp** firewall rule!

##### Remove the allow-custom firewall rules

Remove the **allow-custom** firewall rule and try to ping the internal IP address of **mynet-eu-vm**.

On the **Navigation menu**, click **VPC network** > **Firewall**.

Select the **mynetwork-allow-custom** rule.

Click **Delete**.

Click **Delete** to confirm the deletion. Wait for the firewall rule to be deleted.

Return to the **mynet-us-vm** SSH terminal.

To test connectivity to **mynet-eu-vm**'s internal IP, run the following command, replacing **mynet-eu-vm**'s internal IP:

```bash
ping -c 3 <Enter mynet-eu-vm's internal IP here>
```

> Note: The **100% packet loss** indicates that you cannot ping **mynet-eu-vm**'s internal IP. This is expected because you deleted the **allow-custom** firewall rule!

Close the SSH terminal:

```bash
exit
```

##### Remove the allow-ssh firewall rules

Remove the **allow-ssh** firewall rule and try to SSH to **mynet-us-vm**.

On the **Navigation menu**, click **VPC network** > **Firewall**.

Select the **mynetwork-allow-ssh** rule.

Click **Delete**.

Click **Delete** to confirm the deletion.

Wait for the firewall rule to be deleted.

On the **Navigation menu**, click **Compute Engine** > **VM instances**.

For **mynet-us-vm**, click **SSH** to launch a terminal and connect.

> Note: The **Connection failed** message indicates that you cannot SSH to **mynet-us-vm** because you deleted the **allow-ssh** firewall rule!

#### Task 4. Review

In this lab, you explored the default network along with its subnets, routes, and firewall rules.

You deleted the default network and determined that you cannot create any VM instances without a VPC network.

Thus, you created a new auto mode VPC network with subnets, routes, firewall rules, and two VM instances.

Then you tested the connectivity for the VM instances and explored the effects of the firewall rules on connectivity.

---

## Storage in the Cloud

### 1. Google Cloud storage options

- Diverse storage needs
  - Different applications require different storage solutions.
- Google Cloud storage options
  - Cloud Storage, Cloud SQL, Spanner, Firestore, Bigtable.
- Tailored solutions
  - Choose the right storage service based on data type and workload requirements.

### 2. Cloud Storage

- Object storage
  - Stores data as objects with metadata (such as date created, author, resource type, and permissions), not files or blocks and a globally unique identifier.
  - interacts well with web technologies
  - common objects include video, pictures, and audio recordings
- Cloud Storage
  - Google's object storage service.
- Key features
  - Durable and highly available.
  - Scalable to store any amount of data.
  - Versatile use cases (website content, backups, data distribution).
  - whenever binary large-object storage (also known as a “BLOB”) is needed
- Organization
  - Data stored in buckets with unique names and locations.
- Object immutability
  - New versions created for changes, not overwritten.
- Versioning
  - Track object changes over time.
- Access control
  - IAM roles and access control lists (ACLs) : scope + permission, for granular permissions.
- Lifecycle management
  - Manage object storage costs through automatic policies (deletion, retention).

### 3. Cloud Storage: Storage classes and data transfer

- Storage Classes
  - Standard:
    - For frequently accessed data. hot data.
  - Nearline:
    - For infrequently accessed data (accessed once a month or less). data backups
  - Coldline:
    - For even less frequently accessed data (accessed once every 90 days or less).
  - Archive:
    - For data accessed less than once a year. lowest-cost option, ideal for data archiving
- Common Characteristics
  - Unlimited storage with no minimum object size.
  - Worldwide accessibility and low latency.
  - High durability with geo-redundancy.
  - Uniform experience across storage classes.
  - Encrypted data at rest and in transit.
  - Autoclass for automatic storage tier optimization.
  - Pay-per-use pricing with no upfront costs.
- Data Ingestion
  - online transfer using gcloud storage command-line tool from the Cloud SDK.
  - Cloud Console drag-and-drop (Chrome).
  - Storage Transfer Service for large-scale data transfers. batch transfers to Cloud Storage from another cloud provider
  - Transfer Appliance for massive data transfers. a rackable, high-capacity storage server that you lease from Google Cloud
  - Integration with other Google Cloud services (BigQuery, Cloud SQL, App Engine, Compute Engine).
- Cloud Storage can also store instance startup scripts, Compute Engine images, and objects used by Compute Engine applications.

### 4. Cloud SQL

- Fully managed relational database service.
- Supports MySQL, PostgreSQL, and SQL Server.
- Handles database management tasks (patches, backups, replication).
- Scalable in terms of CPU, RAM, and storage.
- Supports automatic replication and managed backups.
- Encrypts data at rest and in transit.
- Includes network firewall for security.
- Integrates with other Google Cloud services (App Engine, Compute Engine).
- Compatible with standard SQL tools and drivers.

### 5. Spanner

- Fully managed, horizontally scalable relational database.
- Strong consistency and high availability.
- Powers Google's mission-critical applications.
- Ideal for high-performance, globally distributed applications.
- Supports SQL queries, joins, and secondary indexes.
- Handles tens of thousands of reads and writes per second.

### 6. Firestore

- NoSQL document database for mobile, web, and server development.
- Data stored in documents within collections.
- Supports nested data structures and key-value pairs.
- Flexible querying with filtering, sorting, and indexing.
- Real-time data synchronization across devices.
- Offline support for continued app functionality.
- Built on Google Cloud infrastructure for scalability and reliability.
- Automatic multi-region data replication and strong consistency.

### 7. Bigtable

- NoSQL big data database service.
- Powers Google's core services (Search, Analytics, Maps, Gmail).
- Handles massive workloads with low latency and high throughput.
- Ideal for operational and analytical applications including Internet of Things, user analytics, and financial data analysis
- Suitable for large datasets with high write and read rates. more than 1TB of semi-structured or structured data
- Supports NoSQL data with time-series or semantic ordering.
- Integrates with other Google Cloud services and third-party clients.
- Supports streaming and batch data processing.

### 8. Comparing storage options

- Cloud Storage
  - Best for:
    - Storing large immutable objects (images, videos).
  - Capacity:
    - Petabytes, max object size 5 TB.
- Cloud SQL
  - Best for:
    - Online transaction processing with SQL support.
  - Capacity:
    - Up to 64 TB (depends on machine type).
  - Ideal for:
    - Web frameworks, existing applications.
- Cloud Spanner
  - Best for:
    - Horizontally scalable, strongly consistent, high-performance relational database.
  - Capacity:
    - Petabytes.
  - Ideal for:
    - Large-scale transactional applications.
- Cloud Firestore
  - Best for:
    - Mobile and web applications requiring real-time data and offline support.
  - Capacity:
    - Terabytes, max document size 1 MB.
- Cloud Bigtable
  - Best for:
    - Large-scale, high-performance NoSQL workloads.
  - Capacity:
    - Petabytes, max cell size 10 MB, max row size 100 MB.
  - Ideal for:
    - Big data analytics, IoT, financial data.
- BigQuery
  - Data warehouse and analytics platform.
  - Not a primary storage option.
  - Used for data analysis and querying.

### 9. Google Cloud Fundamentals: Getting Started with Cloud Storage and Cloud SQL

#### Overview

In this lab, you create a Cloud Storage bucket and place an image in it.

You also configure an application running in Compute Engine to use a database managed by Cloud SQL.

For this lab, you configure a web server with PHP, a web development environment that is the basis for popular blogging software.

Outside this lab, you will use analogous techniques to configure these packages.

You also configure the web server to reference the image in the Cloud Storage bucket.

#### Objectives

In this lab, you learn how to perform the following tasks:

- Create a Cloud Storage bucket and place an image into it.
- Create a Cloud SQL instance and configure it.
- Connect to the Cloud SQL instance from a web server.
- Use the image in the Cloud Storage bucket on a web page.

#### Task 1. Sign in to the Google Cloud Console

#### Task 2. Deploy a web server VM instance

In the Google Cloud console, on the **Navigation menu**, click **Compute Engine** > **VM instances**.

Click **Create Instance**.

On the **Create an Instance** page, for **Name**, type `bloghost`

For **Region** and **Zone**, select the region and zone assigned by Qwiklabs.

For **Machine type**, accept the default.

For **Boot disk**, use **Image** as **Debian GNU/Linux 11 (bullseye)**.

Leave the defaults for **Identity and API access** unmodified.

For **Firewall**, click **Allow HTTP traffic**.

Click **Advanced options** to open that section of the dialog.

Click **Management** to open that section of the dialog.

Scroll down to the Automation section, and enter the following script as the value for **Startup script**:

```bash
apt-get update
apt-get install apache2 php php-mysql -y
service apache2 restart
```

> Note: Be sure to supply that script as the value of the **Startup script** field. 
> If you accidentally put it into another field, it won't be executed when the VM instance starts.

Leave the remaining settings as their defaults, and click **Create**.

> Note: Instance can take about two minutes to launch and be fully available for use.

On the **VM instances** page, copy the **bloghost** VM instance's internal and external IP addresses to a text editor for use later in this lab.

#### Task 3. Create a Cloud Storage bucket using the gcloud storage command line

All Cloud Storage bucket names must be globally unique.

To ensure that your bucket name is unique, these instructions will guide you to give your bucket the same name as your Google Cloud project ID, which is also globally unique.

Cloud Storage buckets can be associated with either a region or a multi-region location: **US**, **EU**, or **ASIA**.

In this activity, you associate your bucket with the multi-region closest to the region and zone that Qwiklabs or your instructor assigned you to.

On the Google Cloud console, on the top right toolbar, click the **Activate Cloud Shell**. If a dialog box appears, click **Continue**.

For convenience, enter your chosen location into an environment variable called `LOCATION`. Enter one of these commands:

```bash
export LOCATION=US
```

Or

```bash
export LOCATION=EU
```

Or

```bash
export LOCATION=ASIA
```

In Cloud Shell, the `DEVSHELL_PROJECT_ID` environment variable contains your project ID. Enter this command to make a bucket named after your project ID:

```bash
gcloud storage buckets create -l $LOCATION gs://$DEVSHELL_PROJECT_ID
```

If prompted, click **Authorize** to continue.

Retrieve a banner image from a publicly accessible Cloud Storage location:

```bash
gcloud storage cp gs://cloud-training/gcpfci/my-excellent-blog.png my-excellent-blog.png
```

Copy the banner image to your newly created Cloud Storage bucket:

```bash
gcloud storage cp my-excellent-blog.png gs://$DEVSHELL_PROJECT_ID/my-excellent-blog.png
```

Modify the Access Control List of the object you just created so that it's readable by everyone:

```bash
gsutil acl ch -u allUsers:R gs://$DEVSHELL_PROJECT_ID/my-excellent-blog.png
```

#### Task 4. Create the Cloud SQL instance

In the Google Cloud console, on the **Navigation menu**, click **SQL**.

Click **Create instance**.

For **Choose a database engine**, select **Choose MySQL**.

For **Instance ID**, type `blog-db`, and for **Root password** type a password of your choice.

> Note: Choose a password that you remember. There's no need to obscure the password because you use mechanisms to connect that aren't open access to everyone.

For **Choose a Cloud SQL edition**, click **Enterprise** and then select **Sandbox** from the dropdown.

Select **Single zone** and set the region and zone assigned by Qwiklabs.

> Note: This is the same region and zone into which you launched the **bloghost** instance. The best performance is achieved by placing the client and the database close to each other.

Click **Create Instance**.

> Note: Wait for the instance to finish deploying. It will take a few minutes.

Click the name of the instance, **blog-db**, to open its details page.

From the SQL instances details page, copy the **Public IP address** for your SQL instance to a text editor for use later in this lab.

Click **Users** menu on the left-hand side, and then click **Add User Account**.

For **User name**, type `blogdbuser`

For **Password**, type a password of your choice. Make a note of it.

Click **Add** to add the user account in the database.

> Note: Wait for the user to be created.

Click **Connections** menu on the left-hand side, and then click **Networking** tab.

Click **Add a Network**.

> Note: If you're offered the choice between a **Private IP** connection and a **Public IP** connection, choose **Public IP** for purposes of this lab.
> Note: The **Add network** button may be unavailable if the user account creation is not yet complete.

For **Name**, type `web front end`

For **Network**, type the external IP address of your **bloghost** VM instance, followed by `/32`

 The result will look like this:

`35.192.208.2/32`

> Note: Be sure to use the external IP address of your VM instance followed by /32. Do not use the VM instance's internal IP address. Do not use the sample IP address shown here.

Click **Done** to finish defining the authorized network.

Click **Save** to save the configuration change.

> Note: If the message appears like **Another operation is in progress**, wait for few minutes until you see the green check for **blog-db** to save the configuration.

#### Task 5. Configure an application in a Compute Engine instance to use Cloud SQL

On the **Navigation menu**, click **Compute Engine** > **VM instances**.

In the VM instances list, click **SSH** in the row for your VM instance **bloghost**.

In your ssh session on **bloghost**, change your working directory to the document root of the web server:

```bash
cd /var/www/html
```

Use the **nano** text editor to edit a file called `index.php`:

```bash
sudo nano index.php
```

Paste the content below into the file:

```html
<html>
<head><title>Welcome to my excellent blog</title></head>
<body>
<h1>Welcome to my excellent blog</h1>
<?php
$dbserver = "CLOUDSQLIP";
$dbuser = "blogdbuser";
$dbpassword = "DBPASSWORD";
// In a production blog, we would not store the MySQL
// password in the document root. Instead, we would store
//  it in a Secret Manger. For more information see 
// https://cloud.google.com/sql/docs/postgres/use-secret-manager

$conn = new mysqli($dbserver, $dbuser, $dbpassword);

if (mysqli_connect_error()) {
        echo ("Database connection failed: " . mysqli_connect_error());
} else {
        echo ("Database connection succeeded.");
}
?>
</body></html>
```

> Note: In a later step, you will insert your Cloud SQL instance's IP address and your database password into this file. For now, leave the file unmodified.

Press **Ctrl+O**, and then press **Enter** to save your edited file.

Press **Ctrl+X** to exit the nano text editor.

Restart the web server:

```bash
sudo service apache2 restart
```

Open a new web browser tab and paste into the address bar your **bloghost** VM instance's external IP address followed by **/index.php**. The URL will look like this:

`35.192.208.2/index.php`

> Note: Be sure to use the external IP address of your VM instance followed by /index.php. Do not use the VM instance's internal IP address. Do not use the sample IP address shown here.

When you load the page, you will see that its content includes an error message beginning with the words:

`Database connection failed: ...`

> Note: This message occurs because you have not yet configured PHP's connection to your Cloud SQL instance.

Return to your ssh session on **bloghost**. Use the nano text editor to edit `index.php` again.

```bash
sudo nano index.php
```

In the **nano** text editor, replace `CLOUDSQLIP` with the Cloud SQL instance Public IP address that you noted above. Leave the quotation marks around the value in place.

In the **nano** text editor, replace `DBPASSWORD` with the Cloud SQL database password that you defined above. Leave the quotation marks around the value in place.

Press **Ctrl+O**, and then press **Enter** to save your edited file.

Press **Ctrl+X** to exit the nano text editor.

Restart the web server:

```bash
sudo service apache2 restart
```

Return to the web browser tab in which you opened your **bloghost** VM instance's external IP address. When you load the page, the following message appears:

`Database connection succeeded.`

> Note: In an actual blog, the database connection status would not be visible to blog visitors. Instead, the database connection would be managed solely by the administrator.

#### Task 6. Configure an application in a Compute Engine instance to use a Cloud Storage object

In the Google Cloud console, click **Cloud Storage** > **Buckets**.

Click the bucket that is named after your Google Cloud project.

In this bucket, there is an object called `my-excellent-blog.png`. Copy the URL behind the link icon that appears in that object's **Public access** column, or behind the words "Public link" if shown.

> Note: If you see neither a link icon nor a "Public link", try refreshing the browser. If you still do not see a link icon, return to Cloud Shell and confirm that your attempt to change the object's Access Control list with the **gsutil acl ch** command was successful.

Return to your ssh session on your **bloghost** VM instance.

Enter this command to set your working directory to the document root of the web server:

```bash
cd /var/www/html
```

Use the **nano** text editor to edit `index.php`:

```bash
sudo nano index.php
```

Use the arrow keys to move the cursor to the line that contains the **h1** element. Press **Enter** to open up a new, blank screen line, and then paste the URL you copied earlier into the line.

Paste this HTML markup immediately before the URL:

```html
<img src='
```

Place a closing single quotation mark and a closing angle bracket at the end of the URL:

```html
'>
```

The resulting line will look like this:

```html
<img src='https://storage.googleapis.com/qwiklabs-gcp-0005e186fa559a09/my-excellent-blog.png'>
```

The effect of these steps is to place the line containing `<img src='...'>` immediately before the line containing `<h1>...</h1>`

> Note: Do not copy the URL shown here. Instead, copy the URL shown by the Storage browser in your own Cloud Platform project.

Press **Ctrl+O**, and then press **Enter** to save your edited file.

Press **Ctrl+X** to exit the nano text editor.

Restart the web server:

```bash
sudo service apache2 restart
```

Return to the web browser tab in which you opened your **bloghost** VM instance's external IP address.

When you load the page, its content now includes a banner image.

#### Congratulations

In this lab, you configured a Cloud SQL instance and connected an application in a Compute Engine instance to it.

You also worked with a Cloud Storage bucket.

---

## Containers in the Cloud

### 1. Introduction to containers

- The idea of a container is to give the independent scalability of workloads in PaaS and an abstraction layer of the OS and hardware in IaaS.
- Isolation and Portability
  - Packages application code and dependencies into a self-contained unit.
- Efficiency
  - Shares OS kernel with other containers, reducing resource overhead.
- Scalability
  - Quickly deploy and manage multiple instances of an application.
- Microservices Architecture
  - Enables building applications as a collection of interconnected services.
- Rapid Deployment
  - Faster deployment and updates compared to traditional VMs.
- Consistency
  - Ensures consistent application behavior across environments.

### 2. Kubernetes

- Kubernetes is an open-source platform for managing containerized workloads and services.
- It makes it easy to orchestrate many containers on many hosts, scale them as microservices, and easily deploy rollouts and rollbacks.
- Container orchestration platform
  - Manages and scales containerized applications.
- Key components
  - Nodes:
    - Compute instances running containers. represents a computing instance
  - Pods:
    - Groups of one or more containers with shared network and storage. a running process on your cluster
  - Deployments:
    - Manage groups of identical Pods. represent a component of an application
  - Services:
    - Provides stable endpoints for accessing Pods.
- Declarative configuration
  - Define desired state of application and let Kubernetes manage the process.
  - using a Deployment config file
- Rolling updates
  - Gradually deploy new application versions while maintaining service availability.
- Load balancing
  - Distributes traffic across multiple Pods.
- Autoscaling
  - Automatically adjusts number of Pods based on workload.

### 3. Google Kubernetes Engine

- GKE is a Google-hosted managed Kubernetes service in the cloud.
- Managed Kubernetes service
  - Simplifies Kubernetes cluster management.
- Cluster components
  - Multiple Compute Engine instances working together.
- Modes
  - Autopilot:
    - Google manages node configuration, autoscaling, security, and networking.
  - Standard:
    - User manages underlying infrastructure.
- Benefits
  - Autopilot:
    - Optimized for production, enhanced security, operational efficiency.
  - Standard:
    - Full control over node configuration.
- Creation
  - Use Google Cloud Console or gcloud command.
- Customization
  - Choose machine types, number of nodes, and network settings.
- Kubernetes integration
  - Interact with cluster using Kubernetes commands and resources.
- Advanced features
  - Load balancing, node pools, autoscaling, auto-upgrades, node auto-repair, logging, and monitoring.

---

## Applications in the Cloud

### 1. Cloud Run

- Cloud Run is a managed compute platform that runs stateless containers via web requests or Pub/Sub events.
- Serverless compute platform
  - Manages containerized applications without infrastructure overhead.
- Based on Knative (an open API and runtime environment built on Kubernetes)
  - Open-source framework for serverless workloads.
- Fast and scalable
  - Automatic scaling based on demand, pay-per-use pricing.
- Development workflow
  - Write application code. This application should start a server that listens for web requests.
  - uild container image.
  - the container image is pushed to Artifact Registry, Deploy image to Cloud Run.
- HTTPS serving
  - Built-in HTTPS termination.
- Source-based deployment - make sure your container image is secure, well-configured and built in a consistent way
  - Deploy directly from source code using Buildpacks.
  - Cloud Run handles HTTPS serving for you.
- Language support
  - Runs any binary compiled for Linux 64-bit, including popular languages, such as: Java, Python, Node.js, PHP, Go, and C++ and less common ones, such as: Cobol, Haskell, and Perl.
  - key is for the app to handle web requests
- Pricing
  - Pay-per-use based on resource consumption and request count.

### 2. Development in the cloud

- Event-driven compute platform.
- Handles event-based tasks (e.g., image processing).
- Serverless architecture (no server management).
- Pay-per-use billing based on execution time.
- Supports multiple programming languages (Node.js, Python, Go, Java, .NET Core, Ruby, PHP).
- Triggered by Cloud Storage, Pub/Sub, or HTTP requests.
- Used for building application workflows and connecting cloud services.

### 3. Hello Cloud Run

#### Overview

Cloud Run is a managed compute platform that enables you to run stateless containers that are invocable via HTTP requests.

Cloud Run is serverless: it abstracts away all infrastructure management, so you can focus on what matters most — building great applications.

Cloud Run is built from Knative, letting you choose to run your containers either fully managed with Cloud Run, or in your Google Kubernetes Engine cluster with Cloud Run on GKE.

The goal of this lab is for you to build a simple containerized application image and deploy it to Cloud Run.

#### Objectives

In this lab, you learn to:

- Enable the Cloud Run API.
- Create a simple Node.js application that can be deployed as a serverless, stateless container.
- Containerize your application and upload to Container Registry (now called "Artifact Registry.")
- Deploy a containerized application on Cloud Run.
- Delete unneeded images to avoid incurring extra storage charges.

##### Reference - Basic Linux Commands

Below you will find a reference list of a few very basic Linux commands which may be included in the instructions or code blocks for this lab.

Command --> | Action | . | Command --> | Action
--- | --- | --- | --- | ---
mkdir (make directory) | create a new folder | . | cd (change directory) | change location to another folder
ls (list ) | list files and folders in the directory | . | cat (concatenate) | read contents of a file without using an editor
apt-get update | update package manager library | . | ping | signal to test reachability of a host
mv (move ) | moves a file | . | cp (copy) | makes a file copy
pwd (present working directory ) | returns your current location | . | sudo (super user do) | gives higher administration privileges

#### Task 1. Enable the Cloud Run API and configure your Shell environment

From Cloud Shell, enable the **Cloud Run API** 

```bash
gcloud services enable run.googleapis.com
```

If you are asked to authorize the use of your credentials, do so. You should then see a successful message similar to this one:

`Operation "operations/acf.cc11852d-40af-47ad-9d59-477a12847c9e" finished successfully.`

> Note: You can also enable the API using the **APIs & Services** section of the console.

Set the compute region:

```bash
gcloud config set compute/region "REGION"
```

Create a LOCATION environment variable:

```bash
LOCATION="Region"
```

#### Task 2. Write the sample application

In this task, you will build a simple express-based NodeJS application which responds to HTTP requests.

In Cloud Shell create a new directory named `helloworld`, then move your view into that directory:

```bash
mkdir helloworld && cd helloworld
```

Next you'll be creating and editing files. To edit files, use **nano** or the Cloud Shell Code Editor by clicking on the **Open Editor** button in Cloud Shell.

Create a `package.json` file, then add the following content to it:

```bash
nano package.json
```

```json
{
    "name": "helloworld",
    "description": "Simple hello world sample in Node",
    "version": "1.0.0",
    "main": "index.js",
    "scripts": {
    "start": "node index.js"
    },
    "author": "Google LLC",
    "license": "Apache-2.0",
    "dependencies": {
    "express": "^4.17.1"
    }
}
```

Most importantly, the file above contains a start script command and a dependency on the Express web application framework.

Press **CTRL+X**, then **Y**, then **Enter** to save the `package.json` file.

Next, in the same directory, create a `index.js` file, and copy the following lines into it:

```bash
nano index.js
```

```js
const express = require('express');
const app = express();
const port = process.env.PORT || 8080;

app.get('/', (req, res) => {
    const name = process.env.NAME || 'World';
    res.send(`Hello ${name}!`);
});

app.listen(port, () => {
    console.log(`helloworld: listening on port ${port}`);
});
```

This code creates a basic web server that listens on the port defined by the `PORT` environment variable. Your app is now finished and ready to be containerized and uploaded to Container Registry.

Press **CTRL+X**, then **Y**, then **Enter** to save the `index.js` file.

> Note: You can use many other languages to get started with Cloud Run. You can find instructions for Go, Python, Java, PHP, Ruby, Shell scripts, and others from the Quickstarts guide.

#### Task 3. Containerize your app and upload it to Artifact Registry

To containerize the sample app, create a new file named `Dockerfile` in the same directory as the source files, and add the following content:

```bash
nano Dockerfile
```

```dockerfile
# Use the official lightweight Node.js 12 image.
# https://hub.docker.com/_/node
FROM node:12-slim

# Create and change to the app directory.
WORKDIR /usr/src/app

# Copy application dependency manifests to the container image.
# A wildcard is used to ensure copying both package.json AND package-lock.json (when available).
# Copying this first prevents re-running npm install on every code change.
COPY package*.json ./

# Install production dependencies.
# If you add a package-lock.json, speed your build by switching to 'npm ci'.
# RUN npm ci --only=production
RUN npm install --only=production

# Copy local code to the container image.
COPY . ./

# Run the web service on container startup.
CMD [ "npm", "start" ]
```

Press **CTRL+X**, then **Y**, then **Enter** to save the `Dockerfile` file.

Now, build your container image using Cloud Build by running the following command from the directory containing the `Dockerfile`. (Note the $GOOGLE_CLOUD_PROJECT environmental variable in the command, which contains your lab's Project ID):

```bash
gcloud builds submit --tag gcr.io/$GOOGLE_CLOUD_PROJECT/helloworld
```

Cloud Build is a service that executes your builds on Google Cloud.

It executes a series of build steps, where each build step is run in a Docker container to produce your application container (or other artifacts) and push it to Cloud Registry, all in one command.

Once pushed to the registry, you will see a SUCCESS message containing the image name (`gcr.io/[PROJECT-ID]/helloworld`).

The image is stored in Artifact Registry and can be re-used if desired.

List all the container images associated with your current project using this command:

```bash
gcloud container images list
```

Register `gcloud` as the credential helper for all Google-supported Docker registries:

```bash
gcloud auth configure-docker
```

> Note: You may be prompted Do you want to continue? (y/N)? if you are, enter Y to agree.

To run and test the application locally from Cloud Shell, start it using this standard `docker` command:

```bash
docker run -d -p 8080:8080 gcr.io/$GOOGLE_CLOUD_PROJECT/helloworld
```

In the Cloud Shell window, click on **Web preview** and select **Preview on port 8080**.

This should open a browser window showing the "Hello World!" message. You could also simply use `curl localhost:8080`.

#### Task 4. Deploy to Cloud Run

Deploying your containerized application to Cloud Run is done using the following command adding your Project-ID:

```bash
gcloud run deploy --image gcr.io/$GOOGLE_CLOUD_PROJECT/helloworld --allow-unauthenticated --region=$LOCATION
```

The allow-unauthenticated flag in the command above makes your service publicly accessible.

When prompted confirm the `service name` by pressing **Enter**.

> Note: You may be prompted Do you want enable these APIs to continue (this will take a few minutes)? (y/N)? if you are, enter Y to enable the API needed.

Wait a few moments until the deployment is complete.

On success, the command line displays the service URL:

```bash
Service [helloworld] revision [helloworld-00001-xit] has been deployed
and is serving 100 percent of traffic.

Service URL: https://helloworld-h6cp412q3a-uc.a.run.app
```

You can now visit your deployed container by opening the service URL in any browser window.

#### Congratulations

You have just deployed an application packaged in a container image to Cloud Run.

Cloud Run automatically and horizontally scales your container image to handle the received requests, then scales down when demand decreases.

In your own environment, you only pay for the CPU, memory, and networking consumed during request handling.

For this lab you used the gcloud command-line.

Cloud Run is also available via Cloud console.

- From the **Navigation menu**, in the Serverless section, click **Cloud Run** and you should see your helloworld service listed.

#### Task 5. Clean up

While Cloud Run does not charge when the service is not in use, you might still be charged for storing the built container image.

You can either decide to delete your Google Cloud project to avoid incurring charges, which will stop billing for all the resources used within that project, or simply delete your `helloworld` image using this command :

```bash
gcloud container images delete gcr.io/$GOOGLE_CLOUD_PROJECT/helloworld
```

When prompted to continue type `Y`, and press **Enter**.

To delete the Cloud Run service, use this command :

```bash
gcloud run services delete helloworld --region="REGION"
```

When prompted to continue type `Y`, and press **Enter**.

---

## Prompt Engineering

### 1. Prompt Engineering

- Key Concepts
  - Generative AI:
    - A subset of AI that creates new content (text, images, etc.) based on input data.
  - Large Language Model (LLM):
    - A specific type of generative AI focused on language tasks.
  - Prompt:
    - An instruction or question given to a model to generate output.
  - Prompt Engineering:
    - The art of crafting effective prompts to get desired results from LLMs.
- LLM Training and Limitations
  - Pre-training:
    - LLMs learn patterns from massive datasets.
  - Fine-tuning:
    - LLMs are specialized for specific tasks.
  - Hallucinations:
    - LLMs can generate incorrect or nonsensical outputs.
- Google Gemini
  - Generative AI assistant:
    - Integrated into Google Cloud products.
  - Access to vast data:
    - Includes Google Cloud documentation and samples.
  - Enhanced productivity:
    - Provides suggestions, code, and guides.
- Prompt Engineering Best Practices
  - Clear and detailed instructions:
    - Avoid ambiguity.
  - Define boundaries:
    - Specify desired output format and constraints.
  - Adopt a persona:
    - Provide context for the model.
  - Concise sentences:
    - Break down complex prompts.
- Example: Sasha and Network Architecture
  - Prompt refinement:
    - Iterative process to improve results.
  - Role-based prompting:
    - Providing context for the LLM.
  - Leveraging Gemini:
    - Using the model as a collaborative tool.

---

## Next Steps

Follow with me the [notes](ess-gcloud-infra-foundation) of the next course in the series, [Essential Google Cloud Infrastructure: Foundation](https://www.cloudskillsboost.google/course_templates/50).
