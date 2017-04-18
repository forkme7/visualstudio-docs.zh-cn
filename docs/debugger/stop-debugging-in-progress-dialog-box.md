---
title: "“停止正在进行的调试”对话框 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.stopnow"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "“停止正在进行的调试”对话框"
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# “停止正在进行的调试”对话框
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

当调试器尝试停止调试会话，但停止会话需要一段时间时，会出现此对话框。  停止调试会话通常很快，而此对话框并不出现。  但是，有时从正在调试的所有进程中分离需要额外的时间。  如果停止会话需要的时间超过几秒钟（或者发生分离错误），则会出现此对话框。  如果此对话框经常出现，则可能是由于内部问题，您可能需要与产品支持服务联系。  
  
 您可以等待进程分离，直到此对话框消失，或者使用**“立即停止”**按钮强制立即终止。  
  
 **立即停止**  
 单击此按钮可立即结束调试会话。  使用**“立即停止”**将终止而不是分离正在调试的进程。  如果正在调试系统进程，使用**“立即停止”**终止这些进程可能产生不希望出现的意外结果。  
  
## 请参阅  
 [调试器安全](../debugger/debugger-security.md)   
 [Detaching Programs](http://msdn.microsoft.com/zh-cn/f2c756c2-8079-474b-94c2-01c19a141a01)