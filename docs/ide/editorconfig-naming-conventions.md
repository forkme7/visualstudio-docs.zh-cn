---
title: EditorConfig 文件的 .NET 命名约定 | Microsoft Docs
ms.custom: ''
ms.date: 11/20/2017
ms.topic: conceptual
helpviewer_keywords:
- naming conventions [EditorConfig]
- EditorConfig naming conventions
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 14b284c797add9545efdd291b06ce62b0b75cf03
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="net-naming-conventions-for-editorconfig"></a>EditorConfig 适用的 .NET 命名约定

命名约定与类、属性和方法等码位元素的命名有关。 例如，可以指定公共成员必须采用大写形式，或者异步方法必须以“Async”结尾。 可以通过在 [.editorconfig 文件](../ide/create-portable-custom-editor-options.md)中指定这些规则来加以实施。 命名规则冲突显示在“错误列表”中，或者作为建议显示在名称之下，具体取决于为规则选择的严重性。 不需要生成项目即可查看冲突。

命名约定在 .editorconfig 文件中的排序顺序应为从最具体到最抽象。 遇到的第一个可应用规则是唯一应用的规则。

对于每个命名约定，必须使用下面介绍的属性指定适用的符号、命名样式和实施约定的严重性。 属性的顺序并不重要。

首先，为命名规则选择一个标题，该标题可用于完全描述规则所需的每个属性。 例如，`public_members_must_be_capitalized` 是一个良好的描述性命名规则名称。 以下各部分中引用所选标题作为 <namingRuleTitle\>。

## <a name="symbols"></a>符号

首先，识别应用命名规则的一组符号。 此属性采用以下格式：

`dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`

通过将 <symbolTitle\> 替换为描述性标题（如 `public_symbols`），为该组符号提供名称。 将在三个属性名称中使用 <symbolTitle\>，这三个属性用于介绍应用规则的符号（符号种类、可访问性级别和修饰符）。

### <a name="kinds-of-symbols"></a>符号种类

要描述应用命名规则的符号种类，请按照以下格式指定一个属性：

`dotnet_naming_symbols.<symbolTitle>.applicable_kinds = <values>`

以下列表显示了允许的值，可通过以逗号分隔值来指定多个值。

- \*（使用此值可指定所有符号）
- 类
- struct
- 接口
- enum
- 属性
- 方法
- Field — 字段
- Event — 事件
- 委托
- 参数

### <a name="accessibility-levels-of-symbols"></a>符号的可访问性级别

要描述应用命名规则的符号的可访问性级别，请按照以下格式指定一个属性名称：

`dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities = <values>`

以下列表显示了允许的值，可通过以逗号分隔值来指定多个值。

- \*（使用此值可指定所有可访问性级别）
- public
- internal 或 friend
- private
- protected
- protected\_internal 或 protected_friend

> [!NOTE]
> 如果可访问性不适用于目标符号种类，请勿在命名约定中指定可访问性级别。 例如，参数就没有可访问性级别。 如果为参数命名约定指定可访问性级别，那么命名规则将无法正常运行。

### <a name="symbol-modifiers"></a>符号修饰符

要描述应用命名规则的符号的修饰符，请按照以下格式指定一个属性名称：

`dotnet_naming_symbols.<symbolTitle>.required_modifiers = <values>`

以下列表显示了允许的值，可通过以逗号分隔值来指定多个值。

- abstract 或 must_inherit
- async
- const
- readonly
- static 或 shared

`required_modifiers` 为可选属性。 如果忽略此属性，则命名规则应用于所有修饰符。

## <a name="style"></a>样式

识别了应用命名规则的一组符号，现在必须描述命名样式。 样式可以是名称采用特定前缀或特定后缀，也可以是名称中的各个文字以特定字符分隔。 还可以指定大写样式。 样式属性采用以下格式：

`dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`

通过将 <styleTitle\> 值替换为描述性标题（如 `first_word_upper_case_style`），为样式提供名称。 将在描述命名样式（前缀、后缀、文字分隔符和大写）的属性名称中使用 <styleTitle\> 值。 使用其中一个或多个属性描述样式。

