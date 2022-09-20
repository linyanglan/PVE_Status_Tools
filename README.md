<center><h1> PVE_Status_Tools </center>

<hr>

#### 安装方法：

> 注意:需要使用`root`身份执行下面代码

*在终端中按行分别执行以下代码：*
```
export LC_ALL=en_US.UTF-8
apt update && apt -y install git && git clone https://github.com/iKoolCore/PVE_Status_Tools.git
cd PVE_Status_Tools
./PVE_Status_Tools.sh
```

**或**  *直接执行下面一行代码：*
```
wget -qO-  https://raw.githubusercontent.com/iKoolCore/PVE_Status_Tools/main/PVE_Status_Tools.sh | bash
```
#### 还原方法：
方法① ：
用压缩包中对应文件`（PVE 7.2-3）`的原版覆盖，再重启 pveproxy 服务： <br>
```
systemctl restart pveproxy
```
方法② ：
执行命令重新安装 `proxmox-widget-toolkit` 和 `pve-manager` <br>
```
apt reinstall proxmox-widget-toolkit && systemctl restart pveproxy.service   #还原订阅提示并重启服务
apt reinstall pve-manager && systemctl restart pveproxy   #还原概要页面并重启服务
```

#### 注意事项：
① 目前脚本仅适配最新的PVE 7.2-3版本（20220920）更新版本，请备份文件自测；<br>
② 如果你的 PVE 不在压缩包的版本之内，请先更新系统至相同版本。千万不要强行替换，否则后果自负；<br>
③ AMD平台目前仅兼容 Ryzen 7，不可显示核心温度；<br>
④ Intel平台目前不支持 GPU 温度显示。<br>

