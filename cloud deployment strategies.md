# Deployment-Strategies-of-Cloud
## Introduction
First let us understand what Cloud is and what cloud computing is then we will come to the issue of deployment strategies of cloud. Cloud is the computing resources which are provided to us like storage, RAM, CPU, networking etc. over the internet.
While cloud computing is using these on demand resources over the internet  for deploying applications or any other task without hardware being physically present with us. This ensures accesibility, scalability, observability, reliability, authenticity, security etc.
Cloud computing works on 3 main models: 
### IAAS(Infrastructure as a service):
- IaaS contains the basic building blocks for cloud IT and typically provides access to networking features, computers (virtual or on dedicated hardware), and data storage space.
- This provides us with on demand computing resources, scalability and elasticity and full control over the infrastructure
- Examples include: AWS Ec2, Aws S3 bucket, AWS VPC

### PAAS(Platform as a Service):
- Provides a platform for developing, deploying, and managing applications without managing the underlying infrastructure.
- The cloud provider handles operating systems, middleware, and runtime environments while we manage applications and data
- Examples include: AWS elastic beanstlk (which is used for deploying and managing web applications), AWS RDS(Relational Database service)

### SAAS(Software as a Service):
- Delivers software applications over the internet on a subscription basis.
- The cloud provider manages everything, including infrastructure, platform, and application, we just use the software
- The advantage here is that we have ready to use applications and no installation is required.
- Examples: AWS Marketplace offers AMI which has pre installed software which we can select according to our usage, Dropbox which is a cloud-based file storage service that runs on AWS.


Here we will be talking about two types of cloud:
 ### 1. Public Cloud: 
This is a cloud computing model where computing resources like servers, storage, and applications are owned and operated by third-party cloud providers like AWS, GCC(google cloud), Microsoft Azure and are shared among multiple users over the internet.
- This means that a single computing resource can be shared with many users at a particular time which is sometimes undesirable. Nowadays many companies and organisations are using public cloud to host their applications like Netflix, Gmail, Dropbox etc.
Some Advantages of Public Cloud are:
- High Scalability – Instantly increase or decrease resources according to need.
- Reliability – Cloud providers like AWS offer high uptime (99.99%) and they have a contract for the same.
- Global Reach – We can access resources from anywhere using just an internet connection and logging in to cloud providers site.
- Low Cost – We dont have to pay for hardware set up like servers and computing resources like CPU, RAM, Storage etc. as the cloud provider does it for us. 
### 2. Private Cloud:
 This is a cloud computing model where resources are exclusively used and owned by a single organization. It provides greater control, security, and customization, making it ideal for businesses with strict data security and compliance requirements. Examples include Openstack, VMware.
The single organisation hosting the private cloud has full control over it and its hardware resources which gives it <ins> TCO or total cost of ownership over its product </ins>
- Private Cloud is better over public cloud if you want full control over your resources and dont have much budget constraint as it gives TCO as said above while public cloud provides lower set up costs but can have unpredictable costs over time which are undesirable.
Advantages:
- TCO – The company has full control over their resources and hardware which is an ideal situation instead of 3rd party controlling it
- High security – Company has full access and ownership over resources so automatically the security also increases
- Increased Performance – There is no resource sharing with other users so performance is increased.

### Various Deployment Strategies of Cloud:

### 1. Public Cloud Only:
A public cloud is a computing environment where cloud resources are owned and managed by third-party providers such as AWS, Microsoft Azure, and Google Cloud. Users can access these resources on-demand, typically through a pay-as-you-go model.

- **Deployment**:Services are hosted entirely on a public cloud platform such as AWS, Azure, or Google Cloud.

- Users access resources via the internet, utilizing shared cloud infrastructure managed by the provider.

- **Cost Analysis**:Lower upfront costs as infrastructure is managed by the cloud provider.

- Variable operational costs based on usage (compute, storage, networking).

### Advantages

- Scalability and elasticity, allowing businesses to scale up or down as needed.
- No maintenance overhead since the provider manages hardware and software updates.
- Pay-per-use pricing, which reduces capital expenditure.

### Disadvantages

- Limited control over infrastructure as cloud providers enforce certain policies.
- Potential security and compliance concerns, as data is stored on third-party servers.

Examples include: 

