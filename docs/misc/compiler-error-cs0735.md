---
title: "Errore del compilatore CS0735 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs0735"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0735"
ms.assetid: c49925fb-067c-4f29-9bef-a22115ae1507
caps.latest.revision: 4
caps.handback.revision: 4
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Errore del compilatore CS0735
Tipo non valido specificato come argomento dell'attributo TypeForwardedTo  
  
 L'esempio seguente genera l'errore CS0735.  
  
```  
// CS735.cs // compile with: /target:library using System.Runtime.CompilerServices; [assembly:TypeForwardedTo(typeof(int[]))]   // CS0735 [assembly:TypeForwardedTo(typeof(string))]   // OK  
```