# Ansible-Dynamic-Inventory

# Steps

# 1. Create /etc/ansible/ directory and download/copy from here the contents of
	hosts
	ec2.ini
	ansible.cfg

# 2. Assign executable permissions to hosts file
	sudo chmod +x /etc/ansible/hosts
	

# 3. Attach IAM role to the Ansible Server - with Administrator access
	vi hosts, and comment line 172 as this:
		 #from ansible.module_utils import ec2 as ec2_utils, and
   		if your controller node has Python3 then replace the location of shebang(#!) from #!/usr/bin/env python to #!/usr/bin/python3

# 4. Install boto
	sudo pip install boto 

# 5. Execute ansible command: ansible all --list
      This would take a while. However, you may narrow down the search to specific regions in ec2.ini file

# 6. Ping servers
	ansible all -m ping --private-key=path/to/key {there may be need to add the flag "--user ubuntu (or ec2-user)" }

# 7. To see the tags for the servers in your hosts
	/etc/ansible/hosts --list
   Then you can execute commands based on the tags for the servers

===========================================================================================================

# Creating Ansible user (without password authentication) in all host servers

# 1. Create a key
	ssh-keygen

# 2. Copy the content here and create ansibleuser.yml
   
# 3. Execute playbook, after editing the host in the file as desired
	ansible-playbook ansibleuser.yml --private-key=path/to/key {there may be need to add the flag "--user ubuntu (or ec2-user)" }

# 4. You can now ping all
	ansible all -m ping

# 5. You can execute batch commands in the servers

# 6. You can ssh into any of the host servers easily
	ssh ansible@ipAddress
