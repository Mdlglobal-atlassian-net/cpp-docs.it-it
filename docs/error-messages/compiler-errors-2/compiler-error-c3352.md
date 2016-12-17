---
title: "Errore del compilatore C3352 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3352"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3352"
ms.assetid: f233bed7-474e-425f-aad2-7801578169d4
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Errore del compilatore C3352
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'funzione': la funzione specificata non corrisponde al tipo delegato 'tipo'  
  
 Gli elenchi di parametri di `function` e il delegato non corrispondono.  
  
 Per ulteriori informazioni, vedere [delegato](../../windows/delegate-cpp-component-extensions.md).  
  
 Il seguente codice di esempio genera l'errore C3352:  
  
```  
// C3352.cpp  
// compile with: /clr  
delegate int D( int, int );  
ref class C {  
public:  
   int mf( int ) {  
      return 1;  
   }  
  
   // Uncomment the following line to resolve.  
   // int mf(int, int) { return 1; }  
};  
  
int main() {  
   C^ pC = gcnew C;  
   System::Delegate^ pD = gcnew D( pC, &C::mf );   // C3352  
}  
```  
  
 Il seguente codice di esempio genera l'errore C3352:  
  
```  
// C3352_2.cpp  
// compile with: /clr:oldSyntax  
__delegate int D(int, int);  
  
__gc class C {  
public:  
   int mf(int) {  
      return 1;  
   }  
  
   // Uncomment the following line to resolve.  
   // int mf(int, int) { return 1; }  
};  
  
int main() {  
   C *pC = new C;  
   System::Delegate *pD = new D(pC, &C::mf);   // C3352  
}  
```