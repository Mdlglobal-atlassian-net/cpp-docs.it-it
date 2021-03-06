---
title: Operatori di incremento e decremento in forma prefissa
ms.date: 11/04/2016
helpviewer_keywords:
- increment operators, types of
- decrement operators, syntax
- decrement operators
ms.assetid: 9a441bb9-d94a-4b6a-9db2-0d0d76bc480d
ms.openlocfilehash: 041c44829b8a267ca053dc85da0333e86db6b7b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325494"
---
# <a name="prefix-increment-and-decrement-operators"></a>Operatori di incremento e decremento in forma prefissa

Gli operatori unari (`++` e **--**) sono denominati operatori di incremento o di decremento "prefix" quando gli operatori di incremento o decremento vengono visualizzati prima dell'operando. Decremento e incremento suffisso hanno maggiore precedenza, rispetto ad incremento e decremento prefisso. L'operando deve essere un valore integrale, a virgola mobile o un tipo di puntatore e deve essere un'espressione L-value modificabile, vale a dire un'espressione priva dell'attributo **const**. Il risultato è un l-value.

Quando l'operatore si trova prima del suo operando, l'operando viene incrementato o decrementato e il suo nuovo valore corrisponde al risultato dell'espressione.

Un operando di tipo integrale o mobile viene incrementato o decrementato dell'intero 1. Il tipo del risultato è uguale al tipo di operando. Un operando di tipo puntatore viene incrementato o decrementato alle dimensioni dell'oggetto che indirizza. Un puntatore incrementato punta all'oggetto successivo; mentre un puntatore decrementato punta all'oggetto precedente.

## <a name="example"></a>Esempio

In questo esempio viene illustrato l'operatore di decremento prefisso unario:

```
if( line[--i] != '\n' )
    return;
```

In questo esempio, la variabile `i` viene decrementata prima di essere utilizzata come indice in `line`.

## <a name="see-also"></a>Vedere anche

[Operatori unari C](../c-language/c-unary-operators.md)
