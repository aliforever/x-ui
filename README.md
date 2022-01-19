# x-ui
xray panel supporting multi-protocol multi-user

# Features
- System Status Monitoring
- Support multi-user multi-protocol, web page visualization operation
- Supported protocols: vmess, vless, trojan, shadowsocks, dokodemo-door, socks, http
- Support for configuring more transport configurations
- Traffic statistics, limit traffic, limit expiration time
- Customizable xray configuration templates
- Support https access panel (self-provided domain name + ssl certificate)
- For more advanced configuration items, please refer to the panel

# Install & Upgrade
```
bash <(curl -Ls https://raw.githubusercontent.com/vaxilu/x-ui/master/install.sh)
```

## Manual install & upgrade
1. First download the latest compressed package from https://github.com/vaxilu/x-ui/releasesamd64 , generally choose the architecture
2. Then upload the compressed package to the /root/directory of the server and rootlog in to the server with the user

> If your server cpu architecture is not amd64, replace the command amd64with another architecture by yourself

```
cd /root/
rm x-ui/ /usr/local/x-ui/ /usr/bin/x-ui -rf
tar zxvf x-ui-linux-amd64.tar.gz
chmod +x x-ui/x-ui x-ui/bin/xray-linux-* x-ui/x-ui.sh
cp x-ui/x-ui.sh /usr/bin/x-ui
cp -f x-ui/x-ui.service /etc/systemd/system/
mv x-ui/ /usr/local/
systemctl daemon-reload
systemctl enable x-ui
systemctl restart x-ui
```

## Install using docker

> This docker tutorial and docker image are provided by Chasing66

1. install docker
```shell
curl -fsSL https://get.docker.com | sh
```
2. install x-ui
```shell
mkdir x-ui && cd x-ui
docker run -itd --network=host \
    -v $PWD/db/:/etc/x-ui/ \
    -v $PWD/cert/:/root/cert/ \
    --name x-ui --restart=unless-stopped \
    enwaiax/x-ui:latest
```
> Build your own image
```shell
docker build -t x-ui .
```

## suggestion system
- CentOS 7+
- Ubuntu 16+
- Debian 8+

## common problem
## Migrating from v2-ui
First install the latest version of x-ui on the server where v2-ui is installed, and then use the following command to migrate, which will migrate the native v2-ui 所有 inbound 账号数据to x-ui,面板设置和用户名密码不会迁移
> 关闭 v2-uiPlease and after the migration is successful 重启 x-ui, otherwise the inbound of v2-ui will be generated with the inbound of x-ui端口冲突
```
x-ui v2-ui
```

## issue closed
All kinds of small white problems see high blood pressure

## Stargazers over time
[![Stargazers over time](https://starchart.cc/vaxilu/x-ui.svg)](https://starchart.cc/vaxilu/x-ui)
