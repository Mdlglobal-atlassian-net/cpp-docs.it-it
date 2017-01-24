---
title: "Errore del compilatore CS0104 | Microsoft Docs"
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
  - "CS0104"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0104"
ms.assetid: 1a7e9ae8-308b-441b-ba85-fac974222875
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Errore del compilatore CS0104
'reference' è un riferimento ambiguo tra 'identifier' e 'identifier'  
  
 Il programma contiene direttive [using](../Topic/using%20\(C%23%20Reference\).md) per due spazi dei nomi e il codice fa riferimento a un nome presente in entrambi gli spazi dei nomi.  
  
 L'esempio seguente genera l'errore CS0104:  
  
```  
// CS0104.cs using x; using y; namespace x { public class Test { } } namespace y { public class Test { } } public class a { public static void Main() { Test test = new Test();   // CS0104, is Test in x or y namespace? // try the following line instead // y.Test test = new y.Test(); } }  
```