### <a name="require-a-prefix"></a>需要前缀

要指定符号名称必须以特定字符开始，请使用此属性：

`dotnet_naming_style.<styleTitle>.required_prefix = <prefix>`

### <a name="require-a-suffix"></a>需要后缀

要指定符号名称必须以特定字符结尾，请使用此属性：

`dotnet_naming_style.<styleTitle>.required_suffix = <suffix>`

### <a name="require-a-certain-word-separator"></a>需要特定文字分隔符

要指定必须以特定字符分隔符号名称中的各文字，请使用此属性：

`dotnet_naming_style.<styleTitle>.word_separator = <separator character>`

### <a name="require-a-capitalization-style"></a>需要大写样式

要指定符号名称使用特定大写样式，请使用此属性：

`dotnet_naming_style.<styleTitle>.capitalization = <value>`

此属性的允许值为：

- pascal_case
- camel_case
- first\_word_upper
- all\_upper
- all_lower

> [!NOTE]
> 必须在命名样式中指定大写样式，否则会忽略命名样式。

## <a name="severity"></a>严重性

要描述命名规则冲突的严重性，请按照以下格式指定一个属性：

`dotnet_naming_rule.<namingRuleTitle>.severity = <value>`

下表显示允许的严重性值及其含义：

严重性 | 效果
------------ | -------------
none 或 silent | 如未遵循此样式，则不会向用户显示任何内容，但自动生成的代码会遵循此样式。
建议 | 如未遵循此样式，则会以建议形式向用户显示此样式（如前两个字符下带点）。 这在编译时没有影响。
警告 | 如未遵循此样式，“错误列表”中会显示编译器警告。
错误 | 如未遵循此样式，“错误列表”中会显示编译器错误。

> [!NOTE]
> 无需生成项目即可查看命名规则冲突。 它们会在编辑代码时显示在“错误列表”中或以建议形式显示。

## <a name="example"></a>示例

以下 .editorconfig 文件包含命名约定，该约定指定公共属性、方法、字段、事件和委托必须采用大写形式。 请注意，此命名约定指定了多种应用规则的符号，以逗号分隔。

```EditorConfig
# Public members must be capitalized (public_members_must_be_capitalized)
[*.{cs,vb}]
dotnet_naming_rule.public_members_must_be_capitalized.symbols   = public_symbols
dotnet_naming_symbols.public_symbols.applicable_kinds           = property,method,field,event,delegate
dotnet_naming_symbols.public_symbols.applicable_accessibilities = public
dotnet_naming_symbols.public_symbols.required_modifiers         = readonly

dotnet_naming_rule.public_members_must_be_capitalized.style    = first_word_upper_case_style
dotnet_naming_style.first_word_upper_case_style.capitalization = first_word_upper

dotnet_naming_rule.public_members_must_be_capitalized.severity = suggestion
```

以下屏幕截图显示此命名约定在编辑器中的效果。 有两个公共变量的名称没有首字母大写。 一个是 `const`，另一个是 `readonly`。 因为命名规则仅应用于 `readonly` 符号，所以仅 `readonly` 变量显示命名规则建议。

![命名规则建议](media/editorconfig-naming-rule-suggestion.png)

现在，将冲突严重性更改为 `warning`：

```EditorConfig
dotnet_naming_rule.public_members_must_be_capitalized.severity = warning
```

如果关闭代码文件然后重新打开，而不是查看名称冲突下的建议，则会看见绿色波浪线和“错误列表”中的警告：

![命名规则警告](media/editorconfig-naming-rule-warning.png)

## <a name="see-also"></a>请参阅

- [.NET 语言和格式设置约定](../ide/editorconfig-code-style-settings-reference.md)
- [创建可移植的自定义编辑器选项](../ide/create-portable-custom-editor-options.md)
- [.NET 编译器平台的 .editorconfig 文件](https://github.com/dotnet/roslyn/blob/master/.editorconfig)
