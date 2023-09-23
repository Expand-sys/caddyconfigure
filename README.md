# caddy configure
Configures caddy with ansible and reverts changes should there be an issue. 
ONLY COMPATIBLE WITH BINARY VERSION FOR NOW, DOCKER COMPAT WILL COME LATER

## How to use
1. install ansible on any linux machine or WSL install, it can even be the machine you are planning to install Caddy on. https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html
   a. `dnf install -y ansible` for rocky/alma/centos/fedora or `yay -S ansible` for arch based systems, anything else check link in 1 if your operating system is not listed install via python pip3
3. `git clone https://github.com/Expand-sys/caddyconfigure && cd caddyconfigure`
4. `cp caddyfile/Caddyfile.rename-me caddyfile/Caddyfile`
5. edit ./inventory with your favourite text editor e.g. `nano ./inventory` to have the ip address of your target server, can be 127.0.0.1 or localhost if it is running on the same machine, by default it is 127.0.0.1
6. edit vars/default.yml with your favourite text editor e.g. `nano vars/default.yml` if you already have an install of caddy(not docker) set install caddy to false, it wont harm anything to keep it set to true either way it will just update your caddy binary to the latest. and make sure if you want a custom location for your caddy file to change it here aswell.
7. run `ansible-playbook -i inventory main.ansible.yml -k` This script must be run as root user on the target machine so the `-k` will ask for the ssh password for the root user __OF THE TARGET SERVER__ if you have ssh keys set up for the root user you may omit the -k

