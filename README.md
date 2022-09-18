<center><h1> PVE_Status_Tools </center>

## 使用方式
> 注意（非常重要） :
- 需要使用root身份执行下面代码；
- 需要在未修改过的PVE系统之下运行，如果你修改过 `Nodes.pm` 和 `pvemanagerlib.js`,需要恢复原文件才可使用以下代码；

**在终端中按行分别执行以下代码：**
```
export LC_ALL=en_US.UTF-8
apt update && apt -y install git && git clone https://github.com/iKoolCore/PVE_Status_Tools.git
cd PVE_Status_Tools
./PVE_Status_Tools.sh
```

> 建议优化操作：
  - 删除企业源：`rm /etc/apt/sources.list.d/pve-enterprise.list`


