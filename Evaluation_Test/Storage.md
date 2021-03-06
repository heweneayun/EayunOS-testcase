# 配置存储
* 摘要

  EayunOS虚拟化管理中心支持同时使用不同类型的存储，可以在同一个数据中心里新建不同类型的存储域。但只有一个存储域能够作为该数据中心的主存储域。

## 添加NFS存储

1. 登录到Engine管理端，在左侧树形面板中点击【展开所有】按键，在默认数据中心的默认集群下点击选择【存储】。
1. 在右侧的详细列表中，点击菜单中的【新建域】按键。
1. 在弹出的【新建域】窗口中，选择域功能/存储类型为【Data/NFS】，输入域的名称（必填）、描述和注释（选填），选择使用主机，在导出路径中填写配置的NFS域的路径，格式为FQDN://path或IP://path，其他配置保持默认配置。
1. 点击【确定】，NFS数据域创建成功，数据域的状态变化为Locked -> Active。

## 添加iSCSI数据域

1. 登录到Engine管理端，在左侧树形面板中点击【展开所有】按键，在默认数据中心的默认集群下点击选择【存储】。
1. 在右侧的详细列表中，点击菜单中的【新建域】按键。
1. 在弹出的【新建域】窗口中，选择域功能/存储类型为【Data/iSCSI】，输入域的名称（必填）、描述和注释（选填），选择使用主机。
1. 在下方的窗口中，填写iSCSI的地址（可以使用IP也可以使用FQDN），端口为3260，点击【发现】。
1. 在发现的目标列表中，选择一个要target，点击右侧的登录图标。
1. 点击target前方的【+】图标，展开这个target下的所有LUN，勾选要添加的LUN，点击【确定】。
1. iSCSI数据域创建成功，数据域的状态变化为Locked -> Active。
