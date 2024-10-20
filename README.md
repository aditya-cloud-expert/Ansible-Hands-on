# Ansible Quickstart Guide

## TL:DR for installation, configuration and Running 

## Install 
```
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt install ansible
```

## Configure
```
ansible-inventory --list -y

[servers]
server1 ansible_host=<Public IP>
server2 ansible_host=<Public IP>
server3 ansible_host=<Public IP>

[all:vars]
ansible_python_interpreter=/usr/bin/python3
ansible_user=ubuntu
ansible_ssh_private_key_file=<file>

```

## RUN
```
ansible all -a "df -h" -u ubuntu
ansible servers -a "uptime" -u ubuntu

ansible all -m ping -u ubuntu
ansible-playbook -i inventory.ini playbook.yaml
```

## Simple Playbook

```
---
- name: Get the current date from all servers
  hosts: all
  gather_facts: false
  tasks:
    - name: Show date from all machines
      command: date
      register: date_output

    - name: Display the date
      debug:
        var: date_output.stdout
```



# Ansible Zero to Hero

Day 1: Introduction to Ansible and Getting Started

- Overview of Ansible: What is Ansible, its advantages, and why use it?
- Comparison with Shell and Python scripting for automation.
- Installing Ansible on different platforms.
- IDE(VS Code) and Plugin configuration.

Day 2: Ansible Adhoc Commands

- Passwordless Authentication
- Ansible Inventory 
- Understanding Adhoc commands and their usage.
- Examples of common Adhoc commands for system management tasks.
- Exploring the power of Adhoc commands for quick tasks.

Day 3: Writing Your First Ansible Playbook

- Understanding YAML basics and Ansible playbook structure.
- Introduction to Ansible structure: Playbook, Play, Modules, Tasks and Collections.
- Hands-on: Writing a playbook to install apache2 and deploy a static app on aws.

Day 4: Understanding Ansible Roles

- What are Ansible roles and why use them?
- Exploring the folder structure of Ansible roles.
- Comparing roles with playbooks and understanding their advantages.
- Hands-on: Creating a simple role and using it in a playbook.

Day 5: Deep Dive into Ansible Roles with Demo

- Ansible Galaxy - Exploring pre-built Ansible roles.
- Ansible Galaxy - Importing and Installing roles.
- DEMO: Advanced usage of Ansible roles with a practical example project.
- Best practices for organizing roles and playbook structure.

Day 6: Ansible Variables and Precedence

- Create AWS Resources using Ansible (Collections)
- Understanding Ansible variables and their scope with an example
- Jinja2 Templating - Utilizing advanced templating features
- Variable precedence: How Ansible resolves conflicts between different variable sources.
- Hands-on: Using variables in playbooks and roles.

Day 7: Ansible Conditionals and Loops

- Using conditionals in Ansible to control task execution.
- Implementing loops for repetitive tasks.
- Practical examples of conditionals and loops in playbooks.

Day 8: Error Handling in Ansible

- Dealing with errors and failures in Ansible playbooks.
- Error handling techniques and best practices.
- Demonstrating error handling in practical scenarios.

Day 9: Ansible Vault for Security

- Understanding Ansible Vault and its role in securing sensitive data.
- Encrypting and decrypting files using Ansible Vault.
- Best practices for managing secrets and sensitive data in Ansible.

Day 10: Policy as Code

Day 11: Network Automation using Ansible

Day 12: Ansible Tower Deep Dive

- Understanding Ansible Tower
- Comparision with Ansible command line and adhoc commands
- RBAC and Security with Ansible Tower

Day 13: Advanced Ansible Project

- Terraform + Ansible Project

Day 14: Ansible Interview Questions
