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
  "server_port":<port>,
  "local_port":1080,
  "password":<password>,
  "timeout":600,
  "method":"aes-256-cfb"
}
```

+ Run the shadowsocks
```bash
sslocal -c ./shadowsocks.json -d restart
#or
sudo vi /etc/rc.local
sudo sslocal -d restart -c /home/ubuntu/shadowsocks.json
```

+ Install polipo
```bash
sudo apt-get install polipo
```

+ Edit the configuration of polipo
```bash
vi /etc/polipo/config
logSyslog = true
logFile = /var/log/polipo/polipo.log

socksParentProxy = "127.0.0.1:1080"
socksProxyType = socks5
```

+ Run the polipo
```bash
sudo service polipo restart
#or
sudo vi /etc/rc.local
sudo service polipo restart
```
+ Export the proxy
```bash
vi .profile
export http_proxy=http://127.0.0.1:8123
export https_proxy=http://127.0.0.1:8123
```

+ Verify
```bash
curl http://www.google.com
```
