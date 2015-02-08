Vagrant.configure(2) do |config|
  config.vm.define "lamp.vagrant", primary: true, autostart: true do |config_machine|
      #Assigning a provider
      config_machine.vm.provider :virtualbox do |virtualbox, override|
          virtualbox.name = "Backend2 RTI"
		  override.vm.box = "ubuntu/trusty64"
          
		  # Configuring network
          override.vm.network "forwarded_port", guest: 80, host: 8080, auto_correct: true
      end
	  
      # Asinging a provisioner
      config_machine.vm.provision :ansible, run: "always" do |provisioner|
          provisioner.playbook = "Ansible/playbooks/lamp.yml"
          provisioner.extra_vars = "custom_vars.yml" if File.file?("custom_vars.yml")
      end
  end
end
