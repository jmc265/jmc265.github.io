ssh_keygen -o
chezmoi add .ssh/id_rsa.pub
brew intall bitwarden-cli
bw login <email>
bw unlock
export BW_SESSION="<sessionid>"
