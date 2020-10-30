This Playbook will install R1soft server and install R1soft agent on Centos7

The first thing you will need to do is install the r1 server. To do this you will follow every step as I list them for you.

Step: 1

vi /etc/yum.repos.d/r1soft.repo 
[r1soft]
name=R1Soft Repository Server
baseurl=http://repo.r1soft.com/yum/stable/$basearch/
enabled=1
gpgcheck=0

sudo yum install r1soft-cdp-enterprise-server -y

Step: 2

Copy ssh key from the R1soft server to the remote hosts 




Step 3 Add hosts to the inventory file

cat hosts
[r1soft]
youripaddress



Step 4 Run the main.yml playbook  (Nothing in this file needs to be change)

git clone https://github.com/billymartin910/r1-server.git
cd r1soft-ansible
ansible-playbook -i hosts r1soft.yml


Congratulations, The R1-server is setup and now we will continue onto the final touches to install the R1Soft-Agent




Step 5: Inside the file R1Soft-Ansible.yml file you are going to edit the following 2 lines. All you're doing is putting the IP address of your R1-SERVER and port number IF you changed the port number 

  
  
  - name: Get key from server
      when: ansible_os_family == "RedHat"
      command: "r1soft-setup --get-key http://INSERT-IP-HERE"
      
      

 - name: Get Key From Server
      command: "r1soft-setup --get-key http://INSERT-IP-HERE"





Step 6: Run the playbook!

ansible-playbook  R1Soft-Ansible.yml -b













