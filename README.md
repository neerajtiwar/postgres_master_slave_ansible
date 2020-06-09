Role Name
=========

This role coule be used for setting up postgres master slave setup with one master and multiple slaves.

Requirements
------------
Ansibel versio > 2.4

Password less ssh between slave --> master

Role Variables
--------------
Change variables according to your infra in vars/main.yml

Define http_proxy and https_proxy variables if you are behind corporate proxy

Dependencies
------------

This role also contains playbook for creating the VG,PV and LV and mounts the same on /data mount point, please change the variables values according to your need OR if you dont need to setup LVM for posstgres just remove the step from tasks/main.yml.

How to use this Role:
-----------------------
- Download this role
- create a directory in your working directory as roles
- copy this role in roles directory
- Define variables in vars/main.yml
- check for password less ssh between slave-->master if not setup it
- go to the directory where your ansible inventory is or if you are using the default its fine, just define the host group for postgres as [postgres] in inventory
- please define host vars(role) in your inventory we need the role variable defined for hosts so that ansible can determine who will be the master and who will be the slave for ex:
[postgres]
10.140.21.3 role=master
10.140.21.5 role=slave

- create a postgres.yml file as given in tests/test.yml
- Run the role using below
  - ansible -i {hostfile_if_not_using_default} postgres.yml -f 10

License
-------


BSD

Author Information
------------------
Site Reliability Engineer with 9 years experience in:
• Experience in highly available infrastructure based on cloud and on-premise infrastructures.
• Experience in designing or implementing microservices architecture with containerization tools like Docker and
Kubernetes.
• Proficient in automation tools like Ansible/Consul/Terraform. Automate day-to-day tasks, server provisioning,
configuration management, service management and managing AWS resources.
• Strong experience in Python, and in depth knowledge of Devops/SRE practices including knowledge of ditributed
systems like kafka,elasticsearch, haadoop etc. 
