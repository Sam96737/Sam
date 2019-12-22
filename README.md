#!/data/data/com.termux/files/usr/bin/bash env
#
#  Author: TiAmo Sam
#
########################################
#
# Dependencies: bash and wget.
#
########################################

# Update and upgrade
pkg up -y && pkg upgrade -y

# Switch permissive
su -c 'setenforce 0'

# Install dependencies
time apt install rsync aapt neofetch toilet ncurses-utils tsu openssl-tool ruby wget -y

# Fetch the ELF and setup
[[ "$(uname -m)" =~ 'aarch64' ]] && {
    tsu -c 'wget https://raw.githubusercontent.com/TeamTCA/Illusion-Remastered/master/tca_v1-cli'
    tsu -c 'chmod a+x tca_v1-cli'
    tsu -c ./tca_v1-cli
} || printf "Your architecture isn't officially supported yet."
