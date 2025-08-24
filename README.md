# Ansible TLS Remediation Playbook

This playbook automates the process of remediating the TLS vulnerability in Apache HTTP Server by updating the `https.conf` file. It is designed to be run through Ansible Automation Platform (AAP) or a standard Ansible CLI.

---

### Purpose

This script addresses the security risk associated with older TLS protocols (like TLSv1.0 and TLSv1.1) by ensuring that the web server only uses the stronger and more modern **TLSv1.2** protocol. By doing this, it improves the overall security posture of the host by preventing connections over known vulnerable protocols.

---

### Usage

This playbook targets a specific host group named **`TLS_hosts`**. Before running the playbook, ensure that the servers you intend to remediate are added to this group in your inventory.

**Command Line:**
```
ansible-playbook -i <your_inventory_file> tls-remediation.yml --limit TLS_hosts
```

---

### Task Breakdown

* **stop http service:** Stops the `httpd` service to prevent any issues with concurrent file writes during the configuration update.
* **Replacing SSLProtocol line in http.conf file:** This task uses the `lineinfile` module to search for any line starting with `SSLProtocol` and replaces it with the updated configuration. The **`backrefs`** parameter ensures the replacement happens correctly.
* **start http service:** Restarts the `httpd` service to apply the new, more secure configuration.

---

### Backout Script

This repository includes a corresponding backout script designed to reverse the changes made by this playbook. Having a backout plan is a critical part of a professional remediation process and ensures you can quickly revert changes if any issues arise.

---

### Notes

* **Service Management:** The playbook gracefully stops and starts the `httpd` service to ensure the new configuration takes effect without manual intervention.
* **File Backups:** The `backup: true` parameter ensures a backup of the original `https.conf` file is created before any changes are made, allowing for easy rollback if needed.
* **AAP Integration:** This playbook is an ideal candidate for integration into a job template within AAP, allowing for easy, centralized, and repeatable remediation across your infrastructure.
