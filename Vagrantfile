

# Chamando modulo YAML
require 'yaml'

# Lendo o arquivo YAML com as configuracoes do ambiente
env = YAML.load_file('environment.yaml')

Vagrant.configure("2") do |config|
  env.each do |env|
    config.vm.define env['name'] do |vb|
      vb.vm.box      = env['box']
      vb.vm.hostname = env['hostname']
      vb.vm.network "forwarded_port", guest: 80, host: 8080
      vb.vm.network 'public_network', ip: env['ipaddress']
      vb.vm.provision "shell", path: env['provision']
      vb.vm.provider 'virtualbox' do |vb|
       vb.memory = env['memory']
       vb.cpus   = env['cpus']
      end
    end 
   end
end
