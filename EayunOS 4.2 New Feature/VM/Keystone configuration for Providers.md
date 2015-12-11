# Keystone configuration for Providers

# 为不同的OpenStack服务提供不同的KeystoneUrl值

**测试说明**：在ovirt3.6之前的版本中，若要使用OpenStack中提供的服务，需要在命令行中为所有的OpenStack服务设置了一个全局的Keystoneurl值用来验证OpenStack服务。在ovirt3.6的版本中，去掉了在命令行中为OpenStack服务设置全局Keystoneurl值的操作，取而代之的是在ovirt界面中为不同的OpenStack服务配置不同的Keystoneurl值。本测试以在ovirt中添加Glance服务为例进行测试。本测试用例在测试之前已经设置好openstack供应商的Glance服务的URL，同时设置好验证Glance服务的keystone的URL值，直接使用即可。

|用例编号|测试目的|操作|预期结果|实际结果|备注|
|--------|--------|----|--------|--------|----|
|0100000 |在ovirt3.6中可以为不同的OpenStack服务提供不同的Keystoneurl值。|<ol><li>登录ovirt管理平台，在左侧的树形列表中选中【外部供应商】标签。</li><li>点击【添加】按钮，弹出【添加供应商】窗口。</li><li>输入要添加供应商的【名称】。</li><li>在【类型】下拉别表中选择OpenStack Image。在【供应商 URL】项中输入OpenStack Glance服务所在机器的URL以及它的端口号。</li><li>选择【要求验证】输入Openstack Glance服务的【用户名】、【密码】和【Tenant】。用户名和密码用的是Glance服务在Keystone注册的用户名和密码，同时填写tenant，默认的tenant为services，具体视情况而定。之后在【验证URL】选项填写Keystoneurl的值。</li><li>点击【测试】按钮进行访问供应商测试。</li><li>测试成功之后，点击【确定】按钮，将成功添加OpenStack Glance服务。|点击【测试】按钮之后，测试成功通过。|<ol><li>点击【测试】按钮之后会在左侧出现一个信息提示框，信息为：测试成功，访问了供应商。</li><li>点击【确定】按钮成功添加OpenStack Glance服务。|||

  form:https://bugzilla.redhat.com/show_bug.cgi?id=1157999
