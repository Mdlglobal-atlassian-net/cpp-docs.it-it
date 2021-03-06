---
title: Pragma managed, unmanaged
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.unmanaged
- managed_CPP
- unmanaged_CPP
- vc-pragma.managed
helpviewer_keywords:
- managed pragma
- pragmas, unmanaged
- pragmas, managed
- unmanaged pragma
ms.assetid: f072ddcc-e1ec-408a-8ce1-326ddb60e4a4
ms.openlocfilehash: 4c13155d1c84966a593df11baf525a0c3539f02c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218805"
---
# <a name="managed-unmanaged-pragmas"></a>Pragma managed, unmanaged

Abilitare il controllo a livello di funzione per compilare funzioni come gestite o non gestite.

## <a name="syntax"></a>Sintassi

> **#pragma gestiti**\
> **#pragma non gestito**\
> **#pragma gestiti (** [ **push,** ] { **on** | **off** } **)** \
> **gestione #pragma (pop)**

## <a name="remarks"></a>Note

L'opzione del compilatore [/CLR](../build/reference/clr-common-language-runtime-compilation.md) fornisce il controllo a livello di modulo per la compilazione di funzioni come gestite o non gestite.

Per la piattaforma nativa verrà compilata una funzione non gestita. L'esecuzione di tale parte del programma verrà passata alla piattaforma nativa dalla Common Language Runtime.

Le funzioni vengono compilate come gestite per impostazione predefinita quando `/clr` viene usato.

Quando si applicano questi pragma:

- Aggiungere il pragma che precede una funzione, ma non all'interno del corpo di una funzione.

- Aggiungere il pragma dopo le istruzioni `#include`. Non usare questi pragma prima `#include` delle istruzioni.

Il compilatore ignora i pragma **gestiti** e non **gestiti** se `/clr` non viene usato nella compilazione.

Quando viene creata un'istanza di una funzione di modello, lo stato pragma quando viene definito il modello determina se è gestito o non gestito.

Per ulteriori informazioni, vedere [inizializzazione di assembly misti](../dotnet/initialization-of-mixed-assemblies.md).

## <a name="example"></a>Esempio

```cpp
// pragma_directives_managed_unmanaged.cpp
// compile with: /clr
#include <stdio.h>

// func1 is managed
void func1() {
   System::Console::WriteLine("In managed function.");
}

// #pragma unmanaged
// push managed state on to stack and set unmanaged state
#pragma managed(push, off)

// func2 is unmanaged
void func2() {
   printf("In unmanaged function.\n");
}

// #pragma managed
#pragma managed(pop)

// main is managed
int main() {
   func1();
   func2();
}
```

```Output
In managed function.
In unmanaged function.
```

## <a name="see-also"></a>Vedere anche

[Direttive pragma e parola chiave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
