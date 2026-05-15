![](qrcode.png)

# [data-web-server](https://github.com/lafefspietz/data-web-server)

 - [plots.md](plots.md)
 - [index.html](index.html)
 - [file-set.json](file-set.json)
 - [replicate-file-set.php](replicate-file-set.php)
 
This web server uses [wsl](https://en.wikipedia.org/wiki/Windows_Subsystem_for_Linux), [Apache](https://en.wikipedia.org/wiki/Apache_HTTP_Server), [PHP](https://en.wikipedia.org/wiki/PHP), [Jupyter](https://en.wikipedia.org/wiki/Project_Jupyter), [Python](https://en.wikipedia.org/wiki/Python_(programming_language)), [Markdown](https://en.wikipedia.org/wiki/Markdown), [Github Desktop](), Miniforge, for an integrated system of sharing data on the both the local web and publicly available web pages on Github.

First install wsl. open powershell as administrator and try

```
wsl --install
```


```
sudo apt update
sudo apt install apache2 -y
sudo apt install php libapache2-mod-php -y
cd /var/www/html
sudo rm index.html
sudo apt-get install curl
sudo curl -o replicate-file-set.php https://raw.githubusercontent.com/lafefspietz/data-web-server/refs/heads/main/replicate-file-set.php
cd ..
sudo chmod -R 0777 *
cd html
php replicate-file-set.php
sudo chmod -R 0777 *
```

how to get the server visible over local network, do all this by running powerShell as administrator. Note that it has to be as administrator, and it has to be powershell.

run this:

```
Set-NetFirewallHyperVVMSetting -Name '{40E0AC32-46A5-438A-A0B2-2B479E8F2E90}' -DefaultInboundAction Allow
```

then run this:

```
New-NetFirewallRule -DisplayName "Allow WSL Inbound" -Direction Inbound -InterfaceAlias "vEthernet (WSL (Hyper-V firewall))" -Action Allow
```
then run this:

```
netsh interface portproxy reset
netsh interface portproxy add v4tov4 listenport=80 listenaddress=0.0.0.0 connectport=80 connectaddress=127.0.0.1

```

create file .wslconfig which in C:\Users\[username] folder and put the following in it:

```
[wsl2]
networkingMode=NAT
localhostForwarding=true
```

In order to get the server to be visible over the network, some commands had to be run from powershell ran as admin after first getting the IP address at the end of the command using "hostname -I" from the wsl Ubuntu prompt.

```
netsh interface portproxy add v4tov4 listenport=80 listenaddress=0.0.0.0 connectport=80 connectaddress=172.22.23.110
```



This is the .bat file which runs a jupyter notebook:

```

```

