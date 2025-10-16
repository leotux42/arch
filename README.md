
![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXeuSQtguzSvs2RWj_IbyFUUr2PdY9Z6uTmR6lW0nQ5ifSRh6nPdruNq0XsvhhXEBTiKcPX5TAFdwXF2uaI4wOtyX2YIfqdUgUtfgube_3RPdfpi0_vBUVha1s2WqrgEBdrvwJPuWUrdn508CJbsLDQRBJy1?key=VYXvcNk4zFWNxb5YFAyrKA)

Ano: 2020
Update: 2024 october
Autor: Leonardo Meissner  
Keywords: #SistemasOperacionais, #SOs, #Linux, #Arch, #Apps #Virtualizacao #VM
Notas: Arch Bluetooth {{title}}

# Referencias

O artigo e a versao atual no local. Novas atualizacoes serao feitas aos poucos. 
Versao do Artigo: Maio 2024

Artigo Leonardo Arch https://docs.google.com/document/d/1TlM1WzkLPjZQIxeUFgCn9xZEj7Fss-WyMKt8pZ9z9lA/edit#heading=h.225mjayi8s3p

```table-of-contents
```
# 01 - Idioma 


```bash
locale -a
/etc/locale.gen

...
#ps_AF UTF-8  
pt_BR.UTF-8 UTF-8  
#pt_BR ISO-8859-1
...

locale-gen

```

# 02 - Keyboard

Obs: Para o Lenovo. Se for outro mude a versao para portugues. 

   ![[Pasted image 20241007133947.png]]

# 03 - Apps atualizados na sequencia em 2024:

## 03.1 - Pacotes repositório arch

```bash
01-sudo pacman -S Git
02-sudo pacman -S flatpak
03-sudo pacman -S gufw
04-sudo pacman -S neofetch
05-sudo pacman -S gnome-browser-connector
05-sudo pacman -S ffmpeg gst-plugins-ugly gst-plugins-good gst-plugins-base gst-plugins-bad gst-libav gstreamer
06-sudo pacman -S flameshot # script --command "flameshot gui" /dev/null
07 sudo pacman -S ntfs-3g
08- sudo pacman -S tilix
09- sudo pacman -S pacman-contrib
10- git clone yay - makepkg -si 
11- sudo pacman -S  yt-dlp

```

```bash
sudo pacman -S neofetch gnome-browser-connector ffmpeg gst-plugins-ugly gst-plugins-good gst-plugins-base gst-plugins-bad gst-libav gstreamer flameshot ntfs-3g tilix pacman-contrib

```
## 03.2 - Pacotes repositório AUR

```bash
01- yay 
02- Google Chrome
03-Insync
04- Google Earth
05- jdk 

```

## 03.3 - Pacotes Flatpak

```
01-Obsidian
02-Only Office
03-Remmina
04-Nextcloud
05-VLC
06-Anki
07-Okular
08-Opera
09-Discord
10-Telegram
11-vscode
12-pycharm
13-Bottles
14-YTM desktop = youtube music
15-todoist
16-vivaldi
```

## 03.4 - Extensoes do Gnome

```
01-User Themes
02-Icon top 
03-Arch Update
04-Dash to Dock
05-System Monitor
06-
```

## 03.5 - Apps Terminal


```
01-yay cava 
02-ranger
03-cmatrix
```


# 4.0 - Shortcuts

alt + enter = tilix
ctrl + alt + T = kgx   terminal novo do gnome 
super + shift  + s = Flameshot, vide comando no item flameshot
script --command "flameshot gui" /dev/null

Mude para fechar janela super + shift + 1 

![[Pasted image 20250611210853.png]]




# 5.0 - Bluetooth

## 5.1 - Pacotes a serem instalados

```bash
sudo pacman -Syu bluez-utils bluez
sudo systemctl status bluetooth.service
sudo systemctl enable  bluetooth.service




```

