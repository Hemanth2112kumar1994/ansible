# Ansible Practice - Role-Based Automation

## Overview
This repository contains an Ansible setup for automating the installation and configuration of packages (Git, HTTPD, Telnet) along with system monitoring on an EC2 instance. The playbook follows a role-based approach for modular automation.

## Steps Taken

### 1. **Project Setup**
- Created a directory structure for Ansible roles:
  ```bash
  mkdir -p Webserver/roles/{install-git,tasks,install-httpd,tasks,install-telnet,tasks,system,tasks}
  ```
- Initialized the repository and set up GitHub integration:
  ```bash
  git init
  git branch -m main
  git remote add origin https://github.com/Hemanth2112kumar1994/ansible.git
  ```

### 2. **Inventory Configuration**
- Created an `hosts` file with the target EC2 instance details.

### 3. **Playbook Creation (`site.yml`)**
- Defined a main playbook to include all roles:
  ```yaml
  ---
  - name: Configure Webserver
    hosts: 172.31.83.93
    become: yes
    roles:
      - install-git
      - install-httpd
      - install-telnet
      - system
  ```

### 4. **Role Implementations**
#### **install-git Role**
  - Installed Git
  - Checked if Git is running
  - Displayed system metrics

#### **install-httpd Role**
  - Installed Apache HTTPD service
  - Started and enabled the service

#### **install-telnet Role**
  - Installed Telnet service

#### **system Role**
  - Gathered system metrics such as uptime, CPU, and memory usage.
  - Used shell commands to fetch data.

### 5. **Execution of Playbook**
- Ran the Ansible playbook using:
  ```bash
  ansible-playbook -i hosts site.yml
  ```
- Debugged errors related to indentation, role structure, and missing files.

### 6. **Git Operations & Fixes**
- Encountered errors while pushing to GitHub:
  - **Fixed missing branch reference** by creating a `main` branch:
    ```bash
    git checkout -b main
    ```
  - **Resolved update rejection** by pulling remote changes first:
    ```bash
    git pull --rebase origin main
    ```
  - Successfully pushed to GitHub:
    ```bash
    git push -u origin main
    ```

## Outcome
- Successfully automated installation and configuration using Ansible roles.
- Troubleshot and fixed errors related to role execution and Git operations.

## Reference Documentation
- [Ansible Roles](https://docs.ansible.com/ansible/latest/user_guide/playbooks_reuse_roles.html)
- [Git Troubleshooting](https://git-scm.com/docs/git-push)
- [AWS EC2 Ansible Setup](https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html)

---

This practice helped refine role-based Ansible automation and Git workflow for real-world scenarios.

