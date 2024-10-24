# -GitLab-Vasyaeva-Irina
«GitLab» Васяева Ирина <br/>
# Задание 1.
## Разворачивание GitLab с помощью Vagrant <br/>
1. Создание директорию для проекта <br/>
mkdir gitlab-vagrant <br/>
cd gitlab-vagrant <br/>
2. Создание файла Vagrantfile <br/>
Vagrant.configure("2") do |config| <br/>
config.vm.box = "ubuntu/bionic64" <br/>
config.vm.network "forwarded_port", guest: 80, host: 8080 <br/>
config.vm.provision "shell", inline: <<-SHELL <br/>
apt-get update <br/>
apt-get install -y curl openssh-server ca-certificates <br/>
curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ee/script.deb.sh | bash <br/>
EXTERNAL_URL="http://localhost:8080" apt-get install gitlab-ee <br/>
gitlab-ctl reconfigure <br/>
SHELL <br/>
end <br/>
3. Запуск Vagrant <br/>
vagrant up <br/>
4. Проверка доступа к GitLab <br/>
5. Создание нового проекта и пустого репозитория <br/>
Вход в свою учетную запись GitLab и создание нового проекта <br/>
![image](https://github.com/user-attachments/assets/c1b1eabb-0c17-42df-8fe5-f6b7c57c57b4) <br/>
7. Установка и регистрация GitLab Runner <br/>
   curl -L --output /usr/local/bin/gitlab-runner https://gitlab-runner-downloads.s3.amazonaws.com/latest/binaries/gitlab-runner-linux-amd64 <br/>
   chmod +x /usr/local/bin/gitlab-runner <br/>
   gitlab-runner install <br/>
   gitlab-runner register <br/>
   apt-get install -y docker.io <br/>
   gitlab-runner start <br/>