- Hosting a website on AWS EC2 instance or hosting web application on ec2 using the public IP provided by amazon.
  - In this we will first create AWS account and launch ec2 instance to host web app, we will use amazon RDS for database management, amazon s3 for storage of files, Configure IAM roles and security groups for access control and use docker for deploying the application directly on the EC2 instance.

- Using Google Cloud Storage for storing backup data.

### 2. Private Cloud Only:
A private cloud is a cloud infrastructure that is exclusively used by a single organization and the organisation has the full ownership over it and the hardware resources associated with it. It can be hosted on-premises or in a third-party data center but is not shared with other customers.

- **Deployment**: Infrastructure is hosted on-premises or in a dedicated data center.

- Managed entirely by an enterprise IT team or a managed service provider.

- **Cost Analysis**: High capital expenditure (CapEx) for purchasing hardware and setting up infrastructure.

- Operational costs (OpEx) for maintenance, staffing, and electricity.

### Advantages

- Full control over security and compliance, ensuring regulatory adherence.
- Customization and dedicated resources tailored to specific organizational needs.

### Disadvantages

- High initial investment required for setting up the infrastructure.
- Limited scalability compared to public clouds.

### Example Services

- Running OpenStack to deploy erp system on in-house servers.
  - We will first install and configure OpenStack on on-premise servers, set up Ceph Storage(which is simiilar to s3 but is self hosted) for handling storage needs, and use Neutron for network management and Keystone for authentication

- Hosting an enterprise database in a private data center.

### 3. Public on Private Cloud (Hybrid Cloud)
Cloud bursting is a hybrid model where an organization primarily runs applications in a private cloud but dynamically shifts workloads to a public cloud when demand spikes.

- **Deployment**: Deploying certain services on your private cloud and others on a public cloud.
- This allows us to leverage the strengths of both environments.
- Often involves connecting your private cloud to a public cloud through a VPN or dedicated connection.


- **Cost**:Combines the costs of private and public cloud.
- Requires careful cost optimization to balance the two environments.

### Advantages:

- Flexibility: Choose the best environment for each service.
- Scalability: Use public cloud for burst workloads.
- Security: Keep sensitive data in the private cloud.
- Disaster recovery.

### Disadvantages:
- Complexity: Managing two separate environments.
- Integration challenges: Ensuring seamless communication between clouds.
- Increased network complexity.

### Examples:
- Handling peak traffic using AWS.
  - We will host the main site in a private cloud such as OpenStack, then we will configure a load balancer to detect high traffic spikes, Connect OpenStack with AWS via VPN, Use AWS Auto Scaling to add EC2 instances dynamically when demand increases and redirect traffic from the private cloud to AWS during peak loads
- Development and testing: Using the public cloud for development and testing, and the private cloud for production.
- Data backup and archival.

### 4. Private on Public Cloud (Dedicated Cloud on Public Infra)

In this model, a private cloud infrastructure is hosted within a public cloud provider’s environment, offering a dedicated yet managed solution
- **Deployment** : Portions of the private cloud environment are deployed inside a public cloud. For example, using VMWare inside of AWS.
- This is often used for migrating existing workloads to the cloud, without refactoring.

### Cost: 
- The cost of the public cloud resources, plus the cost of the private cloud software liscensing.
- Can be expensive.

### Advantages:
- Allows for lift and shift migration, which reduces migration complexity.
- Can use existing private cloud tools, inside the public cloud.

### Disadvantages:
- Increased cost.
- Increased complexity.
- Performance can be degraded.

### Examples:
- Deploying a bank’s private cloud on AWS VPC
  - We will set up a dedicated AWS VPC with restricted access, use AWS Direct Connect for a private, high-speed connection,deploy workloads on AWS EC2 Bare Metal instances for full control.Implement IAM and security groups for compliance and security and integrate with AWS Key Management Service (KMS) for data encryption.
- Running VMWare workloads inside of AWS, Azure VMWare solution, or Google VMWare engine.

### 5. Private on Private Cloud (Multi-Private Cloud)

A multi-private cloud strategy involves using multiple private cloud environments across different vendors or locations, primarily for redundancy, compliance, and disaster recovery.

- **Deployment**: A dedicated private cloud environment is hosted by a third-party provider.
- Offers the benefits of a private cloud with managed services.
- The hardware is dedicated to one customer.

