# 删除 Affinity 组

| **用例编号** | **测试目的** | **测试步骤** | **预期结果** | **实际结果** | **备注** |
| ------------ | ------------ | ------------ | ------------ | ------------ | -------- |
| 0080526 | 验证一旦删除了一个关联组，那么应用到属于这个关联组的虚拟机上的关联协议将不再有效。 | 1. 点击【虚拟机】标签，选择一台具有关联组的虚拟机。<br/>2. 点击【Affinity 组】子标签，此时会列出与该虚拟机有关的所有 Affinity 组的列表。<br/>3. 选择其中一个列表，点击【删除】按扭。 此时会弹出【删除 Affinity 组】窗口，您确定要删除下列条目吗？<br/>4. 点击【确定】。 | 【删除 Affinity 组】窗口自动关闭，Affinity 组列表中将不再有该关联组。 | 与预期结果一致。 | 
