---
title: "Errore del compilatore CS1676 | Microsoft Docs"
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
  - "CS1676"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1676"
ms.assetid: 5ac83d98-5baa-49fd-b76a-d8ef0865b9dd
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Errore del compilatore CS1676
Il parametro 'number' non deve essere dichiarato con la parola chiave 'keyword'  
  
 Questo errore si verifica quando il modificatore di tipo di parametro in un metodo anonimo non corrisponde a quello usato nella dichiarazione del delegato, a cui si esegue il cast del metodo.  
  
 L'esempio seguente genera l'errore CS1676:  
  
```  
// CS1676.cs delegate void E(ref int i); class Errors { static void Main() { E e = delegate(out int i) { };   // CS1676 // To resolve, use the following line instead: // E e = delegate(ref int i) { }; } }  
```