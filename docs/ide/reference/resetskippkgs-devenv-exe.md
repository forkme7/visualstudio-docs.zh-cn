---
title: -ResetSkipPkgs (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6199bf96bc631cf1018b2cb72a4d3c3cf7c703cc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
清除由希望避免 VSPackages 加载问题的用户添加到 VSPackages 的跳过加载选项，然后启动 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。

## <a name="syntax"></a>语法

```
Devenv /ResetSkipPkgs
```

## <a name="remarks"></a>备注
 SkipLoading 标记的状态禁用 VSPackage 加载，清除这些标记可重新启动 VSPackage 的加载。

## <a name="example"></a>示例
 以下示例清除了所有 SkipLoading 标记。

```
Devenv.exe /ResetSkipPkgs
```

## <a name="see-also"></a>请参阅

- [Devenv 命令行开关](../../ide/reference/devenv-command-line-switches.md)