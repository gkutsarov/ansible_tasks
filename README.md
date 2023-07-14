# Ansible Steps and Best Practices

#Best Practices is to use SSH keys

ssh-keygen -t(ype) ed25519 -C(omment) "Ansible-Key"
ls -la .ssh
ssh-copy-id -i [ssh-key-name].pub [destination-server-ip]


vi .bashrc
alias ssha='eval $(ssh-agent) && ssh-add'

