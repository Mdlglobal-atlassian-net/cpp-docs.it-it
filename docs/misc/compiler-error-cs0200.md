---
title: "Errore del compilatore CS0200 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0200"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0200"
ms.assetid: 1990704a-edfa-4dbd-8477-d9c7aae58c96
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Errore del compilatore CS0200
Non è possibile assegnare un valore alla proprietà o all'indicizzatore 'property' perché è di sola lettura  
  
 Si è provato ad assegnare un valore a un elemento [proprietà](../Topic/Using%20Properties%20\(C%23%20Programming%20Guide\).md), ma la proprietà non ha una funzione di accesso set. Risolvere l'errore aggiungendo una funzione di accesso set. Per altre informazioni, vedere [Procedura: dichiarare e usare proprietà Read Write](../Topic/How%20to:%20Declare%20and%20Use%20Read%20Write%20Properties%20\(C%23%20Programming%20Guide\).md).  
  
## Esempio  
 L'esempio seguente genera l'errore CS0200:  
  
```  
// CS0200.cs public class MainClass { // private int _mi; int I { get { return 1; } // uncomment the set accessor and declaration for _mi /* set { _mi = value; } */ } public static void Main () { MainClass II = new MainClass(); II.I = 9;   // CS0200 } }  
```