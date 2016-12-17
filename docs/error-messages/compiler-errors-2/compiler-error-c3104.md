---
title: "Errore del compilatore C3104 | Microsoft Docs"
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
  - "C3104"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3104"
ms.assetid: b5648d47-e5d3-4b45-a3c0-f46e04eae731
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Errore del compilatore C3104
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

argomento non valido per l'attributo  
  
 È stato specificato un argomento non valido per un attributo.  
  
 Per ulteriori informazioni, vedere [Attribute Parameter Types](../../windows/attribute-parameter-types-cpp-component-extensions.md).  
  
 Questo errore può essere generato in seguito alle operazioni di conformità eseguite dal compilatore per Visual C\+\+ 2005: quando si passano matrici gestite ad attributi personalizzati, il tipo di matrice non viene più dedotto dall'elenco di inizializzazione aggregata.  Il compilatore richiede la specifica del tipo di matrice e dell'elenco di inizializzatori.  
  
## Esempio  
 Nell'esempio seguente viene generato l'errore C3104:  
  
```  
// C3104a.cpp  
// compile with: /clr /c  
using namespace System;  
  
[AttributeUsage(AttributeTargets::Class)]  
public ref struct ABC : public Attribute {  
   ABC(array<int>^){}  
   array<double> ^ param;  
};  
  
[ABC( {1,2,3}, param = {2.71, 3.14})]   // C3104  
// try the following line instead  
// [ABC( gcnew array<int> {1,2,3}, param = gcnew array<double>{2.71, 3.14})]   
ref struct AStruct{};  
```  
  
## Esempio  
 Nell'esempio seguente viene generato l'errore C3104:  
  
```  
// C3104b.cpp  
// compile with: /clr /c  
// C3104 expected  
using namespace System;  
  
int func() {  
   return 0;   
}  
  
[attribute(All)]  
ref class A {  
public:   
   A(int) {}  
};  
  
// Delete the following 2 lines to resolve.  
[A(func())]  
ref class B {};  
  
// OK  
[A(0)]  
ref class B {};  
```  
  
## Esempio  
 Nell'esempio seguente viene generato l'errore C3104:  
  
```  
// C3104c.cpp  
// compile with: /clr:oldSyntax /c  
using namespace System;  
  
[ attribute(Class) ]  
public __gc class AnotherAttr {  
public:  
   AnotherAttr(Object* arr __gc[]) : var0(arr) {}  
   Object* var1 __gc[];  
   Object* var0 __gc[];  
};  
  
[ AnotherAttr( { __box(3.14159), S"pi" }, var1 = { S"a", S"b" } ) ]   // C3104  
public __gc class Class1 {};  
  
// OK  
[ AnotherAttr( new Object * __gc[] {__box(3.14159), S"pi" }, var1 = new Object * __gc[] { S"a", S"b" } ) ]  
public __gc class Class2 {};  
```