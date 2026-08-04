# Mission 13 - Cloud Computing Fundamentals

## Objective

Understand what cloud computing is, how cloud services are delivered, and why cloud security is important for SOC analysts.

---

# Questions & Answers

## 1. What is cloud computing?

Cloud computing means using computing resources such as servers, storage, databases, networking, and software over the internet instead of owning and maintaining physical infrastructure.

Cloud computing allows organizations to access resources on demand while reducing the need to manage their own hardware.

---

## 2. What is the difference between IaaS, PaaS, and SaaS?

### Infrastructure as a Service (IaaS)

IaaS provides customers with cloud infrastructure such as virtual machines, storage, and networking. The cloud provider manages the physical infrastructure, while the customer manages the operating system, applications, and configurations.

### Platform as a Service (PaaS)

PaaS allows customers to develop and run applications while the cloud provider manages the underlying infrastructure, operating system, and platform.

### Software as a Service (SaaS)

SaaS provides customers with ready-to-use applications where the cloud provider manages the application and most of the underlying infrastructure. The customer is mainly responsible for users, access, and data security.

---

## 3. What is the shared responsibility model?

The shared responsibility model means that cloud security responsibilities are divided between the cloud provider and the customer.

The cloud provider is responsible for securing the cloud infrastructure, while the customer is responsible for securing their data, user accounts, permissions, configurations, and cloud resources they control.

The exact responsibilities depend on the cloud service model being used.

---

## 4. Why is cloud security important to a SOC analyst?

Cloud security is important to a SOC analyst because organizations rely heavily on cloud services to store data, run applications, and manage users. SOC analysts need to understand cloud environments so they can investigate suspicious activity, review cloud logs, monitor user behavior, and identify potential security risks.

---

## 5. Imagine a company stores customer information in a cloud service. Name three security risks the company should consider.

Three security risks include:

- Unauthorized access or account compromise.
- Data leaks or exposure of sensitive information.
- Unauthorized downloading or transferring of company data.

Additional risks may include weak permissions, misconfigured cloud resources, and poor access controls.

---

## 6. A cloud user account logs in from an unfamiliar country and then downloads a large amount of company data. What would you investigate first?

I would investigate:

- The unfamiliar IP address and its reputation.
- The user's identity and whether they normally access the system from that location.
- What data was downloaded.
- Whether the download was authorized.
- The device used to access the account.
- Cloud authentication logs and activity history.
- Whether other suspicious activity occurred before or after the download.

---

# What I Learned

This mission introduced me to the fundamentals of cloud computing and how cloud security differs from traditional infrastructure security. I learned that cloud providers and customers share security responsibilities depending on the service model. I also learned that SOC analysts must understand cloud environments to investigate user activity, access patterns, and potential security incidents.
