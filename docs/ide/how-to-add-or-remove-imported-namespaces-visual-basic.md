---
title: "如何：添加或移除导入的命名空间 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "添加导入的命名空间"
  - "导入的命名空间 [Visual Studio]"
  - "命名空间 [Visual Studio], 导入的"
  - "引用 [Visual Studio], 导入的命名空间"
  - "移除导入的命名空间"
ms.assetid: 44cebec3-0ea0-47c2-8406-4edeab6a997e
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# 如何：添加或移除导入的命名空间 (Visual Basic)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

导入命名空间使您得以在代码中使用来自该命名空间的元素，而不用完全限定该元素。  例如，如果要访问 `System.Messaging.MessageQueue` 类中的 `Create` 方法，可以导入 `System.Messaging` 命名空间，然后只需在代码中需要的地方以 `MessageQueue.Create` 的形式引用该元素。  
  
 在**“项目设计器”**的**“引用”**页上管理导入的命名空间。  在此对话框中指定的导入直接传递给编译器 \(`/imports`\)，并应用于项目中的所有文件。  使用 `Imports` 语句可以在单个源代码文件中使用命名空间。  
  
### 添加导入的命名空间  
  
1.  在**“解决方案资源管理器”**中，双击项目的**“我的项目”**节点。  
  
2.  在**“项目设计器”**中，单击**“引用”**选项卡。  
  
3.  在**“导入的命名空间”**列表中，选中希望添加的命名空间对应的复选框。  
  
    > [!NOTE]
    >  为了能够导入命名空间，命名空间必须位于引用的组件中。  如果命名空间没有出现在列表中，则需要添加对包含该命名空间的组件的引用。  有关更多信息，请参见[如何：使用“添加引用”对话框添加或移除引用](http://msdn.microsoft.com/zh-cn/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)。  
  
### 移除导入的命名空间  
  
1.  在**“解决方案资源管理器”**中，双击项目的**“我的项目”**节点。  
  
2.  在**“项目设计器”**中，单击**“引用”**选项卡。  
  
3.  在**“导入的命名空间”**列表中，清除希望移除的命名空间对应的复选框。  
  
## 用户导入  
 用户导入用于导入命名空间中特定的类而不是整个命名空间。  例如，应用程序可能导入了 `Systems.Diagnostics` 命名空间，但是该命名空间中您唯一感兴趣的类是 `Debug` 类。  您可以将 `System.Diagnostics.Debug` 定义为用户导入，然后移除对 `System.Diagnostics` 的导入。  
  
 如果您以后改变了主意，认为真正需要的类是 `EventLog` 类，则可以输入 `System.Diagnostics.EventLog` 作为用户导入，并使用更新功能覆盖 `System.Diagnostics.Debug`。  
  
#### 添加用户导入  
  
1.  在**“解决方案资源管理器”**中，双击项目的**“我的项目”**节点。  
  
2.  在**“项目设计器”**中，单击**“引用”**选项卡。  
  
3.  在**“导入的命名空间”**列表下面的文本框中，输入希望导入的命名空间的完整名称，包括根命名空间。  
  
4.  单击**“添加用户导入”**按钮，将该命名空间添加到**“导入的命名空间”**列表中。  
  
    > [!NOTE]
    >  如果该命名空间与列表中已有的某个命名空间相同，则**“添加用户导入”**按钮将被禁用；您不能将一个导入项添加两次。  
  
#### 更新用户导入  
  
1.  在**“解决方案资源管理器”**中，双击项目的**“我的项目”**节点。  
  
2.  在**“项目设计器”**中，单击**“引用”**选项卡。  
  
3.  在**“导入的命名空间”**列表中，选择希望更改的命名空间。  
  
4.  在**“导入的命名空间”**列表下面的文本框中，输入新的命名空间的名称。  
  
5.  单击**“更新用户导入”**按钮，更新**“导入的命名空间”**列表中的命名空间。  
  
## 请参阅  
 [管理项目中的引用](../ide/managing-references-in-a-project.md)