---
title: Macro di scambio di dati del Registro di sistema
ms.date: 11/04/2016
f1_keywords:
- atlplus/ATL::BEGIN_RDX_MAP
- atlplus/ATL::END_RDX_MAP
- atlplus/ATL::RDX_BINARY
- atlplus/ATL::RDX_CSTRING_TEXT
- atlplus/ATL::RDX_DWORD
- atlplus/ATL::RDX_TEXT
helpviewer_keywords:
- RegistryDataExchange function, macros
ms.assetid: c1bc5e79-2307-43d2-9d10-3a62ffadf473
ms.openlocfilehash: a7d580e4907cec40f97c0cead616665fff7b8a01
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326065"
---
# <a name="registry-data-exchange-macros"></a>Macro di scambio di dati del Registro di sistema

Queste macro eseguono operazioni di scambio di dati del Registro di sistema.

|||
|-|-|
|[BEGIN_RDX_MAP](#begin_rdx_map)|Contrassegna l'inizio della mappa di scambio dei dati del Registro di sistema.|
|[END_RDX_MAP](#end_rdx_map)|Contrassegna la fine della mappa di scambio dei dati del Registro di sistema.|
|[RDX_BINARY](#rdx_binary)|Associa la voce del Registro di sistema specificata a una variabile membro specificata di tipo BYTE.|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Associa la voce del Registro di sistema specificata a una variabile membro specificata di tipo CString.|
|[RDX_DWORD](#rdx_dword)|Associa la voce del Registro di sistema specificata a una variabile membro specificata di tipo DWORD.|
|[RDX_TEXT](#rdx_text)|Associa la voce del Registro di sistema specificata a una variabile membro specificata di tipo TCHAR.|

## <a name="requirements"></a>Requisiti

**Intestazione:** atlplus.h

## <a name="begin_rdx_map"></a><a name="begin_rdx_map"></a>BEGIN_RDX_MAP

Contrassegna l'inizio della mappa di scambio dei dati del Registro di sistema.

```
BEGIN_RDX_MAP
```

### <a name="remarks"></a>Osservazioni

Le seguenti macro vengono utilizzate all'interno della mappa di Scambio dati del Registro di sistema per leggere e scrivere voci nel Registro di sistema:

|Macro|Descrizione|
|-----------|-----------------|
|[RDX_BINARY](#rdx_binary)|Associa la voce del Registro di sistema specificata a una variabile membro specificata di tipo BYTE.|
|[RDX_DWORD](#rdx_dword)|Associa la voce del Registro di sistema specificata a una variabile membro specificata di tipo DWORD.|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Associa la voce del Registro di sistema specificata a una variabile membro specificata di tipo CString.|
|[RDX_TEXT](#rdx_text)|Associa la voce del Registro di sistema specificata a una variabile membro specificata di tipo TCHAR.|

La funzione globale [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)o la funzione membro con lo stesso nome creata dalle BEGIN_RDX_MAP e END_RDX_MAP macro, deve essere utilizzata ogni volta che il codice deve scambiare dati tra il Registro di sistema e le variabili specificate nella mappa RDX.

## <a name="end_rdx_map"></a><a name="end_rdx_map"></a>END_RDX_MAP

Contrassegna la fine della mappa di scambio dei dati del Registro di sistema.

```
END_RDX_MAP
```

## <a name="rdx_binary"></a><a name="rdx_binary"></a>RDX_BINARY

Associa la voce del Registro di sistema specificata a una variabile membro specificata di tipo BYTE.

```
RDX_BINARY(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parametri

*rootkey (chiave radice)*<br/>
Radice della chiave del Registro di sistema.

*Sottochiave*<br/>
Sottochiave del Registro di sistema.

*Valuename*<br/>
Chiave del Registro di sistema.

*Membro*<br/>
Variabile membro da associare alla voce del Registro di sistema specificata.

*member_size*<br/>
Dimensione, in byte, della variabile membro.

### <a name="remarks"></a>Osservazioni

Questa macro viene utilizzata insieme alle macro BEGIN_RDX_MAP e END_RDX_MAP per associare una variabile membro a una determinata voce del Registro di sistema. La funzione globale [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)o la funzione membro con lo stesso nome creata dalle macro BEGIN_RDX_MAP e END_RDX_MAP, deve essere utilizzata per eseguire lo scambio di dati tra il Registro di sistema e le variabili membro nella mappa RDX.

## <a name="rdx_cstring_text"></a><a name="rdx_cstring_text"></a>RDX_CSTRING_TEXT

Associa la voce del Registro di sistema specificata a una variabile membro specificata di tipo CString.

```
RDX_CSTRING_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parametri

*rootkey (chiave radice)*<br/>
Radice della chiave del Registro di sistema.

*Sottochiave*<br/>
Sottochiave del Registro di sistema.

*Valuename*<br/>
Chiave del Registro di sistema.

*Membro*<br/>
Variabile membro da associare alla voce del Registro di sistema specificata.

*member_size*<br/>
Dimensione, in byte, della variabile membro.

### <a name="remarks"></a>Osservazioni

Questa macro viene utilizzata insieme alle macro BEGIN_RDX_MAP e END_RDX_MAP per associare una variabile membro a una determinata voce del Registro di sistema. La funzione globale [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)o la funzione membro con lo stesso nome creata dalle macro BEGIN_RDX_MAP e END_RDX_MAP, deve essere utilizzata per eseguire lo scambio di dati tra il Registro di sistema e le variabili membro nella mappa RDX.

## <a name="rdx_dword"></a><a name="rdx_dword"></a>RDX_DWORD

Associa la voce del Registro di sistema specificata a una variabile membro specificata di tipo DWORD.

```
RDX_DWORD(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parametri

*rootkey (chiave radice)*<br/>
Radice della chiave del Registro di sistema.

*Sottochiave*<br/>
Sottochiave del Registro di sistema.

*Valuename*<br/>
Chiave del Registro di sistema.

*Membro*<br/>
Variabile membro da associare alla voce del Registro di sistema specificata.

*member_size*<br/>
Dimensione, in byte, della variabile membro.

### <a name="remarks"></a>Osservazioni

Questa macro viene utilizzata insieme alle macro BEGIN_RDX_MAP e END_RDX_MAP per associare una variabile membro a una determinata voce del Registro di sistema. La funzione globale [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)o la funzione membro con lo stesso nome creata dalle macro BEGIN_RDX_MAP e END_RDX_MAP, deve essere utilizzata per eseguire lo scambio di dati tra il Registro di sistema e le variabili membro nella mappa RDX.

## <a name="rdx_text"></a><a name="rdx_text"></a>RDX_TEXT

Associa la voce del Registro di sistema specificata a una variabile membro specificata di tipo TCHAR.

```
RDX_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parametri

*rootkey (chiave radice)*<br/>
Radice della chiave del Registro di sistema.

*Sottochiave*<br/>
Sottochiave del Registro di sistema.

*Valuename*<br/>
Chiave del Registro di sistema.

*Membro*<br/>
Variabile membro da associare alla voce del Registro di sistema specificata.

*member_size*<br/>
Dimensione, in byte, della variabile membro.

### <a name="remarks"></a>Osservazioni

Questa macro viene utilizzata insieme alle macro BEGIN_RDX_MAP e END_RDX_MAP per associare una variabile membro a una determinata voce del Registro di sistema. La funzione globale [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)o la funzione membro con lo stesso nome creata dalle macro BEGIN_RDX_MAP e END_RDX_MAP, deve essere utilizzata per eseguire lo scambio di dati tra il Registro di sistema e le variabili membro nella mappa RDX.

## <a name="see-also"></a>Vedere anche

[Macro](../../atl/reference/atl-macros.md)<br/>
[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)
