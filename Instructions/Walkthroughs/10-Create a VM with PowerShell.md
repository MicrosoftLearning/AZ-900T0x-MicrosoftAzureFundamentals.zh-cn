---
wts:
  title: 10 - 使用 PowerShell 创建 VM（10 分钟）
  module: 'Module 03: Describe core solutions and management tools'
ms.openlocfilehash: a6c6e26b535658ebb01beac8037adcb5c15dc6e8
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/27/2022
ms.locfileid: "137907465"
---
# <a name="10---create-a-vm-with-powershell-10-min"></a>10 - 使用 PowerShell 创建 VM（10 分钟）

在本演练中，我们将配置 Cloud Shell，使用 Azure PowerShell 模块创建资源组和虚拟机，并查看 Azure 顾问建议。 

# <a name="task-1-configure-the-cloud-shell"></a>任务 1：配置 Cloud Shell 

在此任务中，我们将配置 Cloud Shell。 

1. 登录到 [Azure 门户](https://portal.azure.com)。**你可以在资源选项卡（此“说明”选项卡旁边！）中找到登录凭据**
2. 单击 Azure 门户右上方的图标，在 Azure 门户中打开 Azure Cloud Shell。

    ![Azure 门户“Azure Cloud Shell”图标的屏幕截图。](../images/1002.png)

3. 提示选择“Bash”或“PowerShell”时，选择“PowerShell”  。

4. 在“你没有安装任何存储”屏幕中，选择“显示高级设置”，然后填写以下信息 

    | 设置 | 值 |
    |  -- | -- |
    | 资源组 | **新建资源组** |
    | 存储帐户（新建一个帐户并使用全局唯一名称，例如 cloudshellstoragemystorage） | cloudshellxxxxxxx |
    | 文件共享（新建） | shellstorage |

5. 选择“创建存储”

# <a name="task-2-create-a-resource-group-and-virtual-machine"></a>任务 2：创建资源组和虚拟机

在此任务中，我们将使用 PowerShell 创建资源组和虚拟机。  

1. 确保在“Cloud Shell”窗格左上方的下拉菜单中选中“PowerShell”。

2. 在 Powershell 窗口中运行以下命令，验证新资源组。 按 Enter 运行该命令。

    ```PowerShell
    Get-AzResourceGroup | Format-Table
    ```

3. 将以下命令粘贴到终端窗口，创建虚拟机。 

    ```PowerShell
    New-AzVm `
    -ResourceGroupName "myRGPS" `
    -Name "myVMPS" `
    -Location "East US" `
    -VirtualNetworkName "myVnetPS" `
    -SubnetName "mySubnetPS" `
    -SecurityGroupName "myNSGPS" `
    -PublicIpAddressName "myPublicIpPS"
    ```
    
4. 当系统出现提示时，提供将被配置为该虚拟 machines.azureadmin 上的本地管理员帐户的用户名 (azureuser) 和密码 (Pa$$w0rd1234) 

5. 创建 VM 后，关闭 Cloud Shell 窗格的 PowerShell 会话。

6. 在 Azure 门户中，搜索“虚拟机”并验证 myVMPS 是否正在运行 。 这可能需要几分钟的时间。

    ![此屏幕截图显示了“虚拟机”页面，其中 myVMPS 处于正在运行的状态。](../images/1001.png)

7. 访问新虚拟机并查看“概述”和“联网”设置，以验证是否已正确部署你的信息。 

# <a name="task-3-execute-commands-in-the-cloud-shell"></a>任务 3：在 Cloud Shell 中执行命令

在此任务中，我们将练习从 Cloud Shell 执行 PowerShell 命令。 

1. 单击 Azure 门户右上方的图标，在 Azure 门户中打开 Azure Cloud Shell。

2. 确保在“Cloud Shell”窗格左上方的下拉菜单中选中“PowerShell”。

3. 检索有关你的虚拟机的信息，包括名称、资源组、位置和状态。 注意 PowerState 为“正在运行”。

    ```PowerShell
    Get-AzVM -name myVMPS -status | Format-Table -autosize
    ```

4. 使用以下命令停止虚拟机。 

    ```PowerShell
    Stop-AzVM -ResourceGroupName myRGPS -Name myVMPS
    ```
5. 出现提示时，确认（选择“是”）操作。 等待至显示“成功”状态。

6. 验证你的虚拟机状态。 PowerState 现在应为“解除分配”。 你还可以在门户中验证虚拟机状态。 关闭 Cloudshell。

    ```PowerShell
    Get-AzVM -name myVMPS -status | Format-Table -autosize
    ```

# <a name="task-4-review-azure-advisor-recommendations"></a>任务 4：查看 Azure 顾问建议

**注意：** “使用 Azure CLI 创建 VM”实验室中存在同样的任务。 

在此任务中，我们将查看针对虚拟机的 Azure 顾问建议。 

1. 从“所有服务”边栏选项卡，搜索并选择“顾问” 。 

2. 在“顾问”边栏选项卡中，选择“概述”。 请注意，按可靠性、安全性、性能和成本对建议进行分组。 

    ![顾问“概述”页面的屏幕截图。 ](../images/1003.png)

3. 选择“所有建议”并花一些时间查看每个建议和建议的操作。 

    **注意：** 建议会根据资源情况而有所不同。 

    ![顾问“所有建议”页面的屏幕截图。 ](../images/1004.png)

4. 请注意，可将建议下载为 CSV 或 PDF 文件。 

5. 请注意，你可以创建警报。 

6. 如有时间，请继续尝试使用 Azure PowerShell。 

恭喜！ 你已配置了 Cloud Shell，使用 PowerShell 创建了虚拟机，使用 PowerShell 命令进行了练习，并查看了顾问建议。

**注意**：为了避免产生额外费用，可以选择删除此资源组。 搜索资源组，单击你的资源组，然后单击“删除资源组”。 验证资源组的名称，然后单击“删除”。 关注“通知”，了解删除操作的进度。
