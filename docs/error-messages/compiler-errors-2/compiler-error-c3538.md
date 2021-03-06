---
title: Errore del compilatore C3538
ms.date: 11/04/2016
f1_keywords:
- C3538
helpviewer_keywords:
- C3538
ms.assetid: ef3698a5-7356-4c62-b9af-5d3a4baed958
ms.openlocfilehash: d1bd287c6b7e0b07938db55c282c69cd00fd25df
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761543"
---
# <a name="compiler-error-c3538"></a>Errore del compilatore C3538

in un elenco di dichiaratori 'auto' deve sempre essere dedotto nello stesso tipo

Tutte le variabili dichiarate in un elenco di dichiarazioni non restituiscono lo stesso tipo.

### <a name="to-correct-this-error"></a>Per correggere l'errore

1. Assicurarsi che tutte le dichiarazioni `auto` nell'elenco siano dedotte nello stesso tipo.

## <a name="example"></a>Esempio

Le seguenti istruzioni generano l'errore C3538. Ogni istruzione dichiara più variabili, ma ogni uso della parola chiave `auto` non viene dedotto nello stesso tipo.

```cpp
// C3538.cpp
// Compile with /Zc:auto
// C3538 expected
int main()
{
// Variable x1 is a pointer to char, but y1 is a double.
   auto * x1 = "a", y1 = 3.14;
// Variable c is a char and c1 is char*, but c2, and c3 are pointers to pointers.
   auto c = 'a', *c1 = &c, * c2 = &c1, * c3 = &c2;
// Variable x2 is an int, but y2 is a double and z is a char.
   auto x2(1), y2(0.0), z = 'a';
// Variable a is a pointer to int, but b is a pointer to double.
   auto *a = new auto(1), *b = new auto(2.0);
   return 0;
}
```

## <a name="see-also"></a>Vedere anche

[Auto (parola chiave)](../../cpp/auto-keyword.md)
