---
title: "如何：使用痕迹导航 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 如何：使用痕迹导航
更改 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 中显示的活动集的方法主要有三种：  
  
1.  双击以钻入子活动。  
  
2.  单击痕迹栏上的按钮以导航到祖先活动。  
  
3.  就地展开或折叠活动。  
  
### 使用痕迹导航  
  
1.  双击 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 的活动，将根活动改为单击的活动。此时单击的活动将在根处完全展开，其祖先将显示在痕迹栏中。这有时称为钻入或钻出某个活动。  
  
2.  若要导航到当前根活动的一个祖先，请单击痕迹栏中的相应活动。  
  
### 就地展开或折叠活动  
  
1.  单击活动上的 V 形将就地展开或折叠该活动。  
  
2.  单击该按钮更改展开状态时，新的展开状态将保存在 XAML 中。  
  
    > [!WARNING]
    >  并非所有活动都可就地展开。在两种情况下不能就地展开活动：一种是活动的父级不允许其子级就地展开（例如，流程图中的活动不能就地展开），另一种是活动设计器不允许自身就地展开。虽然 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 中包含的所有活动设计器都没有后一种行为，但有的自定义活动可能具有此行为。  
  
### 展开或折叠所有活动  
  
1.  使用用户界面中的**“全部展开”**和**“全部折叠”**按钮可以展开或折叠当前痕迹根下的所有活动。请注意，全部展开和全部折叠是全局状态。这意味着使用痕迹导航更改根活动时，将保持全部展开或全部折叠状态，直到单击**“还原”**为止。  
  
2.  应用全部展开或全部折叠状态后，可以单击出现的**“还原”**按钮回到之前应用于每个活动的查看状态。  
  
    > [!WARNING]
    >  如果某个活动（如 <xref:System.Activities.Statements.Flowchart>）无法就地展开，则对 **“Flowchart”** 设计器将禁用与**“全部展开”**和**“全部折叠”**按钮相关联的功能。[!INCLUDE[crabout](../test/includes/crabout_md.md)]**流程图** 设计器，请参见 [流程图](../workflow-designer/flowchart-activity-designer.md) 主题。  
  
    > [!WARNING]
    >  全部展开对于**“Switch”**和**“TryCatch”**活动设计器还有特殊效果。单击**“全部展开”**时，所有 switch 事例和所有 try\/catch\/finally 块都将显示。单击**“还原”**或**“全部折叠”**时，这些设计器会返回到它们的默认状态，在此状态下可以单击单个事例\/块来查看其内容。