### Cost:
- Higher than public cloud, but may be lower than on-premise private cloud.
- Cost is based on dedicated resources, and management services.

### Advantages:
- Enhanced security and compliance.
- Dedicated resources and performance.
- Managed services.

### Disadvantages:
- Less flexibility than public cloud.
- Higher costs than public cloud.
- Vendor lock in.

### Examples:
- A government agency running services across multiple data centers
  - Deploy OpenStack in two or more private data centers, use VMware vSphere for virtualization, configure Cisco ACI for interconnecting networks, deploy workloads on Red Hat OpenShift for containerized apps.Implement multi-site replication and failover for disaster recovery.

- Financial institutions with strict compliance requirements.

### 6. Public on Public Cloud (Multi-Public Cloud)

This strategy involves distributing services across multiple public cloud providers to improve reliability, avoid vendor lock-in, and optimize costs.

- **Deployment**:
- Utilizes multiple public cloud providers.
- Services are distributed across different clouds.
- Allows for best-of-breed selection and vendor diversification.

### Cost:
- Variable, depending on usage across multiple providers.
- Requires careful cost management.

### Advantages:
- Avoids vendor lock-in.
- Leverages best-of-breed services.
- Improved resilience and redundancy.
- Geographic distribution.

### Disadvantages:
- Increased complexity in management.
- Integration challenges.
- Potential for higher costs.

### Examples:
- Using AWS for compute, Azure for databases, and GCP for data analytics.
- Hosting different microservices on AWS and Google Cloud
  - Deploy backend microservices using AWS Lambda (serverless), host frontend on Google Firebase.Deploy additional services on Google Kubernetes Engine (GKE).Use Google Cloud Pub/Sub to synchronize data between clouds.Implement API Gateway for a unified service endpoint.

### 7. OpenStack on Kubernetes

This approach involves running OpenStack services as containerized applications within Kubernetes clusters, offering a modern, scalable infrastructure.

- **Deployment**: OpenStack, an open-source cloud computing platform, is deployed on Kubernetes, a container orchestration platform.
- Kubernetes manages the OpenStack control plane and services.
- Openstack provides the IaaS, and Kubernetes manages the Openstack services.

### Cost:
- Cost includes hardware, software licensing, and operational expenses.
- Requires skilled personal.

### Advantages:
- Improved scalability and resilience of OpenStack.
- Simplified management of OpenStack services.
- Containerized deployment of OpenStack components.
- Modernization of Openstack.

### Disadvantages:
- Increased complexity in setup and management.
- Requires expertise in both OpenStack and Kubernetes.
- Can create more overhead.

### Examples:
- Running OpenStack control plane inside Kubernetes for scalability
  - Deploy a Kubernetes cluster using KubeSpray or Rancher. Install OpenStack Helm to deploy OpenStack services as containers. Use KubeVirt for VM-based workloads within Kubernetes. Deploy Prometheus for monitoring OpenStack services. Implement Ingress Controllers for managing OpenStack API traffic.
- Telecommunications companies using OpenStack for network functions virtualization (NFV).

### 8. Kubernetes on OpenStack

This model involves deploying Kubernetes clusters on top of OpenStack infrastructure, allowing containerized workloads to run efficiently in a private cloud.

- **Deployment**: Kubernetes is deployed on top of OpenStack's infrastructure.
- OpenStack provides the underlying virtual machines and storage for Kubernetes clusters.
- Openstack provides the IaaS, and Kubernetes provides the PaaS.

### Cost:
- Cost includes OpenStack infrastructure and Kubernetes management.
- Requires less overhead than openstack on kubernetes.

### Advantages:
- Leverages OpenStack's infrastructure capabilities.
- Provides a flexible and scalable platform for containerized applications.
- Allows to use Kubernetes on private clouds.

### Disadvantages:
- Requires integration between OpenStack and Kubernetes.
- Performance can be affected by OpenStack's virtualization layer.

### Examples:
- Deploying Kubernetes on an OpenStack cloud for containerized workloads
  - Set up an OpenStack cloud environment. Use OpenStack Magnum to provision Kubernetes clusters. Deploy containerized applications using Helm Charts. Use Ceph Storage for Kubernetes Persistent Volumes. Implement Kubernetes Operators for automated management of applications.

- Companies using OpenStack for their IaaS (infrastructure as a service) and Kubernetes for their PaaS (platform as a service).
