# Pakete die zur Installation benötigt werden installieren
```bash
sudo su &&
apt update &&
apt install ca-certificates curl gnupg apt-transport-https gpg
```

# GPG-Key downloaden und Repository hinterlegen im System

```bash
curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /usr/share/keyrings/docker.gpg
```

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker.gpg] https://download.docker.com/linux/debian bookworm stable" |tee /etc/apt/sources.list.d/docker.list > /dev/null 
```

```bash
apt update 
```

# Docker-Pakete installieren

```bash
apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin docker-compose
```
