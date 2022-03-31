---
wts:
  title: 09 - 使用模板创建 VM（10 分钟）
  module: 'Module 03: Describe core solutions and management tools'
ms.openlocfilehash: d4d29b62fc5dfa2e050ac51fcf4d5067e8fd3283
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/27/2022
ms.locfileid: "137907601"
---
# <a name="09---create-a-vm-with-a-template-10-min"></a>09 - 使用模板创建 VM（10 分钟）

在本演练中，我们将使用快速启动模板部署虚拟机并检查监视功能。

# <a name="task-1-explore-the-quickstart-gallery-and-locate-a-template"></a>任务 1：了解快速入门库并找到模板 

在此任务中，我们将浏览 Azure 快速启动库并部署可创建虚拟机的模板。 

1. 在实验室环境中，打开一个新的浏览器窗口，然后输入 T https://azure.microsoft.com/en-us/resources/templates/?azure-portal=true 。 在该库中，你将找到许多最近更新的热门模板。 这些模板可自动部署 Azure 资源，包括安装常用软件包。 浏览多种不同类型的可用模板。

3. 选择“部署一个简单的 Windows VM”

4. 单击“**部署到 Azure**”按钮。 浏览器会话将自动重定向到 [Azure 门户](http://portal.azure.com/)。

  **注意**：“部署到 Azure”按钮使你能够通过 Azure 门户部署模板。 在此类部署过程中，系统将仅提示你输入少量的配置参数。 

5. 当系统出现提示时，请使用说明前面提供的凭据登录 Azure 订阅。

6. 单击“编辑模板”。 资源管理器模板使用 JSON 格式。 查看参数和变量。  然后找到虚拟机名称对应的参数。 将名称更改为“myVMTemplate”。 单击“保存”以保存更改。 

    ![突出显示 VM 名称更改的模板的屏幕截图。](../images/0901.png)

7. 现在配置模板所需的参数（将 DNS 标签前缀中的“xxxx”替换为字母和数字，以使标签在全局范围内唯一）。 所有其他设置均保留默认值。 

    | 设置| Value|
    |----|----|
    | 订阅 | 保留提供的默认值|
    | 资源组 | **新建资源组** |
    | 区域 | 保留默认值 |
    | 管理员用户名 | **azureuser** |
    | 管理员密码 | **Pa$$w0rd1234** |
    | DNS 标签前缀 | myvmtemplatexxxx |
    | OS 版本 | **2019-Datacenter** |


9. 单击“查看 + 创建”。

10. 监视你的部署。 

# <a name="task-2-verify-and-monitor-your-virtual-machine-deployment"></a>任务 2：验证和监视虚拟机部署

在此任务中，我们将验证虚拟机是否已正确部署。 

1. 从“所有服务”边栏选项卡，搜索并选择“虚拟机” 。

2. 确保已创建新的虚拟机。 

    ![“虚拟机”页面的屏幕截图。 显示并正在运行新 VM。](../images/0902.png)

3. 选择你的虚拟机，然后在“概述”窗格中选择“监视”选项卡，向下滚动以查看监视数据 。

    **注意**：监视时间范围可以在 1 小时和 30 天之间进行调整。

4. 查看提供的不同图表，包括 CPU（平均值）、网络（总计）和磁盘字节（总计）  。 

    ![虚拟机监视图表的屏幕截图。](../images/0903.png)

5. 单击任何图表。 注意，你可以“添加指标”并更改图表类型。

6. 返回到“概述”边栏选项卡。 （向左滑动切换栏）
7. 单击“活动日志”（左窗格）。 活动日志记录创建或修改资源等事件。 

8. 单击“添加筛选器”，并尝试搜索其他事件类型和操作。 

    ![已选中事件类型的“添加筛选器”页面的屏幕截图。](../images/0904.png)

恭喜！ 你已成功从模板创建了资源并将该模板部署到了 Azure。

**注意**：为了避免产生额外费用，可以选择删除此资源组。 搜索资源组，单击你的资源组，然后单击“删除资源组”。 验证资源组的名称，然后单击“删除”。 关注“通知”，了解删除操作的进度。
