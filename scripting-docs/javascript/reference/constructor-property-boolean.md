---
title: "constructor 属性（布尔值） | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b67ca875-23c6-4687-a5ce-1cdd25d1c923
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# constructor 属性（布尔值）
指定创建一个布尔值的函数。  
  
## 语法  
  
```  
  
boolean.constructor([[value])  
```  
  
#### 参数  
 `boolean`  
 布尔值的名称。  
  
 `value`  
 可选。  指定该布尔值的值。  这可以是数字 1 或 0，也可以是字符串“true”或“false”。  
  
## 备注  
 `constructor` 属性包含了对某种函数的引用，此种函数构造了布尔值对象的实例。  
  
## 示例  
 下面的示例阐释了 constructor 属性的用法。  
  
```javascript  
var x = new Boolean("true");  
  
if (x.constructor == Boolean)  
    document.write("Object is a Boolelan.");  
  
// Output:  
// Object is a Boolean.  
  
```  
  
## 要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]