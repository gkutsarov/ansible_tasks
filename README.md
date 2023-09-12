## Ansible tasks used to automate various scenarios when configuring a VM ##

1. Task 1 uses **variables** as parameters passed to **install_playbook.yml** when run. Packages to be installed are declared as variables in variables/main.yml
   
2. Task 2 makes use of secrets.yml file which is encrypted with ansible vault. The password to encrypt/decrypt **secrets.yml** is stored in **password_file**. Ansible is configured to use this file to encrypt the **secrets.yml** (see ansible.cfg). Ansible playbook creates a user named developer with home dir /var/lib/developer with the password stored in **secrets.yml**

In addition, we use hosts.j2 jinja template to grab the IP address and hostname from our inventory file and set /etc/hosts file on the production node with that information.

3. Task 3 uses the best practice of ansible roles. Installing packages, copying files, configuring network ports, and restarting services.
