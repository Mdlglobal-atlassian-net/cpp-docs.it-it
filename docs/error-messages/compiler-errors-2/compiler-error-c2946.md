---
title: Errore del compilatore C2946
ms.date: 11/04/2016
f1_keywords:
- C2946
helpviewer_keywords:
- C2946
ms.assetid: c86dfbfc-7702-4f09-8a53-d205710e99c2
ms.openlocfilehash: c0ea10b3614e20e7f47c8f6632843544b4842751
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755369"
---
# <a name="compiler-error-c2946"></a>Errore del compilatore C2946

creazione di un'istanza esplicita. 'class' non è una specializzazione della classe modello

Non è possibile creare un'istanza esplicita di una classe non basata su modello.

## <a name="example"></a>Esempio

L'esempio seguente genera l'errore C2946.

```cpp
// C2946.cpp
class C {};
template C;  // C2946
int main() {}
```
