<center><h1> PVE_Status_Tools </center>

<hr>

#### 一、安装方法：

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
#### 二、还原方法：
方法① ：
用压缩包中对应文件`（PVE 7.2-3）`的原版覆盖，再重启 `pveproxy服务`： <br>
```
systemctl restart pveproxy
```
方法② ：
执行命令重新安装 `proxmox-widget-toolkit` 和 `pve-manager` <br>
```
apt reinstall proxmox-widget-toolkit && systemctl restart pveproxy.service   #还原订阅提示并重启服务
apt reinstall pve-manager && systemctl restart pveproxy   #还原概要页面并重启服务
```

#### 三、注意事项：
> ① 目前脚本仅适配最新的PVE 7.2-3版本（20220920）更新版本，请备份文件自测；<br>
> ② 如果你的 PVE 不在压缩包的版本之内，请先更新系统至相同版本。千万不要强行替换，否则后果自负；<br>
> ③ AMD平台目前仅兼容 Ryzen 7，不可显示核心温度；<br>
> ④ Intel平台目前不支持 GPU 温度显示。<br>
> ⑤开机会自动加载配置，一般无需其他操作<br>
> ⑥部分设备的风扇信息可能因为驱动如果开机无法自动加载，需要在 `/etc/modules` ，将模块名称添加到文件末尾并回行。it87模块添加it87，nct6687模块添加nct6687

<hr>

**如果执行以上安装之后，PVE的信息显示完全且无问题，下面传感器驱动可不操作执行。<br>以下传感器驱动模块安装适用于部分微星主板和CW-N5105的V3版本**

<hr>

#### 四、传感器驱动（非必须）
1. DKMS 动态内核驱动模块

操作方法：

① WinSCP等SFTP功能软件访问PVE，按照功能需求，复制文件到对应路径；<br>
② SSH 访问 PVE，执行以下命令: 
```
apt-get update && apt-get install -y dkms pve-headers #安装 dkms 和 pve-headers
```
将 xxx-dkms_xxxx_all.deb 上传至 PVE /tmp 文件夹
```
dpkg -i /tmp/xxx-dkms_xxxx_all.deb #安装 deb 驱动包
```

2. 确保已安装lm-sensors
```
apt-get update && apt-get install -y lm-sensors
```

3. it87模块驱动的额外操作，加载模块到内核
```
modprobe it87 force_id=0x8686 ignore_resource_conflict=1
```

4. 更新 initramfs (初始化 RAM 系统)

```
update-initramfs -u -k all
```

#### 五、更新日志：
2022.9.20.001 更新日志：

> 1、调整依赖工具包的安装时机，解决报错；<br>
> 2、增加一些代码注释。

#### 六、相关资源：

 [PVE暗黑主题 ｜ PVEDiscordDark ](https://github.com/Weilbyte/PVEDiscordDark) thanks to [Weilbyte](https://github.com/Weilbyte)  **<small>(click to visit) </small>**
