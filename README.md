# ubuntu-openvpn
1. Install openvpn
```
sudo su apt-get openvpn -y
```
2. masuk ke

```
cd /etc/openvpn/client/
```

3. download certificate
```
git clone https://github.com/MrLockAi/cert.git
```
```
cd cert
```
4. buat config
```
nano open.ovpn
```
paste code berikut
```
client
dev tun
proto tcp
remote example.com 1194
resolv-retry infinite
nobind
persist-key
persist-tun
ca ca.crt
cert client.crt
key client.key
remote-cert-tls server
cipher AES-128-CBC
auth SHA1
auth-user-pass
redirect-gateway def1
```

5. Tancap Gas
```
sudo openvpn --config client.ovpn
```

6. cek routing
```
netstat -nr
```
