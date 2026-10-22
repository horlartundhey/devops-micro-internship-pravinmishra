# Assignment 6 — Capstone: Deploy Book Review App (Three-Tier Architecture) on Azure

Part of the DevOps Micro Internship (DMI) with Agentic AI

---

## Purpose

This is the most important assignment of the course. You will deploy the Book Review App in a production-ready, best-practice-compliant three-tier architecture on Azure: separated presentation, application, and database tiers, least-privilege network access, a controlled public entry point, protected secrets, and availability/monitoring evidence.

---

# Task 1 — Design the Azure Three-Tier Architecture

## Goal

Create an architecture diagram and implementation plan identifying the presentation, application, and database components, the chosen Azure services, the public entry point, and the internal traffic paths.

### Evidence

#### Screenshot 1 — Architecture diagram showing the public entry point, three tiers, network boundaries, and traffic flow

![Screenshot 1](screenshots/sc28.png)

---

#### Screenshot 2 — Written architecture assumptions and selected Azure services

![Screenshot 2](screenshots/sc29.png)

---

# Task 2 — Create the Azure Network Foundation

## Goal

Create a dedicated Resource Group and VNet with separate subnets for the web, application, and database tiers, keeping the application and database tiers without direct public access.

### Evidence

#### Screenshot 3 — Resource Group overview showing the assignment resources

![Screenshot 3](screenshots/sc30.png)

---

#### Screenshot 4 — VNet overview showing the address space and all required subnets

![Screenshot 4](screenshots/sc31.png)

---

#### Screenshot 5 — Route-table or Private DNS evidence where applicable

![Screenshot 5](screenshots/sc32.png)

---

# Task 3 — Configure Security and Secret Management

## Goal

Apply least-privilege NSG rules so traffic flows Internet → public entry point → web tier → application tier → database tier, and store credentials in Azure Key Vault or another approved secure mechanism.

### Evidence

#### Screenshot 6 — NSG rules proving least-privilege access between the tiers

![Screenshot 6](screenshots/sc33.png)

---

#### Screenshot 7 — Key Vault or approved secret-management configuration (without displaying secret values)

![Screenshot 7](screenshots/sc34.png)

---

# Task 4 — Deploy the Presentation (Web) Tier

## Goal

Deploy the Book Review App presentation layer on the approved web-tier compute service, configured to route requests to the internal application-tier endpoint, and not directly exposed except through the public entry service.

### Evidence

#### Screenshot 8 — Web-tier compute overview showing subnet and availability configuration

![Screenshot 8](screenshots/sc35.png)

---

#### Screenshot 9 — Terminal or service output proving the presentation layer is running

![Screenshot 9](screenshots/sc36.png)

---

# Task 5 — Deploy the Business (Application) Tier

## Goal

Deploy the Book Review App backend privately in the application subnet, configured to use the private database endpoint and secured environment values, reachable only through its internal endpoint.

### Evidence

#### Screenshot 10 — Application-tier compute overview showing private subnet placement

![Screenshot 10](screenshots/sc37.png)

---

#### Screenshot 11 — Backend process, service, or listening-port evidence

![Screenshot 11](screenshots/sc38.png)

---

#### Screenshot 12 — Internal health-check or API response (without exposing secrets)

![Screenshot 12](screenshots/sc39.png)

---

# Task 6 — Deploy the Managed Database Tier

## Goal

Create a private Azure managed database (public access disabled), with availability/backup/retention settings, the Book Review App schema imported, and access restricted to the application tier only.

### Evidence

#### Screenshot 13 — Database overview showing private connectivity and public access disabled

![Screenshot 13](screenshots/sc40.png)

---

#### Screenshot 14 — Availability, backup, and retention configuration

![Screenshot 14](screenshots/sc41.png)

---

#### Screenshot 15 — Successful schema or connectivity verification (without exposing credentials)

![Screenshot 15](screenshots/sc42.png)

---

# Task 7 — Configure Traffic Management, Availability, and Monitoring

## Goal

Configure the approved public entry service with health probes and backend pools, internal routing for the application tier where required, and enable Azure Monitor/diagnostics/logs/alerts for the key resources.

### Evidence

#### Screenshot 16 — Public entry service showing listener, frontend endpoint, and healthy web targets

![Screenshot 16](screenshots/sc43.png)

---

#### Screenshot 17 — Internal application-tier load-balancing or routing configuration where applicable

![Screenshot 17](screenshots/sc44.png)

---

#### Screenshot 18 — Azure Monitor, diagnostic settings, logs, metrics, or alert evidence

![Screenshot 18](screenshots/sc45.png)

---

# Task 8 — Validate the Production-Style Deployment

## Goal

Confirm the Book Review App works end to end through the public endpoint, with at least one database read and one write, confirm private tiers are not internet-reachable, and complete a safe availability test.

### Evidence

#### Screenshot 19 — Browser showing the Book Review App through the public endpoint

![Screenshot 19](screenshots/sc46.png)

---

#### Screenshot 20 — Proof of successful database-backed read and write operations

![Screenshot 20](screenshots/sc47.png)

---

#### Screenshot 21 — Evidence that private tiers are not publicly accessible

![Screenshot 21](screenshots/sc48.png)

---

#### Screenshot 22 — Availability-test and healthy-target evidence

![Screenshot 22](screenshots/sc49.png)

---

#### Public Endpoint

Paste your public endpoint URL here:

`http://9.205.140.64`

---

### Notes

