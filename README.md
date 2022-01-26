# pi-config

## Initial configuration

### SSH
Create file named `ssh` (without any extension) in the root directory of the boot partition.

### WiFi
* Create file named `wpa_supplicant.conf` in the root directory of the boot partition.
* Copy & paste the following into it.

```conf
country=PL # Your 2-digit country code
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
    ssid="YOUR_NETWORK_NAME"
    psk="YOUR_PASSWORD"
}
```

### User managment
* Add user & create home dir
```sh
sudo useradd --create-home user_name
```
* Set password
```sh
sudo passwd user_name
```
* Add user to sudo
```sh
sudo usermod -aG sudo user_name
```
* Delete default (`pi`) user
```sh
sudo userdel -r pi
```

### Update
```sh
sudo apt update
sudo apt upgrade
```

### Update pi config
```sh
sudo raspi-config
```

### ZSH
* Install
```sh
sudo apt intall zsh
```
* Set zsh as default shell
```sh
chsh -s $(which zsh)
```
* Install Oh my zsh
```sh
sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
```
* Other
```sh
sudo apt install fonts-powerline fonts-firacode
```
* Plugins

    * [autosugestions](https://github.com/zsh-users/zsh-autosuggestions)
    * [syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)

### Samba server

### Docker

* Install
```sh
curl -sSL https://get.docker.com | sh

sudo usermod -aG docker user_name

sudo install python3 python3-pip

sudo pip3 -v install docker-compose
```

* Enable auto-startup
```sh
sudo systemctl enable docker
```

### Mount external drive
```
sudo mkdir /mnt/external_hdd
sudo chown -R USER:USER /mnt/external_hdd
```

* Get UUID
```sh
sudo blkid
```

* Edit /etc/fstab
```
UUID="UUID FROM blkid" /mnt/external_hdd ext4 defaults,auto,users,rw,nofail,noatime 0 0
```

## Links
* [IOTstack](https://github.com/SensorsIot/IOTstack)
* [Oh my zsh](https://ohmyz.sh/)
* [Awesome Pi](https://github.com/thibmaek/awesome-raspberry-pi)