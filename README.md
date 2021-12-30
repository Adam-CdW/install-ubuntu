# install-ubuntu

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

### ZSH config
https://github.com/Adam-CdW/zsh_config


### Désactiver les logs d'erreur PCIE
```
sudo vi /etc/default/grub
```
==> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=off"
```
sudo update-grub
reboot
```
