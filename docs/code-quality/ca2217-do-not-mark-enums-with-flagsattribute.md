---
title: CA2217：不要使用 FlagsAttribute 标记枚举
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
helpviewer_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
dev_langs:
- VB
- CSharp
- CPP
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 12cc5f9fc58ac533d118b693587cf807f44b288f
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2018
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217：不要使用 FlagsAttribute 标记枚举

|||
|-|-|
|TypeName|DoNotMarkEnumsWithFlags|
|CheckId|CA2217|
|类别|Microsoft.Usage|
|是否重大更改|非重大更改|

## <a name="cause"></a>原因

外部可见的枚举将标有<xref:System.FlagsAttribute>，和它具有一个或多个值不是 2 的两个或其他组合幂该枚举定义值。

## <a name="rule-description"></a>规则说明

枚举应具有<xref:System.FlagsAttribute>存在仅当在枚举中定义的每个值是两个或的组合的幂定义值。

## <a name="how-to-fix-violations"></a>如何解决冲突

若要修复与此规则的冲突，移除<xref:System.FlagsAttribute>枚举中。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告

不禁止显示此规则发出的警告。

## <a name="example-that-should-not-have-the-attribute"></a>不应具有属性的示例

下面的示例演示一个枚举， `Color`，包含值 3。 3 不是两个或定义的值的任意组合的幂。 `Color`枚举不应标记为<xref:System.FlagsAttribute>。

[!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]

## <a name="example-that-should-have-the-attribute"></a>应具有属性的示例

下面的示例演示一个枚举， `Days`，满足的要求标有<xref:System.FlagsAttribute>。

[!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]

## <a name="related-rules"></a>相关的规则

[CA1027：用 FlagsAttribute 标记枚举](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>请参阅

- <xref:System.FlagsAttribute?displayProperty=fullName>
