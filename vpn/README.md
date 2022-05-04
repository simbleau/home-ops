<div align="center">

<img src="https://simpleicons.org/icons/openvpn.svg" width="144px" height="144px"/>

# OpenVPN
[![sponsor me](https://img.shields.io/badge/sponsor-30363D?style=for-the-badge&logo=GitHub-Sponsors&logoColor=#white)](https://github.com/sponsors/simbleau)
[![buy me a coffee](https://img.shields.io/badge/Buy_Me_A_Coffee-FFDD00?style=for-the-badge&logo=buy-me-a-coffee&logoColor=black)](https://buymeacoffee.com/simbleau)
[![K3S](https://img.shields.io/badge/k3s-v1.23-brightgreen?style=for-the-badge&logo=kubernetes&logoColor=white)](https://k3s.io/)

</div>

---

## 📖 Overview
This directory contains OpenVPN server and client matter for my home infrastructure. These files are [__Age__](https://github.com/FiloSottile/age) encrypted and protected against accidental exposure through [__Pre-Commit__](https://pre-commit.com/).

---

## 📁 Files
- [__`client.ovpn.age`__](./cluster/): Age encrypted client configuration file for OpenVPN.
- [__`server.ovpn.cert.age`__](./helm/): Age encrypted server certificate for OpenVPN.

---

## 🔄 Cryptography

### Client
- **Decryption**: `age --decrypt -i key.txt client.ovpn.age > client.ovpn`
- **Encryption**: `age --encrypt <public key> client.ovpn > client.ovpn.age`

### Server
- **Decryption**: `age --decrypt -i key.txt server.ovpn.cert.age > server.ovpn.cert`
- **Encryption**: `age --encrypt <public key> server.ovpn.cert > server.ovpn.cert.age`
