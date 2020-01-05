IMAGE_NAME = "bento/ubuntu-16.04"

Vagrant.configure("2") do |config|
    config.ssh.insert_key = false

    config.vm.provider "virtualbox" do |v|
        v.memory = 1024
        v.cpus = 1
    end
      
    config.vm.define "myBuilder" do |builder|
        builder.vm.box = IMAGE_NAME
        builder.vm.network "private_network", ip: "192.168.50.10"
        builder.vm.hostname = "myBuilder"
        builder.vm.provision "file", source: "./tomcat/Dockerfile", destination: "/tmp/docker/Dockerfile"
        builder.vm.provision "ansible" do |ansible|
            ansible.playbook = "tomcat/myBuilder.yml"
            ansible.extra_vars = {
                node_ip: "192.168.50.10",
            }
        end
    end

    config.vm.define "myApp" do |app|
        app.vm.box = IMAGE_NAME
        app.vm.network "private_network", ip: "192.168.50.11"
        app.vm.hostname = "myApp"
        app.vm.provision "ansible" do |ansible|
            ansible.playbook = "tomcat/myApp.yml"
            ansible.extra_vars = {
                node_ip: "192.168.50.11",
            }
        end
    end
end
