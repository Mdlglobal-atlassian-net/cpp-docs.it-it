---
title: "Errore del compilatore C3229 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3229"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3229"
ms.assetid: f2d90923-aa8b-444f-ab10-1f37dbb864e1
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Errore del compilatore C3229
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': i riferimenti indiretti in un parametro di tipo generico non sono consentiti  
  
 Non è possibile usare i parametri generici con `*`, `^` o `&`.  
  
## Esempio  
 L'esempio seguente genera l'errore C3229.  
  
```  
// C3229.cpp // compile with: /clr /c generic <class T> ref class C { T^ t;   // C3229 }; // OK generic <class T> ref class D { T u; };  
```  
  
## Esempio  
 L'esempio seguente genera l'errore C3229.  
  
```  
// C3229_b.cpp // compile with: /clr /c generic <class T>   // OK ref class Utils { static void sort(T elems[], size_t size);   // C3229 static void sort2(T elems, size_t size);   // OK };  
```