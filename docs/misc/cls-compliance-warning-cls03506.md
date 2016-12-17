---
title: "Avviso di conformit&#224; a CLS CLS03506 | Microsoft Docs"
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
  - "CLS03506"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03506"
ms.assetid: baec820c-aabb-44c4-b0cd-043c3ca9c537
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Avviso di conformit&#224; a CLS CLS03506
**La specifica CLS non consente i modificatori necessari visibili pubblicamente \(modreq\), ma consente i modificatori facoltativi \(modopt\) che non riconosce**  
  
 La specifica CLS non consente i modificatori necessari visibili pubblicamente \(modreq\), ma consente i modificatori facoltativi \(modopt\) che non riconosce.  
  
 Verificare che le firme del metodo non contengano tipi contrassegnati con modificatori necessari visibili pubblicamente.  
  
 Per altre informazioni sul controllo di conformità a CLS \(Common Language Subset\), vedere [Assembly conformi a CLS](http://msdn.microsoft.com/it-it/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 L'esempio seguente genera l'errore CLS03506:  
  
```  
// CLS03506.cpp // compile with: /clr /LD // CLS03506 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class One { public: void F1(volatile Int32 parameter) {}   // CLS03506 void F2( Int32 parameter) {}   // OK };  
```