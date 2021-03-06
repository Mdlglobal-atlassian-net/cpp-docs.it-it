---
title: Costanti file
ms.date: 11/04/2016
f1_keywords:
- _O_EXCL
- _O_RDWR
- _O_APPEND
- _O_RDONLY
- _O_TRUNC
- _O_CREAT
- _O_WRONLY
helpviewer_keywords:
- _O_RDWR constant
- O_EXCL constant
- O_RDWR constant
- O_WRONLY constant
- O_APPEND constant
- O_CREAT constant
- _O_CREAT constant
- _O_APPEND constant
- _O_EXCL constant
- O_TRUNC constant
- _O_RDONLY constant
- _O_TRUNC constant
- O_RDONLY constant
- _O_WRONLY constant
ms.assetid: c8fa5548-9ac2-4217-801d-eb45e86f2fa4
ms.openlocfilehash: f0bf85dc8f27fca1720cde7f5a8b2029a791849c
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739971"
---
# <a name="file-constants"></a>Costanti file

## <a name="syntax"></a>Sintassi

```
#include <fcntl.h>
```

## <a name="remarks"></a>Osservazioni

L'espressione integer formata da una o più di queste costanti determina il tipo di operazioni di lettura o scrittura consentite. È formato dalla combinazione di uno o più costanti con una costante in modalità di conversione.

Le costanti di file sono le seguenti:

|Costante|Description|
|-|-|
| `_O_APPEND`  | Riposiziona il puntatore di file alla fine del file prima di ogni operazione di scrittura.  |
| `_O_CREAT`  | Crea e apre un nuovo file per la scrittura; ciò non ha effetto se esiste il file specificato da *filename*.  |
| `_O_EXCL`  | Restituisce un errore se esiste il file specificato da *filename*. Si applica solo se utilizzato con `_O_CREAT`.  |
| `_O_RDONLY`  | Apre il file in sola lettura; se questo flag viene fornito, né `_O_RDWR` né `_O_WRONLY` possono essere forniti.  |
| `_O_RDWR`  | Apre il file in lettura e scrittura; se questo flag viene fornito, né `_O_RDONLY` né `_O_WRONLY` possono essere forniti.  |
| `_O_TRUNC`  | Apre e tronca un file esistente a lunghezza zero; il file deve avere l'autorizzazione di scrittura. Il contenuto del file viene eliminato. Se questo flag viene fornito, non è possibile specificare `_O_RDONLY`.  |
| `_O_WRONLY`  | Apre il file in sola scrittura; se questo flag viene fornito, né `_O_RDONLY` né `_O_RDWR` possono essere forniti.  |

## <a name="see-also"></a>Vedere anche

[_open, _wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[Costanti globali](../c-runtime-library/global-constants.md)
