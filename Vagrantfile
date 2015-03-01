VAGRANTFILE_API_VERSION = "2"
 
Dotenv.load

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
 
  (0..3).each do |num|
    config.vm.define "shua-cdh#{num}" do |node|
      node.vm.provider :google do |provider, override|
        provider.google_project_id = "#{ENV['GOOGLE_CLOUD_PROJECT_ID']}"
        provider.google_client_email = "#{ENV['SERVICE_ACCOUNT_EMAIL_ADDRESS']}"
        provider.google_key_location = "#{ENV['PATH_TO_YOUR_PRIVATE_KEY']}"

        provider.image = "rhel-6-v20150127"
        provider.machine_type = "n1-standard-1"

        provider.name = "shua-cdh#{num}"
        provider.network = "default"
        provider.disk_size = 20

        override.vm.box = "gce"
        override.vm.box_url = "https://github.com/mitchellh/vagrant-google/raw/master/google.box"

        override.ssh.username = "#{ENV['USERNAME']}"
        override.ssh.private_key_path = "~/.ssh/google_compute_engine"
      end
    end
  end
 
  #config.vm.provision :ansible do |ansible|
  #  ansible.playbook = "ansible/site.yml"
  #  ansible.inventory_path = "ansible/production"
  #end
 
end

