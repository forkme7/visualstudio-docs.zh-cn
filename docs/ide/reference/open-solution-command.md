---
title: “打开解决方案”命令
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.opensolution
helpviewer_keywords:
- Open Solution command
- File.OpenSolution command
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 652305e6d5d360169645e7801e788b39b8982400
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="open-solution-command"></a>“打开解决方案”命令
打开一个现有解决方案，关闭其他所有打开的解决方案。

## <a name="syntax"></a>语法

```
File.OpenSolution filename
```

## <a name="arguments"></a>自变量
 `Filename`

 必须的。 要打开的解决方案的完整路径和文件名。

 `filename` 参数的语法要求用引号将包含空格的路径括起来。

## <a name="remarks"></a>备注
 键入内容时，自动完成功能会尝试查找正确的路径和文件名。

## <a name="example"></a>示例
 此示例打开解决方案 Test1.sln。

```
>File.OpenSolution "c:\MySolutions\Test1\Test1.sln"
```

## <a name="see-also"></a>请参阅

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [“命令”窗口](../../ide/reference/command-window.md)
- [“查找/命令”框](../../ide/find-command-box.md)
- [Visual Studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)