# ✅ Module 2 – Intermediate Playbook Features

Welcome to Module 2! This guide covers essential intermediate features in Ansible playbooks.

---

## 1. Variables

Define variables inside playbooks or load them from files.

<details>
<summary>Example: Inline Variables</summary>

```yaml
- name: Demo with variables
    hosts: all
    vars:
        greeting: "Hello from Ansible"
    tasks:
        - name: Show greeting
            debug:
                msg: "{{ greeting }}"
```
</details>

---

## 2. Conditionals (`when`)

Run tasks only when certain conditions are true.

<details>
<summary>Example: Run Only for Oracle Users</summary>

```yaml
- name: Run only for oracle users
    hosts: all
    tasks:
        - name: Show current user
            shell: whoami
            register: user_out

        - name: Run only if oracle user
            debug:
                msg: "Hello Oracle"
            when: user_out.stdout == "oracle"
```
</details>

---

## 3. Loops

Run tasks multiple times with different values.

<details>
<summary>Example: Creating Multiple Directories</summary>

```yaml
- name: Loop demo
    hosts: all
    tasks:
        - name: Create multiple directories
            file:
                path: "/tmp/{{ item }}"
                state: directory
            loop:
                - dir1
                - dir2
                - dir3
```
</details>

---

## 4. Facts (`gather_facts`)

Facts are system data automatically collected by Ansible.
It automatically collects detailed information (facts) about a host before running tasks—OS, IP, memory, CPU, network interfaces, etc.
Facts are stored in ansible_facts and can be used in playbooks.
<details>
<summary>Example: Display Hostname from Facts</summary>

```yaml
- name: Display hostname from facts
    hosts: all
    gather_facts: yes
    tasks:
        - name: Show OS and hostname
            debug:
                msg: "You are on {{ ansible_hostname }} running {{ ansible_distribution }}"
```
</details>

---

## 5. Handlers

Handlers run tasks only when notified, such as restarting services after a config change.

<details>
<summary>Example: Using Handlers</summary>

```yaml
- name: Handlers demo
    hosts: all
    tasks:
        - name: Simulate config change
            copy:
                content: "dummy"
                dest: /tmp/test.conf
            notify: Restart Service

    handlers:
        - name: Restart Service
            shell: echo "Service restarted"
```
</details>

---

> **Tip:** Use these features to write more powerful, flexible, and maintainable Ansible playbooks!
