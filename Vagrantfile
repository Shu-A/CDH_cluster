VAGRANTFILE_API_VERSION = "2"
 
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
 
    config.vm.box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v6.5.3/centos65-x86_64-20140116.box"
    config.vm.box = "CentOS-6.5-x86"
 
    config.vm.define :cdh00 do |c|
        c.vm.box = "CentOS-6.5-x86"
        c.vm.hostname = "cdh00.vagrant.com"
        c.vm.network :private_network, ip: "192.168.0.100", virtualbox__intnet: "intnet"
        c.vm.network :forwarded_port, guest: 7180, host: 7180, id: "scm"
        c.vm.provider :virtualbox do |v|
            v.name = "cdh00"
            v.memory = 512
        end
    end
 
    config.vm.define :cdh01 do |c|
        c.vm.box = "CentOS-6.5-x86"
        c.vm.hostname = "cdh01.vagrant.com"
        c.vm.network :private_network, ip: "192.168.0.101", virtualbox__intnet: "intnet"
        c.vm.provider :virtualbox do |v|
            v.name = "cdh01"
            v.memory = 2048

            file_to_disk = "./.tmp/disk_" + c.vm.hostname + ".vdi"
            unless File.exist?(file_to_disk)
                v.customize ['createhd', '--filename', file_to_disk, '--size', 10 * 1024]
                v.customize ['storageattach', :id, '--storagectl', 'SATA', '--port', 1, '--device', 0, '--type', 'hdd', '--medium', file_to_disk]
            end
        end
    end
 
    config.vm.define :cdh02 do |c|
        c.vm.box = "CentOS-6.5-x86"
        c.vm.hostname = "cdh02.vagrant.com"
        c.vm.network :private_network, ip: "192.168.0.102", virtualbox__intnet: "intnet"
        c.vm.provider :virtualbox do |v|
            v.name = "cdh02"
            v.memory = 2048
            
            file_to_disk = "./.tmp/disk_" + c.vm.hostname + ".vdi"
            unless File.exist?(file_to_disk)
                v.customize ['createhd', '--filename', file_to_disk, '--size', 10 * 1024]
                v.customize ['storageattach', :id, '--storagectl', 'SATA', '--port', 1, '--device', 0, '--type', 'hdd', '--medium', file_to_disk]
            end
        end
    end
 
    config.vm.define :cdh03 do |c|
        c.vm.box = "CentOS-6.5-x86"
        c.vm.hostname = "cdh03.vagrant.com"
        c.vm.network :private_network, ip: "192.168.0.103", virtualbox__intnet: "intnet"
        c.vm.provider :virtualbox do |v|
            v.name = "cdh03"
            v.memory = 2048

            file_to_disk = "./.tmp/disk_" + c.vm.hostname + ".vdi"
            unless File.exist?(file_to_disk)
                v.customize ['createhd', '--filename', file_to_disk, '--size', 10 * 1024]
                v.customize ['storageattach', :id, '--storagectl', 'SATA', '--port', 1, '--device', 0, '--type', 'hdd', '--medium', file_to_disk]
            end
        end
    end
 
    config.vm.provision :ansible do |ansible|
        ansible.playbook = "ansible/site.yml"
        ansible.inventory_path = "ansible/production"
    end
 
end

