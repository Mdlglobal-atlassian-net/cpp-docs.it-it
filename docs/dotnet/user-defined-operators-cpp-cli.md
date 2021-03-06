---
title: Operatori definiti dall'utente (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- user-defined operators under /clr
ms.assetid: 42f93b4a-6de4-4e34-b07b-5a62ac014f2c
ms.openlocfilehash: cf80eb4c440c1308e8ea06a563c18569e4e4ddf2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384504"
---
# <a name="user-defined-operators-ccli"></a>Operatori definiti dall'utente (C++/CLI)

Operatori definiti dall'utente per i tipi gestiti sono consentiti come membri statici o membri di istanza o in ambito globale. Tuttavia, solo gli operatori statici sono accessibili tramite i metadati per i client che vengono scritti in un linguaggio diverso da Visual C++.

In un tipo riferimento, uno dei parametri di un operatore definito dall'utente statico deve essere uno dei seguenti:

- Un handle (`type` ^) a un'istanza del tipo di inclusione.

- Un riferimento indiretto tipo riferimento (`type`^ & o di tipo ^ %) per un handle per un'istanza del tipo di inclusione.

In un tipo valore, uno dei parametri di un operatore definito dall'utente statico deve essere uno dei seguenti:

- Dello stesso tipo del tipo di inclusione valore.

- Un riferimento indiretto al tipo puntatore (`type`^) per il tipo di inclusione.

- Un riferimento indiretto tipo riferimento (`type`% o `type`&) per il tipo di inclusione.

- Un riferimento indiretto tipo riferimento (`type`^ % o `type`^ &) per l'handle.

È possibile definire gli operatori seguenti:

|Operatore|Form unario/binario?|
|--------------|--------------------------|
|!|Unario|
|!=|Binario|
|%|Binario|
|&|Unario e binario|
|&&|Binario|
|*|Unario e binario|
|+|Unario e binario|
|++|Unario|
|,|Binario|
|-|Unario e binario|
|--|Unario|
|->|Unario|
|/|Binario|
|<|Binario|
|<<|Binario|
|\<=|Binario|
|=|Binario|
|==|Binario|
|>|Binario|
|>=|Binario|
|>>|Binario|
|^|Binario|
|False|Unario|
|true|Unario|
|&#124;|Binario|
|&#124;&#124;|Binario|
|~|Unario|

## <a name="example"></a>Esempio

```cpp
// mcppv2_user-defined_operators.cpp
// compile with: /clr
using namespace System;
public ref struct X {
   X(int i) : m_i(i) {}
   X() {}

   int m_i;

   // static, binary, user-defined operator
   static X ^ operator + (X^ me, int i) {
      return (gcnew X(me -> m_i + i));
   }

   // instance, binary, user-defined operator
   X^ operator -( int i ) {
      return gcnew X(this->m_i - i);
   }

   // instance, unary, user-defined pre-increment operator
   X^ operator ++() {
      return gcnew X(this->m_i++);
   }

   // instance, unary, user-defined post-increment operator
   X^ operator ++(int i) {
      return gcnew X(this->m_i++);
   }

   // static, unary user-defined pre- and post-increment operator
   static X^ operator-- (X^ me) {
      return (gcnew X(me -> m_i - 1));
   }
};

int main() {
   X ^hX = gcnew X(-5);
   System::Console::WriteLine(hX -> m_i);

   hX = hX + 1;
   System::Console::WriteLine(hX -> m_i);

   hX = hX - (-1);
   System::Console::WriteLine(hX -> m_i);

   ++hX;
   System::Console::WriteLine(hX -> m_i);

   hX++;
   System::Console::WriteLine(hX -> m_i);

   hX--;
   System::Console::WriteLine(hX -> m_i);

   --hX;
   System::Console::WriteLine(hX -> m_i);
}
```

```Output
-5
-4
-3
-2
-1
-2
-3
```

## <a name="example"></a>Esempio

L'esempio seguente illustra una sintesi di operatori, che è disponibile solo quando si usa **/clr** da compilare. Sintesi di operatori consente di creare il modulo di assegnazione di un operatore binario, se non è definito, in cui la parte sinistra dell'operatore di assegnazione è un tipo CLR.

```cpp
// mcppv2_user-defined_operators_2.cpp
// compile with: /clr
ref struct A {
   A(int n) : m_n(n) {};
   static A^ operator + (A^ r1, A^ r2) {
      return gcnew A( r1->m_n + r2->m_n);
   };
   int m_n;
};

int main() {
   A^ a1 = gcnew A(10);
   A^ a2 = gcnew A(20);

   a1 += a2;   // a1 = a1 + a2   += not defined in source
   System::Console::WriteLine(a1->m_n);
}
```

```Output
30
```

## <a name="see-also"></a>Vedere anche

[Classi e struct](../extensions/classes-and-structs-cpp-component-extensions.md)
