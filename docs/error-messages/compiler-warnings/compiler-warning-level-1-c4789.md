---
title: Avviso del compilatore (livello 1) C4789
ms.date: 03/25/2019
f1_keywords:
- C4789
helpviewer_keywords:
- C4789
ms.assetid: 5800c301-5afb-4af0-85c1-ceb54d775234
ms.openlocfilehash: 36278615631d017db1d1c2fc4eecf8c1612892de
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518400"
---
# <a name="compiler-warning-level-1-c4789"></a>Avviso del compilatore (livello 1) C4789

> il buffer '*Identifier*' di dimensioni *N* byte verrà sovraccaricato; I byte *M* verranno scritti a partire dall'offset *L*

## <a name="remarks"></a>Note

**C4789** avverte i sovraccarichi del buffer quando vengono usate funzioni di runtime C (CRT) specifiche. Può inoltre segnalare dimensioni non corrispondenti quando vengono passati parametri o vengono assegnate assegnazioni. L'avviso è possibile se le dimensioni dei dati sono note in fase di compilazione. Questo avviso è relativo alle situazioni in cui potrebbe essere eluso il normale rilevamento di dimensioni non corrispondenti dei dati.

**C4789** avverte quando i dati vengono copiati in un blocco di dati troppo piccolo in fase di compilazione.

L'avviso viene visualizzato se la copia utilizza il formato intrinseco di una delle funzioni CRT seguenti:

- [strcpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)

- [memset](../../c-runtime-library/reference/memset-wmemset.md)

- [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md), [wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)

L'avviso viene visualizzato anche quando si esegue il cast di un parametro a un tipo di dati più grande, quindi si effettua un'assegnazione di copia da un riferimento lvalue.

L' C++ oggetto visivo potrebbe generare questo avviso per un percorso di codice che non viene mai eseguito. È possibile disabilitare temporaneamente l'avviso usando `#pragma`, come mostrato in questo esempio:

```cpp
#pragma warning( push )
#pragma warning( disable : 4789 )
// unused code that generates compiler warning C4789`
#pragma warning( pop )
```

Questo idioma impedisce C++ agli oggetti visivi di generare l'avviso per quel blocco di codice specifico. `#pragma warning(push)` mantiene lo stato esistente prima che `#pragma warning(disable: 4789)` lo modifichi. `#pragma warning(pop)` ripristina lo stato di cui è stato eseguito il push ed elimina gli effetti di `#pragma warning(disable:4789)`. Per altre informazioni sulla direttiva C++ per il preprocessore `#pragma`, vedere direttive [warning](../../preprocessor/warning.md) e [Pragma e la parola chiave __Pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).

## <a name="example"></a>Esempio

L'esempio seguente genera l'errore C4789.

```cpp
// C4789.cpp
// compile with: /Oi /W1 /c
#include <string.h>
#include <stdio.h>

int main()
{
    char a[20];
    strcpy(a, "0000000000000000000000000\n");   // C4789

    char buf2[20];
    memset(buf2, 'a', 21);   // C4789

    char c;
    wchar_t w = 0;
    memcpy(&c, &w, sizeof(wchar_t));
}
```

## <a name="example"></a>Esempio

Anche l'esempio seguente genera l'errore C4789.

```cpp
// C4789b.cpp
// compile with: /W1 /O2 /c
// processor: x86
short G;

int main()
{
   int * p = (int *)&G;
   *p = 3;   // C4789 - writes an int through a pointer to short
}
```
