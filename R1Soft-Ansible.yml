---
- name: R1soft agent installation on new servers
  hosts: r1soft
  connection: ssh
  tasks:

# Copy repo file from ansible master to remote hosts
    - name: Create repo file
      when: ansible_os_family == "RedHat"
      copy:
        src: /etc/yum.repos.d/r1soft.repo
        dest: /etc/yum.repos.d/r1soft.repo
        owner: root
        group: root

# Install r1soft agent on the remote hosts "RedHat"
    - name: Install Agent
      when: ansible_os_family == "RedHat"
      package:
        name: serverbackup-enterprise-agent
        state: installed

# Add the Server's key to the Agent's configuration
    - name: Get key from server
      when: ansible_os_family == "RedHat"
      command: "r1soft-setup --get-key http://104.248.112.31:8080"


# Restart the cdp-agent on CentOS6 distribution
    - name: Restart R1soft Agent
      when: (ansible_distribution == "CentOS" and ansible_distribution_major_version == "6")
      service:
        name: cdp-agent
        state: restarted


# Restart the cdp-agent on CentOS7 distribution
    - name: Restart R1soft agent
      when: (ansible_distribution == "Centos" and ansible_distribution_major_version == "7")
      systemd:
        name: sbm-agent
        state: restarted

# Modifying R1soft repository on Ubuntu
    - name: Install R1soft on Ubuntu
      when: ansible_distribution == "Ubuntu"
      command: "echo deb http://repo.r1soft.com/apt stable main >> /etc/apt/sources.list"

# GPG sing and verify package
    - name: Next command
      when: ansible_distribution == "Ubuntu"
      uri:
        url: http://repo.r1soft.com/r1soft.asc

    - name: Next command
      when: ansible_distribution == "Ubuntu"
      command: "apt-key add r1soft.asc"

# Update the package
    - name: Next command
      when: ansible_distribution == "Ubuntu"
      command: "apt-get update"
# Install R1soft agent
    - name: Install agent
      when: ansible_distribution == "Ubuntu"
      apt:
        name: "r1soft-cdp-enterprise-agent"
        state: present

# Getting the key from R1soft server
    - name: Get Key From Server
      command: "r1soft-setup --get-key http://104.248.112.31:8080"
