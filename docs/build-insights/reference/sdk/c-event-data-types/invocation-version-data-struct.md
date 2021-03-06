---
title: struttura INVOCATION_VERSION_DATA
description: L'SDK di analisi di compilazione di C'è INVOCATION_VERSION_DATA riferimento alla struttura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_VERSION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1211b4eb999fd63767af71c6884d7d20d6920df0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325477"
---
# <a name="invocation_version_data-structure"></a>struttura INVOCATION_VERSION_DATA

::: moniker range="<=vs-2015"

L'SDK di approfondimenti per la compilazione in Cè è compatibile con Visual Studio 2017 e versioni successive. Per visualizzare la documentazione di queste versioni, impostare il controllo del selettore di versione di Visual Studio per questo articolo su Visual Studio 2017 o Visual Studio 2019.To see the documentation for these versions, set the Visual Studio **Version** selector control for this article to Visual Studio 2017 or Visual Studio 2019. Si trova nella parte superiore del sommario in questa pagina.

::: moniker-end
::: moniker range=">=vs-2017"

La `INVOCATION_VERSION_DATA` struttura descrive un numero di versione come un gruppo di valori integrali.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct INVOCATION_VERSION_DATA_TAG
{
    unsigned short VersionMajor;
    unsigned short VersionMinor;
    unsigned short BuildNumberMajor;
    unsigned short BuildNumberMinor;

} INVOCATION_VERSION_DATA;
```

## <a name="members"></a>Membri

|  |  |
|--|--|
| `VersionMajor` | Il numero principale della versione. |
| `VersionMinor` | Il numero minore della versione. |
| `BuildNumberMajor` | Il numero principale della build. |
| `BuildNumberMinor` | Il numero minore della build. |

::: moniker-end
