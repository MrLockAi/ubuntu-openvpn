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
remote host.fituradv.site 1194
resolv-retry infinite
nobind
persist-key
persist-tun
ca /etc/openvpn/client/cert/ca.crt
cert /etc/openvpn/client/cert/client.crt
key /etc/openvpn/client/cert/client.key
remote-cert-tls server
cipher AES-128-CBC
auth SHA1
auth-user-pass
redirect-gateway def1
```
5. Copy ke root
```
cp client.ovpn /root
```

7. 
8. Tancap Gas
```
sudo openvpn --config client.ovpn
```

7. cek routing
```
netstat -nr
```
auto start
```
sudo systemctl enable openvpn@client.service
