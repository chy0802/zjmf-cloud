#魔方云系统使用方法

1. 使用以下命令安装魔方云系统（之前已经安装过免费版的，直接跳到第3步）：

wget https://raw.githubusercontent.com/aazooo/zjmf/main/install-zjmf-cloud_new -O install-zjmf-cloud_new && chmod +x install-zjmf-cloud_new && ./install-zjmf-cloud_new

国内服务器可以用以下命令：

wget https://ghproxy.com/https://raw.githubusercontent.com/aazooo/zjmf/main/install-zjmf-cloud_new -O install-zjmf-cloud_new && chmod +x install-zjmf-cloud_new && ./install-zjmf-cloud_new

以上命令是access模式安装脚本，如果要Trunk模式，是在最后加 -t，轻量版是在最后加 -l

2. 填写授权码的时候

随便填写一个的32位大写的MD5字符串。

3. 输入以下命令完成授权：

echo -n "echo \"success\"" > /home/zjmf/dashboard/www/extend/other/extension
wget https://raw.githubusercontent.com/aazooo/zjmf/main/other/check_main -O /home/zjmf/dashboard/www/extend/other/check_main
chmod +x /home/zjmf/dashboard/www/extend/other/extension
chmod +x /home/zjmf/dashboard/www/extend/other/check_main
wget https://raw.githubusercontent.com/aazooo/zjmf/main/ext/php7.2/idcsmart.so -O /usr/lib64/php/modules/idcsmart.so
echo "extension=idcsmart.so" >> /etc/php.d/40-idcsmart.ini
systemctl restart php-fpm

国内服务器可以用以下命令：

echo -n "echo \"success\"" > /home/zjmf/dashboard/www/extend/other/extension
wget https://ghproxy.com/https://raw.githubusercontent.com/aazooo/zjmf/main/other/check_main -O /home/zjmf/dashboard/www/extend/other/check_main
chmod +x /home/zjmf/dashboard/www/extend/other/extension
chmod +x /home/zjmf/dashboard/www/extend/other/check_main
wget https://ghproxy.com/https://raw.githubusercontent.com/aazooo/zjmf/main/ext/php7.2/idcsmart.so -O /usr/lib64/php/modules/idcsmart.so
echo "extension=idcsmart.so" >> /etc/php.d/40-idcsmart.ini
systemctl restart php-fpm

----------------------------------------------------------

自建授权接口站点（可选）
这部分是可选的，如果内置授权接口出现连接不稳定等情况，可以选择自建。

新建一个网站，上传授权接口源码，并配置好伪静态。

在php配置文件（php.ini）加入idcsmart.url这个配置项，填写授权接口地址，例如：

idcsmart.url=http://www.example.com/

注意一定要以/结尾。然后重启php进程生效。

---------------------------------------------------------

by chy0802
