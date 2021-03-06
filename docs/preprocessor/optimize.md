---
title: Pragma optimize
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.optimize
- optimize_CPP
helpviewer_keywords:
- pragmas, optimize
- optimize pragma
ms.assetid: cb13c1cc-186a-45bc-bee7-95a8de7381cc
ms.openlocfilehash: 6d7b99b7a72c133d56a209cf42fa9ef670a4a7f9
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220510"
---
# <a name="optimize-pragma"></a>Pragma optimize

Specifica le ottimizzazioni in base alla funzione.

## <a name="syntax"></a>Sintassi

> **#pragma optimize ("** [ *Optimization-list* ] **",** { **on** | **off** } **)**

## <a name="remarks"></a>Note

Il pragma optimize deve trovarsi all'esterno di una funzione. Viene applicata alla prima funzione definita dopo che il pragma è stato individuato. Gli argomenti **on** e **off** attivano o disattivano le opzioni specificate nell' *elenco di ottimizzazione* .

L' *elenco di ottimizzazione* può essere costituito da zero o più parametri indicati nella tabella seguente.

### <a name="parameters-of-the-optimize-pragma"></a>Parametri di Pragma optimize

| Parametro/i | Tipo di ottimizzazione |
|--------------------|--------------------------|
| **g** | Abilita le ottimizzazioni globali. |
| **s** o **t** | Specificare sequenze brevi o veloci di codice macchina. |
| **y** | Generare i puntatori ai frame nello stack del programma. |

Questi parametri sono le stesse lettere utilizzate con le opzioni [/o](../build/reference/o-options-optimize-code.md) del compilatore. Ad esempio, il pragma seguente rappresenta l'equivalente dell'opzione del compilatore `/Os`:

```cpp
#pragma optimize( "s", on )
```

L'utilizzo del pragma optimize con la stringa vuota ( **""** ) è un formato speciale della direttiva:

Quando si usa il parametro **off** , vengono attivate tutte le ottimizzazioni **, g**, **s**, **t**e **y**, off.

Quando si usa il parametro **on** , vengono reimpostate le ottimizzazioni per quelle specificate tramite l'opzione del compilatore [/o](../build/reference/o-options-optimize-code.md) .

```cpp
#pragma optimize( "", off )
/* unoptimized code section */
#pragma optimize( "", on )
```

## <a name="see-also"></a>Vedere anche

[Direttive pragma e parola chiave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
