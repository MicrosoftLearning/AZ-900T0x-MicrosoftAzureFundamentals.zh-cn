---
wts:
  title: 02 - 创建 Web 应用（10 分钟）
  module: Module 02 - Core Azure Services (Workloads)
ms.openlocfilehash: 7b7acc368eff3c653579d54a12828e02a615a672
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/27/2022
ms.locfileid: "137907660"
---
# <a name="02---create-a-web-app-10-min"></a>02 - 创建 Web 应用（10 分钟）

在本演练中，我们将创建一个运行 Docker 容器的 Web 应用。 Docker 容器包含一条“欢迎”消息。 

Azure 应用服务实际上是四种服务的集合，所有这些服务都旨在帮助你托管和运行 Web 应用程序。 这四种服务（Web 应用、移动应用、API 应用和逻辑应用）看起来有所不同，但最终都以非常类似的方式运行。 Web 应用是这四种服务中最为常用的服务，并且是我们在本实验室中将要使用的服务。

# <a name="task-1-create-a-web-app"></a>任务 1：创建 Web 应用 

在此任务中，你将创建一个 Azure 应用服务 Web 应用。 

1. 登录到 [Azure 门户](http://portal.azure.com/)。 

2. 在“所有服务”边栏选项卡上，搜索并选择“应用服务”，然后单击“+ 添加、+ 创建、+ 新建”  

3. 在“Web 应用”边栏选项卡的“基本”选项卡上，指定以下设置（用字母和数字替换 Web 应用名称中的“xxxx”，使得该名称具有全局唯一性）  。 保留所有其他设置的默认值，包括应用服务计划。 

    | 设置 | Value |
    | -- | -- |
    | 订阅 | 使用提供的默认值 |
    | 资源组 | **新建资源组**|
    | 名称 | myDockerWebAppxxxx |
    | 发布 | Docker 容器 |
    | 操作系统 | **Linux** |
    | 区域 | **美国东部** |
    
    **注意：** 请记得更改 xxxx，确保 Web 应用名称是唯一的。

4. 单击“下一步”>“Docker”，并配置容器信息。  

    | 设置 | 值 |
    | -- | -- |
    | 选项 | 单个容器 |
    | 映像源 | **Docker 中心** |
    | 访问类型 | **Public** |
    | 映像和标记 | mcr.microsoft.com/azuredocs/aci-helloworld |
    
 **注意：** 启动命令是可选项，在本练习中不需要。

5. 单击“查看 + 创建”，然后单击“创建” 。 

# <a name="task-2-test-the-web-app"></a>任务 2：测试 Web 应用

在此任务中，我们将测试 Web 应用。

1. 等待 Web 应用进行部署。

2. 从“通知”中单击“前往资源” 。 

3. 在“概述”边栏选项卡上找到“URL” 。 将 URL 复制到剪贴板。

    ![Web 应用“属性”边栏选项卡的屏幕截图。 突出显示 URL。](../images/0801.png)

4. 在新的浏览器窗口中，粘贴 URL，然后按 Enter。 欢迎使用 Azure 容器实例！ 将显示欢迎消息。

    ![“欢迎访问 Azure 容器实例”页面的屏幕截图。](../images/0802.png)

5. 切换回 Web 应用的“概述”边栏选项卡并向下滚动。 你将注意到多个跟踪数据输入/输出和请求的图表。 如果重复几次步骤 4，应该能够看到这些图表中显示的相应遥测。 这包括请求数和平均响应时间。 

**注意**：为了避免产生额外费用，可以选择删除此资源组。 搜索资源组，单击你的资源组，然后单击“删除资源组”。 验证资源组的名称，然后单击“删除”。 关注“通知”，了解删除操作的进度。

恭喜，你成功创建了一个 Azure 应用服务。
