##### 1.配置服务端SS [github下载](https://github.com/shadowsocks/shadowsocks-libev)
    例如服务器IP 66.66.66.66，SS监听  0.0.0.0:1443，SS密码ssPassword

##### 2.配置服务端 kcptun[github下载](https://github.com/xtaci/kcptun)
配置参数
```
{
"listen": ":2019", //kcptun监听地址
"target": "127.0.0.1:1443", //SS服务地址
"key": "kcptunPassword", //kcptun密码
"crypt": "aes",
"mode": "fast2",
"mtu": 1350,
"sndwnd": 1024,
"rcvwnd": 1024,
"datashard": 70,
"parityshard": 30,
"dscp": 46,
"nocomp": false,
"acknodelay": false,
"nodelay": 0,
"interval": 40,
"resend": 0,
"nc": 0,
"sockbuf": 4194304,
"keepalive": 10
}
```

##### 3.PC端SS配置，[SS-windows](https://github.com/shadowsocks/shadowsocks-windows)
配置数据
```
{
      "server": "66.66.66.66",
      "server_port": 1443,
      "password": "ssPassword",
      "localPort":"1080" //SS本机监听端口
    }
```

##### 4.PC端kcptun配置
参数必须和服务端kcptun参数一致
```
{
  "localaddr": "127.0.0.1:1070", //kcptun本地监听地址
  "remoteaddr": "66.66.66.66:2019", //kcptun服务端地址
  "key": "kcptunPassword",
  "crypt": "aes",
  "mode": "fast2",
  "mtu": 1350,
"sndwnd": 1024,
"rcvwnd": 1024,
"datashard": 70,
"parityshard": 30,
"dscp": 46,
"nocomp": false,
}
```
#### 5.Android系统SS+kcptun,[SS_github](https://github.com/shadowsocks/shadowsocks-android/releases),[SS_kcptun插件](https://github.com/shadowsocks/kcptun-android/releases)
添加SS服务器数据，新增一个服务器数据ss_kcptun    
服务器66.66.66.66，    
远程端口2019（kcptun服务端端口）,    
密码ssPassword，    
启用插件kcptun,参数必须跟服务端kcp参数一致


## systemctl ss多端口自启动
```
cp /lib/systemd/system/shadowsocks-libev.service /lib/systemd/system/shadowsocks-libev1.service
vim /lib/systemd/system/shadowsocks-libev1.service
        Description=Shadowsocks-libev 1 Server Service
        EnvironmentFile=/etc/default/shadowsocks-libev1

cp /etc/default/shadowsocks-libev /etc/default/shadowsocks-libev1
vim /etc/default/shadowsocks-libev1
        CONFFILE="/etc/shadowsocks-libev/config1.json"

cp /etc/shadowsocks-libev/config.json /etc/shadowsocks-libev/config1.json
vim /etc/shadowsocks-libev/config1.json

```

#### v2ray
```
bash <(curl -L -s https://install.direct/go.sh)
```