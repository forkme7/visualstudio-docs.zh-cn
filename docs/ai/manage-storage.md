---
ms.technology: vs-ai-tools
ms.openlocfilehash: b941d0ba55c540de4bda1cb0f9c4ed18ceab524f
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/28/2018
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>浏览存储以上传数据或下载模型和日志

可以在远程计算机或 Azure 文件共享上访问所有存储，以上传数据或下载模型和日志。 或者，如果要访问特定作业的日志和作业输出，也可以在作业浏览器中执行相同的操作

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>访问远程计算器或文件共享上的所有数据
1. 打开“服务器资源管理器”
2. 展开远程计算机或 Batch AI 计算上下文
3. 右键单击“存储”，然后单击“浏览”

    ![storage](media\manage-storage\browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>在远程计算机或文件共享上访问作业特定数据
1. 打开 [“作业历史记录”](job-details.md)
2. 选择作业
3. 单击“工作文件夹”，或单击 StdOut/Stderr 快速访问这些重要的日志文件

    ![storage](media\manage-storage\job-workingfolder.png)
