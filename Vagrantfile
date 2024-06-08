Vagrant.configure("2") do |config|
  # rmq01
  config.vm.define "rmq01" do |rmq01|
    rmq01.vm.hostname = "rmq01"
    rmq01.vm.box = "ubuntu/jammy64"
    rmq01.vm.network "public_network", ip: "192.168.0.220"
    rmq01.vm.provider "virtualbox" do |vb|
      # Display the VirtualBox GUI when booting the machine
      vb.gui = false
      vb.name = "rmq01"
      # Customize the amount of memory on the VM:
      vb.memory = "1024"
      vb.cpus = 1
    end
    # Копирование файлов с локалхоста
    rmq01.vm.provision "file", source: "./consumer.py", destination: "/home/vagrant/consumer.py"
    rmq01.vm.provision "file", source: "./producer.py", destination: "/home/vagrant/producer.py"
    rmq01.vm.provision "file", source: "./consumer_auth.py", destination: "/home/vagrant/consumer_auth.py"
    rmq01.vm.provision "shell", inline: <<-SHELL
    # Добавление файлов хоста
    sudo echo "192.168.0.220 rmq01" | sudo tee -a /etc/hosts
    sudo echo "192.168.0.221 rmq02" | sudo tee -a /etc/hosts
    sudo apt update
    sudo apt upgrade
    # Установка и настройка  python3-pip и rabbitmq-server
    sudo apt install python3-pip -y
    pip3 install pika
    sudo apt install rabbitmq-server -y
    sudo systemctl enable rabbitmq-server
    sudo systemctl start rabbitmq-server
    sudo rabbitmq-plugins enable rabbitmq_management
    sudo rabbitmqctl add_user pergunovdv mypassword
    sudo rabbitmqctl set_user_tags pergunovdv administrator
    sudo rabbitmqctl set_permissions -p / pergunovdv ".*" ".*" ".*"
    sudo systemctl restart rabbitmq-server
    sudo rabbitmqctl set_policy ha-all ".*" '{"ha-mode":"all"}'
    sudo cp /var/lib/rabbitmq/.erlang.cookie /vagrant/
    SHELL
  end

  # rmq02
  config.vm.define "rmq02" do |rmq02|
    rmq02.vm.hostname = "rmq02"
    rmq02.vm.box = "ubuntu/jammy64"
    rmq02.vm.network "public_network", ip: "192.168.0.221"
    rmq02.vm.provider "virtualbox" do |vb|
      # Display the VirtualBox GUI when booting the machine
      vb.gui = false
      vb.name = "rmq02"
      # Customize the amount of memory on the VM:
      vb.memory = "1024"
      vb.cpus = 1
    end
    # Копирование файлов с локалхоста
    rmq02.vm.provision "file", source: "./consumer.py", destination: "/home/vagrant/consumer.py"
    rmq02.vm.provision "file", source: "./producer.py", destination: "/home/vagrant/producer.py"
    rmq02.vm.provision "shell", inline: <<-SHELL
    # Добавление файлов хоста
    sudo echo "192.168.0.220 rmq01" | sudo tee -a /etc/hosts
    sudo echo "192.168.0.221 rmq02" | sudo tee -a /etc/hosts
    sudo apt update
    sudo apt upgrade
    # Установка и настройка  python3-pip и rabbitmq-server
    sudo apt install python3-pip -y
    pip3 install pika
    sudo apt install rabbitmq-server -y
    sudo systemctl enable rabbitmq-server
    sudo systemctl start rabbitmq-server
    sudo rabbitmq-plugins enable rabbitmq_management
    sudo cp /vagrant/.erlang.cookie /var/lib/rabbitmq/
    sudo systemctl restart rabbitmq-server
    sudo rabbitmqctl stop_app
    sudo rabbitmqctl join_cluster rabbit@rmq01
    sudo rabbitmqctl start_app
    sudo rabbitmqctl set_policy ha-all ".*" '{"ha-mode":"all"}'
    SHELL
  end
end
  

