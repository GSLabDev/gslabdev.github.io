---
layout: project
title:  "Ansible community contribution"
date:   2020-06-10 16:54:46
author: Masarrat Mahedvi, Pallavi Joshi, Sakar Mehra, Suyeb Ansari, Pallavi Chaudhari
categories:
- project
img: ansible-community-contribution.png
thumb: thumb02.jpg
carousel:
- ansible-community-contribution.png
client: https://github.com/ansible-collections/community.windows Pull requests - 90, 112, 127, 131 and https://github.com/ansible-collections/azure Pull request - 248, 254
---

#### Ansible Community Contribution
Ansible is an open-source software provisioning, configuration management, and application-deployment tool. It has different modules for integration. Following are the features that we have developed in different ansible module.

Windows Ansible Collection:
1. winZip Module: Added a new feature of password parameter which unarchive password protected zip files.
2. win_dns_record Module: Added a new feature of SRV dns record to an existing win_dns_record module.
3. win_firewall_rule  Module: Added a new feature that allows the user to enable or disable all the firewall rules in a particular group.
4. win_dns_record Module: Added a new feature of NS DNS record to an existing win_dns_record module.

Azure Ansible Collection:
1. azure_rm_backupazurevm Module: Added a new features of backup Azure VM for enabling protection, trigger on-demand backup, modify backup, top protection but retain existing data, Stop protection and delete data.
2. azure_rm_backupazurevm_info Module: Added a new feature to get detail information about Azure VM backups.
3. azure_rm_recoveryservicesvault Module: Added a new features of Azure Recovery Services Vault for create, update and delete azure recovery services vault.
4. azure_rm_recoveryservicesvault_info Module: Added a new feature to get detail information about Azure Recovery Services Vault.

#### Our Contributions
Feature implementation in different Ansible Collections and Ansible Module.