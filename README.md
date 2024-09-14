## Fedora
```bash
sudo dnf upgrade

### Setup xrdp
sudo dnf install xrdp -y 
sudo systemctl enable xrdp 
sudo systemctl start xrdp 
sudo systemctl status xrdp 
sudo firewall-cmd --permanent --add-port=3389/tcp 
sudo firewall-cmd --reload 
sudo chcon --type=bin_t /usr/sbin/xrdp 
sudo chcon --type=bin_t /usr/sbin/xrdp-sesman

### Setup rust and deno Arm
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
cargo install deno --jobs 1

### Setup deno Arm
curl -s https://gist.githubusercontent.com/LukeChannings/09d53f5c364391042186518c8598b85e/raw/ac8cd8c675b985edd4b3e16df63ffef14d1f0e24/deno_install.sh | sh

# Setup Neovim Fedora Arm
sudo dnf copr enable agriffis/neovim-nightly
sudo dnf install neovim

# Setup Neovim Fedora x64
curl -LO https://github.com/neovim/neovim/releases/latest/download/nvim.appimage
chmod u+x nvim.appimage
sudo mv nvim.appimage /usr/local/bin/nvim

# Setup SMB
sudo dnf install samba samba-client

sudo systemctl enable smb nmb
sudo systemctl start smb nmb

sudo nano /etc/samba/smb.conf

# If SELinux is enforcing, you need to set the correct context for the home directory:
sudo setsebool -P samba_enable_home_dirs 1
sudo chcon -R -t samba_share_t /home/tadachi

Ensure the home directory and its contents have the correct permissions:
sudo chown -R tadachi:tadachi /home/tadachi
sudo chmod -R 755 /home/tadachi

sudo smbpasswd -a tadachi

sudo systemctl restart smb
sudo systemctl restart nmb
```

## Postgres
```
sudo dnf update -y
sudo dnf module reset postgresql -y
sudo dnf install postgresql-server postgresql-contrib
sudo systemctl enable postgresql
sudo postgresql-setup --initdb --unit postgresql
plsql tadachi
sudo psql tadachi
psql
sudo systemctl start postgresql
sudo -u postgres psql
psql tadachi
```

## Linux Cmds
```bash
nmap -p 22 142.104.8.188

# To prevent your Linux system from suspending or going into hibernation, you need to disable the following systemd targets:
sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target

# To re-enable the suspend and hibernation modes, run the command:
sudo systemctl unmask sleep.target suspend.target hibernate.target hybrid-sleep.target

# List ips nicely
ip a
```
