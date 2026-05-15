![](qrcode.png)

# [data-web-server](https://github.com/lafefspietz/data-web-server)

This web server uses wsl, Apache, PHP, Jupyter, Python, Markdown, Github Desktop, for an integrated system of sharing data on the both the local web and publicly available web pages on Github.


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


 - [plots.md](plots.md)
 - [index.html](index.html)
 - [file-set.json](file-set.json)
 - [replicate-file-set.php](replicate-file-set.php)