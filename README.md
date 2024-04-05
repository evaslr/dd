# 乌班图系统的甲骨文云需要开启防火墙
```
iptables -P INPUT ACCEPT
```
```
iptables -P FORWARD ACCEPT
```
```
iptables -P OUTPUT ACCEPT
```
```
iptables -F
```
```
apt-get purge netfilter-persistent
```


# dd甲骨文等机器，准备工作。

更新apt源

```
apt-get update
```
更新
```
apt-get upgrade
```

安装需要的工具包

```
apt-get install -y xz-utils openssl gawk file wget curl sudo jq
```

然后执行以下脚本，脚本全自动运行，dd之后会造成断开链接的情况，不用担心，请耐心等待20分钟或更久。可以通过ping端口来检测是否DD完成。

- 默认密码
```
MoeClub.org
```


- Debian 9
```
bash <(wget --no-check-certificate -qO- 'https://raw.githubusercontent.com/evaslr/dd/main/InstallNET.sh') -d 9 -v 64 -a -firmware
```

- Debian 10
```
bash <(wget --no-check-certificate -qO- 'https://raw.githubusercontent.com/evaslr/dd/main/InstallNET.sh') -d 10.3 -v 64 -a -firmware
```

- Debian 11
```
bash <(wget --no-check-certificate -qO- 'https://raw.githubusercontent.com/evaslr/dd/main/InstallNET.sh') -d 11 -v 64 -a -firmware
```

- BBR
```
echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf
```

```
echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf
```

```
sysctl -p
```

```
sysctl net.ipv4.tcp_available_congestion_control
```

```
lsmod | grep bbr
```
