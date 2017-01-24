---
title: "_CItan | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CItan"
apilocation: 
  - "msvcr100.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr80.dll"
  - "msvcrt.dll"
  - "msvcr110.dll"
  - "msvcr90.dll"
  - "msvcr120.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_CItan"
  - "CItan"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CItan intrinseco"
  - "_CItan intrinseco"
ms.assetid: d1ea3113-50a2-45a6-b6bc-680fcdcc0928
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CItan
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Calcola la tangente del valore in cima allo stack.  
  
## Sintassi  
  
```  
void __cdecl _CItan();  
```  
  
## Note  
 Questa versione della funzione `tan` è una convenzione di chiamata specializzata accettata dal compilatore.  La funzione accelera l'esecuzione in quanto impedisce la generazione di copie e aiuta con allocazione dei registri.  
  
 Il valore risultante viene inserito in cima allo stack.  
  
## Requisiti  
 **piattaforma:** x86  
  
## Vedere anche  
 [Riferimento alfabetico alle funzioni](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [tan, tanf, tanl, tanh, tanhf, tanhl](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)