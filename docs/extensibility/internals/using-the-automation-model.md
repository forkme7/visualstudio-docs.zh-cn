---
title: 使用自动化模型 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 679e9966e66de1c79cb3c6394f1d80ab6d6733bb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="using-the-automation-model"></a>使用自动化模型
你的 VSPackage 连接到自动化后，你可以通过调用获取的属性和方法<xref:EnvDTE.DTEClass.GetObject%2A>方法<xref:EnvDTE._DTE>对象传递一个字符串，表示要检索的对象。  
  
## <a name="obtaining-project-objects"></a>获取项目对象  
 以下是两个代码示例演示如何自动化使用者获取项目自动化对象。 有关如何获取 DTE 对象的信息，请参阅[如何： 获取对 DTE 和 DTE2 对象的引用](http://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4)。  
  
```vb  
Sub DoAutomation()  
    Dim MyProjects As Projects  
    MyProjects = DTE.GetObject("AcmeProject")  
End Sub  
```  
  
```cpp  
void DoAutomation(void)  
{  
  CComQIPtr<Projects> pMyPkg; // Use an IDispatch-derived object type.  
    pMyPkg = pDTE->GetObject("AcmeProjects");   
  
   // The '=' performs a Query Interface.  
   // Assumes pDTE is already available as a global.  
   // Use pMyPkg to access your projects object's properties and methods.  
}  
  
```  
  
 此时，你可以使用属于特定 VSPackage 来下移层次结构模型的标准项目对象。  
  
 下面的代码示例演示如何获取是一种自定义项目类型的属性的自定义对象。:  
  
```vb  
Dim MyPrj As Project  
Dim MyPrjItem As ProjectItem  
Dim objMyObject as MyExtendedObject  
  
MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project  
objMyObject = MyPrj.Object 'You call .Object to get to special Project  
                           'implementation  
objMyObject.MySpecialMethodOrProperty  
```  
  
 下面的代码列出所有中的属性的名称[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]环境**常规**选项**工具**菜单：  
  
```vb  
dim objDTE  
dim objEnv  
set objDTE = CreateObject("VisualStudio.DTE")  
set objEnv = objDTE.Properties("Environment", "General")  
for each obj in ObjEnv  
MsgBox obj.Name  
Next  
  
```  
  
## <a name="see-also"></a>另请参阅  
 <xref:EnvDTE.DTEClass.GetObject%2A>