---
title: "Library Support for Mixed Assemblies | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: ["cpp-windows"]
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: ["C++"]
helpviewer_keywords: ["msvcm90[d].dll", "mixed assemblies [C++], library support", "msvcmrt[d].lib", "libraries [C++], mixed assemblies"]
ms.assetid: 1229595c-9e9d-414d-b018-b4e4c727576d
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Library Support for Mixed Assemblies
Visual C++ supports the use of the C++ Standard Library, the Common RunTime library (CRT), ATL, and MFC for applications compiled with [/clr (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md). This allows existing applications that use these libraries to use .NET Framework features as well.  
  
 This support introduces the following new DLL and import libraries:  
  
-   Msvcmrt[d].lib if you compile with /clr. Mixed assemblies links to this import library.  
  
-   Msvcm90[d].dll and Msvcurt[d].lib if you compile with /clr:pure. The DLL is a mixed assembly providing managed C Run Time (CRT) support, and is part of a managed assembly installed in the global assembly cache (GAC). Pure assemblies link to this import library and end up bound to Msvcm90.dll.  
  
 This support provides several related benefits:  
  
-   The CRT and C++ Standard Library are available to both mixed and pure code. The CRT and C++ Standard Library provided are not verifiable; ultimately, your calls are still routed to the same CRT and C++ Standard Library as you are using from native code.  
  
-   Correct unified exception handling in pure and mixed images.  
  
-   Static initialization of C++ variables in pure and mixed images.  
  
-   Support for per-AppDomain and per-process variables in managed code.  
  
-   Resolves the loader lock issues that applied to mixed DLLs compiled in Visual Studio 2003 and earlier.  
  
 In addition, this support presents the following limitations:  
  
-   Only the CRT DLL model is supported (both for code compiled with /clr or /clr:pure).  
  
-   You cannot mix pure and mixed objects in a single image if those objects use the Visual C++ libraries (because all objects must be pure in a pure image). If you do this, you receive link-time errors.  
  
 You should update your common language runtime (CLR) to the current version as it is not guaranteed to work with earlier versions. Code built with these changes will not run on CLR version 1.x.  
  
## See Also  
 [Mixed (Native and Managed) Assemblies](../dotnet/mixed-native-and-managed-assemblies.md)