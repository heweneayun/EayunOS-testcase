# 创建一个Windows虚拟机

## 创建Windows 7虚拟机

1. 登录到Engine管理端，在左侧树形面板中点击【展开所有】按键，在默认数据中心的默认集群下点击【虚拟机】，在右侧的虚拟机详细列表中，点击菜单中的【新建虚拟机】按键。
1. 在弹出的【新建虚拟机】窗口中，选择操作系统为Windows 7 x64，优化选择为【桌面】输入虚拟机名称（必填）、描述和注释（选填），其他配置保持默认配置，你也可以根据需要更改相关的配置。
1. 点击【确定】后，弹出【新建虚拟机-引导操作】窗口，点击【配置虚拟机磁盘】为该虚拟机配置磁盘，在打开的【添加虚拟机磁盘】窗口中，输入添加磁盘的大小，其他配置保持默认配置，点击【确定】，回到【新建虚拟机-引导操作】窗口，点击【以后再配置】结束新建虚拟机磁盘操作，关闭窗口。
1. 虚拟机创建成功，显示在虚拟机列表中，虚拟机状态变化为image Locked -> Down，虚拟机磁盘的状态变化为Locked -> Up。


## 安装Windows 7虚拟机

1. 选中刚才新建的Windows 7虚拟机，点击菜单中的【只运行一次】。
1. 在弹出的【运行虚拟机】窗口中，勾选附加CD，选择Windows7的ISO镜像，在引导序列中，选择CD-ROM，点击【上移】，点击【确定】运行虚拟机。
1. 当询问【您想将 Windows 安装在何处？】时，点击虚拟机菜单中的【更换CD】，选择ovirt-guest-tools.iso，点击【确定】。
1. 点击【加载驱动程序】，在【选择要安装的驱动程序】窗口中，点击【浏览】，选择driver -> win7 -> x86（32位操作系统选择x86，64位操作系统选择amd64），点击【确定】。
1. 选择【Red Hat VirtIO SCSI controller】，点击【下一步】，安装驱动程序。
1. 安装驱动完成后，回到【您想将 Windows 安装在何处？】的窗口，点击虚拟机菜单中的【更换CD】，换回Windows7的安装镜像。
1. 点击【下一步】后，继续安装Windows7操作系统。
1. 等待，直到虚拟机操作系统安装完成，新用户输入用户名，进入系统。

## 通过Windows模板创建虚拟机

* 前提条件：已经创建好一个Windows的模板。

1. 在左侧树形面板中点击【展开所有】按键，在默认数据中心下的默认集群下点击【虚拟机】，在右侧的虚拟机详细列表中，点击菜单中的【新建虚拟机】按键。
1. 在弹出的【新建虚拟机】窗口中，选择基于模板为Windows7_Template（在上述过程中所创建的模板），输入虚拟机的名称（必填）、描述和注释（选填），其他配置保持默认配置，你也可以根据需要更改相关的配置。
1. 点击【确定】后，虚拟机创建成功，虚拟机的状态变化为image Locked -> Down，虚拟机磁盘的状态变化为Locked -> Up。
1. 选择该虚拟机，点击菜单中的运行图标或右键选择【运行】，运行虚拟机，虚拟机的状态变化为Powering Up -> Up。
1. 点击菜单中的控制台图标或右键选择【控制台】，能够打开控制台连接到虚拟机，虚拟机能够正常使用。
