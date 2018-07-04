# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.provision "shell", inline: <<-SHELL
    echo "127.0.0.1 localhost
192.168.99.10 docker.salas4linux.com.br
192.168.99.11 devops.salas4linux.com.br
192.168.99.12 automation.salas4linux.com.br" > /etc/hosts
    mkdir /root/.ssh/
    #CHAVE PRIVADA
    echo "-----BEGIN RSA PRIVATE KEY-----
MIIEpQIBAAKCAQEA1GLNHpHJfU268yFsvj22t/dOPZCVqlFOaiWQI1AGE4mAdkTQ
+EOhwM4pac6BR4NwZKvZMp7N3mYWlGYuuNtlu3h3UJgbgly38Fml+QVbsJt8Ffmz
dAfPysWVrF1Pii2YfJrnMlkJ0Lp+mXItx6hITe9QkO2BUH1TS4fCjDpfZY0/2SBn
dtd/A6PiIeyTZJLXs/tCJiLNg7Y3VFnbO7HUWb0mm/t5xkbDlpgAcPtXg2c6Nyxr
5zHDEHtcf1zMADTdowg6baOX4I0RvjO006kkp3Py+lHSJB5Ht+b88mAM+JDniMV7
G3ehSS5UlR+k4AzZrxr00Mh7B7za/MVkXw3fuwIDAQABAoIBAACnlU5E0MQsGylo
rvcfJZMHlhwmd++gdIdrOjiBpKMmx1iV+bbqLnNzrzj+Q/O+efg1d2PqjWPkGKm4
buhu9K9RPbzn2x3Zv09kV1ifJZszv3wp2t2+sGtFlKKFXxtj7JZlu9Sx5Y/ZI07B
xVZaNG7ZD/yCXuWqnTkcYAMiouyjM2EeI06Kt2QnnmL2f5OtArhWTm+SyI283kUP
M3iHmg6oAx8hQkQAVPU/etTVmN3h8jthM6r/6a96vXD2Wr9JTgxB0J6jxl/UIzB8
ravKBWjF+8m3tf/S2wtAbyzbn0IIFiWs3wLu/BQ9ypdQkeYUJOjOe5wNRwNvXHVy
FsKoX4ECgYEA7iQ0McoUCthYyZkkTl5nC2O+O0aWdFX7Yyj23VXIVqo4LGoTXng2
o5iS30WtNIIW0aqTDxVuLnVgGolEQStyFyiXiEpY+1biW2FnzohIEP1X0LcRrHcq
wgnvp0I9Xg4U7yULPxQx0tj4BG2DXiE2BZeDDbe3BOqU9ISFY8R7K+ECgYEA5FAl
9/tO8cw7M62uPTMM4WrRl4A4izYQ/1muXAWA04lpYKsWfxgT+oFEZTTmmEIvUA6V
gAyXn4PBYMEgg66szqMrJifcVhHjuBsQIoiZ2uUtKj7Q+y0ilMBetubjK42IasA4
GMpyJZjuSa8CqMZjhFAgPyIVLj2hssEPlTPAHxsCgYEAsERR8eyOizx587aL3goY
IaERhJSJ9tBRw6LlnwzIvgU+kPlvHsTCRLNBO0w6mRwVQdoNAeQt6utsWBf0UnyS
9TtRdkr5tAgqgdMGYCQVm6W54z4uMcb++iMapWXtQHoR2rVDrswG2PdKFRTuYLUa
ZGcyVOv/5v6vhJG2nhMnzGECgYEA0ch7OsKlpTOdajy6Du2rdiyqbOSaEAAb2iVT
Oqar2rM2KmbKAvni0ZiZec0D3P9jbdIYuFHZt+5eb0LFV3nWuv/ek+6oXEWP0gi7
6J9Pj3xo5ZpWd5TfY4LnBHReZBRmNoBsiwrpm3ZL7VRrwxyXMGpXVutAPv7OZutS
ICwu6eUCgYEAi8mzS/J+oDyEI0jkgdpRgRhrZrIyqAD1Nqghdb+jaAM1lvpQ320M
VZp5nrTD/iZqsITpXENCDtqb+OMswvfnTWSOOCaN3lsVO9NX1XcsgplstZnzHG11
nUXUjfXMOxLSWIPCOmIaUbtshOzzYidgOO2aNNFgbGE16OkQsDJr9Hg=
-----END RSA PRIVATE KEY-----" >> /root/.ssh/id_rsa
    #CHAVE PUBLICA
    echo "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDUYs0ekcl9TbrzIWy+Pba39049kJWqUU5qJZAjUAYTiYB2RND4Q6HAzilpzoFHg3Bkq9kyns3eZhaUZi6422W7eHdQmBuCXLfwWaX5BVuwm3wV+bN0B8/KxZWsXU+KLZh8mucyWQnQun6Zci3HqEhN71CQ7YFQfVNLh8KMOl9ljT/ZIGd2138Do+Ih7JNkktez+0ImIs2DtjdUWds7sdRZvSab+3nGRsOWmABw+1eDZzo3LGvnMcMQe1x/XMwANN2jCDpto5fgjRG+M7TTqSSnc/L6UdIkHke35vzyYAz4kOeIxXsbd6FJLlSVH6TgDNmvGvTQyHsHvNr8xWRfDd+7">> /root/.ssh/authorized_keys
    chmod 600 /root/.ssh/id_rsa
  SHELL
#DOCKER
  config.vm.define "docker" do |docker|
    docker.vm.hostname = "docker"
    docker.vm.box = "ubuntu/xenial64"
    docker.vm.box_check_update = false
    docker.vm.network "private_network", ip: "192.168.99.10", dns: "8.8.8.8"
  end

#DEVOPS
  config.vm.define "devops" do |devops|
    devops.vm.hostname = "devops"
    devops.vm.box = "ubuntu/xenial64"
    devops.vm.box_check_update = false
    devops.vm.network "private_network", ip: "192.168.99.11", dns: "8.8.8.8"
  
    config.vm.provider "virtualbox" do |devops|
      devops.memory = "3072"
    end
  end

#AUTOMATION
  config.vm.define "automation" do |automation|
    automation.vm.hostname = "automation"
    automation.vm.box = "centos/7"
    automation.vm.box_check_update = false
    automation.vm.network "private_network", ip: "192.168.99.12", dns: "8.8.8.8"
  end


end
