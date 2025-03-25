# **IB网络互联**

## 部署

1. 给IB卡配置IP

   ```bash
   sudo vim /etc/netplan/01-network-manager-all.yaml
   ```

   ```yaml
   network:
     version: 2
     renderer: networkd
     ethernets:
       ibp1s0:
         addresses:
           - 192.168.1.1/24 #自定义
   ```

2. 命令

   ```bash
   ibstat #查看状态
   sudo netplan generate #检验配置文件
   sudo netplan apply #启动配置
   sudo systemctl restart systemd-networkd #重启服务
   ifconfig #检查网口是否分配IP地址
   ```

   