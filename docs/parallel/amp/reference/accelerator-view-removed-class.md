---
title: Classe accelerator_view_removed
ms.date: 03/27/2019
f1_keywords:
- accelerator_view_removed
- AMPRT/accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed::accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed::get_view_removed_reason
helpviewer_keywords:
- AMPRT/Concurrency::accelerator_view_removed::accelerator_view_removed Class
ms.assetid: 262446de-311c-454e-a5ed-e2aaced0d88a
ms.openlocfilehash: 9a3f6f349fc3103893639fe209dcf23a07ffec56
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127124"
---
# <a name="accelerator_view_removed-class"></a>Classe accelerator_view_removed

Eccezione generata quando una chiamata a DirectX sottostante ha esito negativo a causa del meccanismo di rilevamento e ripristino del timeout di Windows.

## <a name="syntax"></a>Sintassi

```cpp
class accelerator_view_removed : public runtime_exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Costruttori pubblici

|Nome|Descrizione|
|----------|-----------------|
|[Costruttore accelerator_view_removed](#ctor)|Inizializza una nuova istanza della classe `accelerator_view_removed`.|

### <a name="public-methods"></a>Metodi pubblici

|Nome|Descrizione|
|----------|-----------------|
|[get_view_removed_reason](#get_view_removed_reason)|Restituisce un codice di errore HRESULT che indica la causare la rimozione dell'oggetto `accelerator_view`.|

## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà

`exception`

`runtime_exception`

`out_of_memory`

## <a name="requirements"></a>Requisiti

**Intestazione:** amprt. h

**Spazio dei nomi:** Concurrency

## <a name="ctor"></a>accelerator_view_removed

Inizializza una nuova istanza della classe [accelerator_view_removed](accelerator-view-removed-class.md) .

### <a name="syntax"></a>Sintassi

```cpp
explicit accelerator_view_removed(
    const char * message,
    HRESULT view_removed_reason ) throw();

explicit accelerator_view_removed(
    HRESULT view_removed_reason ) throw();
```

### <a name="parameters"></a>Parametri

*message*<br/>
Descrizione dell'errore.

*view_removed_reason*<br/>
Codice di errore HRESULT che indica la rimozione dell'oggetto `accelerator_view`.

### <a name="return-value"></a>Valore restituito

Nuova istanza della classe `accelerator_view_removed`.

## <a name="get_view_removed_reason"></a>get_view_removed_reason

Restituisce un codice di errore HRESULT che indica la causare la rimozione dell'oggetto `accelerator_view`.

### <a name="syntax"></a>Sintassi

```cpp
HRESULT get_view_removed_reason() const throw();
```

## <a name="see-also"></a>Vedere anche

[Spazio dei nomi Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
