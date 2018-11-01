---
title: Errore del compilatore C2117
ms.date: 11/04/2016
f1_keywords:
- C2117
helpviewer_keywords:
- C2117
ms.assetid: b947379d-5861-42fc-ac26-170318579cbd
ms.openlocfilehash: 2f6a1e26972f093e50c5e655935f750195ab7d3b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435165"
---
# <a name="compiler-error-c2117"></a>Errore del compilatore C2117

'identifier': overflow dei limiti della matrice

Una matrice ha troppi inizializzatori:

- Gli inizializzatori e gli elementi della matrice non corrispondono nella dimensione e quantità.

- Nessuno spazio per il carattere di terminazione null in una stringa.

L'esempio seguente genera l'errore C2117:

```
// C2117.cpp
int main() {
   char abc[4] = "abcd";   // C2117
   char def[4] = "abd";   // OK
}
```