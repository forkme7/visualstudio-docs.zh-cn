---
title: "使用命令行参数安装 Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 04/06/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 9328c347d548a03a536cea16bd5851817c03d5a2
ms.openlocfilehash: 09c6971e21e48d250e3a9869860459fd8cbbb50f
ms.lasthandoff: 04/10/2017

---
# <a name="use-command-line-parameters-to-install-visual-studio-2017"></a>使用命令行参数安装 Visual Studio 2017
通过命令提示符安装 Visual Studio 2017 时，可以使用各种命令行参数来控制或自定义安装。 通过命令行可以进行以下操作：
- 启动预先选定了特定选项的安装。
- 自动执行安装过程。
- 创建安装文件的缓存（布局）以备日后使用。

命令行选项与安装引导程序结合使用，安装引导程序是启动下载过程的小型（大约 1 MB）文件。 安装引导程序是你从 Visual Studio 网站下载时启动的第一个可执行文件。 通过下面这些链接，可以直接获取要安装的产品版本的最新版安装引导程序：

* [Visual Studio 2017 Enterprise](https://aka.ms/vs/15/release/vs_enterprise.exe)
* [Visual Studio 2017 Professional](https://aka.ms/vs/15/release/vs_professional.exe)
* [Visual Studio 2017 Community](https://aka.ms/vs/15/release/vs_community.exe)

## <a name="list-of-command-line-parameters"></a>命令行参数列表  
 Visual Studio 命令行参数不区分大小写。

>  语法：`vs_enterprise.exe [command] <options>...`

（将 `vs_enterprise.exe` 替换为要安装的相应产品版本。 有关示例，请参阅[命令行参数示例](command-line-parameter-examples.md)页。）


| **命令** | **描述** |
| ----------------------- | --------------- |
| (空白) | 安装产品。 |
| ```modify``` | 修改已安装的产品。 |
| ```update``` | 更新已安装的产品。 |
| ```repair``` | 修复已安装的产品。 |
| ```uninstall``` | 卸载已安装的产品。 |


| **安装选项** | **描述** |
| ----------------------- | --------------- |  
| ```--installPath <dir>``` | 要对其执行操作的实例的安装目录。 对于 install 命令，这是该实例的安装位置。 对于其他命令，这是以前安装的实例的安装位置。 |
| ```--layout <dir>``` | **可选**：指定一个目录来创建脱机安装缓存。 选择此选项也会隐式添加“--wait”选项。 如果通过批处理文件调用，此命令会先完成，然后再执行批处理文件中的下一个命令。 |
| ```--lang <language-locale>``` *[<语言-区域设置> ...]* | **可选**：与 --layout 结合使用，用包含指定语言的资源包让脱机安装缓存做好准备。 有关详细信息，请参阅本页的[语言区域设置列表](#list-of-language-locales)部分。|
| ```--addProductLang <language-locale>``` | **可选**：在安装或修改操作期间，这可确定要在产品中安装的 UI 语言包。 可以在命令行处多次使用此选项，从而添加多个语言包。 如果不存在此参数，安装将使用计算机区域设置。 有关详细信息，请参阅本页的[语言区域设置列表](#list-of-language-locales)部分。|
| ```--removeProductLang <language-locale>``` | **可选**：在安装或修改操作期间，这可确定要从产品中删除的 UI 语言包。 可以在命令行处多次使用此选项，从而添加多个语言包。 有关详细信息，请参阅本页的[语言区域设置列表](#list-of-language-locales)部分。|
| ```--add <workload or component ID>``` *[<工作负荷或组件 ID> ...]* | **可选**：要添加的一个或多个工作负荷或组件 ID。 将安装项目的所需组件，而不是建议组件或可选组件。 可以使用“--includeRecommended”和/或“--includeOptional”全局控制附加组件。 若要更精细地控制，可以向 artifactId 追加“;includeRecommended”和/或“;includeOptional”（例如，“--add Workload1;includeRecommended”或“--add Workload2;includeOptional;includeRecommended”）。 有关详细信息，请参阅[工作负载和组件 ID](workload-and-component-ids.md) 页。|
| ```--remove <workload or component ID>``` *[<工作负荷或组件 ID> ...]* | **可选**：要删除的一个或多个工作负荷或组件 ID。 有关详细信息，请参阅[工作负载和组件 ID](workload-and-component-ids.md) 页。|
| ```--in <path>``` | **可选**：响应文件的 URI 或路径。  |
| ```--all``` | **可选**：是否安装产品的所有工作负荷和组件。 |
| ```--allWorkloads``` | **可选**：安装所有工作负荷及其所需的组件，不安装建议组件或可选组件。 |
| ```--includeRecommended``` | **可选**：包含所有已安装工作负载的推荐组件，但不包含可选组件。 可使用 --allWorkloads 或 --add 指定工作负荷。 |
| ```--includeOptional``` | **可选**：包含所有已安装工作负荷的可选组件，但不包含建议组件。 可使用 --allWorkloads 或 --add 指定工作负荷。  |
| ```--quiet, -q``` | **可选**：执行安装时不显示任何用户界面。 |
| ```--passive, -p``` | **可选**：显示用户界面，但不请求用户进行任何交互。 |
| ```--norestart``` | **可选**：如果存在，带有 --passive 或 --quiet 的命令不会自动重启计算机（如有必要）。 如果既未指定 --passive 也未指定 --quiet，则忽略此参数。  |
| ```--nickname <name>``` | **可选**：此参数定义分配给已安装产品的别名。 别名长度不能超过 10 个字符。  |
| ```--productKey``` | **可选**：这定义要用于已安装产品的产品密钥。 它由 25 个字母数字字符组成，格式为“xxxxx-xxxxx-xxxxx-xxxxx-xxxxx”或“xxxxxxxxxxxxxxxxxxxxxxxxx”。 |
| ```--help, --?, -h, -?``` | 显示此页的脱机版本。 |

> 注意：在指定多个工作负荷和组件时，必须对每个项重复 `--add` 或 `--remove` 命令行开关。

| **高级安装选项** | **描述** |
| ----------------------- | --------------- |  
| ```--channelId <id>``` | **可选**：将要安装的实例的通道 ID。 如果指定了 --installPath，则此参数对于 install 命令是必需参数，对于其他命令则可忽略。 |
| ```--channelUri <uri>``` | **可选**：通道清单的 URI。 此参数可用于 install 命令；其他命令则可忽略。 |
| ```--installChannelUri <uri>``` | **可选**：要用于安装的通道清单的 URI。 由 --channelUri 指定的 URI（指定 --installChannelUri 时必须指定此 URI）将用于检测更新。 如果不想更新，则必须指定不带参数的 --channelUri。 此参数可用于 install 命令；其他命令则可忽略。 |
| ```--installCatalogUri <uri>``` | **可选**：要用于安装的目录清单的 URI。 如果指定此参数，通道管理器在使用安装通道清单中的 URI 之前，会先尝试从此 URI 下载目录清单。 此参数用于支持脱机安装，安装期间会使用已下载的产品目录创建布局缓存。 此参数可用于 install 命令；其他命令则可忽略。 |
| ```--productId <id>``` | 将要安装的实例的产品 ID。 如果指定了 --installPath，则此参数对于 install 命令是必需参数，对于其他命令则可忽略。 |
| ```--wait``` | **可选**：进程将等待安装完成后才会返回退出代码。 在需要等待安装完成以处理来自该安装的返回代码的自动安装中，这非常有用。 |
| ```--locale <language-locale>``` | **可选**：更改安装程序本身的用户界面的显示语言。 将保留设置。 有关详细信息，请参阅本页的[语言区域设置列表](#list-of-language-locales)部分。|

## <a name="list-of-workload-ids-and-component-ids"></a>工作负荷 ID 和组件 ID 列表
有关按 Visual Studio 产品排序的工作负载和组件 ID 的列表，请参阅 [Visual Studio 2017 工作负载和组件 ID](workload-and-component-ids.md) 页面。

## <a name="list-of-language-locales"></a>语言区域设置列表
| **语言-区域设置** | **语言** |
| ----------------------- | --------------- |  
| cs-CZ | 捷克语 |
| de-DE | 德语 |
| zh-CN | 英语 |
| es-ES | 西班牙语 |
| fr-FR | 法语 |
| it-IT | 意大利语 |
| ja-JP | 日语 |
| ko-KR | 朝鲜语 |
| pl-PL | 波兰语 |
| pt-BR | 葡萄牙语 - 巴西 |
| ru-RU | 俄语 |
| tr-TR | 土耳其语 |
| zh-CN | 中文 - 简体 |
| zh-TW | 中文 - 繁体 |


## <a name="error-codes"></a>错误代码
`%ERRORLEVEL%` 环境变量设为下列值之一，具体视操作结果而定：

| **值** | **结果** |
| --------- | ---------- |
| 0 | 操作成功完成 |
| 3010 | 操作成功完成，但安装需要重启才能使用 |
| 其他 | 发生了故障，请查看日志，了解详细信息 |

每个操作都会在 `%TEMP%` 目录中生成多个日志文件来指明安装进度。 按日期对文件夹进行排序，然后查找以“`dd_bootstrapper`”、“`dd_client`”和“`dd_setup`”开头的文件，分别查找安装引导程序、安装程序应用和安装程序引擎。

## <a name="see-also"></a>另请参阅

 * [安装 Visual Studio 2017](install-visual-studio.md)
 * [创建 Visual Studio 2017 的脱机安装](create-an-offline-installation-of-visual-studio.md)
 * [Visual Studio 2017 安装的命令行参数示例](command-line-parameter-examples.md)
 * [报告 Visual Studio 2017 的问题](../ide/how-to-report-a-problem-with-visual-studio-2017.md)
