# Ansible Project for Windows Laptops

This Ansible project installs and configures Sysmon and Splunk Forwarder on Windows laptops. The laptops are DHCP clients, and their IP addresses range from 10.83.100.100 to 10.83.100.200.

---

## Table of Contents

- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [How to Run](#how-to-run)

---

## Project Structure

```tree
├───ansible-main
│   │   ansible.cfg
│   │   discovered_inventory.ini
│   │   inventory.ini
│   │
│   ├───group_vars
│   │       all.yml
│   │
│   ├───host_vars
│   ├───playbooks
│   │       all.yml
│   │       discover_hosts.yml
│   │       splunkforwarder.yml
│   │       sysmon.yml
│   │
│   ├───roles
│   │   ├───discover_hosts
│   │   │   ├───tasks
│   │   │   │       main.yml
│   │   │   │
│   │   │   └───templates
│   │   │           hosts.j2
│   │   │
│   │   ├───splunkforwarder
│   │   │   └───tasks
│   │   │           configure.yml
│   │   │           install.yml
│   │   │           main.yml
│   │   │
│   │   └───sysmon
│   │       └───tasks
│   │               configure.yml
│   │               install.yml
│   │               main.yml
│   │
│   └───templates
└───software
    ├───Splunk
    │       inputs.conf
    │       outputs.conf
    │       splunkforwarder-9.0.4-de405f4a7979-x64-release.msi
    │
    └───Sysmon
            Sysmon.exe
            sysmonconfig.xml
```

---

## Prerequisites

1. Install [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) on your local machine.
2. Install the [Windows Remote Management (WinRM)](https://docs.ansible.com/ansible/latest/user_guide/windows_winrm.html) plugin for Ansible.
3. Make sure your Windows username and password are specified in the `inventory.ini` file.

---

## How to Run

1. Open a terminal or command prompt and navigate to the `ansible-main` directory.
2. Run the following command:

```sh
ansible-playbook -i inventory.ini playbooks/all.yml
```

This command will execute the entire project: discover the Windows hosts, install and configure Sysmon, and install and configure the Splunk Forwarder on each discovered host using the provided username and password.