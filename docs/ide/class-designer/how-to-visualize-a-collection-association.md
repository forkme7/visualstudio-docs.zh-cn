---
title: 如何：可视化集合关联（类设计器）
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.collectionassociationline
- vs.classdesigner.ShowAssociationException
helpviewer_keywords:
- collection associations
- collections, collection associations
- Class Designer [Visual Studio], collection associations
ms.assetid: 54e39838-2fc9-4dc2-85b6-7e88a743108e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 472eef35c781c027c39b99326e097db7ca249c29
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-visualize-a-collection-association-class-designer"></a>如何：直观显示集合关联（类设计器）

属于其他类型的集合的属性和字段可在类图上作为集合关联显示。 普通关联可将字段或属性显示为行，此行将拥有的类链接到字段的类型，与此不同，集合关联作为行显示，此行将拥有的类链接到已收集的类型。

## <a name="to-create-a-collection-association"></a>创建集合联合

1.  在代码中，创建一个属性或字段，其本身属于强类型集合。

2.  在类图中扩展类，以便显示属性和字段。

3.  在类中，右键单击该字段或属性，然后选择“显示为集合关联”。

     此属性或字段将显示为链接到已收集类型的关联行。

## <a name="see-also"></a>请参阅

- [如何：创建类型之间的关联](how-to-create-associations-between-types.md)
- [设计类和类型](designing-and-viewing-classes-and-types.md)
- [查看类型和关系](viewing-types-and-relationships.md)
