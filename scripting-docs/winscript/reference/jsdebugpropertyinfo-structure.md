---
title: "JsDebugPropertyInfo 结构 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: JsDebugPropertyInfo
apilocation: jscript9diag.dll
ms.assetid: 3a5463a7-2013-4846-9ab2-8beb675a5a6a
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e9d2ae0d93729d4c333509e0178f4c4829ebf13
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="jsdebugpropertyinfo-structure"></a>JsDebugPropertyInfo 结构
指示与某一属性有关的信息。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct tagJsDebugPropertyInfo{   BSTR name;   BSTR type;   BSTR value;   BSTR fullName;   JS_PROPERTY_ATTRIBUTES attr;} JsDebugPropertyInfo;  
```  
  
## <a name="members"></a>成员  
 `name`  
 属性的名称。  
  
 `type`  
 属性的类型。  
  
 `value`  
 该属性的值。  
  
 `fullName`  
 属性的完整名称。  
  
 `attr`  
 一个表示属性特性的枚举。  
  
## <a name="requirements"></a>要求  
 **标头：** jscript9diag.h  
  
## <a name="see-also"></a>另请参阅  
 [Windows 脚本接口参考](../../winscript/reference/windows-script-interfaces-reference.md)