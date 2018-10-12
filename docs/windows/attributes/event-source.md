---
title: event_source (attributo COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.event_source
dev_langs:
- C++
helpviewer_keywords:
- event handling, attributes
- event logs, event source
- event sources, creating
- event_source attribute
- event sources
- event handling, creating event source
ms.assetid: 0983e36a-6127-4fbb-8a22-8dfec6564c16
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 750e51264f12d1c8961ced4e8b606ea5d040d8c9
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2018
ms.locfileid: "48791300"
---
# <a name="eventsource"></a>event_source

Crea un'origine evento.

## <a name="syntax"></a>Sintassi

```cpp
[ event_source(type, optimize=[speed | size], decorate=[true | false]) ]
```

### <a name="parameters"></a>Parametri

*type*<br/>
Un'enumerazione di uno dei valori seguenti:

- `native` per codice C/C++ non gestito (impostazione predefinita per le classi non gestite).

- `com` per il codice COM. È necessario usare `coclass` quando `type`=`com`. Questo valore richiedere che si includano i file di intestazione seguente:

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*optimize*<br/>
Quando *tipo* viene `native`, è possibile specificare `optimize=size`, per indicare che ci sono 4 byte di spazio di archiviazione (minimo) per tutti gli eventi in una classe o `optimize=speed` (predefinito) per indicare che ci sono 4 * (numero di eventi) byte di spazio di archiviazione.

*decorare*<br/>
Quando *tipo* viene `native`, è possibile specificare `decorate=false`, per indicare che il nome espanso nel file unito (. mrg) non deve includere il nome della classe contenitore. [/FX](../../build/reference/fx-merge-injected-code.md) consente di generare file mrg. `decorate=false`, che è l'impostazione predefinita, si risolve in nomi di tipo completi nel file unito.

## <a name="remarks"></a>Note

L'attributo **event_source** di C++ specifica che la classe o struttura a cui viene applicato sarà un'origine evento.

**event_source** viene usato in combinazione con il [event_receiver](event-receiver.md) attributo e il [event](../../cpp/event.md) (parola chiave). Usare `event_receiver` per creare i ricevitori di eventi. Uso **event** sui metodi all'interno dell'origine evento per specificare tali metodi come eventi.

> [!NOTE]
> Una classe o una struttura basata su template non può contenere eventi.

## <a name="requirements"></a>Requisiti

### <a name="attribute-context"></a>Contesto attributo

|||
|-|-|
|**Si applica a**|**classe**, **struct**|
|**Ripetibile**|No|
|**Attributi obbligatori**|**Coclasse** quando `type`=`com`|
|**Attributi non validi**|nessuno|

Per altre informazioni, vedere [contesti di attributi](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vedere anche

[Attributi del compilatore](compiler-attributes.md)<br/>
[event_receiver](event-receiver.md)<br/>
[__event](../../cpp/event.md)<br/>
[__hook](../../cpp/hook.md)<br/>
[__unhook](../../cpp/unhook.md)<br/>
[Attributi di classe](class-attributes.md)  