---
title: Classe CAtlWinModule
ms.date: 11/04/2016
f1_keywords:
- CAtlWinModule
- ATLBASE/ATL::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::AddCreateWndData
- ATLBASE/ATL::CAtlWinModule::ExtractCreateWndData
helpviewer_keywords:
- CAtlWinModule class
ms.assetid: 7ec844af-0f68-4a34-b0c8-9de50a025df0
ms.openlocfilehash: 5cdf13ebbb982ad8184a52dcf1a3e30d71e4e5b0
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167708"
---
# <a name="catlwinmodule-class"></a>Classe CAtlWinModule

Questa classe fornisce supporto per i componenti di Windows ATL.

> [!IMPORTANT]
> Questa classe e i relativi membri non possono essere utilizzati nelle applicazioni eseguite nel Windows Runtime.

## <a name="syntax"></a>Sintassi

```cpp
class CAtlWinModule : public _ATL_WIN_MODULE
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Costruttori pubblici

|Nome|Descrizione|
|----------|-----------------|
|[CAtlWinModule:: CAtlWinModule](#catlwinmodule)|Costruttore.|
|[CAtlWinModule:: ~ CAtlWinModule](#dtor)|Distruttore.|

### <a name="public-methods"></a>Metodi pubblici

|Nome|Descrizione|
|----------|-----------------|
|[CAtlWinModule:: AddCreateWndData](#addcreatewnddata)|Aggiunge un oggetto dati.|
|[CAtlWinModule:: ExtractCreateWndData](#extractcreatewnddata)|Restituisce un puntatore all'oggetto dati del modulo della finestra.|

## <a name="remarks"></a>Osservazioni

Questa classe fornisce supporto per tutte le classi ATL che richiedono funzionalità di windowing.

## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)

`CAtlWinModule`

## <a name="requirements"></a>Requisiti

**Intestazione:** atlbase. h

## <a name="catlwinmoduleaddcreatewnddata"></a><a name="addcreatewnddata"></a>CAtlWinModule:: AddCreateWndData

Questo metodo inizializza e aggiunge una `_AtlCreateWndData` struttura.

```cpp
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```

### <a name="parameters"></a>Parametri

*pData*<br/>
Puntatore alla `_AtlCreateWndData` struttura da inizializzare e aggiungere al modulo corrente.

*pObject*<br/>
Puntatore al puntatore **this** di un oggetto.

### <a name="remarks"></a>Osservazioni

Questo metodo chiama [AtlWinModuleAddCreateWndData](winmodule-global-functions.md#atlwinmoduleaddcreatewnddata) che Inizializza una struttura [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) . Questa struttura archivia il puntatore **this** , usato per ottenere l'istanza della classe nelle routine della finestra.

## <a name="catlwinmodulecatlwinmodule"></a><a name="catlwinmodule"></a>CAtlWinModule:: CAtlWinModule

Costruttore.

```cpp
CAtlWinModule();
```

### <a name="remarks"></a>Osservazioni

Se l'inizializzazione non riesce, viene generata un'eccezione **EXCEPTION_NONCONTINUABLE** .

## <a name="catlwinmodulecatlwinmodule"></a><a name="dtor"></a>CAtlWinModule:: ~ CAtlWinModule

Distruttore.

```cpp
~CAtlWinModule();
```

### <a name="remarks"></a>Osservazioni

Libera tutte le risorse allocate.

## <a name="catlwinmoduleextractcreatewnddata"></a><a name="extractcreatewnddata"></a>CAtlWinModule:: ExtractCreateWndData

Questo metodo restituisce un puntatore a una `_AtlCreateWndData` struttura.

```cpp
void* ExtractCreateWndData();
```

### <a name="return-value"></a>Valore restituito

Restituisce un puntatore alla `_AtlCreateWndData` struttura aggiunta in precedenza con [CAtlWinModule:: AddCreateWndData](#addcreatewnddata)o null se non è disponibile alcun oggetto.

## <a name="see-also"></a>Vedere anche

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)<br/>
[Cenni preliminari sulle classi](../../atl/atl-class-overview.md)<br/>
[Classi modulo](../../atl/atl-module-classes.md)
