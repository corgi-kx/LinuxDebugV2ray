# LinuxDebugV2ray
ubuntu19.04安装v2ray客户端，成功翻墙

先安装curl工具
sudo apt install curl 
安装完成后执行官方脚本
bash <(curl -L -s https://install.direct/go.sh)

说明
此脚本会自动安装以下文件：

/usr/bin/v2ray/v2ray：V2Ray 程序；
/usr/bin/v2ray/v2ctl：V2Ray 工具；
/etc/v2ray/config.json：配置文件；
/usr/bin/v2ray/geoip.dat：IP 数据文件
/usr/bin/v2ray/geosite.dat：域名数据文件

修改/etc/v2ray/config.json配置文件（如果安装过windows版，可以去该软件下 导出配置文件 粘贴到此目录下）
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
启动v2ray
service v2ray start

到此步骤v2ray算是安装配置完成了，但是如果想翻墙 还需要配置代理设置

我本人使用的谷歌浏览器






