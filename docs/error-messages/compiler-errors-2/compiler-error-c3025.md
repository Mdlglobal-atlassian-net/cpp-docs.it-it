---
title: Errore del compilatore C3025
ms.date: 11/04/2016
f1_keywords:
- C3025
helpviewer_keywords:
- C3025
ms.assetid: 4442f5a3-d9ea-4873-b1fb-e7e5bd3cbe5e
ms.openlocfilehash: d0aac601285d4f345809f805fcccd62b7de7bab1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741976"
---
# <a name="compiler-error-c3025"></a>Errore del compilatore C3025

'clause': prevista espressione integrale

Una clausola richiede un'espressione integer ma è stata assegnata un'espressione noninteger.

## <a name="example"></a>Esempio

L'esempio seguente genera l'errore C3025.

```cpp
// C3025.cpp
// compile with: /openmp /link vcomps.lib
#include <stdio.h>
#include "omp.h"

float f = 2.0F;

int main()
{
    int i = 0;

    // OK
    puts("Test with int");
    #pragma omp parallel for num_threads(i)
    for (i = 1; i <= 2; ++i)
        printf_s("Hello World - thread %d - iteration %d\n",
                 omp_get_thread_num(), i);

    puts("Test with float");
    #pragma omp parallel for num_threads(f)   // C3025
    for (i = 1; i <= 2; ++i)
        printf_s("Hello World - thread %d - iteration %d\n",
                 omp_get_thread_num(), i);
}
```
