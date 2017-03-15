---
title: "literal (C++ Component Extensions) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "literal"
  - "literal_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "literal keyword [C++]"
ms.assetid: 6b1a1f36-2e1d-4a23-8eb6-172f4f3c477f
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# literal (C++ Component Extensions)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una variabile \(membro dati\) contrassegnata come `literal` in una compilazione **\/clr** è l'equivalente nativo di una variabile `static const`.  
  
## Tutte le piattaforme  
 **Osservazioni**  
  
 \(Non esistono note per questa funzionalità del linguaggio che si applichino a tutti i runtime\).  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 **Osservazioni**  
  
 Non esistono note per questa funzionalità del linguaggio che si applichino solo a Windows Runtime.  
  
### Requisiti  
 Opzione del compilatore: **\/ZW**  
  
## Common Language Runtime  
  
## Note  
 Un membro dati contrassegnato come `literal`deve essere inizializzato una volta dichiarato e il valore deve essere un intero, un enum o un tipo stringa costante.  La conversione dal tipo dell'espressione di inizializzazione al tipo del membro dati static const non deve richiedere una conversione definita dall'utente.  
  
 Non viene allocata nessuna memoria per il campo letterale a runtime; il compilatore inserisce solo il suo valore nei metadati per la classe.  
  
 Una variabile contrassegnato `static const` non sarà disponibile nei metadati ad altri compilatori.  
  
 Per ulteriori informazioni, vedere [Statico](../misc/static-cpp.md) e [const](../cpp/const-cpp.md).  
  
 `literal` è una parola chiave sensibile al contesto.  Per ulteriori informazioni, vedere [Parole chiave sensibili al contesto](../windows/context-sensitive-keywords-cpp-component-extensions.md).  
  
## Esempio  
 Questo esempio mostra che una variabile `literal` implica `static`.  
  
```  
// mcppv2_literal.cpp  
// compile with: /clr  
ref struct X {  
   literal int i = 4;  
};  
  
int main() {  
   int value = X::i;  
}  
```  
  
## Esempio  
 L'esempio seguente mostra l'effetto di letterale nei metadati:  
  
```  
// mcppv2_literal2.cpp  
// compile with: /clr /LD  
public ref struct A {  
   literal int lit = 0;  
   static const int sc = 1;  
};  
```  
  
 Si noti la differenza nei metadati per `sc` e `lit`: la direttiva `modopt` viene applicata a `sc`, ovvero può essere ignorata dagli altri compilatori.  
  
```  
.field public static int32 modopt([mscorlib]System.Runtime.CompilerServices.IsConst) sc = int32(0x0000000A)  
```  
  
```  
.field public static literal int32 lit = int32(0x0000000A)  
```  
  
## Esempio  
 L'esempio seguente, creato in C\#, referenzia i metadati creati nell'esempio precedente e mostra l'effetto di variabili `literal` e `static const` :  
  
```  
// mcppv2_literal3.cs  
// compile with: /reference:mcppv2_literal2.dll  
// A C# program  
class B {  
   public static void Main() {  
      // OK  
      System.Console.WriteLine(A.lit);  
      System.Console.WriteLine(A.sc);  
  
      // C# does not enforce C++ const  
      A.sc = 9;  
      System.Console.WriteLine(A.sc);  
  
      // C# enforces const for a literal  
      A.lit = 9;   // CS0131  
  
      // you can assign a C++ literal variable to a C# const variable  
      const int i = A.lit;  
      System.Console.WriteLine(i);  
  
      // but you cannot assign a C++ static const variable  
      // to a C# const variable  
      const int j = A.sc;   // CS0133  
      System.Console.WriteLine(j);  
   }  
}  
```  
  
## Requisiti  
 Opzione del compilatore: **\/clr**  
  
## Vedere anche  
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)