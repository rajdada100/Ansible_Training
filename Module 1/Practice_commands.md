# 🧩 Command Structure

**Example:**

```bash
ansible all -i /path/to/hosts -m shell -a "uptime"
```

---

### 🔹 ansible
This is the command-line tool used to run ad-hoc commands on remote hosts.

### 🔹 all
This tells Ansible which hosts or group of hosts to run the command on.

| Target         | Meaning                              |
| -------------- | ------------------------------------ |
| `all`          | All hosts in your inventory          |
| `webservers`   | A group defined in your inventory    |
| `e3rab01spcora01` | A specific host                   |

➡️ You can replace `all` with any host/group name from your inventory.

### 🔹 -i /path/to/hosts
This option specifies the inventory file. It tells Ansible where to find the list of target hosts.

**Example:**
```bash
-i /saba/sabatools/local/dba/scripts/ANSIBLE/INVENTORY/hosts
```

### 🔹 -m
`-m` stands for "module". This tells Ansible what kind of task to perform.

| Module   | Purpose                                      |
| -------- | -------------------------------------------- |
| ping     | Test connectivity                            |
| shell    | Run shell commands                           |
| command  | Run basic Linux commands (no shell features) |
| copy     | Copy files                                   |
| yum      | Install packages (Red Hat-based)             |
| apt      | Install packages (Debian-based)              |
| file     | Create/delete files or directories           |
| service  | Start/stop services                          |

### 🔹 -a
`-a` stands for "arguments". You pass module-specific parameters here.

**Examples:**

- For shell module:  
  ```bash
  -a "uptime"
  ```
- For copy module:  
  ```bash
  -a "src=/etc/hosts dest=/tmp/hosts"
  ```
- For yum module:  
  ```bash
  -a "name=git state=present"
  ```

🧪 **Putting it Together**

---

✅ **Example 1: Ping all hosts**

```bash
ansible all -i /path/to/hosts -m ping
```
*Runs the ping module on all hosts.*

> No `-a` needed because ping has no arguments.

---

✅ **Example 2: Run a shell command**

```bash
ansible all -i /path/to/hosts -m shell -a "df -h"
```
*Runs the shell module to execute `df -h` on all hosts.*