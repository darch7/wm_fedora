#!/bin/sh

echo " ██████╗ ███████╗██████╗ ██╗    ██╗███╗   ███╗██████╗ ██╗   ██╗██████╗  █████╗ ██████╗  ██████╗██╗  ██╗        ███████╗███████╗██████╗  ██████╗ ██████╗  █████╗  ;"
echo " ██╔══██╗██╔════╝██╔══██╗██║    ██║████╗ ████║██╔══██╗╚██╗ ██╔╝██╔══██╗██╔══██╗██╔══██╗██╔════╝██║  ██║        ██╔════╝██╔════╝██╔══██╗██╔═══██╗██╔══██╗██╔══██╗  ;"
echo " ██████╔╝███████╗██████╔╝██║ █╗ ██║██╔████╔██║██████╔╝ ╚████╔╝ ██║  ██║███████║██████╔╝██║     ███████║        █████╗  █████╗  ██║  ██║██║   ██║██████╔╝███████║  ;"
echo " ██╔══██╗╚════██║██╔═══╝ ██║███╗██║██║╚██╔╝██║██╔══██╗  ╚██╔╝  ██║  ██║██╔══██║██╔══██╗██║     ██╔══██║        ██╔══╝  ██╔══╝  ██║  ██║██║   ██║██╔══██╗██╔══██║  ;"
echo " ██████╔╝███████║██║     ╚███╔███╔╝██║ ╚═╝ ██║██████╔╝   ██║   ██████╔╝██║  ██║██║  ██║╚██████╗██║  ██║███████╗██║     ███████╗██████╔╝╚██████╔╝██║  ██║██║  ██║  ;"
echo " ╚═════╝ ╚══════╝╚═╝      ╚══╝╚══╝ ╚═╝     ╚═╝╚═════╝    ╚═╝   ╚═════╝ ╚═╝  ╚═╝╚═╝  ╚═╝ ╚═════╝╚═╝  ╚═╝╚══════╝╚═╝     ╚══════╝╚═════╝  ╚═════╝ ╚═╝  ╚═╝╚═╝  ╚═╝  ;"

                                                                                                                                                                                                                                                            
sleep 3

sudo -v
while true; do
  sudo -nv; sleep 1m
  kill -0 $$ 2>/dev/null || exit
done &

#Instalar bspwmbydarch_fedora

cd 
sudo dnf install -y fedora-workstation-repositories && sudo dnf install -y https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm 
sudo dnf repolist --all 
sleep 4
clear

# Dnf rapido
echo "fastestmirror=true" | sudo tee --append /etc/dnf/dnf.conf ;
echo "deltarpm=true" | sudo tee --append /etc/dnf/dnf.conf
clear

cat /etc/dnf/dnf.conf
 
sleep 3

# actualizar mirrors
sudo dnf update -y 
cd 
clear
# instalacion bspwm y librerias de xorg
sudo dnf install -y bspwm sxhkd make gcc libXinerama-devel libXft libXft-devel harfbuzz-devel xkbcomp-devel @base-x 
sudo dnf install -y xdg-user-dirs

# crear carpetas de usuario
xdg-user-dirs-update --force

# instalación de grupos de fedora
sudo dnf groupinstall -y "Administration Tools" "Hardware-Support" "Development Tools" "Multimedia" "Input Methods" "Fonts" "C Development Tools and Libraries" "Container Management" 

# clonacion de repos y copiado de carpeta a su respectivos lugares 
git clone https://github.com/darch7/bspwmbydarch_fedora 
cp -R bspwmbydarch_fedora/config/* $HOME/.config/ 
cp -R bspwmbydarch_fedora/.local $HOME/ 
mkdir .local/share
mv .local/fonts $HOME/.local/share/fonts  
sudo chmod +x .local/bin 
cp -R bspwmbydarch_fedora/home/.[^.]* $HOME/  
cd bspwmbydarch_fedora/compilar/st  
sudo make clean install  
cd  

# instalacion de dependencias 
sudo dnf install -y NetworkManager-tui NetworkManager picom light xrdb xkbcomp libva-intel-driver materia-gtk-theme papirus-icon-theme blueberry xsetroot cmake meson rofi nitrogen pcmanfm zsh zsh-autosuggestions zsh-syntax-highlighting zathura-zsh-completion tmux htop telegram-desktop xarchiver ffmpeg maim xclip xdotool mpv firefox dnf-utils ranger neovim neofetch slock transmission sxiv dunst zathura-pdf-poppler zathura papirus-icon-theme calcurse neofetch polybar   

# creacion de .xinitrc
touch .xinitrc
echo "exec bspwm" > ~/.xinitrc
sleep 3 

clear

# instalacion de dm
sudo dnf install -y slim  
sudo systemctl enable slim  
sudo systemctl set-default graphical.target 
sudo cp -R bspwmbydarch_fedora/slim /usr/share/

clear

sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/powerlevel10k
echo 'source ~/powerlevel10k/powerlevel10k.zsh-theme' >>~/.zshrc

# comprobación y final
neofetch  
sleep 5
uname -r  
sleep 3

echo "BspwmbyDarch_fedora instalado"  
sleep 5
clear
sudo systemctl reboot
