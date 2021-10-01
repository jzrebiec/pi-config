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

### Samba server

### Docker


## Links
* [IOTstack](https://github.com/SensorsIot/IOTstack)
* [Oh my zsh](https://ohmyz.sh/)
* [Awesome Pi](https://github.com/thibmaek/awesome-raspberry-pi)