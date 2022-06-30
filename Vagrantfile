Vagrant.configure("2") do |config|

  config.vm.define "web01" do |web01|
    web01.vm.box = "geerlingguy/centos7"
	web01.vm.network "private_network", ip: "192.168.56.11"
	web01.vm.provider "virtualbox" do |vb|
     vb.memory = "1024"
	 vb.cpus = 2
   end
   web01.vm.provision "shell", inline: <<-SHELL
     yum update
	 yum install httpd wget unzip -y
	 systemctl start httpd
	 systemctl enable httpd
	 cd /tmp/
	 wget https://www.tooplate.com/zip-templates/2119_gymso_fitness.zip
	 unzip -o 2119_gymso_fitness.zip
	 cp -r 2119_gymso_fitness/* /var/www/html/
	 systemctl restart httpd
   SHELL
  end

  config.vm.define "web02" do |web02|
    web02.vm.box = "ubuntu/bionic64"
	web02.vm.network "private_network", ip: "192.168.56.12"
	web02.vm.provider "virtualbox" do |vb|
     vb.memory = "1024"
	 vb.cpus = 2
   end
   web02.vm.provision "shell", inline: <<-SHELL
     apt update
	 apt install apache2 wget unzip -y
	 systemctl start apache2
	 systemctl enable apache2
	 cd /tmp/
	 wget https://www.tooplate.com/zip-templates/2119_gymso_fitness.zip
	 unzip -o 2119_gymso_fitness.zip
	 cp -r 2119_gymso_fitness/* /var/www/html/
	 systemctl restart apache2
   SHELL
  end
end
