<<<<<<< HEAD
# Installing R1soft agent on CentOS6, CentOS7 and Ubuntu
This ansible playbook will install R1soft agent. Please follow the steps

Step 1 Create r1soft server


Step 2 Copy ssh key from the R1soft server to the remote hosts
ssh-copy-id


Step 3 Add hosts to the inventory file
```
cat hosts
[r1soft]
youripaddress

```

Step 4 Run the playbook 

```
git clone https://github.com/farkhodsadykov/r1soft-ansible
cd r1soft-ansible
ansible-playbook -i hosts r1soft.yml
```


## Installing R1soft agent on Windows
This ansible playbook will install R1soft agent on Windows machines. Please follow the steps

Step 1 Install python on windows machines

Step3 Install winrm on ansible master
```
pip install pywinrm
```

Step 2 Specify the hosts inside inventory file
cat hosts
```
[windows]
54.242.150.159
[windows:vars]
ansible_user=Administrator
ansible_password=r!iE9G8IuOex?8lHlKs=?eEflUk?tnIK
ansible_connection=winrm
ansible_port=5986
ansible_winrm_server_cert_validation=ignore
```

Step 3 Run the playbook 

```
ansible-playbook r1soft_windows.yml
```
=======
# AnsibleProject2-R1Soft
>>>>>>> 5b139536621b27d8a4ec635121ae8d7975cef49d
