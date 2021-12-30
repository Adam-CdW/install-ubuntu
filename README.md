# Finalisation de l'installation d'un machine de dev
Prérequis : avoir une install clean d'Ubuntu 20.04

### Préparation
```
sudo apt update
sudo apt dist-upgrade
sudo apt upgrade
sudo apt install software-properties-common
sudo apt install ubuntu-restricted-extras
```

### Script ansible
https://github.com/adimeo-lab/ansible-dev-machine

```
ansible-playbook \
  -i hosts playbook.yml \
  --extra-vars "lsb_release=focal ansible_user=ubuntu ansible_password=ubuntu email_username=codingpool ansible_become_password=ubuntu"
```
Ensuite il faut reboot :
```
reboot
sudo apt update
sudo apt upgrade
```

### ZSH config
https://github.com/Adam-CdW/zsh_config

### Install docker-composer
https://docs.docker.com/compose/install/

### Mise en place de MKCERT
#### Installation de `mkcert`
Suivre les instructions d'installation (_build from source_ conseillé) : https://github.com/FiloSottile/mkcert#installation
```
cd
sudo apt install libnss3-tools
sudo apt install golang
git clone https://github.com/FiloSottile/mkcert && cd mkcert
go build -ldflags "-X main.Version=$(git describe --tags)"
sudo cp mkcert /usr/local/bin/mkcert
sudo chmod +x /usr/local/bin/mkcert
cd ..
sudo rm -rf mkcert
```

#### Initialisation de `mkcert` pour créer une autorité de confiance local
```
mkcert -install
```

#### On génère un certificat wildcard pour couvrir tous nos besoins d'url local
```
cd ~
mkdir certs
mkcert -cert-file certs/local-cert.pem -key-file certs/local-key.pem "*.local" "*.adimeo.local" "*.docker.local"
```

#### On crée un lien symbolique de nos certificat à la racine de notre ordinateur pour les lier à `Traefik`
```
sudo ln -s ~/certs/ /
```


  
### Désactiver les logs d'erreur PCIE
```
sudo vi /etc/default/grub
```
==> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=off"
```
sudo update-grub
reboot
```
