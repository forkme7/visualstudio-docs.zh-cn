---
title: IDebugExtendedField::IsClosedType |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 00c1e8bc4eba53a3109f08dc1b8d17c2901612c4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="idebugextendedfieldisclosedtype"></a>IDebugExtendedField::IsClosedType
确定是否字段表示封闭的类型。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT IsClosedType(  
   void  
);  
```  
  
```csharp  
int IsClosedType();  
```  
  
## <a name="return-value"></a>返回值  
 如果此字段为封闭式的类型，将返回`S_OK`; 否则为返回`S_FALSE`。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)