# 添加主机
* 摘要
  EayunOS主机的添加除了可以通过EayunOS系统中的【EayunOS Manager】来注册外，还可以直接从管理门户中添加主机。

1. 可以在创建完数据中心后，在【新建数据中心-引导操作】中点击【配置主机】来创建主机；如果点击了【以后再配置】，可以点击数据中心菜单中的【引导操作】，重新打开该窗口，点击【配置主机】进行配置；或点击树形面板中的【展开所有】按键，选择默认数据中心的集群，点击主机，在其菜单中点击【新建】按键。
1. 在弹出的【新建主机】窗口中，可以对左侧选项进行一一配置，在本实验中，配置如下：

  * 在【常规】标签中输入名称、描述、注释，其他保持默认配置。
  * 在【电源管理】【SPM】【控制台】【网络供应商】标签下的配置使用默认配置。

1. 点击【确定】，弹出【电源管理配置】窗口，提示电源管理为配置，是否继续，点击【确定】继续，或点击【配置电源管理】为主机配置电源管理，本实验中点击【确定】。
1. 创建主机成功，仍然显示【新建数据中心-引导操作】窗口，可以点击【以后再配置】跳过剩下的操作，也可以继续进行（如果是直接在主机标签下新建，则没有【新建数据中心-引导操作】的窗口显示，会返回到主机列表中，主机由于没有配置电源管理而在主机名前面显示一个警告的小叹号，主机状态变化为Installing -> Up。

> #### 注意
> 主机的添加需要打开SSH并配置root密码。
