# ELK-SIEM-Ansible-Playbook
Ansible Playbook to install the ELK Stack. To use this playbook follow these steps:

Requirements:
1) 2 Ubuntu VMs.
  1.1) 1 for Absible VM (2GB Ram | 2CPUs | 20GB)
  1.2) 1 for ELK SIEM (4GB Ram | 4CPUs | 40GB)


#################

Install ansible on Ubuntu VM (1.1)
  sudo apt update
  sudo apt upgrade -y 
  sudo apt install software-properties-common -y
  sudo add-apt-repository --yes --update ppa:ansible/ansible
  sudo apt update
  sudo sudo apt install ansible
  
###############

Install ELK SIEM using Ansible

1) Clone this repo into your / on your ansible VM (1.1)
3) change the ip addresses from 192.168.3.6 to your ELK SIEM VM IP addresses (1.2) in the site.yml file
4) Run the Playbook site.yml ( ansible-playbook site.yml) ## This will take a while, get a coffee.
5) Sign into kibana at http://yoursiemip:5601
6)Next, get some data in your siem.

