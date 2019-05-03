

#####安装curl工具

`sudo apt install curl`

#####安装完成后执行v2ray官方脚本

`bash <(curl -L -s https://install.direct/go.sh)`

>说明
此脚本会自动安装以下文件：
/usr/bin/v2ray/v2ray：V2Ray 程序；
/usr/bin/v2ray/v2ctl：V2Ray 工具；
/etc/v2ray/config.json：配置文件；
/usr/bin/v2ray/geoip.dat：IP 数据文件
/usr/bin/v2ray/geosite.dat：域名数据文件

#####根据你服务器端的配置来修改/etc/v2ray/config.json配置文件（如果安装过windows版，可以去该软件下 导出配置文件 粘贴到此目录下）

    {
    "log": {
     "access": "",
    "error": "",
    "loglevel": "warning"
    },
    "inbounds": [
    {
      "port": 1080,
      "listen": "127.0.0.1",
      "protocol": "socks",
      "sniffing": {
        "enabled": true,
        "destOverride": [
          "http",
          "tls"
        ]
      },
      "settings": {
        "auth": "noauth",
        "udp": true,
        "ip": null,
        "clients": null
      },
      "streamSettings": null
    }
    ],
    "outbounds": [
    {
      "tag": "proxy",
      "protocol": "vmess",
      "settings": {
        "vnext": [
          {
            "address": "cc.*****.com",
            "port": 443,
            "users": [
              {
                "id": "**********",
                "alterId": 16,
                "email": "****",
                "security": "auto"
              }
            ]
          }
        ],
        "servers": null,
        "response": null
      },
      "streamSettings": {
        "network": "ws",
        "security": "tls",
        "tlsSettings": {
          "allowInsecure": true,
          "serverName": null
        },
        "tcpSettings": null,
        "kcpSettings": null,
        "wsSettings": {
          "connectionReuse": true,
          "path": "/qqgame",
          "headers": {
            "Host": "cc.acgjs.com"
          }
        },
        "httpSettings": null,
        "quicSettings": null
      },
      "mux": {
        "enabled": true
      }
    },
    {
      "tag": "direct",
      "protocol": "freedom",
      "settings": {
        "vnext": null,
        "servers": null,
        "response": null
      },
      "streamSettings": null,
      "mux": null
    },
    {
      "tag": "block",
      "protocol": "blackhole",
      "settings": {
        "vnext": null,
        "servers": null,
        "response": {
          "type": "http"
        }
      },
      "streamSettings": null,
      "mux": null
    }
    ],
    "dns": null,
    "routing": {
    "domainStrategy": "IPIfNonMatch",
    "rules": []
    }
    }



#####启动v2ray

`service v2ray start`

#####查看是否启动v2ray

`service v2ray status`

![显示活跃则代表启动成功](https://upload-images.jianshu.io/upload_images/17680481-35a9468b777d2ab7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



#####到此步骤v2ray算是安装配置完成了，但是如果想成功访问谷歌 还需要配置代理设置
>代理设置就是config.json里面写的，一般设置成127.0.0.1 端口号 1080

#####我本人使用的chrome浏览器 ---> 设置----> 高级-----> 无障碍-----> 打开代理设置------> 设置手动里面的代理ip

![](https://upload-images.jianshu.io/upload_images/17680481-a3901a19b567f1ed.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/17680481-30c7c3ec77d0ecee.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/17680481-da1377a264c7b323.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![科学上网成功](https://upload-images.jianshu.io/upload_images/17680481-b11040a316b6f5b2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
