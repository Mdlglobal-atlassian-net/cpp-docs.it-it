---
title: Errore ML non irreversibile A2133
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2133
helpviewer_keywords:
- A2133
ms.assetid: 5ba50911-22c8-43b7-90e2-946fc612e05f
ms.openlocfilehash: 9e13dd48c77b9574229023e3cfc4cc2f2221d153
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62201210"
---
# <a name="ml-nonfatal-error-a2133"></a>Errore ML non irreversibile A2133

**registrare il valore sovrascritto da INVOKE**

Un registro è stato passato come argomento a una routine, ma il codice generato dallo [INVOKE](../../assembler/masm/invoke.md) passare altri argomenti eliminato il contenuto del registro.

I registri AX, AL, AH, registri EAX, DX, lista di distribuzione, DH ed EDX potrebbero utilizzabile nell'assembler per eseguire la conversione dei dati.

Usare un registro diverso.

## <a name="see-also"></a>Vedere anche

[Messaggi di errore ML](../../assembler/masm/ml-error-messages.md)<br/>