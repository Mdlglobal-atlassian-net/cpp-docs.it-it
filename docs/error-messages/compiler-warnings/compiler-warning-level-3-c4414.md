---
title: Avviso del compilatore (livello 3) C4414
ms.date: 11/04/2016
f1_keywords:
- C4414
helpviewer_keywords:
- C4414
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
ms.openlocfilehash: 4625f6bdb4aa6fe86ca881a8e36e5673e55ccb87
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185594"
---
# <a name="compiler-warning-level-3-c4414"></a>Avviso del compilatore (livello 3) C4414

' Function ': breve salto alla funzione convertita in near

I Short Jump generano istruzioni Compact che diramano a un indirizzo all'interno di un intervallo limitato dall'istruzione. L'istruzione include un offset breve che rappresenta la distanza tra il salto e l'indirizzo di destinazione, la definizione della funzione. Durante il collegamento, una funzione può essere spostata o soggetta a ottimizzazioni in fase di collegamento che provocano lo spostamento della funzione fuori dall'intervallo raggiungibile da un offset breve. Il compilatore deve generare un record speciale per il salto, che richiede che l'istruzione JMP sia vicina o LONTANa. Il compilatore ha effettuato la conversione.

Il codice seguente, ad esempio, genera C4414:

```cpp
// C4414.cpp
// compile with: /W3 /c
// processor: x86
int DoParityEven();
int DoParityOdd();
unsigned char global;
int __declspec(naked) DoParityEither()
{
   __asm
   {
      test global,0
      jpe SHORT DoParityEven  // C4414
      jmp SHORT DoParityOdd   // C4414
   }
}
```
