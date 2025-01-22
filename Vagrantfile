Vagrant.configure("2") do |config|

    config.vm.box = "bento/ubuntu-22.04"  # Usa la misma caja base de Ubuntu 22.04
  
    # Configuración de red
    config.vm.network "forwarded_port", guest: 80, host: 8080
    config.vm.network "private_network", ip: "192.168.155.10"
  
    # Configuración de la VM
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
    end
  
    # ansible_local --> La mv se va a autoprovisionar con ansible (se instala ansible en ella misma y configura con su propio ansible)
    config.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "provision/playbook.yml"  # Define el playbook de Ansible
      ansible.extra_vars = { host_key_checking: false } # Evita problemas de clave SSH
    end
  
  end  



# vagrant reload --provision
# vagrant ssh
# vagrant destroy -f; vagrant up (para volver a probar con powershell)