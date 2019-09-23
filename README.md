# proxy
install poxy server with shawdowsocks.

1:
yum update

2:
reboot

3:
yum install gcc gcc-c++ telnet curl wget

4:
reboot

5:
wget https://bootstrap.pypa.io/get-pip.py

6:
python get-pip.py

7:
pip install shadowsocks

8:
vim firewalld.sh

firewall-cmd --zone=public --add-port=56211/tcp --permanent 
firewall-cmd --zone=public --add-port=56218/tcp --permanent 
firewall-cmd --zone=public --add-port=55211/tcp --permanent 
firewall-cmd --zone=public --add-port=55218/tcp --permanent 
firewall-cmd --zone=public --add-port=80/tcp --permanent 
firewall-cmd --zone=public --add-port=8080/tcp --permanent 
firewall-cmd --zone=public --add-port=443/tcp --permanent 
firewall-cmd --zone=public --add-port=443/udp --permanent 
firewall-cmd --zone=public --add-port=6728/tcp --permanent 
firewall-cmd --zone=public --add-port=6728/udp --permanent 
firewall-cmd --zone=public --add-port=37010/tcp --permanent 
firewall-cmd --complete-reload 
firewall-cmd --zone=public --list-ports

9:
chmod 755 ./firewalld.sh

10:
./firewalld.sh

11:
reboot

12:
sudo mkdir /etc/shadowsocks

13:
sudo vim /etc/shadowsocks/shadowsocks.json

{
    "server":"0.0.0.0",
    "server_port":37010,
    "password":"",
    "timeout":300,
    "method":"rc4-md5",
    "fast_open": true
}

14:
vim ./shackdows.sh

ssserver -c /etc/shadowsocks/shadowsocks.json -d start

15:
sudo chmod 755 ./shackdows.sh

16:
./shackdows.sh