## 5.2 - Links Referencia

  [https://wiki.archlinux.org/index.php/Bluetooth#Front-ends](https://wiki.archlinux.org/index.php/Bluetooth#Front-ends)

[https://www.youtube.com/watch?v=rOL-T31l0lQ](https://www.youtube.com/watch?v=rOL-T31l0lQ)

## 5.3 - Alguns comandos de Bluetooth

bluetoothctl
power on
agent on
scan on
devices
para parear digite     pair mas address
coonect mac address
lsmod | grep btusb
modprobe btusb

# 6.0 - Som 

```bash
pacman -S sof-firmware sof-tools alsa-ucm-conf
```

# 7.0 - Docker

![[Docker]]

# 9.0 - Maquinas Virtuais:
## Vmplayr

Quando der errado no VMON kernel 

https://www.blogopcaolinux.com.br/2022/07/Instalando-o-VMware-Workstation-no-Ubuntu-22-04-LTS.html


## Virtualbox Arch 

----- 2024 dezembro inicio ---- 

sudo pacman -S virtualbox virtiualbox-guest-iso 

opcao 2 - > host-modules-arch

Reinstale o linux headers 

sudo pacman -Syy linux-headers

Depois instalei via aur o extension pack 

[virtualbox-ext-oracle](https://aur.archlinux.org/packages/virtualbox-ext-oracle)

Depois add no grupo vboxiusers pra liberar usb 

sudo usermod -aG vboxusers leonardo

Obs: Isso acima foi feito na maquina lenovo. 

Na maquina dell ja tive que desativar o secure boot, tive que bootar pelo kernel mais atual e nao o LTS. 
Instalei o virtualboox, erro de 1901, coloquei no grupo, instaleo o headers do kernel atual, porem so resovleu depois que dei o sudo pacman -Syu para atualziar o sistema. 

----- 2024 dezembro fim ---- 



Ver artigo leonardo google docs

https://docs.google.com/document/d/1TlM1WzkLPjZQIxeUFgCn9xZEj7Fss-WyMKt8pZ9z9lA/edit
## VirtManager Arch 

sudo pacman -S qemu libvirt ebtables dnsmasq bridge-utils openbsd-netcat virt-manager

Vai dar coflito com o ebtables e iptables 

Entre no arquivo: 

sudo nano /etc/libvirt/libvirt.conf

Descomente 

unix_sock_group = "libvirt"
unix_sock_rw_perms = "0777"



sudo systemctl enable libvirtd
sudo systemctl start libvirtd

sudo systemctl enable dnsmasq
sudo systemctl start dnsmasq

sudo gpasswd -a leonardo libvirt


https://www.google.com/search?client=firefox-b-d&q=instalando+virt-manager+on+arch#fpstate=ive&vld=cid:e38ae748,vid:FGeI4nSOHto



# 10 - Pacman 


```bash
sudo pacman -Qi vim   # Ve as versoes do pacote
sudo pacman -Rns - # remove pacote e suas dependencias 
sudo reflector -c Brazil 0a 6(ou G) --sort rate --save /etc/pacman.d/mirrorlist   # escolher repositorio mais rapidos 



```


# 11 - Network 

source: https://wiki.archlinux.org/title/NetworkManager

nmtui 
nmcli 

Look
Cal 2021
Ncal -3
Storge. Io

# 11 - NTFS ON ARCH

Resolvi com o comenado sudo blkid ....
e depois o ntdsfix na particao da vm


![35cc4246a669eea4d407f3f562e2722a.png](:/411f918d5aa1498b991cc7b7beec9c28)




# 12 - Resolvenod displayport dock 6000 dell 

https://forum.manjaro.org/t/displaylink-with-dell-dock-station-problem/140687

deixa ver hoje 2024 

fiz isso 

evdi-git deu erro e intelei esse evdi-compat-git instead
displaylink


# 13- Hyprland 

```bash
sudo pacman -S hyprland kitty waybar wofi hyprpaper
```

#monitor=,preferred,auto,auto
monitor=HDMI-A-1, 2560x1080, 0x0, 1
monitor=eDP-1,1920x1080, 1920x0, 1
#monitor=HDMI-A-1,preferred,auto,auto



uau -S hyprland dolphin wofi hyprpapper alacritty 

.config/hyper/hyprland
Conf 

Mkdir .config/alalacritty 
Co /usr/share/doc/alacritty/examoke/alaciritty.yml 
Descimenta
Pasding pra 10 é pq 
Opa Itu 0.8
Gitclone gir …: stephan-reabe/wallpapper.git

Vim hyorpapper.conf
Uau -s waybar
Mkdir waybar
Co /etc/xg/qyanarcinfug cooir 
Tira os barras 
Trinta awesome fonte trf

Coloque pra iniciar com o sistema 

# 14- UPDATE

sudo pacman -Syuu
yay -Sua
flatpak update


2025 
pacote do vfat

pacman -S dosfstools

# 15- Gnome Minimal

‘’’
gdm gnome-shell gnome-desktop gnome-session gnome-keyring gnome-control-center gnome-settings-daemon gnome-software gnome-console xdg-users-dirs-gtk adawaita-icon-theme nautilus loupe gnome-backgrounds 

Gstreamer gst-libav gst-plugins-base gst-plugins-good gst-plugins-ugly gst-plugins-bad ffmpeg 

Sudo suatemctl enable gdm 

Suatemctl —user enable pipewire pipewire-pulse

‘’’

# 16-pacman 

