---
title: "Avviso di conformit&#224; a CLS CLS03603 | Microsoft Docs"
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
  - "CLS03603"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03603"
ms.assetid: 8bd74395-6b44-427d-8fe0-648dd946e6d2
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Avviso di conformit&#224; a CLS CLS03603
I campi statici globali non sono conformi a CLS  
  
 I metodi e i campi static globali non sono conformi a CLS.  
  
 Per altre informazioni sul controllo di conformità a CLS \(Common Language Subset\), vedere [Assembly conformi a CLS](http://msdn.microsoft.com/it-it/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 L'esempio seguente genera l'errore CLS03603:  
  
```  
// CLS03603.cpp // compile with: /clr /LD // CLS03603 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; int i;   // CLS03603 public ref class MyClass { public: int i;   // OK };  
```