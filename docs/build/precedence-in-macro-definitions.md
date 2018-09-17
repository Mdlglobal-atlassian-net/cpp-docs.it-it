---
title: Precedenza nelle definizioni di Macro | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, precedence in macro definitions
- macros, precedence
ms.assetid: 0c13182d-83cb-4cbd-af2d-f4c916b62aeb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 21a3d8873fd1fee61afec865181bab27305bebfd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722215"
---
# <a name="precedence-in-macro-definitions"></a>Precedenza nelle definizioni delle macro

Se una macro contiene più definizioni, NMAKE Usa la definizione di precedenza più alta. Nell'elenco seguente mostra l'ordine di precedenza, dal più alto al più basso:

1. Una macro definita nella riga di comando

1. Una macro definita in un makefile o file di inclusione

1. Una macro di variabili di ambiente ereditata

1. Una macro definita nel file. Tools. ini

1. Macro predefinita, ad esempio [CC](../build/command-macros-and-options-macros.md) e [AS](../build/command-macros-and-options-macros.md)

Utilizzare /E macro ereditate dalle variabili di ambiente per eseguire l'override di makefile macro con lo stesso nome. Usare **! UNDEF** per eseguire l'override di una riga di comando.

## <a name="see-also"></a>Vedere anche

[Definizione di una macro di NMAKE](../build/defining-an-nmake-macro.md)