---
title: "Errore del compilatore C2761 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2761"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2761"
ms.assetid: 38c79a05-b56d-485b-820f-95e8c0cb926f
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Errore del compilatore C2761
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'funzione': ridichiarazione della funzione membro non consentita  
  
 Non è possibile ridichiarare una funzione membro.  La funzione può essere definita, ma non ridichiarata.  
  
## Esempio  
 Nell'esempio seguente viene generato l'errore C2761:  
  
```  
// C2761.cpp  
class a {  
   int t;  
   void test();  
};  
  
void a::a;     // C2761  
void a::test;  // C2761  
  
```  
  
## Esempio  
 Non è possibile definire i membri non static di una classe o di una struttura.  Nell'esempio seguente viene generato l'errore C2761:  
  
```  
// C2761_b.cpp  
// compile with: /c  
struct C {  
   int s;  
   static int t;  
};  
  
int C::s;   // C2761  
int C::t;   // OK  
```