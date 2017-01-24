---
title: "Errore del compilatore CS1010 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1010"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1010"
ms.assetid: 3d47277a-253f-464b-a603-e3b37e0e7b0d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Errore del compilatore CS1010
Nuova riga nella costante  
  
 [string](../Topic/string%20\(C%23%20Reference\).md) non è stato delimitato in modo corretto.  
  
 L'esempio seguente genera l'errore CS1010:  
  
```  
// CS1010.cs class Sample { static void Main() { string a = "Hello World;   // CS1010 // Use the following line, with end quote before semicolon: string a = "Hello World"; // } }  
```  
  
## Vedere anche  
 [NIB \- Stringhe \(Guida per programmatori C\#\)](http://msdn.microsoft.com/it-it/1a32b1c9-0d99-468a-9734-e3a47f2e897a)