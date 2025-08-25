# Linux TLS Hardening & Remediation

This repository contains a collection of Ansible playbooks and scripts designed to audit, remediate, and back out TLS (Transport Layer Security) configurations on Linux systems. This project automates a critical security function, ensuring consistency and compliance with modern hardening standards across a variety of web servers.

### Key Features

* **All-in-One Remediation:** The `tls_allInOne.yml` playbook is a powerful, consolidated tool that can remediate TLS configurations for **Apache, Tomcat, and NGINX** with a single command, dramatically improving efficiency.

* **Modular Playbooks:** The repository also includes individual playbooks for specific applications (`tls_httpd_remediation.yml`, `tls_tomcat_remediation.yml`, `tls_nginx_remediation.yml`) for more targeted use cases.

* **Built-in Backout Functionality:** Separate playbooks (`tls_httpd_BACKOUT.yml` and `tls_tomcat_BACKOUT.yml`) leverage Ansible's backup functionality to restore the previous configurations, allowing for safe and rapid rollbacks if needed.

* **Proactive Security:** The playbooks enforce strong security best practices, such as enabling only modern TLS protocols (`TLSv1.2` and `TLSv1.3`) and managing cipher preferences.

### Purpose

Modern security posture requires robust and consistently applied configurations. This project automates the manual, time-consuming tasks of TLS hardening, ensuring that systems are protected against common vulnerabilities related to misconfigured encryption protocols. It's a proactive approach to vulnerability management that improves efficiency and reduces human error.

### File Breakdown

* `tls_allInOne.yml`: A single, versatile playbook that handles TLS remediation for Apache, Tomcat, and NGINX based on a provided variable. **(Note: This playbook is still in active development and may contain unfinished features.)**

* `tls_httpd_remediation.yml`: Specifically remediates TLS configurations on Apache web servers.

* `tls_tomcat_remediation.yml`: Specifically remediates TLS configurations on Tomcat application servers.

* `tls_nginx_remediation.yml`: Specifically remediates TLS configurations on NGINX web servers.

* `tls_httpd_BACKOUT.yml`: Restores the last known Apache configuration from an Ansible backup.

* `tls_tomcat_BACKOUT.yml`: Restores the last known Tomcat configuration from an Ansible backup.

* `testDynamicTlsRem.yml`: An in-progress playbook for dynamically finding and managing TLS files.

### Technologies

* **Ansible:** The automation engine used to manage and deploy all configurations.

* **YAML:** The language for defining all Ansible playbooks.

* **Linux:** Specifically targeting RHEL, Ubuntu, and CentOS.

### Status

This repository is an active work-in-progress. The code is under development and may contain tests or unfinished modules. It is a live project that showcases my passion for building practical, automated security solutions.

### Usage

1.  Clone the repository to your local machine:

    ```
    git clone [https://github.com/scottyplex/LinuxTLS.git](https://github.com/scottyplex/LinuxTLS.git)
    
    ```

2.  Navigate to the project directory:

    ```
    cd LinuxTLS
    
    ```

3.  Run the appropriate playbook with Ansible to target your hosts. For the all-in-one playbook, you will need to specify the web application via the command line or a variable file.
