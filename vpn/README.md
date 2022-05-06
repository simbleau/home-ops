<div align="center">

<img src="https://simpleicons.org/icons/openvpn.svg" width="144px" height="144px"/>

# OpenVPN
[![sponsor me](https://img.shields.io/badge/sponsor-30363D?style=for-the-badge&logo=GitHub-Sponsors&logoColor=#white)](https://github.com/sponsors/simbleau)
[![buy me a coffee](https://img.shields.io/badge/Buy_Me_A_Coffee-FFDD00?style=for-the-badge&logo=buy-me-a-coffee&logoColor=black)](https://buymeacoffee.com/simbleau)
[![openvpn](https://img.shields.io/badge/OpenVPN-EA7E20?style=for-the-badge&logo=openvpn&logoColor=black)](https://openvpn.net)

</div>

---

## 📖 Overview
This directory contains OpenVPN server and client matter for my home infrastructure. These files are [__Age__](https://github.com/FiloSottile/age) encrypted and protected against accidental exposure through [__Pre-Commit__](https://pre-commit.com/).

---

## 📁 Files
- [__`server.ovpn.cert.age`__](./server.ovpn.cert.age): Age encrypted server certificate for OpenVPN.
- [__`client.ovpn.age`__](./client.ovpn.age): Age encrypted client configuration file for OpenVPN.
- [__`login.confg.age`__](./login.conf.age): Age encrypted client login credentials for OpenVPN.

---

## 🔓 Connection Test

```
sops -d login.conf.age > login.conf
sops -d client.ovpn.age > client.ovpn
sudo openvpn --config client.ovpn --auth-user-pass login.conf
```

---

## 🔄 Cryptography

### Client
- **Decryption**: `sops -d client.ovpn.age > client.ovpn`
- **Encryption**: `sops -e --age <public key> client.ovpn > client.ovpn.age`

### Server
- **Decryption**: `sops -d server.ovpn.cert.age > server.ovpn.cert`
- **Encryption**: `sops -e --age <public key> server.ovpn.cert > server.ovpn.cert.age`
