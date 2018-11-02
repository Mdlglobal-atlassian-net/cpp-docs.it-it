---
title: Errore del compilatore C3207
ms.date: 11/04/2016
f1_keywords:
- C3207
helpviewer_keywords:
- C3207
ms.assetid: 4a28b976-142a-4cff-aa2f-480b892c50ca
ms.openlocfilehash: 51873e089499e42f4ddeb97c95e3f18416df447c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515492"
---
# <a name="compiler-error-c3207"></a>Errore del compilatore C3207

'function': argomento di modello non valido per 'arg'. Previsto modello di classe

La definizione di una funzione di modello prevede che accetti un argomento di modello template. Tuttavia è stato passato un argomento di tipo modello.

L'esempio seguente genera l'errore C3207:

```
// C3207.cpp
template <template <class T> class TT>
void f(){}

template <class T>
struct S
{
};

void f1()
{
   f<S<int> >();   // C3207
   // try the following line instead
   // f<S>();
}
```