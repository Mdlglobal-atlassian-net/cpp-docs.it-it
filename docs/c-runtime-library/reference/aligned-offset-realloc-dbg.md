---
title: _aligned_offset_realloc_dbg
ms.date: 11/04/2016
api_name:
- _aligned_offset_realloc_dbg
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- aligned_offset_realloc_dbg
- _aligned_offset_realloc_dbg
helpviewer_keywords:
- aligned_offset_realloc_dbg function
- _aligned_offset_realloc_dbg function
ms.assetid: 64e30a12-887e-453b-aea8-aed793fca9d8
ms.openlocfilehash: ce85fd0dec54a3963af5ae807dfb6f56f92eda7a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939756"
---
# <a name="_aligned_offset_realloc_dbg"></a>_aligned_offset_realloc_dbg

Modifica la dimensione di un blocco di memoria allocato con [_aligned_malloc](aligned-malloc.md) o [_aligned_offset_malloc](aligned-offset-malloc.md) (solo versione di debug).

## <a name="syntax"></a>Sintassi

```C
void * _aligned_offset_realloc_dbg(
   void *memblock,
   size_t size,
   size_t alignment,
   size_t offset,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametri

*memblock*<br/>
Puntatore al blocco di memoria corrente.

*size*<br/>
Dimensione dell'allocazione di memoria.

*alignment*<br/>
Valore di allineamento, che deve essere una potenza intera di 2.

*offset*<br/>
Offset nell'allocazione di memoria per imporre l'allineamento.

*filename*<br/>
Puntatore al nome del file di origine che ha richiesto l'operazione **aligned_offset_realloc** o **null**.

*linenumber*<br/>
Numero di riga nel file di origine in cui è stata richiesta l'operazione **aligned_offset_realloc** o **null**.

## <a name="return-value"></a>Valore restituito

**_aligned_offset_realloc_dbg** restituisce un puntatore void al blocco di memoria riallocato (e possibilmente spostato). Il valore restituito è **null** se la dimensione è zero e l'argomento del buffer non è **null**o se la memoria disponibile non è sufficiente per espandere il blocco alla dimensione specificata. Nel primo caso il blocco originale viene liberato. Nel secondo caso il blocco originale resta invariato. Il valore restituito punta a uno spazio di archiviazione che garantisce il corretto allineamento per l'archiviazione di qualsiasi tipo di oggetto. Per ottenere un puntatore a un tipo diverso da void, usare un cast del tipo sul valore restituito.

## <a name="remarks"></a>Note

**_aligned_offset_realloc_dbg** è una versione di debug della funzione [_aligned_offset_realloc](aligned-offset-realloc.md) . Quando _ [debug](../../c-runtime-library/debug.md) non è definito, ogni chiamata a **_aligned_offset_realloc_dbg** viene ridotta a una chiamata a **_aligned_offset_realloc**. Sia **_aligned_offset_realloc** che **_aligned_offset_realloc_dbg** riallocano un blocco di memoria nell'heap di base, ma **_aligned_offset_realloc_dbg** supporta diverse funzionalità di debug: buffer su entrambi i lati della parte utente di blocco in cui verificare la presenza di perdite e *filename*/*lineNumber* informazioni per determinare l'origine delle richieste di allocazione. Il rilevamento di tipi di allocazione specifici con un parametro di tipo blocco non è una funzionalità di debug supportata per le allocazioni allineate. Le allocazioni allineate verranno visualizzate come tipo di blocco _NORMAL_BLOCK.

Analogamente a [_aligned_offset_malloc](aligned-offset-malloc.md), **_aligned_offset_realloc_dbg** consente l'allineamento di una struttura a un offset all'interno della struttura.

**_realloc_dbg** rialloca il blocco di memoria specificato con una quantità di spazio leggermente superiore a quella richiesta dal *newSize*. *newSize* potrebbe essere maggiore o minore delle dimensioni del blocco di memoria allocato in origine. Lo spazio aggiuntivo viene usato dal gestore dell'heap di debug per collegare i blocchi di memoria di debug e per fornire all'applicazione informazioni di intestazione di debug e buffer di sovrascrittura. La riallocazione potrebbe comportare lo spostamento del blocco di memoria originale in un'altra posizione nell'heap nonché la modifica della dimensione del blocco di memoria. Se il blocco di memoria viene spostato, i contenuti del blocco originale verranno sovrascritti.

Questa funzione imposta **errno** su **ENOMEM** se l'allocazione di memoria non riesce o se la dimensione richiesta è maggiore di **_HEAP_MAXREQ**. Per ulteriori informazioni su **errno**, vedere [errno, doserrno, _sys_errlist e _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Inoltre, **_aligned_offset_realloc_dbg** convalida i relativi parametri. Se l' *allineamento* non è una potenza di 2 o se l' *offset* è maggiore o uguale a *size* e diverso da zero, questa funzione richiama il gestore di parametri non validi, come descritto in convalida dei [parametri](../../c-runtime-library/parameter-validation.md). Se l'esecuzione può continuare, questa funzione restituisce **null** e imposta **errno** su **EINVAL**.

Per informazioni sulle modalità di allocazione, inizializzazione e gestione dei blocchi di memoria nella versione di debug dell'heap di base, vedere [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Per informazioni sui tipi di blocchi di allocazione e su come vengono usati, vedere [Tipi di blocchi sull'heap di debug](/visualstudio/debugger/crt-debug-heap-details). Per informazioni sulle differenze tra chiamare una funzione standard dell'heap e la sua versione di debug nella build di debug di un'applicazione, vedere [Versioni di debug di funzioni di allocazione heap](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Requisiti

|Routine|Intestazione obbligatoria|
|-------------|---------------------|
|**_aligned_offset_realloc_dbg**|\<crtdbg.h>|

Per altre informazioni sulla compatibilità, vedere [Compatibilità](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Librerie

Solo le versioni di debug delle [librerie di runtime di C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vedere anche

[Routine di debug](../../c-runtime-library/debug-routines.md)<br/>
