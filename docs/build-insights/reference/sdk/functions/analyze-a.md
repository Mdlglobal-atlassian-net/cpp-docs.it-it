---
title: AnalisiA
description: Informazioni di riferimento per la funzione AnalyzeA di Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalyzeA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7c7602c49ab5f3ce67693424019e253727563293
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324133"
---
# <a name="analyzea"></a>AnalisiA

::: moniker range="<=vs-2015"

L'SDK di approfondimenti per la compilazione in Cè è compatibile con Visual Studio 2017 e versioni successive. Per visualizzare la documentazione di queste versioni, impostare il controllo del selettore di versione di Visual Studio per questo articolo su Visual Studio 2017 o Visual Studio 2019.To see the documentation for these versions, set the Visual Studio **Version** selector control for this article to Visual Studio 2017 or Visual Studio 2019. Si trova nella parte superiore del sommario in questa pagina.

::: moniker-end
::: moniker range=">=vs-2017"

La `AnalyzeA` funzione viene utilizzata per analizzare gli eventi MSVC letti da una traccia ETW (Event Tracing for Windows) di input.

## <a name="syntax"></a>Sintassi

```cpp
enum RESULT_CODE AnalyzeA(
    const char*                inputLogFile,
    const ANALYSIS_DESCRIPTOR* analysisDescriptor);
```

### <a name="parameters"></a>Parametri

*inputLogFile*\
Traccia ETW di input da cui si desidera leggere gli eventi.

*analysisDescriptor (esempio)*\
Puntatore a un oggetto [ANALYSIS_DESCRIPTOR.](../other-types/analysis-descriptor-struct.md) Utilizzare questo oggetto per configurare l'analisi.

### <a name="return-value"></a>Valore restituito

Codice di risultato dall'enumerazione [RESULT_CODE.](../other-types/result-code-enum.md)

::: moniker-end
