# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.define "server1" do |server1|
    server1.vm.box = "centos/7"
	server1.vm.hostname = "dev"
	server1.vm.network "public_network", bridge: "External", auto_config: false
	
	server1.vm.provision "shell", run: "always", inline: <<-SHELL
		echo -e "TYPE=Ethernet\nDEVICE=eth0\nBOOTPROTO=static\nIPADDR=192.168.0.189\nNETMASK=255.255.255.0\nGATEWAY=192.168.0.1\nDNS1=192.168.0.1\nNAME=eth0\nUUID=00:15:5D:00:6E:14\nONBOOT=yes" > /etc/sysconfig/network-scripts/ifcfg-eth0
		grep -l '#PasswordAuthentication yes' /etc/ssh/sshd_config | xargs sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/g'
		shutdown -r 1
	SHELL
	
	server1.vm.provider "hyperv" do |h|
	  h.memory = "1024"
	  h.cpus = "1"
	  h.vmname = "dev"
	end
  end

  config.vm.define "server2" do |server2|
    server2.vm.box = "centos/7"
	server2.vm.hostname = "prod"
	server2.vm.network "public_network", bridge: "External", auto_config: false
	
	server2.vm.provision "shell", run: "always", inline: <<-SHELL
		echo -e "TYPE=Ethernet\nDEVICE=eth0\nBOOTPROTO=static\nIPADDR=192.168.0.190\nNETMASK=255.255.255.0\nGATEWAY=192.168.0.1\nDNS1=192.168.0.1\nNAME=eth0\nUUID=00:15:5D:00:6E:14\nONBOOT=yes" > /etc/sysconfig/network-scripts/ifcfg-eth0
		grep -l '#PasswordAuthentication yes' /etc/ssh/sshd_config | xargs sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/g'
		shutdown -r 1
	SHELL
  
	server2.vm.provider "hyperv" do |h|
	  h.memory = "1024"
	  h.cpus = "1"
	  h.vmname = "prod"
	end
  end

  config.vm.define "server3" do |server3|
    server3.vm.box = "centos/7"
	server3.vm.hostname = "webserver1"
	server3.vm.network "public_network", bridge: "External", auto_config: false
	
	server3.vm.provision "shell", run: "always", inline: <<-SHELL
		echo -e "TYPE=Ethernet\nDEVICE=eth0\nBOOTPROTO=static\nIPADDR=192.168.0.183\nNETMASK=255.255.255.0\nGATEWAY=192.168.0.1\nDNS1=192.168.0.1\nNAME=eth0\nUUID=00:15:5D:00:6E:14\nONBOOT=yes" > /etc/sysconfig/network-scripts/ifcfg-eth0
		grep -l '#PasswordAuthentication yes' /etc/ssh/sshd_config | xargs sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/g'
		shutdown -r 1
	SHELL
	
	server3.vm.provider "hyperv" do |h|
	  h.memory = "1024"
	  h.cpus = "1"
	  h.vmname = "webserver1"
	end
  end

  config.vm.define "server4" do |server4|
    server4.vm.box = "centos/7"
	server4.vm.hostname = "dbserver1"
	server4.vm.network "public_network", bridge: "External", auto_config: false
	
	server4.vm.provision "shell", run: "always", inline: <<-SHELL
		echo -e "TYPE=Ethernet\nDEVICE=eth0\nBOOTPROTO=static\nIPADDR=192.168.0.185\nNETMASK=255.255.255.0\nGATEWAY=192.168.0.1\nDNS1=192.168.0.1\nNAME=eth0\nUUID=00:15:5D:00:6E:14\nONBOOT=yes" > /etc/sysconfig/network-scripts/ifcfg-eth0
		grep -l '#PasswordAuthentication yes' /etc/ssh/sshd_config | xargs sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/g'
		shutdown -r 1
	SHELL
	
	server4.vm.provider "hyperv" do |h|
	  h.memory = "1024"
	  h.cpus = "1"
	  h.vmname = "dbserver1"
	end
  end
  
  config.vm.define "server5" do |server5|
    server5.vm.box = "centos/7"
	server5.vm.hostname = "ansible"
	server5.vm.network "public_network", bridge: "External"
	
	server5.vm.provision "shell", inline: <<-SHELL
		yum install epel-release -y
		yum install ansible -y
		yum install git -y
		sudo su
		cd ~
		mkdir ansible_tasks
		cd ansible_tasks
		git init
		git pull https://github.com/gkutsarov/ansible_tasks.git
		ssh-keygen -N '' -f ~/.ssh/ansible <<< y
		sleep 30
		sshpass -p vagrant ssh -o StrictHostKeyChecking=no root@192.168.0.183
		sshpass -p vagrant ssh -o StrictHostKeyChecking=no root@192.168.0.185
		sshpass -p vagrant ssh -o StrictHostKeyChecking=no root@192.168.0.189
		sshpass -p vagrant ssh -o StrictHostKeyChecking=no root@192.168.0.190
		sshpass -p vagrant ssh-copy-id -i /root/.ssh/ansible.pub root@192.168.0.183
		sshpass -p vagrant ssh-copy-id -i /root/.ssh/ansible.pub root@192.168.0.185
		sshpass -p vagrant ssh-copy-id -i /root/.ssh/ansible.pub root@192.168.0.189
		sshpass -p vagrant ssh-copy-id -i /root/.ssh/ansible.pub root@192.168.0.190
	SHELL
	
	server5.vm.provider "hyperv" do |h|
	  h.memory = "1024"
	  h.cpus = "1"
	  h.vmname = "ansible"
	end
  end
  
end

