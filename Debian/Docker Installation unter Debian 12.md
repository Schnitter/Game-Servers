# Pakete die zur Installation benötigt werden installieren

sudo su &&
apt update &&
apt install ca-certificates curl gnupg apt-transport-https gpg

# GPG-Key downloaden und Repository hinterlegen im System

curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /usr/share/keyrings/docker.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker.gpg] https://download.docker.com/linux/debian bookworm stable" |tee /etc/apt/sources.list.d/docker.list > /dev/null 

apt update 

# Docker-Pakete installieren

apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin docker-compose
