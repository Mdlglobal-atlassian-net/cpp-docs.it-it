---
title: Errore degli strumenti del linker LNK1301
ms.date: 11/04/2016
f1_keywords:
- LNK1301
helpviewer_keywords:
- LNK1301
ms.assetid: 760da428-7182-4b25-b20a-de90d4b9a9cd
ms.openlocfilehash: 6a82d7756f1460c56d87a3d7b1360c140de19827
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160607"
---
# <a name="linker-tools-error-lnk1301"></a>Errore degli strumenti del linker LNK1301

Moduli clr LTCG incompatibile con /LTCG: parametro

Un modulo compilato con /GL e /clr è stato passato al linker insieme a uno delle ottimizzazioni PGO parametri (PGO) di /LTCG.

Ottimizzazione PGO non sono supportati per i moduli /clr.

Per altre informazioni, vedere:

- [/GL (ottimizzazione intero programma)](../../build/reference/gl-whole-program-optimization.md)

- [/LTCG (generazione di codice in fase di collegamento)](../../build/reference/ltcg-link-time-code-generation.md)

- [/clr (compilazione Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Ottimizzazioni PGO](../../build/profile-guided-optimizations.md)

### <a name="to-correct-this-error"></a>Per correggere l'errore

1. Non compilare con /clr o non si collega con uno dei parametri di ottimizzazione PGO di /LTCG.

## <a name="example"></a>Esempio

L'esempio seguente genera l'errore LNK1301:

```
// LNK1301.cpp
// compile with: /clr /GL /link /LTCG:PGI LNK1301.obj
// LNK1301 expected
class MyClass {
public:
   int i;
};
```