# 📘 Module 1: What Is Ansible?

Ansible is an **open-source automation tool** used for:
- Configuration management
- Application deployment
- Task automation
- IT orchestration

It is simple, agentless, and powerful — making it ideal for managing infrastructure at scale.

---

## 🔑 Key Features of Ansible

- **Agentless**: No software needed on target nodes.
- **Simple YAML Syntax**: Uses YAML (Yet Another Markup Language) for playbooks.
- **Idempotent**: Ensures repeated runs don’t cause unintended side effects.
- **Extensible**: Use thousands of built-in modules or write your own.
- **Secure**: Uses SSH for communication and doesn’t require root login.

---

## 🧠 How Ansible Works

Ansible uses a **control node** (where Ansible is installed) to connect to **managed nodes** (the target machines). It communicates over SSH (or WinRM for Windows), pushes small programs called **modules**, runs them remotely, and removes them after execution.


Control Node (Ansible installed)
|
| SSH/WinRM
▼
Managed Nodes


---

## ⚙️ What Is a Module in Ansible?

Modules are small programs written in Python (or other languages) that:
- Are pushed to the target machine
- Run specific tasks (e.g., create a user, install a package)
- Return JSON data back to Ansible

Modules are **idempotent**, meaning they only change the system if needed.

---

## 🧪 Example: Using the `ping` Module

You can use ad-hoc commands to run a module without writing a full playbook.

```bash
ansible webservers -m ping

This checks connectivity with all hosts in the webservers group using the ping module.

🛠️ Example: Using the service Module
ansible webservers -m service -a "name=httpd state=started"
Starts the Apache (httpd) service on all servers in the webservers group.

📦 Playbook Example Using a Module
- name: Ensure Apache is running
  hosts: webservers
  become: true
  tasks:
    - name: Start Apache service
      service:
        name: httpd
        state: started


## 📎 Summary

| Term           | Meaning                                                |
|----------------|--------------------------------------------------------|
| Control Node   | System where Ansible is installed                      |
| Managed Node   | Remote systems managed via SSH                         |
| Module         | Unit of work (e.g., user, service, package)            |
| Idempotent     | Safe to run repeatedly without unwanted side effects   |
| YAML           | Format for writing playbooks (human-readable syntax)   |





