---
title: Errore del compilatore C2991
ms.date: 11/04/2016
f1_keywords:
- C2991
helpviewer_keywords:
- C2991
ms.assetid: a87e4404-26e8-4927-b3ee-5d02b3b8bee1
ms.openlocfilehash: 8a6cf04d89cd18cb5374f2d930b5395a297ce8f5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751508"
---
# <a name="compiler-error-c2991"></a>Errore del compilatore C2991

ridefinizione del parametro di tipo 'parameter'

Si è verificato un conflitto di tipo tra due definizioni generiche o di modello di `parameter`. Quando si definiscono più parametri generici o di modello, è necessario usare tipi equivalenti.

L'esempio seguente genera l'errore C2991:

```cpp
// C2991.cpp
// compile with: /c
template<class T, class T> struct TC {};   // C2991
// try the following line instead
// template<class T, class T2> struct TC {};
```

L'errore C2991 può verificarsi anche quando si usano i generics:

```cpp
// C2991b.cpp
// compile with: /clr /c
generic<class T,class T> ref struct GC {};   // C2991
// try the following line instead
// generic<class T,class T2> ref struct GC {};
```
