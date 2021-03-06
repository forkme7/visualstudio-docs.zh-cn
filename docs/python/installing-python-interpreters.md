---
title: 选择并安装 Python 解释程序
description: Visual Studio 中支持的 Python 解释器的完整列表，并简要说明了可以在哪里找到它们的安装程序。
ms.date: 02/20/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: ed5ac9e470b55281d1273bfe665be0813b37bf55
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/19/2018
---
# <a name="installing-python-interpreters"></a>安装 Python 解释器

默认情况下，在 Visual Studio 2017 中安装 Python 开发工作负载也会安装 Python 3（64 位）。 可以选择安装 32 位和 64 位版本的 Python 2、Python 3、Anaconda 2 和 Anaconda 3，如[安装](installing-python-support-in-visual-studio.md)中所述。

除了 Visual Studio 安装程序，还可以手动安装下表列出的任何解释器。 例如，如果在安装 Visual Studio 之前安装了 Anaconda 3，则不需要通过 Visual Studio 安装程序再次进行安装。

对于 Visual Studio 2015 及更早版本，必须手动安装其中一个解释器。

Visual Studio（所有版本）通过检查注册表（下面的 [PEP 514 - Windows 注册表中的 Python 注册](https://www.python.org/dev/peps/pep-0514/)）自动检测各个已安装的 Python 解释器及其环境。

如果 Visual Studio 并未检测到安装的环境，请参阅[手动标识现有环境](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment)。

Visual Studio 在 [Python 环境窗口](managing-python-environments-in-visual-studio.md)中显示所有已知环境，并自动检测现有解释器的更新。

| 解释器 | 描述 |
| --- | --- |
| [CPython](https://www.python.org/) | 最常用的“本机”解释器，32 位和 64 位版本可用（建议使用 32 位）。 包括最新的语言功能、最大的 Python 包兼容性、完整的调试支持以及与 [IPython](http://ipython.org/) 的互操作。 另请参阅：[Should I use Python 2 or Python 3?](http://wiki.python.org/moin/Python2orPython3)（应使用 Python 2 还是 Python 3？） 请注意，Visual Studio 2015 及更早版本不支持 Python 3.6，并且会生成错误“不支持 Python 版本 3.6”。 请改用 Python 3.5 或更早版本。 |
| [IronPython](https://github.com/IronLanguages/ironpython2) | Python 的 .NET 实现，32 位和 64 位版本可用，提供 C#/F#/Visual Basic 互操作、对 .NET API 的访问、标准 Python 调试（但不是 C++ 混合模式调试）和混合 IronPython/C# 调试。 但 IronPython 不支持虚拟环境。 |
| [Anaconda](https://www.continuum.io) | Python 提供技术支持的开放式数据科学平台，包括最新版本的 CPython 和大部分难以安装的包。 如果你不能做出决定，我们建议使用它。 |
| [PyPy](http://www.pypy.org/) | Python 的高性能跟踪 JIT 实现，适用于长时间运行的程序以及识别性能问题但找不到其他解决方法的情况。 可与 Visual Studio 配合使用，但对高级调试功能的支持有限。 |
| [Jython](http://www.jython.org/) | Java 虚拟机 (JVM) 上 Python 的实现。 与 IronPython 类似，Jython 中运行的代码可与 Java 类和库交互，但可能无法使用许多适用于 CPython 的库。 可与 Visual Studio 配合使用，但对高级调试功能的支持有限。 |

对于想要提供新形式的 Python 环境检测的开发人员，请参阅 [PTVS 环境检测](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (github.com)。

## <a name="moving-an-interpreter"></a>移动解释器

如果将现有解释器移到使用文件系统的新位置，则 Visual Studio 不会自动检测更改。

- 如果最初通过“Python 环境”窗口指定解释器的位置，则使用该窗口中的“配置”选项卡来编辑其环境，以确定新位置。 请参阅[手动标识现有环境](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment)。

- 如果使用安装程序安装解释器，则使用以下步骤在新位置重新安装解释器：

  1. 将 Python 解释器还原到其原始位置。
  2. 使用其安装程序卸载解释器，这会清除注册表项。
  3. 在所需位置重新安装解释器。
  4. 重新启动 Visual Studio，它应该会自动检测新位置来代替原来的位置。

遵循此过程，确保标识解释器位置的注册表项正确更新，以供 Visual Studio 使用。 使用安装程序还可以处理可能存在的任何其他副作用。

## <a name="see-also"></a>请参阅

- [管理 Python 环境](managing-python-environments-in-visual-studio.md)
- [为项目选择解释器](selecting-a-python-environment-for-a-project.md)
- [对依赖项使用 requirements.txt](managing-required-packages-with-requirements-txt.md)
- [搜索路径](search-paths.md)
- [“Python 环境”窗口参考](python-environments-window-tab-reference.md)