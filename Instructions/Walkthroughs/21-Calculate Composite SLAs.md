---
wts:
  title: 21 - 计算复合 SLA（5 分钟）
  module: 'Module 06: Describe Azure cost management and service level agreements'
ms.openlocfilehash: 1d27d18cd1a0b2ad6ab09c7fc65a51d5a8f13711
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/27/2022
ms.locfileid: "137907304"
---
# <a name="21---calculate-composite-slas-5-min"></a>21 - 计算复合 SLA（5 分钟）

在本演练中，我们将确定 Azure 服务的可用性 SLA，然后计算基于应用程序复合 SLA 的预期可用性。

我们的示例应用程序由这些 Azure 服务组成。 我们不会深入探讨体系结构配置和注意事项，这里的目的是提供一个高级示例。

+ 应用服务：托管应用程序。
+ Azure AD B2C：对用户登录进行身份验证和管理配置文件。
+ **应用程序网关**：管理应用程序访问和缩放。 
+ **Azure SQL 数据库**：存储应用程序数据。 

# <a name="task-1-determine-the-sla-uptime-percentage-values-for-our-application"></a>任务 1：确定应用程序的 SLA 正常运行时间百分比值

1. 在浏览器中，转到 [Azure 服务的 SLA 摘要](https://azure.microsoft.com/en-us/support/legal/sla/summary/)页面。

2. 找到“应用服务”SLA 运行时间值 “99.95％”。 单击“查看完整详细信息”，然后展开“SLA 详细信息”。 注意“每月运行时间百分比”和“服务额度”。

3. 返回 SLA 网页，找到“Azure Active Directory B2C”服务并确定 SLA 运行时间值“99.9％”。 

4. 找到“应用程序网关”SLA 运行时间值 99.95％。 

5. Azure SQL 数据库使用高级层，但未针对区域冗余部署进行配置。 找到“Azure SQL 数据库”SLA 运行时间值“99.99％”。 

    **注意**：Azure SQL 数据库的不同配置和部署有不同的运行时间值。 在计划部署与配置以及计算其成本时，清楚所需的运行时间值很重要。 运行时间的微小变化会影响服务成本，并可能增加配置的复杂性。 在 Azure SLA 摘要网页上，你可能还会对一些其他服务感兴趣，例如虚拟机、储存帐户和 Cosmos DB。

# <a name="task-2-calculate-the-application-composite-sla-percentage-uptime"></a>任务 2：计算应用程序复合 SLA 百分比运行时间

1. 如果构成应用程序的任一服务不可用，则用户将无法登录和使用该应用程序。 因此，应用程序的总运行时间的构成如下：

    应用服务 % 运行时间 X Azure AD B2C % 运行时间 X Azure 应用程序网关 % 运行时间 X Azure SQL 数据库 % 运行时间  =  总 % 运行时间    

    换成百分比值如下：

    99.95% X 99.9% X 99.95% X 99.99%  =  99.79%    

    这是使用当前服务和体系结构的应用程序的基于 SLA 的预期可用性。

恭喜！ 你已确定了示例应用程序中每个服务的基于 SLA 的正常运行时间，并计算了该应用程序的基于复合 SLA 的预期可用性。
