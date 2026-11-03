# Capstone Assignment — Deploy the Book Review App Using Terraform and Claude Code Agentic AI

Part of the DevOps Micro Internship (DMI) with Agentic AI

---

## Student Details

**Full Name:** Olatunde Ibitoye  
**Cloud Platform:** AWS or Azure  
**GitHub Repository URL:** [https://github.com/horlartundhey/devops-micro-internship-pravinmishra](https://github.com/horlartundhey/devops-micro-internship-pravinmishra) 
**Public Application URL / Load-Balancer DNS:** [http://book-review-capstone-pub-alb-1362760868.eu-north-1.elb.amazonaws.com/](http://book-review-capstone-pub-alb-1362760868.eu-north-1.elb.amazonaws.com/)

---

## Purpose

Deploy the Book Review App using Terraform on AWS or Azure in a secure, highly available, production-style three-tier architecture. Use Claude Code, specialized subagents, Terraform MCP, and validation hooks to support the engineering workflow while keeping all infrastructure-changing operations under human control.

---

# Task 0 — Prepare the Project and Agentic AI Environment

## Goal

Prepare the Book Review App project and configure the provided Claude Code Agentic AI starter kit with project context, specialized subagents, Terraform MCP, validation hooks, and safety guardrails.

## Evidence

### Screenshot 1 — Project `CLAUDE.md`

Add a screenshot of the project `CLAUDE.md` showing the three-tier architecture, security boundaries, Terraform requirements, and human-approval rules.

![Screenshot 1](screenshots/sc76.png)

---

### Screenshot 2 — Terraform Engineer Subagent

Add a screenshot showing the Terraform Engineer subagent configuration.

![Screenshot 2](screenshots/sc77.png)

---

### Screenshot 3 — Architecture and Security Reviewer Subagent

Add a screenshot showing the Architecture and Security Reviewer subagent configuration.

![Screenshot 3](screenshots/sc78.png)

---

### Screenshot 4 — Terraform MCP Connection

Add a screenshot showing Terraform MCP connected and available.

![Screenshot 4](screenshots/sc79.png)

---

### Screenshot 5 — Validation Hooks

Add a screenshot showing the configured Claude Code validation hooks.

![Screenshot 5](screenshots/sc80.png)

---

# Task 1 — Design the Three-Tier Architecture

## Goal

Design the required secure, highly available three-tier architecture and create an architecture diagram before building the infrastructure.

The diagram must show:

- VPC or VNet
- Availability Zones or equivalent availability locations
- Six subnets
- Internet connectivity
- NAT or outbound design
- Public load balancer
- Web Tier
- Internal load balancer
- Application Tier
- Managed MySQL
- Read replica
- Main traffic flow

## Architecture Diagram

![Architecture Diagram](screenshots/book_review_capstone_architecture.png)

---

# Task 2 — Build the Terraform Networking and Security Layers

## Goal

Create the modular Terraform project and implement the network and security layers across the required public and private subnets.

## Evidence

### Screenshot 6 — Modular Terraform Project Structure

Add a screenshot showing the modular Terraform project structure.

![Screenshot 6](screenshots/sc81.png)

---

### Screenshot 7 — Six-Subnet Architecture

Add a screenshot showing the six-subnet architecture across two availability locations.

![Screenshot 7](screenshots/sc82.png)

---

### Screenshot 8 — Public and Private Tier Separation

Add a screenshot showing the public and private tier separation, including routing and security boundaries.

![Screenshot 8](screenshots/sc83.png)

---

# Task 3 — Build the Load-Balancing and Compute Layers

## Goal

Deploy the public and internal load balancers and the Web and Application compute resources required by the Book Review App.

## Evidence

### Screenshot 9 — Web and Application Compute

Add a screenshot showing the Web and Application compute resources in their required subnets.

![Screenshot 9](screenshots/sc92.png)

---

### Screenshot 10 — Public Load Balancer

Add a screenshot showing the internet-facing public load balancer.

![Screenshot 10](screenshots/sc84.png)

---

### Screenshot 11 — Internal Load Balancer

Add a screenshot showing the private internal load balancer.

![Screenshot 11](screenshots/sc85.png)

---

### Screenshot 12 — Healthy Targets

Add a screenshot showing healthy target groups or backend pools.

![Screenshot 12](screenshots/sc86.png)

---

# Task 4 — Build the Managed MySQL Database Layer

## Goal

Deploy a private, highly available managed MySQL database with a read replica and restrict database connectivity to the Application Tier.

## Evidence

### Screenshot 13 — Managed MySQL Database

Add a screenshot showing the managed MySQL database deployment.

![Screenshot 13](screenshots/sc87.png)

---

### Screenshot 14 — High Availability

Add a screenshot showing the Multi-AZ or high-availability configuration.

![Screenshot 14](screenshots/sc88.png)

---

### Screenshot 15 — Read Replica

Add a screenshot showing the read replica configuration.

![Screenshot 15](screenshots/sc89.png)

---

### Screenshot 16 — Private Database Access

Add a screenshot showing that the database is private and accepts MySQL traffic only from the Application Tier.

![Screenshot 16](screenshots/sc90.png)

---

# Task 5 — Validate, Review, and Apply the Terraform Configuration

## Goal

Validate the Terraform configuration, review the execution plan using both Agentic AI and human judgment, and apply the infrastructure changes only after all required checks pass.

## Evidence

### Screenshot 17 — Terraform Validation

Add a screenshot showing successful `terraform validate` output.

![Screenshot 17](screenshots/sc91.png)

---

### Screenshot 18 — Terraform Plan

Add a screenshot showing the Terraform plan output.

![Screenshot 18](screenshots/sc93.png)

---

### Screenshot 19 — Terraform Apply

Add a screenshot showing successful `terraform apply` completion.

![Screenshot 19](screenshots/sc94.png)

---

# Task 6 — Deploy and Configure the Book Review Application

## Goal

Deploy and configure the Book Review App across the Web, Application, and Database tiers and verify the complete application functionality.

## Evidence

### Screenshot 20 — Homepage

Add a screenshot showing the Book Review App homepage through the public endpoint.

![Screenshot 20](screenshots/sc95.png)

---

### Screenshot 21 — Login or Authentication

Add a screenshot showing successful login or authentication.

![Screenshot 21](screenshots/sc96.png)

---

### Screenshot 22 — Book Data

Add a screenshot showing the book listing or book details.

![Screenshot 22](screenshots/sc97.png)

---

### Screenshot 23 — Review Functionality

Add a screenshot showing the review functionality working successfully.

![Screenshot 23](screenshots/sc98.png)

---

### Screenshot 24 — Backend or API Evidence

Add a screenshot showing that the backend or API is working successfully.

![Screenshot 24](screenshots/sc99.png)

---

### Screenshot 25 — Database Reads and Writes

Add a screenshot showing successful database reads and writes.

![Screenshot 25](screenshots/sc100.png)

## Public Application URL

**Public Application URL / DNS:** [http://book-review-capstone-pub-alb-1362760868.eu-north-1.elb.amazonaws.com/](http://book-review-capstone-pub-alb-1362760868.eu-north-1.elb.amazonaws.com/)

---

# Task 7 — Demonstrate the Agentic AI Workflow

## Goal

Demonstrate how Claude Code assisted with Terraform generation, architecture and security review, and evidence-based troubleshooting while infrastructure-changing decisions remained under human control.

You do not need to submit your complete Claude Code conversation history. Include only focused evidence.

## Evidence

### Screenshot 26 — AI-Assisted Terraform Generation

Add a screenshot showing one useful example of AI-assisted Terraform generation or improvement.

![Screenshot 26](screenshots/sc101.png)

---

### Screenshot 27 — Architecture or Security Review

Add a screenshot showing one structured architecture or security review result.

![Screenshot 27](screenshots/sc102.png)

---

### Screenshot 28 — AI-Assisted Troubleshooting

Add a screenshot showing one AI-assisted troubleshooting interaction based on collected evidence.

![Screenshot 28](screenshots/sc103.png)

---

# Task 8 — Complete the Final Architecture Review

## Goal

Review the completed infrastructure against the original capstone requirements and resolve significant architecture, security, reliability, and cost issues.

Confirm that the final review covers:

- Tier separation
- Availability
- Public exposure
- Routing
- Security rules
- Load balancing
- Database privacy
- Secrets
- Terraform quality
- Module structure
- Reliability
- Obvious cost risks

Use Screenshot 27 as the focused evidence for the structured architecture or security review.

---

# Task 9 — Answer the Reflection Questions

## Goal

Reflect on the architecture, Terraform implementation, and Agentic AI workflow. Answer each question briefly in your own words.

## Architecture

### 1. Why did you separate the Web, Application, and Database tiers?

Each tier has a different job and a different exposure. The Web tier serves users, the App tier runs the API logic, and the database holds the data, so I gave each its own subnets and security group. That means a compromise or a misconfiguration in one tier doesn’t automatically reach the next, and each tier can be scaled, patched, or locked down independently

### 2. Why is the Application Tier private?

Users never need to reach the API directly. They go through the public ALB and Web tier, and Nginx forwards /api calls to the internal ALB. The App instances have no public IP, accept port 3001 only from the internal ALB’s security group, and reach the internet only outbound through the NAT gateway for package installs.

### 3. Why is MySQL private?

A database is the most sensitive asset, and nothing on the internet should be able to connect to it. It sits in subnets with no internet or NAT route, publicly_accessible = false, and a security group that allows 3306 only from the App tier’s security group, with no egress rules. I proved it by reading the data from an App instance, the only place that can reach it.

### 4. Why are multiple Availability Zones used?

So one AZ failing doesn’t take the application down. The subnets, both ALBs, and the Auto Scaling groups span two AZs, and the database has a Multi-AZ standby. One exception is my single NAT gateway, which I accepted as a cost tradeoff: if its AZ failed, the App tier would lose outbound internet access, though inbound traffic would continue.

### 5. What is the difference between Multi-AZ/high availability and a read replica?

Multi-AZ keeps a synchronous standby copy in another AZ purely for failover. It isn’t readable, and the endpoint stays the same after a failover. A read replica is an asynchronous copy with its own endpoint, meant for scaling reads, and promoting it to a primary is a manual step. I used both: Multi-AZ for availability and a replica for read capacity.

## Terraform

### 6. How did you divide your Terraform into modules?

Five modules plus a root: network (VPC, six subnets, gateways, routes), security (the five security groups and their rules), load-balancer (both ALBs, target groups, listeners), database (subnet group, primary, replica, secrets), and compute (launch templates, ASGs, IAM, key pair). Each phase was built, validated, and reviewed separately.

### 7. How do the modules communicate through variables and outputs?

Each module exposes outputs, and the root main.tf passes them into the next module. The network module’s VPC and subnet IDs feed the security, load balancer, database, and compute modules. The security group IDs feed the load balancer, database, and compute modules. The target group ARNs feed compute, and the database’s secret ARN feeds the App role’s policy. The port variables live at the root and feed both the security and load balancer modules, so they can’t drift apart.

### 8. What did you specifically check in `terraform plan`?

I checked the counts (63 to add, 0 to change, 0 to destroy) and that nothing was replaced or destroyed. I searched for every 0.0.0.0/0 and confirmed it appeared only on the public ALB’s port 80 ingress and the documented web and app egress rules. I checked that SSH used my own /32 and not the placeholder, that publicly_accessible was false, that multi_az was true on the primary only, that the AMI was pinned, and that no password value appeared anywhere. On the second plan, I confirmed the primary was updated in place and not replaced.

## Agentic AI

### 9. What was the purpose of `CLAUDE.md`?

It’s the project’s standing context, loaded at the start of every session. It holds the architecture, the CIDR plan, the security rules, the Terraform requirements, and the human-approval rules, so Claude and its subagents all worked from the same constraints without me repeating them.

### 10. What work did the Terraform Engineer subagent perform?

It designed each phase before writing anything, checked current provider documentation through Terraform MCP, asked me the open decisions, and then implemented the modules. It ran fmt, init -backend=false, and validate, and never ran apply or destroy.

### 11. What did the Architecture and Security Reviewer identify?

It reviewed each phase read-only and reported PASS, WARN, or FAIL. It caught things like missing validation on admin_cidr and the port variables, the name-prefix regex gap on the load balancers, an npm step that could abort the web bootstrap before Nginx was configured, a possible target-group race, and the risk that the ASG would replace unhealthy instances and delete my manual deployment.

### 12. Why did you use Terraform MCP instead of relying only on Claude's existing Terraform knowledge?

Provider arguments change between versions, and memory isn’t reliable. The MCP server let the agents read the current AWS provider documentation (6.71), for example how deletion_protection maps to the real argument and how write-only passwords work. It also has a limit: it serves documentation and can’t query AWS, so it couldn’t predict the RDS restriction that broke my first apply.

### 13. What was the purpose of your validation hooks?

They add automatic guardrails that don’t depend on Claude’s behaviour. A pre-command hook blocks any terraform apply or destroy that uses -auto-approve, and a post-edit hook formats the Terraform after every file change. I also moved apply and destroy into the deny rules, so only I can run them

### 14. Describe one real issue Claude helped you troubleshoot.

My first apply failed creating the read replica: RDS doesn’t allow replicas when the source uses a Secrets Manager-managed master password. I gave Claude the exact error, and it diagnosed the cause and compared options. We chose a write-only password generated by Terraform and stored in a Secrets Manager secret, so nothing sensitive reaches state or outputs. The plan showed the primary updating in place, and the second apply completed the replica.

### 15. Describe one recommendation you reviewed, modified, or rejected instead of accepting blindly.

Claude suggested enabling an instance refresh for the apply that changed the App launch template. I rejected that, because a refresh waits for healthy replacements and no app was deployed yet. I terminated the two App instances myself, so the ASG replaced them from the new template. I also chose a single NAT gateway over the recommended one per AZ to save cost, and a longer 1800 second grace period so the ASG wouldn’t delete my hand-deployed work.

---

# Task 10 — Publish the Mandatory LinkedIn Post

## Goal

Publish a LinkedIn post describing the capstone, the technical work completed, the Agentic AI workflow, and the lessons learned.

Write the post in your own words, include at least one project image or other proof, and ensure that it can be viewed by the submission reviewer.

## LinkedIn Post URL

**LinkedIn Post URL:** [https://www.linkedin.com/posts/olatunde-ibitoye_dmibypravinmishra-aws-terraform-ugcPost-7523281383688011777-Ggpf/?utm_source=share&utm_medium=member_desktop&rcm=ACoAAB_xj1QBIy4RnDuKMoQp8yo4i8QCKxf266A](https://www.linkedin.com/posts/olatunde-ibitoye_dmibypravinmishra-aws-terraform-ugcPost-7523281383688011777-Ggpf/?utm_source=share&utm_medium=member_desktop&rcm=ACoAAB_xj1QBIy4RnDuKMoQp8yo4i8QCKxf266A)

---

# Submission Instructions

- Complete Tasks 0–10 in sequence.
- Include all Screenshots 1–28 exactly as specified.
- Ensure that your full name is visible in the required screenshots.
- Include the selected cloud platform.
- Include the completed architecture diagram.
- Include the modular Terraform project structure.
- Include the working public application URL or public load-balancer DNS.
- Include all required Agentic AI workflow evidence.
- Answer all 15 reflection questions briefly in your own words.
- Include the published LinkedIn post URL.
- Do not expose cloud credentials, database passwords, SSH private keys, JWT secrets, access tokens, account IDs, Terraform state containing sensitive values, or other confidential information.
- Review all screenshots and project files carefully before submitting through GitHub.

---

# Completion Checklist

- [x] Selected AWS or Azure
- [x] Added and reviewed the Agentic AI starter files
- [x] Configured `CLAUDE.md`
- [x] Configured the Terraform Engineer subagent
- [x] Configured the Architecture and Security Reviewer subagent
- [x] Connected Terraform MCP
- [x] Configured validation hooks and safety guardrails
- [x] Created the architecture diagram
- [x] Created the six-subnet design
- [x] Configured public Web Tier routing
- [x] Kept the Application Tier private
- [x] Kept the Database Tier private
- [x] Configured tier-specific Security Groups or NSGs
- [x] Restricted backend port `3001`
- [x] Restricted MySQL port `3306` to the Application Tier
- [x] Created the public load balancer
- [x] Created the internal load balancer
- [x] Configured listeners and health checks
- [x] Deployed the Web Tier compute resources
- [x] Deployed the private Application Tier compute resources
- [x] Provisioned private managed MySQL
- [x] Configured Multi-AZ or high availability
- [x] Configured a read replica
- [x] Created the modular Terraform project
- [x] Used variables, outputs, and module dependencies
- [x] Used current Terraform documentation through MCP
- [x] Used hooks for deterministic validation
- [x] Completed `terraform fmt`
- [x] Completed `terraform validate`
- [x] Reviewed `terraform plan`
- [x] Completed the Terraform Engineer review
- [x] Completed the Architecture and Security review
- [x] Applied the infrastructure only after human approval
- [x] Deployed and configured the backend
- [x] Deployed and configured the frontend
- [x] Configured Nginx where required
- [x] Configured the internal backend endpoint
- [x] Configured the public frontend endpoint
- [x] Verified the homepage
- [x] Verified login or authentication
- [x] Verified book data
- [x] Verified review functionality
- [x] Verified the backend API
- [x] Verified database reads and writes
- [x] Verified healthy load-balancer targets
- [x] Included AI-assisted Terraform generation evidence
- [x] Included one architecture or security review
- [x] Included one AI-assisted troubleshooting example
- [x] Completed the final architecture review
- [x] Answered all 15 reflection questions
- [x] Published the mandatory LinkedIn post
- [x] Added the LinkedIn post URL
- [x] Captured all 28 required screenshots
- [x] Confirmed that my full name is visible in the required screenshots
- [x] Checked that no secrets or sensitive information are exposed

---

## About DMI & CloudAdvisory

DevOps Micro Internship (DMI) is a project-based DevOps program run by Pravin Mishra (The CloudAdvisory), focused on real-world execution, systems thinking, and career readiness.

It helps learners build strong DevOps foundations through hands-on experience.

---

## Resources

- Book Review App Repository: [https://github.com/pravinmishraaws/book-review-app](https://github.com/pravinmishraaws/book-review-app)
- DMI Official Website: [https://dmi.pravinmishra.com](https://dmi.pravinmishra.com)
- University: [https://university.pravinmishra.com](https://university.pravinmishra.com)
- Discord Community: [https://discord.pravinmishra.com](https://discord.pravinmishra.com)
- Blog: [https://dmi.pravinmishra.com/blog](https://dmi.pravinmishra.com/blog)
- YouTube Playlist: [https://www.youtube.com/playlist?list=PLFeSNDtI4Cho](https://www.youtube.com/playlist?list=PLFeSNDtI4Cho)
- Pravin Mishra on LinkedIn: [https://www.linkedin.com/in/pravin-mishra-aws-trainer/](https://www.linkedin.com/in/pravin-mishra-aws-trainer/)
- CloudAdvisory on LinkedIn: [https://www.linkedin.com/company/thecloudadvisory/](https://www.linkedin.com/company/thecloudadvisory/)

---

*This submission is part of the DevOps Micro Internship (DMI) Cohort 3 — Agentic AI Track.*
