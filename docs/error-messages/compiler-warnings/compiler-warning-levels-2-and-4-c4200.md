---
title: Avviso del compilatore (livelli 2 e 4) C4200
ms.date: 11/04/2016
f1_keywords:
- C4200
helpviewer_keywords:
- C4200
ms.assetid: e44d6073-937f-42b7-acc1-65e802b475c6
ms.openlocfilehash: 4b0750fe50e18214e0841eff6b3459438e9a6aec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197951"
---
# <a name="compiler-warning-levels-2-and-4-c4200"></a>Avviso del compilatore (livelli 2 e 4) C4200

usata estensione non standard: matrice di dimensioni zero in struct/union

Una struttura o un'unione contiene una matrice di dimensioni pari a zero.

La dichiarazione di una matrice con dimensione zero è un'estensione Microsoft. L'avviso è di livello 2 quando viene compilato un file C++ e di livello 4 quando viene compilato un file C. La compilazione C++ fornisce inoltre l'avviso: "Impossibile generare un operatore di costruttore di copia o di assegnazione copia se un tipo definito dall'utente contiene una matrice di dimensioni zero". Questo esempio genera l'avviso C4200:

```cpp
// C4200.cpp
// compile by using: cl /W4 c4200.cpp
struct A {
    int a[0];  // C4200
};
int main() {
}
```

Questa estensione non standard viene spesso usata per interfacciare il codice con le strutture di dati esterni che hanno una lunghezza variabile. Se questo scenario si applica al codice, è possibile disabilitare l'avviso:

## <a name="example"></a>Esempio

```cpp
// C4200b.cpp
// compile by using: cl /W4 c4200a.cpp
#pragma warning(disable : 4200)
struct A {
    int a[0];
};
int main() {
}
```
