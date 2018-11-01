---
title: Errore del compilatore C2470
ms.date: 11/04/2016
f1_keywords:
- C2470
helpviewer_keywords:
- C2470
ms.assetid: e17d2cb8-b84c-447c-976a-625f0c96f3fe
ms.openlocfilehash: 2a4f8c8052081fe90801dfeb30d942fbb9a91a01
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517156"
---
# <a name="compiler-error-c2470"></a>Errore del compilatore C2470

'function': sembra una definizione di funzione, ma non sono presenti elenchi di parametri; corpo apparente della verrà ignorato

Una definizione di funzione manca l'elenco di argomenti.

L'esempio seguente genera l'errore C2470:

```
// C2470.cpp
int MyFunc {};  // C2470
void MyFunc2() {};  //OK

int main(){
   MyFunc();
   MyFunc2();
}
```