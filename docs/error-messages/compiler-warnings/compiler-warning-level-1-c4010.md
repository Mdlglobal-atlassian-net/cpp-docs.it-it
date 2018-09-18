---
title: Compilatore Warning (level 1) C4010 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4010
dev_langs:
- C++
helpviewer_keywords:
- C4010
ms.assetid: d607a9ff-8f8f-45c0-b07b-3b2f439e5485
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52449689d329cee45cc69b63c315ce9335befbe0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073102"
---
# <a name="compiler-warning-level-1-c4010"></a>Compilatore Warning (level 1) C4010

commento a riga singola contiene il carattere di continuazione di riga

Un commento a riga singola, che è stato introdotto per / /, contiene una barra rovesciata (\\) che funge da un carattere di continuazione di riga. Il compilatore considera la riga successiva da una continuation e lo considera come un commento.

Alcune sintassi verso gli editor non indicano la riga che segue il carattere di continuazione come commento. Ignora in tutte le righe che causano il problema di colorazione della sintassi.

L'esempio seguente genera l'errore C4010:

```
// C4010.cpp
// compile with: /WX
int main() {
   // the next line is also a comment because of the backslash \
   int a = 3; // C4010
   a++;
}
```