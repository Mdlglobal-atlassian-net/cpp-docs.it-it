---
title: Errore del compilatore C2764
ms.date: 11/04/2016
f1_keywords:
- C2764
helpviewer_keywords:
- C2764
ms.assetid: 3754f5af-e094-4425-be20-d0c9a9b5baec
ms.openlocfilehash: 8d318742a367487f3688717046a6a798c2add87a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759841"
---
# <a name="compiler-error-c2764"></a>Errore del compilatore C2764

' param ': parametro di modello non utilizzato o deducibile nella specializzazione parziale ' specializzazione '

Un parametro di modello non viene utilizzato in una specializzazione parziale. In questo modo la specializzazione parziale non può essere utilizzata perché non è possibile dedurre il parametro di modello.

## <a name="example"></a>Esempio

L'esempio seguente genera l'C2764:

```cpp
// C2764.cpp
#include <stdio.h>
template <class T1, class T2>
struct S  {
   int m_i;
};

template <class T1, class T2>
struct S<int, T2*> {   // C2764
// try the following line instead
// struct S<T1(*)(T2), T2*> {
   char m_c;
};

int main() {
   S<int, char> s1;
   S<void (*)(short), short *> s2;
   s2.m_c = 10;
   s1.m_i = s2.m_c;
   printf_s("%d\n", s1.m_i);
}
```
