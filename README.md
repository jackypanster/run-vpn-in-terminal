### Run vpn in terminal

+ Install shadowsocks
```bash
sudo apt-get update
sudo apt-get install python-pip
sudo apt-get install python-setuptools m2crypto
sudo pip install shadowsocks
```

+ Edit the configuration of sslocal
```bash
touch shadowsocks.json
vi shadowsocks.json
{
"server":<server>,
"server_port":9000,
"local_port":1080,
"password":<password>,
"timeout":600,
"method":"aes-256-cfb"
}
```
