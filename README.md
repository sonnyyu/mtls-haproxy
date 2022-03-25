# Install software
```bash
git clone https://github.com/sonnyyu/mtls-haproxy
cd mtls-haproxy
```
# Use mtls-cert-manage generate server/client/ca certificate 

[https://github.com/sonnyyu/mtls-cert-manage](https://github.com/sonnyyu/mtls-cert-manage)

# Copy Server Certificate from mtls-cert-manage
```bash
cd ~/mtls-cert-manage/pki/haproxycerts
cp server.pem ca.crt ~/mtls-haproxy/haproxy/etc/certs
```
# Copy Client Certificate from mtls-cert-manage
```bash
cd ~/mtls-cert-manage/pki/clientcerts
cp * ~/mtls-haproxy/certs
```
# Getting started nginx with certificate
```bash
docker-compose up -d
```
# Quit 
```bash
docker-compose down 
```
# Quit and remove Volume
```bash
docker-compose down -v
```
# Test mTLS
```bash
cd ~/mtls-haproxy/cert
curl --cert client1.crt --key client1.key --cacert ca.crt https://192.168.1.204
curl --cert client1.crt:password1 --key client1.key --cacert ca.crt https://192.168.1.204
curl --cert-type P12 --cert client1.p12 --cacert ca.crt https://192.168.1.204
```
# Install certificate at PC
[Install certificate](https://github.com/sonnyyu/mtls-cert-manage#install-certificate-at-windows)

# Open Browser
```bash
https://192.168.1.204
```
