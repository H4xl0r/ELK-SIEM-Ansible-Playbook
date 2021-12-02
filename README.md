# ELK-SIEM-Ansible-Playbook
Ansible Playbook to install the ELK Stack.

Requirements:
2x Ubuntu VMs.
  * 1x Ubuntu VM for Ansible VM (2GB Ram | 2CPUs | 20GB)(1.1)
  * 1x Ubuntu VM for ELK SIEM (4GB Ram | 4CPUs | 40GB)(1.2)


#################

Install ansible on Ubuntu VM (1.1)
  * sudo apt update
  * sudo apt upgrade -y 
  * sudo apt install software-properties-common -y
  * sudo add-apt-repository --yes --update ppa:ansible/ansible
  * sudo apt update
  * sudo sudo apt install ansible
  * 
  * edit /etc/ansible/hosts and add:
    ```
    [local]
    localhost

    [elkservers]
    192.168.2.6 ansible_user=sshuser
    ```
    Change the IP to your IP of ELK SIEM VM (1.2) ! <br>
    Change the SSH-User to your SSH-User of ELK SIEM VM (1.2) !
    
  * then run:
    * ssh-keygen
    * ssh-copy-id -i ~/.ssh/id_rsa.pub sshuser@192.168.2.6 
      * Change the sshuser to your SSH-User of ELK SIEM VM (1.2) and change the Ip to your Ip Of ELK SIEM VM (1.2)
    
###############

Install ELK SIEM using Ansible
  1. Clone this repo into your / on your ansible VM (1.1)
     * `git clone https://github.com/H4xl0r/ELK-SIEM-Ansible-Playbook`
  2. Change the Ip in the site.yml file to your ELK SIEM VM IP addresses (1.2) 
  3. Run the Playbook site.yml
      * `ansible-playbook site.yml -K`
        * Enter the password for the SSH-User of ELK SIEM VM (1.2)
  4) Sign into kibana at http://yoursiemip:5601

################

To autostart the Services (reboot ELK SIEM VM (1.2))
``` sudo /bin/systemctl daemon-reload
sudo /bin/systemctl enable kibana.service
sudo /bin/systemctl enable logstash.service
sudo /bin/systemctl enable elasticsearch.service
sudo /bin/systemctl enable filebeat.service ```
