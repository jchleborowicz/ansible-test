VAGRANT_API_VERSION = "2"

ssh_pub_key = File.readlines("#{Dir.home}/.ssh/id_rsa.pub").first.strip

Vagrant.configure(VAGRANT_API_VERSION) do |config|
  # Use the same key for each machine
  config.ssh.insert_key = false

  config.vm.define "vagrant1" do |vagrant1|
    vagrant1.vm.box = "ubuntu/trusty64"
    vagrant1.vm.network "forwarded_port", guest: 80, host: 8081
    vagrant1.vm.network "forwarded_port", guest: 443, host: 8441
    vagrant1.vm.provision "shell" do |s|
      s.inline = <<-SHELL
         echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys
         sudo bash -c "echo #{ssh_pub_key} > /root/.ssh/authorized_keys"
      SHELL
    end
  end

  config.vm.define "vagrant2" do |vagrant2|
    vagrant2.vm.box = "ubuntu/trusty64"
    vagrant2.vm.network "forwarded_port", guest: 80, host: 8082
    vagrant2.vm.network "forwarded_port", guest: 443, host: 8442
    vagrant2.vm.provision "shell" do |s|
      s.inline = <<-SHELL
         echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys
         sudo bash -c "echo #{ssh_pub_key} > /root/.ssh/authorized_keys"
      SHELL
    end
  end

  config.vm.define "vagrant3" do |vagrant3|
    vagrant3.vm.box = "ubuntu/trusty64"
    vagrant3.vm.network "forwarded_port", guest: 80, host: 8083
    vagrant3.vm.network "forwarded_port", guest: 443, host: 8443
    vagrant3.vm.provision "shell" do |s|
      s.inline = <<-SHELL
         echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys
         sudo bash -c "echo #{ssh_pub_key} > /root/.ssh/authorized_keys"
      SHELL
    end
  end
end
