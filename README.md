# Overwall-Cloudflare-IP

安装cdnspeedtest https://github.com/immortalwrt-collections/openwrt-cdnspeedtest/releases
vi /etc/config/overwall
修改 config servers 'cf'
vi cdnspeedtest.sh 参照下面bash，运行 bash cdnspeedtest.sh， 只要设置一个每天凌晨的计划任务自动更新ip就行，完全不用人工去找ip了。
运行需要的 ip.txt 在这 https://github.com/XIU2/CloudflareSpeedTest


#!/bin/bash

/etc/init.d/overwall stop
cdnspeedtest -url https://hongbin.info/files/MPL-GAN.pdf -dn 1 -sl 50 -tl 250 -tll 40

declare ip
ip=$(cat result.csv | cut -d',' -f1 | sed -n 2p)
uci set overwall.cf.server=$ip
uci commit overwall
/etc/init.d/overwall restart



