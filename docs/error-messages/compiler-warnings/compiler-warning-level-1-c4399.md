---
title: "Compiler Warning (level 1) C4399 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: ["cpp-tools"]
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: ["C4399"]
dev_langs: ["C++"]
helpviewer_keywords: ["C4399"]
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Compiler Warning (level 1) C4399
'symbol' : per-process symbol should not be marked with __declspec(dllimport) when compiled with /clr:pure  
  
 The **/clr:pure** compiler option is deprecated in Visual Studio 2015.  
  
 Data from a native image or an image with native and CLR constructs can not be imported into a pure image. To resolve this warning, compile with **/clr** (not **/clr:pure**) or delete `__declspec(dllimport)`.  
  
## Example  
 The following sample generates C4399.  
  
```  
// C4399.cpp  
// compile with: /clr:pure /doc /W1 /c  
__declspec(dllimport) __declspec(process) extern const int i;   // C4399  
```