# install-ubuntu

https://github.com/adimeo-lab/ansible-dev-machine


sudo apt update
sudo apt dist-upgrade
sudo apt upgrade
sudo apt install software-properties-common
sudo apt install ubuntu-restricted-extras

ZSH config : https://github.com/Adam-CdW/zsh_config

Afficher les fichiers et dossiers cachés : ctrl+ h

### Désactiver les logs d'erreur PCIE
sudo vi /etc/default/grub

==> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=off"

sudo update-grub
reboot
