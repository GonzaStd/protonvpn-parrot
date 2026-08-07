# ProtonVPN installer for ParrotOS
I struggled while trying to install ProtonVPN in ParrotOS. Proton shows [how to install graphical ProtonVPN on Debian](https://protonvpn.com/support/official-linux-vpn-debian). As Parrot is derived from Debian I thought it would be the same process. But Parrot uses its own repositories and there are conflicts between packages. So, the solution is to add exclusions so ProtonVPN installs all the packages it needs, its dependencies, from Proton official's repository.

Exclusions:
```text
# DEBIAN/postinst/
Package: python3-proton*
Pin: release o=Parrot
Pin-Priority: -1

Package: python-proton*
Pin: release o=Parrot
Pin-Priority: -1

Package: proton*
Pin: release o=Parrot
Pin-Priority: -1


Package: proton*
Pin: origin repo.protonvpn.com
Pin-Priority: 1001

Package: python3-proton*
Pin: origin repo.protonvpn.com
Pin-Priority: 1001

Package: python-proton*
Pin: origin repo.protonvpn.com
Pin-Priority: 1001
```

So it prioritizes ProtonVPN repo more than Parrot repo.

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

