---
title: Errore del compilatore C2572
ms.date: 11/04/2016
f1_keywords:
- C2572
helpviewer_keywords:
- C2572
ms.assetid: f1a42d69-727d-4ce5-88c8-d5f55dea66ac
ms.openlocfilehash: 78402c054573de8c9860e96b6abe60ec5c3cfe38
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2018
ms.locfileid: "50621247"
---
# <a name="compiler-error-c2572"></a>Errore del compilatore C2572

'member': ridefinizione del parametro predefinito: parametro param

I parametri predefiniti non possono essere ridefiniti. Se è necessario un altro valore per il parametro, il parametro predefinito deve essere lasciato non definito.

L'esempio seguente genera l'errore C2572:

```
// C2572.cpp
// compile with: /c
void f(int i = 1);   // function declaration

// function definition
void f(int i = 1) {}   // C2572

// try the following line instead
// void f(int i) {}
```