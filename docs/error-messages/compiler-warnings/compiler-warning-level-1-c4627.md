---
title: Avviso del compilatore (livello 1) C4627
ms.date: 09/09/2018
f1_keywords:
- C4627
helpviewer_keywords:
- C4627
ms.assetid: 8840f3e6-b496-423a-8635-eb55d5f854a2
ms.openlocfilehash: 06db3d7e585dfe49b2e0854973f63834648613b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221378"
---
# <a name="compiler-warning-level-1-c4627"></a>Avviso del compilatore (livello 1) C4627

> «*header_file*': ignorato durante la ricerca utilizzo di intestazione precompilata

Se il file di origine corrente ha il [/Yu \(utilizzare file di intestazione precompilato)](../../build/reference/yu-use-precompiled-header-file.md) opzione set, il compilatore ignora tutti gli elementi nel file prima che l'intestazione precompilata è incluso. Avviso **C4627** se viene generato in Visual Studio 2015 e versioni precedenti *header_file* prima il file di intestazione precompilata, e se l'intestazione precompilata non include inoltre *header_file*.

## <a name="example"></a>Esempio

Questo esempio viene illustrato come può verificarsi l'errore e Mostra come risolverlo:

```cpp
// c4627.cpp
#include <iostream>       // C4627 - iostream not included by pch.h
#include "pch.h"          // precompiled header file that does not include iostream
// #include <iostream>    // To fix, move the iostream header include here from above
int main()
{
    std::cout << "std::cout is defined!\n";
}
```

## <a name="see-also"></a>Vedere anche

[Creazione di file di intestazione precompilata](../../build/creating-precompiled-header-files.md)
