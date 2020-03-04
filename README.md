Caddy一键安装脚本：
 wget -N --no-check-certificate https://raw.githubusercontent.com/ToyoDAdoubi/doubi/master/caddy_install.sh && chmod +x caddy_install.sh && bash caddy_install.sh

echo "http://xxx.ml:80 {
redir https://xxx.ml:12671{url}
}
https://xxx.ml:12671 {
gzip
tls xxx@xxx.ml
root /var/www/web-master
redir  https://xxx.ml{uri} 301 
}" > /usr/local/caddy/Caddyfile

mkdir /var/www

cd /var/www

wget https://github.com/mospring001/web/archive/master.zip

apt install unzip

unzip master.zip

cd /var/www/web-master

unzip web.zip

cd

重启：service caddy restart  
查看状态：service caddy status

wget --no-check-certificate -O shadowsocks-all.sh https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks-all.sh
chmod +x shadowsocks-all.sh
./shadowsocks-all.sh 2>&1 | tee shadowsocks-all.log

修改配置文件：/etc/shadowsocks-r/config.json
vi /etc/shadowsocks-r/config.json
1.“server_port”: 端口改为443
2."redirect": ["*:443#127.0.0.1:12671"], 
重启SSR服务

/etc/init.d/shadowsocks-r restart
