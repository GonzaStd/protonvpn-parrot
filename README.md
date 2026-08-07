# Build it manually
`dpkg-deb --build --root-owner-group protonvpn-release 
protonvpn-parrot-release_1.0.8+parrot1_all.deb `

# One line graphical install
```bash
wget https://github.com/GonzaStd/protonvpn-parrot/releases/download/v1.0.8%2Bparrot1/protonvpn-parrot-release_1.0.8+parrot1_all.deb && \
sudo apt update && sudo apt upgrade -y && \
sudo apt install ./protonvpn-parrot-release_1.0.8+parrot1_all.deb -y && \
sudo apt update && rm protonvpn-parrot-release_1.0.8+parrot1_all.deb && \
sudo apt install proton-vpn-gnome-desktop -y
```

