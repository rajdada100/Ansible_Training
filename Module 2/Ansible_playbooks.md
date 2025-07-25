# 🧩 Module 2: Ansible Playbooks

## 🎯 Objective
Learn to write structured automation scripts using YAML — called playbooks — to automate multi-step tasks across multiple hosts.

---

## 🧠 What is a Playbook?

A playbook is a YAML file that:

- Describes what tasks to run on which hosts
- Uses Ansible modules
- Supports variables, conditionals, loops, handlers, roles, etc.
- Is idempotent — running the same playbook multiple times won’t change anything unless required

---

## 🧱 Basic Anatomy of a Playbook

Here’s a simple playbook to install Apache:

```yaml
# install_apache.yml
- name: Install Apache Web Server
  hosts: webservers
  become: yes

  tasks:
    - name: Install httpd
      yum:
        name: httpd
        state: present

    - name: Start and enable httpd
      service:
        name: httpd
        state: started
        enabled: yes
```

---

## 🔑 Key Components Explained

| Component   | Purpose                                 |
| ----------- | --------------------------------------- |
| `- name:`   | Description of the play                 |
| `hosts:`    | Target group/hosts from inventory       |
| `become:`   | Use sudo (for tasks needing root)       |
| `tasks:`    | List of actions to perform              |
| `yum:` / `service:` | Ansible modules used to perform tasks |

---

## ▶️ How to Run a Playbook

```bash
ansible-playbook -i /path/to/hosts install_apache.yml
```

---

## 🧪 Lab: Try This

### ✅ Step 1: Create inventory group

Update your inventory file to have:

```ini
[webservers]
e3paa01spcmon02
e3pab01spcmon03
```

---

### ✅ Step 2: Write a playbook

Save the following as `playbook_demo.yml`:

```yaml
- name: Practice Playbook - System Info
  hosts: webservers
  become: no

  tasks:
    - name: Show hostname
      shell: hostname

    - name: Show disk space
      shell: df -h
```

---

### ✅ Step 3: Run it

```bash
ansible-playbook -i /path/to/hosts playbook_demo.yml
```