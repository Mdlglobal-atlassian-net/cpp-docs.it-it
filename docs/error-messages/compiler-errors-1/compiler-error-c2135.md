---
title: Errore del compilatore C2135
ms.date: 11/04/2016
f1_keywords:
- C2135
helpviewer_keywords:
- C2135
ms.assetid: aa360d22-4f79-4de1-b384-93cadd10975f
ms.openlocfilehash: 4bc9d8bc3db5fbd826ded37d93ac812116356eb2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757488"
---
# <a name="compiler-error-c2135"></a>Errore del compilatore C2135

'bit operator': operazione su campo di bit non valida

L'operatore address-of (`&`) non può essere applicato a un campo di bit.

L'esempio seguente genera l'errore C2135:

```cpp
// C2135.cpp
struct S {
   int i : 1;
};

struct T {
   int j;
};
int main() {
   &S::i;   // C2135 address of a bit field
   &T::j;   // OK
}
```
