# 创建和使用桌面虚拟机

|用例编号|测试目的|操作|预期结果|实际结果|备注| 
|--------|--------|----|--------|--------|----|
|1|Windows模板创建虚拟机|     在左侧树形面板中点击【展开所有】按键，在默认数据中心下的默认集群下点击【虚拟机】，在右侧的虚拟机详细列表中，点击菜单中的【新建虚拟机】按键，在弹出的【新建虚拟机】窗口中，选择基于模板为Windows7_Template（在上述过程中所创建的模板），输入虚拟机的名称（必填）、描述和注释（选填），其他配置保持默认配置，你也可以根据需要更改相关的配置，点击【确定】后，虚拟机创建成功，虚拟机的状态变化为image Locked -> Down，虚拟机磁盘的状态变化为Locked -> Up，选择该虚拟机，点击菜单中的运行图标或右键选择【运行】，运行虚拟机，虚拟机的状态变化为Powering Up -> Up，点击菜单中的控制台图标或右键选择【控制台】，能够打开控制台连接到虚拟机，虚拟机能够正常使用 |利用Windows模板创建虚拟机成功|成功利用Windows模板创建虚拟机||
|2|虚拟机分配UserRole权限 |     管理员从管理门户登录到Engine管理端，点击【虚拟机】，在该虚拟机（本实验选择上述创建的Windows 7虚拟机）的【权限】子标签下，点击菜单中的【添加】按键，在弹出的【添加权限给用户】窗口中，在【搜索】处输入要赋予权限的用户名，点击【执行】，列表下显示该用户，点击勾选该用户，在窗口下方【要分配的角色】下拉列表中选择【UserRole】，点击【确定】，成功分配UserRole权限给虚拟机，在该虚拟机的【权限】子标签中显示拥有UserRole权限的用户 |成功为虚拟机分配UserRole权限 |成功为虚拟机分配UserRole权限||
|3| 使用虚拟机池之新建虚拟机池|     点击左侧树形面板中的【系统】，在右侧详细列表中点击【池】标签，点击菜单中的【新建】按键，在弹出的【新建池】窗口中，选择基于模板（本实验中选择Windows7_Template模板），输入池名称（必填）、描述和注释（选填），输入这个池中的虚拟机数量（本实验中填写6）、每个用户的最大虚拟机数目（本实验中填写2），其他配置可以保持默认配置，如果有需要可以修改相应配置，点击【确定】，虚拟机池开始创建，观察到详细列表中分配的虚拟机数量增加，直到增加到设置的虚拟机数量；在该池的【虚拟机】子标签下，看到虚拟机被依次创建，以【池名称-序号】命名，创建完毕后，虚拟机状态为Down |虚拟机池新建成功|虚拟机池新建成功|
|4|使用虚拟机池之分配UserRole权限给虚拟机池 |     选择需要分配权限的虚拟机池，点击虚拟机池的【权限】子标签，点击菜单中的【添加】按键，在弹出的【添加权限给用户】窗口中，在搜索下选择域，输入用户名，点击【执行】，搜索结果会显示在列表中，勾选需要分配权限的用户，在窗口下方的【要分配的角色】下拉菜单中选择【UserRole】，点击【确定】，添加权限成功，在权限列表中显示用户及相应角色，该用户拥有访问虚拟机池的权限 |成功分配UserRole权限给虚拟机池 |成功分配UserRole权限给虚拟机池|
|5|使用虚拟池之分配虚拟机|         登录到用户门户，选择所创建的虚拟机池，点击该虚拟机池的绿色的【运行】图标，会显示【采用虚拟机】字样，此时从池中分配出一台虚拟机，并将该虚拟机运行，能够被用户使用，再次点击该虚拟机池的绿色的【运行】图标，会显示【采用虚拟机】字样，此时可以从池中再次分配一台虚拟机，能够被用户使用，此操作可重复，直至池中无虚拟机为止，池中的虚拟机是无状态的（stateless），因此对虚拟机所做的一些该变会在虚拟机关闭后销毁 |分配虚拟机成功|成功分配虚拟机|
|6|使用虚拟机池之释放虚拟机|登录到用户门户，记录虚拟机的名称，创建一个文件（本实验中创建一个文件，名为test.txt），点击红色的【关闭】图标，关闭虚拟机并将虚拟机释放，虚拟机返回虚拟机池，选择虚拟机池，再次点击绿色的【运行】图标，会显示【采用虚拟机】的字样，此时从池中分配出一台虚拟机，并将该虚拟机运行，该虚拟机可能不是原先关闭释放的虚拟机，请核对虚拟机名称，如果是之前关闭的虚拟机，打开该虚拟机，看到原本创建的文件已经被销毁 |虚拟机释放成功|虚拟机释放成功|
|7|使用虚拟机池之分离虚拟机池中的虚拟机|     虚拟机池是无状态的虚拟机，可以从池中分离出来，在【池】标签下，点击选择要分离虚拟机的池，点击池的【虚拟机】子标签，选择要分离的虚拟机，点击子标签中的【分离】按键，在弹出的【分离虚拟机】确认框中，点击【确定】，虚拟机从池中分离出去，虚拟机不再是无状态的虚拟机|分离虚拟机池中的虚拟机成功|分离虚拟机池中的虚拟机成功|
|8|使用虚拟机池之删除虚拟机池|     按照以上步骤分离池中的虚拟机（如果想一次分离多台虚拟机，可以使用shift选择连续的或ctrl选择不连续的多台虚拟机，进行分离操作），分离最后一台虚拟机时，弹出【分离虚拟机】确认框，在下方有提示：“注意：您选择了从池里删除所有虚拟机，这将把池自身也删除。”，点击【确定】，该虚拟机从池中分离，虚拟机池被删除，被分离的虚拟机显示在虚拟机列表中 |虚拟机删除成功|成功删除虚拟机|
