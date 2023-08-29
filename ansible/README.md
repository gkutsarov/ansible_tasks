<<<<<<< HEAD
# ansible_tasks

On my way to DevOps ^^
=======
# Ansible Steps and Best Practices

#Best Practices is to use SSH keys
#Ansible Repository

ssh-keygen -t(ype) ed25519 -C(omment) "Ansible-Key"
ls -la .ssh
ssh-copy-id -i [ssh-key-name].pub [destination-server-ip]


vi .bashrc
alias ssha='eval $(ssh-agent) && ssh-add'


>>>>>>> af1d9b29b2c4dd90290afb2090d12fdd036c90b2
