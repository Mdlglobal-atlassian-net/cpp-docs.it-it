---
title: Errore del compilatore C3034
ms.date: 11/04/2016
f1_keywords:
- C3034
helpviewer_keywords:
- C3034
ms.assetid: 49db8bac-2720-4622-94e3-7988f1603fa3
ms.openlocfilehash: d0a5da87feeabc5d3d5b558ce0dd6bdfe3869d53
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165567"
---
# <a name="compiler-error-c3034"></a>Errore del compilatore C3034

impossibile annidare la direttiva OpenMP 'direttiva1' direttamente nella direttiva 'direttiva2'

Alcune direttive non possono essere annidate. Per correggere questo errore, è possibile unire le istruzioni di entrambe le direttive nel blocco di una direttiva oppure creare direttive consecutive.

L'esempio seguente genera l'errore C3034:

```
// C3034.cpp
// compile with: /openmp /link vcomps.lib
int main() {

   #pragma omp single
   {
      #pragma omp single   // C3034
      {
      ;
      }
   }

   // Two consecutive single clauses are OK.
   #pragma omp single
   {
   }

   #pragma omp single
   {
   }
}
```