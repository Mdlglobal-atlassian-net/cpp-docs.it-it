---
title: Errore del compilatore C3041
ms.date: 11/04/2016
f1_keywords:
- C3041
helpviewer_keywords:
- C3041
ms.assetid: 9df1ae44-3ac7-4c6c-899f-f35ffe7ccf0d
ms.openlocfilehash: 43f75e9d054f574eb121d20eb35d302cef849566
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182574"
---
# <a name="compiler-error-c3041"></a>Errore del compilatore C3041

'var': la variabile nella clausola 'copyprivate' deve essere privata nel contesto di inclusione

Una variabile passata a [copyprivate](../../parallel/openmp/reference/copyprivate.md) non può essere condivisa nel contesto di inclusione.

L'esempio seguente genera l'errore C3041:

```
// C3041.cpp
// compile with: /openmp /c
#include "omp.h"
double d;
int main() {
   #pragma omp parallel shared(d)
   // try the following line instead
   // #pragma omp parallel private(d)
   {
      // or don't make d copyprivate
      #pragma omp single copyprivate(d)   // C3041
      {
      }
   }
}
```