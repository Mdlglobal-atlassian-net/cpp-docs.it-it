---
title: Errore del compilatore C2474
ms.date: 11/04/2016
f1_keywords:
- C2474
helpviewer_keywords:
- C2474
ms.assetid: 64e6c61e-6e77-480e-bcf0-b30a2fc482ac
ms.openlocfilehash: c49f38b828a41c72135ba9182d4d0f5eee4df1de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475309"
---
# <a name="compiler-error-c2474"></a>Errore del compilatore C2474

'keyword': manca un punto e virgola adiacente, potrebbe trattarsi di una parola chiave o di un identificatore.

Il compilatore prevedeva un punto e virgola e non è riuscito a interpretare il codice. Per correggere questo errore, aggiungere il punto e virgola.

## <a name="example"></a>Esempio

L'esempio seguente genera l'errore C2474.

```
// C2474.cpp
// compile with: /clr /c

ref class A {
   ref class B {}
   property int i;   // C2474 error
};

// OK
ref class B {
   ref class D {};
   property int i;
};

ref class E {
   ref class F {} property;
   int i;
};
```