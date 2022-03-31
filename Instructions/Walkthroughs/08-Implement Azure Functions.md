---
wts:
  title: 08 - 实现 Azure Functions（5 分钟）
  module: 'Module 03: Describe core solutions and management tools'
ms.openlocfilehash: 419d49832a4059e447d2621fe4f209dc5ada2474
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/27/2022
ms.locfileid: "137907469"
---
# <a name="08---implement-azure-functions-5-min"></a>08 - 实现 Azure Functions（5 分钟）

在本演练中，我们将创建一个函数应用，用于在出现 HTTP 请求时显示 Hello 消息。 

# <a name="task-1-create-a-function-app"></a>任务 1：创建函数应用 

在此任务中，我们将创建一个函数应用。

1. 登录 [Azure 门户](https://portal.azure.com)。

2. 在门户顶部的“搜索”栏中，搜索并选择“函数应用”，然后在“函数应用”边栏选项卡中，单击“+ 添加、+ 创建、+新建”   。

3. 在“函数应用”边栏选项卡的“基本信息”选项卡上，指定以下设置（将函数应用名称中的 xxxx 替换为字母和数字，使该名称在全局范围内唯一，并将所有其他设置保留为默认值）： 

    | 设置 | Value |
    | -- | --|
    | 订阅 | 保留提供的默认值 |
    | 资源组 | **新建资源组** |
    | Function App 名称 | function-xxxx |
    | 发布 | **代码** |
    | 运行时堆栈 | **.NET** |
    | 版本 | **3.1** |
    | 区域 | **美国东部** |

    注意 - 请记住更改 xxxx 以使其成为唯一的函数应用名称

4. 单击“查看 + 创建”，然后在验证成功后，单击“创建”以开始预配和部署新的 Azure 函数应用 。

5. 等待说明已创建资源的通知出现。

6. 部署完成后，在“部署”边栏选项卡上单击“转到资源”。 此外，导航回“函数应用”边栏选项卡，单击“刷新”并验证新创建的函数应用是否具有“正在运行”状态  。 

    ![带有新函数应用的“函数应用”页面的屏幕截图。](../images/0701.png)

# <a name="task-2-create-a-http-triggered-function-and-test"></a>任务 2：创建一个 HTTP 触发的函数并对其进行测试

在此任务中，我们将使用 Webhook + API 函数，用于在出现 HTTP 请求时显示消息。 

1. 在“函数应用”边栏选项卡上，单击新创建的函数应用。 

2. 在“函数应用”边栏选项卡的“函数”部分，单击“函数”，然后单击“+ 添加、+ 创建、+ 新建”  。

    ![此屏幕截图显示了如何在 Azure 门户中为“dot net 入门”窗格在 Azure Functions 中选择开发环境这一步骤。 突出显示用于新建门户内函数的显示元素。 突出显示元素为：展开函数应用、添加新函数、门户内和继续按钮。](../images/0702.png)

3. 右侧将显示“添加函数”弹出窗口。 在“选择模板”部分中，单击“HTTP 触发器” 。 单击“添加” 

    ![此屏幕截图显示了如何在 Azure 门户中为“dot net 入门”窗格在 Azure Functions 中创建函数这一步骤。 突出显示“HTTP 触发器”卡，以说明用于向 Azure 函数添加新 Webhook 的显示元素。](../images/0702a.png)

4. 在 HttpTrigger1 边栏选项卡的“开发人员”部分，单击“编码 + 测试”。 

5. 在“编码 + 测试”边栏选项卡上，查看自动生成的代码，并注意该代码旨在运行 HTTP 请求和日志信息。 另请注意，该函数将返回包含名称的 Hello 消息。 

    ![函数代码的屏幕截图。 突出显示 Hello 消息。](../images/0704.png)

6. 在函数编辑器顶部单击“获取函数 URL”。 

7. 请确保“密钥”下拉列表中的值设置为默认值，并单击“复制”以复制函数 URL  。 

    ![此屏幕截图显示了 Azure 门户中函数编辑器内的“获取函数 URL”窗格。 突出显示显示元素获取函数 URL 按钮、设置键下拉列表和复制 URL 按钮，以指示如何从函数编辑器中获取和复制函数 URL。](../images/0705.png)

8. 打开一个新的浏览器选项卡，并将复制的函数 URL 粘贴到 Web 浏览器的地址栏中。 当请求该页面时，该函数将运行。 请注意，返回的消息会指出函数需要请求正文中的名称。

    ![“请提供一个名称”这一消息的屏幕截图。](../images/0706.png)

9. 将 &name=*yourname* 附加到 URL 的末尾。

    **注意**：例如，如果你的名字是 Cindy，最终 URL 将与以下所示类似：`https://azfuncxxx.azurewebsites.net/api/HttpTrigger1?code=X9xx9999xXXXXX9x9xxxXX==&name=cindy`

    ![此屏幕截图显示了 Web 浏览器的地址栏中突出显示的函数 URL 和附加的示例用户名。 此外，突出显示 hello 消息和用户名，以说明主浏览器窗口中函数的输出。](../images/0707.png)

10. 按 Enter 键后，函数将运行并跟踪每个调用。 若要查看跟踪，请返回到门户“HttpTrigger1 \| 代码 + 测试”边栏选项卡，并单击“监视”。 可以通过选择时间戳来配置 Application Insights，然后单击“在 Application Insights 中运行查询”。

    ![此屏幕截图显示了在 Azure 门户的函数编辑器中运行函数所产生的跟踪信息日志。](../images/0709.png) 

恭喜！ 你已创建一个函数应用，当出现 HTTP 请求时，它会显示 Hello 消息。  

**注意**：为了避免产生额外费用，可以选择删除此资源组。 搜索资源组，单击你的资源组，然后单击“删除资源组”。 验证资源组的名称，然后单击“删除”。 关注“通知”，了解删除操作的进度。