Summarize what worked, issues encountered and how they were fixed, and the availability/security/secrets/monitoring/backup choices made.

What worked

I deployed the Book Review app as a three-tier architecture in Denmark East, inside one resource group (Book-Review-RG). A single VNet (10.0.0.0/16) holds a Web subnet (10.0.1.0/24), an App subnet (10.0.2.0/25), and a DB subnet (10.0.3.0/26), each with its own route table and NSG. Users reach the app only through a Standard public load balancer. It forwards to the Web VM (Nginx plus the Next.js frontend). Nginx proxies /api requests to a Standard internal load balancer, which forwards to the App VM (Express API on port 3001). The App VM has no public IP and gets outbound internet through a NAT gateway. The database is Azure Database for MySQL Flexible Server with private access, reachable only from the App subnet. Registration, login, and review submission work through the public endpoint, and the data lands in the database.

Issues encountered and fixes

VM size unavailable. The default region rejected B1s for my subscription. I used Cloud Shell (az vm list-skus) to find a region where it was allowed, switched to Denmark East, and kept the cost near $8/month per VM instead of $70.
Public IP quota. The subscription allows 3 public IPs per region, and leftover resources from the previous assignment were using them. I deleted those resource groups, including an unused Bastion, to free the slots for the NAT gateway, Web VM, and public load balancer.
NAT gateway and public IP mismatch. The NAT gateway wouldn't accept the IP I created earlier because the SKUs must match. I created a new public IP with the matching SKU, attached it, and deleted the old one.
Backend password ignored. The backend failed with "Access denied (using password: NO)". The password starts with #, which .env treats as a comment. Quoting the value fixed it.
PM2 not surviving restarts. pm2 startup only prints a command; it doesn't run it. I ran the printed command, saved the process list, and confirmed the service was enabled.
Doubled API path. The frontend called /api/api/books because one fetch in page.js added /api on top of NEXT_PUBLIC_API_URL=/api. I removed the extra prefix and rebuilt.
Wrong internal load balancer IP. The page hung on "Loading books" because Nginx was proxying to 10.0.2.50, but the internal load balancer's frontend IP was 10.0.2.5. I tested each hop from the Web VM, found the mismatch, and corrected the Nginx proxy_pass.
Port mismatch in the instructions. The guide mixed 3001 and 5000 for the backend. I used 3001 everywhere (NSG, load balancer rule, health probe, and Nginx).
Build memory. B1s has 1 GiB of RAM, so I added a swap file before running the Next.js build.

Design choices

Availability: one VM per tier on low-cost B1s, behind Standard load balancers with TCP health probes. PM2 restarts crashed processes and is registered with systemd for reboots. I tested failure detection by stopping Nginx and killing the backend process. Zone-redundant HA for the database depends on the Burstable tier supporting it.
Security: least-privilege NSGs allow only Internet to Web on 80/443, Web to App on 3001, and App to DB on 3306, with SSH restricted to my IP and to the Web subnet. The App VM and database have no public IP, the DB subnet has no internet route, and MySQL requires TLS. I reached the App VM only through the Web VM as a jump host and removed the copied key afterward.
Secrets: the database password and JWT secret live in a .env file on the App VM, kept out of the repository and redacted in my evidence. Azure Key Vault would be the next step for a real production setup.
Monitoring: Log Analytics workspace with diagnostic settings on the load balancers and MySQL.
Backup: the MySQL flexible server uses automated backups with 7-day retention. High availability is not enabled on the Burstable tier.

---

# Submission Instructions

- Add all required screenshots and links in your submission
- Do not expose passwords, keys, connection strings, or subscription IDs

---

# Completion Checklist

- [x] Task 1: Architecture diagram and assumptions documented (Screenshots 1–2)
- [x] Task 2: Network foundation created with isolated tiers (Screenshots 3–5)
- [x] Task 3: Least-privilege security and secret management configured (Screenshots 6–7)
- [x] Task 4: Presentation tier deployed (Screenshots 8–9)
- [x] Task 5: Application tier deployed privately (Screenshots 10–12)
- [x] Task 6: Managed database tier deployed privately (Screenshots 13–15)
- [x] Task 7: Public entry, internal routing, and monitoring configured (Screenshots 16–18)
- [x] Task 8: End-to-end validation and availability test completed (Screenshots 19–22, Public Endpoint, Notes)
- [x] No sensitive data exposed

---

## 📌 About DMI & CloudAdvisory

DevOps Micro Internship (DMI) is a project-based DevOps program run by Pravin Mishra (The CloudAdvisory) focused on real-world execution, systems thinking, and career readiness.

It helps learners build strong DevOps foundations with hands-on experience.

---

## 📌 Resources

- 🌐 DMI Official Website: https://dmi.pravinmishra.com?utm_source=github&utm_medium=readme  
- 🎓 University: https://university.pravinmishra.com?utm_source=github&utm_medium=readme  
- 💬 Discord Community: https://discord.pravinmishra.com?utm_source=github&utm_medium=readme  
- 📝 Blog: https://dmi.pravinmishra.com/blog?utm_source=github&utm_medium=readme  
- ▶️ YouTube Playlist: https://www.youtube.com/playlist?list=PLFeSNDtI4Cho  
- 🔗 Pravin Mishra (LinkedIn): https://www.linkedin.com/in/pravin-mishra-aws-trainer/  
- 🏢 CloudAdvisory (LinkedIn): https://www.linkedin.com/company/thecloudadvisory/

---

*This submission is part of DevOps Micro Internship (DMI) — Agentic AI Track.*
