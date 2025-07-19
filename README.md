# Project & Portfolio II: Virtualized-webstack-blueprint

This project reflects the work I completed at Full Sail University, where I designed and implemented a multi-server network solution with web, database, and application services using virtualization, cloud concepts, and strong security practices.

---

## 🎯 Course Objectives

In this course, I:

✅ Applied knowledge of application servers, system scripting, cloud networking, and virtualization  
✅ Built a networked, multi-server environment using Linux systems  
✅ Designed and deployed a website solution with WordPress and Ghost  
✅ Configured web servers, reverse proxies, and databases  
✅ Documented configurations and created audit reports  
✅ Applied security best practices and defense-in-depth strategies

---

## 🛠️ Technologies & Tools Used

- **Linux OS:** Ubuntu, CentOS, Rocky Linux
- **Web Servers:** Apache2, NginX
- **Scripting:** Bash, Shell commands
- **Virtualization:** VMware Workstation, Docker
- **CMS Platforms:** WordPress, Ghost
- **Database:** MySQL
- **Cloud Concepts:** Principles from my LinkedIn Learning courses
- **Security Tools:** Shield Security Plugin for WordPress, SELinux configurations
- **Networking Tools:** SSH, Firewall management (ufw, firewalld)
- **Other:** Git, Nano Editor, EPEL Repos

---

## 🚀 Weekly Breakdown & Project Steps

Below is how I structured my project over the four weeks, combining my syllabus tasks and technical solutions documented in my milestones.

---

### Week 1 – Security & Initial Setup

- Identified vulnerabilities in web systems for a small business use case
- Installed and configured:
  - CentOS 7
  - Rocky Linux 8
  - Ubuntu 20.04 LTS
- Enabled SSH for remote management across virtual machines
- Applied initial system updates and security configurations:
  - SELinux configurations
  - Firewall management (ufw, firewalld)

**Courses supporting this week:**

- Learning Virtualization

---

### Week 2 – Scripting & IT Audit Documentation

- Practiced scripting for:
  - Updating systems automatically
  - Installing essential tools like Nano, Git
- Created IT audit documentation, including:
  - Network topology diagrams
  - Detailed command references
  - Audit trails for server builds

**Learnings from:**

- Learning Cloud Computing: Core Concepts

---

### Week 3 – System Builds & Web Deployment

#### Ghost Blog Deployment

- Installed Docker on CentOS
- Pulled the Ghost container:

    ```bash
    docker run -d --name ghost -p 0000:0000 -e url=http://10.10.xxx.xx:0000 ghost
    ```

- Verified Ghost container:

    ```bash
    docker ps
    ```

---

#### NginX Reverse Proxy

- Deployed NginX on Rocky Linux
- Configured NginX to act as a reverse proxy for Ghost:

    ```nginx
    location /blog {
        proxy_pass http://10.10.xxx.xx:xxxx;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_read_timeout 900;
    }
    ```

- Commands used:

    ```bash
    systemctl start nginx
    systemctl enable nginx
    systemctl reload nginx
    ```

---

## Week 4 – WordPress Deployment & Security Hardening

### 🛠️ LAMP Stack Installation

**Installed Apache2:**

```bash
sudo apt install apache2
```

**Installed MySQL Server:**

```bash
sudo apt install mysql-server
```

**Installed PHP and required libraries:**

```bash
sudo apt install php libapache2-mod-php php-mysql
```

---

### 🌐 WordPress Setup

**Created MySQL DB and user:**

```sql
CREATE DATABASE add;
CREATE USER 'addusr'@'localhost' IDENTIFIED BY 'add';
GRANT ALL ON Wadd.* TO 'WpUsr'@'localhost';
FLUSH PRIVILEGES;
```

**Downloaded WordPress via Git:**

```bash
sudo git clone https://github.com/WordPress/WordPress /var/www/html/
```

**Configured WordPress with wp-config.php details:**

- DB Name: `add`
- User: `add`
- Password: `add`

---

### 🔒 WordPress Security

**Hardened file permissions:**

```bash
sudo find /var/www/html/ -type f -exec chmod 644 {} \;
sudo find /var/www/html/ -type d -exec chmod 750 {} \;
```

**Moved wp-config.php for security:**

```bash
sudo mv wp-config.php /var/www/
sudo chmod 400 /var/www/wp-config.php
```

**Installed Shield Security plugin in WordPress:**

- Enabled firewall protection
- Activated 2FA
- Configured brute force protection

**Created `.htaccess` rules to protect wp-includes:**

```apache
<IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteBase /
    RewriteRule ^wp-admin/includes/ - [F,L]
    RewriteRule !^wp-includes/ - [S=3]
    RewriteRule ^wp-includes/[^/]+\.php$ - [F,L]
    RewriteRule ^wp-includes/js/tinymce/langs/.+\.php - [F,L]
    RewriteRule ^wp-includes/theme-compat/ - [F,L]
</IfModule>
```

---

### 📚 Courses Supporting This Week

- WordPress 5 Essential Training
- Getting Your Website Online

---

## 🔐 Security Highlights

- Implemented Defense-in-Depth:
  - System-level hardening (SELinux, firewalls)
  - Web server configurations
  - WordPress plugin protection
  - File permissions and ownership
- Performed vulnerability testing and validation
- Created a rollback plan with VM snapshots
- Documented findings and resolutions

---

## 🎓 LinkedIn Certifications Earned

During this course, I completed:

- Learning Cloud Computing: Core Concepts
- Learning Virtualization
- Getting Your Website Online
- WordPress 5 Essential Training

---

## 💡 Lessons Learned

> “This course taught me how interconnected every layer of technology is—from virtualization, to cloud networking, to application security.  
> I gained valuable hands-on experience in deploying multi-server environments and learned the importance of audit documentation, security hardening, and proactive troubleshooting.” – Daphnie Bruno
