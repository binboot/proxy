# proxy
install poxy server with shawdowsocks.

1:
yum update

2:
reboot

3:
yum install gcc gcc-c++ telnet curl

4:
reboot

5:
yum install wget

6:
wget https://bootstrap.pypa.io/get-pip.py

7:
python get-pip.py

8:
pip install shadowsocks

9:
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

10:
chmod 755 ./firewalld.sh

11:
./firewalld.sh

12:
reboot

13:
sudo mkdir /etc/shadowsocks

14:
sudo vim /etc/shadowsocks/shadowsocks.json

{
    "server":"0.0.0.0",
    "server_port":37010,
    "password":"",
    "timeout":300,
    "method":"rc4-md5",
    "fast_open": true
}

15:
vim ./shackdows.sh

ssserver -c /etc/shadowsocks/shadowsocks.json -d start

16:
sudo chmod 755 ./shackdows.sh

17:
./shackdows.sh

