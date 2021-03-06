---
title: 代码生成和 T4 文本模板
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f0a2b6ef6e73fcc4b3fe754377bdad5fdc05eef2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="code-generation-and-t4-text-templates"></a>代码生成和 T4 文本模板
在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]中， *T4 文本模板* 是文本块与可生成文本文件的控制逻辑的混合体。 控制逻辑被编写为 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 或 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]中的程序代码的片段。 使用 Visual Studio 2015 Update 2 及更高版本时，可在 T4 模板指令中使用 C# 6.0 版功能。 所生成的文件可以是任何类型的文本，例如 Web 网页、资源文件或任何语言的程序源代码。

 T4 文本模板有两种类型：

 在应用程序中执行**运行时 T4 文本模板** （“预处理过的”模板）以生成文本字符串（通常作为其输出的一部分）。
例如，你可以创建一个模板来定义 HTML 页：

```
<html><body>
 The date and time now is: <#= DateTime.Now #>
</body></html>
```

 注意：该模板与生成的输出类似。 该模版与生成的输出的相似性有助于避免在想要更改时出现错误。

 此外，该模板包含程序代码的片段。 你可使用这些片段来重复文本节、创建条件节以及显示应用程序数据。

 若要生成输出，应用程序将调用由此模板生成的函数。 例如：

```csharp
string webResponseText = new MyTemplate().TransformText();

```

 你的应用程序可在未安装 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的计算机上运行。

 若要创建运行时模板，将“预处理过的文本模板”  文件添加到你的项目中。 或者，你也可以添加一个纯文本文件，并将其“自定义工具”  属性设置为 **TextTemplatingFilePreprocessor**。

 有关详细信息，请参阅[使用 T4 文本模板的运行时文本生成](../modeling/run-time-text-generation-with-t4-text-templates.md)。 有关模板的语法的详细信息，请参阅[编写 T4 文本模板](../modeling/writing-a-t4-text-template.md)。

 在**中执行** 设计时 T4 文本模板 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 以定义部分源代码以及应用程序的其他资源。
通常，你会使用多个模块读取单个输入文件或数据库中的数据，然后生成部分 `.cs`、 `.vb`或其他源文件。 每个模板生成一个文件。 这些模版在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 或 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]内执行。

 例如，输入数据可能是配置数据的 XML 文件。 每当在开发过程中编辑 XML 文件时，文本模板都会重新生成部分应用程序代码。 其中一个模板可能类似于以下示例：

```
<#@ output extension=".txt" #>
<#@ assembly name="System.Xml" #>
<#
 System.Xml.XmlDocument configurationData = ...; // Read a data file here.
#>
namespace Fabrikam.<#= configurationData.SelectSingleNode("jobName").Value #>
{
  ... // More code here.
}

```

 依赖于 XML 文件中的值，所生成的 `.cs` 文件类似于以下示例：

```
namespace Fabrikam.FirstJob
{
  ... // More code here.
}
```

 再如，该输入可能是业务活动中的工作流关系图。 当用户更改其业务工作流，或当你开始与具有不同工作流的新用户协作时，很容易重新生成代码以适应新模型。

 通过设计时模板，可以在需要时更快更可靠地更配置。 通常，输入根据业务需求定义（如工作流示例所示）。 这样可以更容易地和你的用户讨论更改。 设计时模板也因此成为敏捷开发过程中使用的有用工具。

 若要创建运行时模板，请将“文本模版”  文件添加到你的项目中。 或者，你也可以添加一个纯文本文件，并将其“自定义工具”  属性设置为 **TextTemplatingFileGenerator**。

 有关详细信息，请参阅[使用 T4 文本模板生成设计时代码](../modeling/design-time-code-generation-by-using-t4-text-templates.md)。 有关模板的语法的详细信息，请参阅[编写 T4 文本模板](../modeling/writing-a-t4-text-template.md)。

> [!NOTE]
>  术语 *“模型”* 有时用来描述由一个或多个模板所读取的数据。 该模型可以是任何格式、任何类型的文件或数据库。 而不必是 UML 模型或域特定语言模型。 “模型”仅表示可以业务概念的形式定义的数据，而不是类似的代码。

 文本模板转换功能命名为 *T4*。

## <a name="in-this-section"></a>本节内容
 [使用 T4 文本模板的运行时文本生成](../modeling/run-time-text-generation-with-t4-text-templates.md)任何应用程序生成的文本文件，预编译的文本模板是定义文本的简单且可靠的方法。 但是，此方法不适用于在运行时更改的文本模板。

 [使用 T4 文本模板生成设计时代码](../modeling/design-time-code-generation-by-using-t4-text-templates.md)生成代码和从模型的其他资源使你可以更新你的应用程序通过更新模型。

 [代码生成过程中的生成](../modeling/code-generation-in-a-build-process.md)如果已安装[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]可视化和建模 SDK，你可以确保在模型中，生成的软件保持最新更改。

 [编写 T4 文本模板](../modeling/writing-a-t4-text-template.md)文本模板文件的语法。

 [演练： 使用文本模板生成代码](../modeling/walkthrough-generating-code-by-using-text-templates.md)的一种方式使用代码生成演示。

 [调试 T4 文本模板](../modeling/debugging-a-t4-text-template.md)如何调试文本模板，以及一些常见的文本模板错误。

 [生成使用 TextTransform 实用程序的文件](../modeling/generating-files-with-the-texttransform-utility.md)可用于运行文本模板转换的命令行工具。

 [自定义 T4 文本转换](../modeling/customizing-t4-text-transformation.md)如何编写指令处理器和数据源的自定义模板化主机。

## <a name="see-also"></a>请参阅

- [从域特定语言生成代码](../modeling/generating-code-from-a-domain-specific-language.md)