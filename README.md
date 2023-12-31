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
```
