这个项目旨在自动化从 kernel.org 获取最新的 stable 版本内核，并编译该内核，同时拉取 Google 的 BBR v3 源码并集成到编译过程中。

## 安装内核
```shell
bash <(curl -Ls https://raw.githubusercontent.com/Naochen2799/Latest-Kernel-BBR3/main/bbr3.sh) 
```

### 启用 bbrv3

```bash
# 设置 bbrv3
echo 'net.ipv4.tcp_congestion_control=bbr' | sudo tee -a /etc/sysctl.conf
sudo sysctl -p

# 查看当前的TCP流控算法
sysctl net.ipv4.tcp_congestion_control

# 查看可用的TCP流控算法，以module形式被编译的算法将不会显示
sysctl net.ipv4.tcp_available_congestion_control
```

如果想启用 bbrv3，流控算法应设置为 `bbr`，如果想使用早期版本的 bbr，流控算法应设置为 `bbr1`
💡 Sponsorship Statement
This project is supported by VTEXS's "Free VPS Plan for Open Source Projects".
Thank you VTEXS for supporting the open source community!💡
💡 贊助聲明
本項目由 VTEXS 的「開源項目免費 VPS 計劃」提供算力支持。
感謝 VTEXS 對開源社區的支持！
