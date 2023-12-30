## Fedora
```bash
sudo dnf upgrade

sudo dnf install xrdp -y 
sudo systemctl enable xrdp 
sudo systemctl start xrdp 
sudo systemctl status xrdp 
sudo firewall-cmd --permanent --add-port=3389/tcp 
sudo firewall-cmd --reload 
sudo chcon --type=bin_t /usr/sbin/xrdp 
sudo chcon --type=bin_t /usr/sbin/xrdp-sesman

curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
cargo install deno --jobs 1
```
