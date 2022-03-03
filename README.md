# Oneinstack脚本搭建Typecho
-------------------------------------
前言
----------------
一直使用宝塔建站 但是一想到删库塔就不得不担心自己小破站

所以就不得已得加强对自己的学习  以下教程是自己总合了多个教程

脚本来源
----------------------
Oneinstack官网：https://oneinstack.com/auto/

Oneinstack GitHub：https://github.com/oneinstack/oneinstack

参考了此博客：https://xians.me/29

准备工作
-----------------
一台VPS（内存大小什么的不用太大也不要太小） 系统随便自己（我这里使用的是Ubuntu18.04）

解析好的域名(需要多个域名可自行解析）

搭建Oneinstack环境
-----------------------
自行去Oneinstack官网选择你需要的插件和版本

请记住你数据库生成的密码或者自己设定数据库密码

Oneinstack官网：https://oneinstack.com/auto/

![image](https://user-images.githubusercontent.com/94978556/156348011-bd10635d-adb5-4719-92b9-98b6d1d495dc.png)

安装过程可能较长 1-3小时不等  耐心等待完成 会自动重启VPS

添加站点
--------------
执行 进入oneinstack指令
```
cd oneinstack
```

执行 添加网站指定
```
./vhost.sh
```

执行上面两条命令后按照下面所示操作就可以 步骤可能有所不同 自己参照图片选择

![image](https://user-images.githubusercontent.com/94978556/156349422-4cd9e050-74ca-4230-9d5c-74fb877c94f6.png)

**配置完成后需要到/usr/local/php/etc/php.ini目录下 修改一下cgi参数,不然安装好Typecho后进入后台会出现Access denied**

**将其中cgi.fix_pathinfo = `0`改为 `1` 即可 如果已经是`1`了就不用修改了**

添加数据库
------------------------
**访问你VPS的IP 登录phpMyAdmin（数据库）用户名一般就是ROOT  密码是在你安装脚本生成的密码 然后添加数据库即可**

如果还不会请自行谷歌添加数据库教程

安装Typecho
------------------------------
可自行获取最新的版本号：https://typecho.org/download 然后自行修改一下以下脚本版本号就可以了 你也可以直接使用以下脚本

进入网站目录指令
```
cd /data/wwwroot/你的站点
```
Typecho安装指令
```
wget https://github.com/typecho/typecho/releases/download/v1.1-17.10.30-release/1.1.17.10.30.-release.tar.gz && tar xzf 1.1.17.10.30.-release.tar.gz && cd build && mv * .. && cd .. && rm -rf 1.1.17.10.30.-release.tar.gz build && chown -R www:www *
```
**配置完成后直接访问你的站点 配置你的数据库**

![image](https://user-images.githubusercontent.com/94978556/156352109-cca5656d-eea6-420d-852b-396a2bc2372d.png)

至此整个搭建结束
------------------------------------
Oneinstack 一些使用方法可自行去官网查询：https://oneinstack.com/install/

删除网站指令
```
rm -rf /usr/local/nginx/conf/vhost/kkx666.cf.conf
```
删除网站目录指令
```
rm -rf /data/wwwroot/kkx666.cf
```

