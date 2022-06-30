Vagrant.configure("2") do |config|
	
	config.vm.define "web01" do |web01|
	web01.vm.box = "geerlingguy/centos7"
	web01.vm.network "private_network", ip: "192.168.56.10"
	web01.vm.provider "virtualbox" do |vb|
	vb.memory = "1024"
	vb.cpus = 2
  end
  web01.vm.provision "shell", inline: <<-SHELL
	yum install httpd wget unzip -y
	cd /tmp/
	systemctl start httpd
	systemctl enable httpd
	wget https://www.tooplate.com/zip-templates/2121_wave_cafe.zip
	unzip -o 2121_wave_cafe.zip
	cp -r 2121_wave_cafe/* /var/www/html
	systemctl restart httpd
 SHELL
end

	config.vm.define "web02" do |web02|
	web02.vm.box = "geerlingguy/centos7"
	web02.vm.network "private_network", ip: "192.168.56.11"
	web02.vm.provider "virtualbox" do |vb|
	vb.mempry = "1024"
	vb.cpus = 2
 end
web02.vm.provision "shell", inline: <<-SHELL
	yum install httpd wget unzip -y
	systemctl start httpd
	systemctl enable httpd
	cd /tmp/
	wget https://www.tooplate.com/zip-templates/2124_vertex.zip
	unzip 2124_vertex.zip
	cp -r 2124_vertex/* /var/www/html
	systemctl restart httpd
  SHELL
 end
end
