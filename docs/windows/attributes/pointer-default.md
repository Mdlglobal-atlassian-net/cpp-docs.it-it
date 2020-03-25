---
title: pointer_default (C++ attributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.pointer_default
helpviewer_keywords:
- pointer_default attribute
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
ms.openlocfilehash: d0c5832623c1e418f4c6e8bdb606d1d363503483
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166536"
---
# <a name="pointer_default"></a>pointer_default

Specifica l'attributo del puntatore predefinito per tutti i puntatori, ad eccezione dei puntatori di primo livello visualizzati negli elenchi di parametri.

## <a name="syntax"></a>Sintassi

```cpp
[ pointer_default(value) ]
```

### <a name="parameters"></a>Parametri

*value*<br/>
Valore che descrive il tipo di puntatore: **ptr**, **ref**o **Unique**.

## <a name="remarks"></a>Osservazioni

L'attributo **pointer_default** C++ ha la stessa funzionalità dell'attributo [pointer_default](/windows/win32/Midl/pointer-default) MIDL.

## <a name="example"></a>Esempio

Vedere l'esempio per [DefaultValue](defaultvalue.md) per un esempio di utilizzo di **pointer_default**.

## <a name="requirements"></a>Requisiti

### <a name="attribute-context"></a>Contesto attributo

|||
|-|-|
|**Si applica a**|**interface**|
|**Ripetibile**|No|
|**Attributi obbligatori**|nessuno|
|**Attributi non validi**|nessuno|

Per altre informazioni sui contesti di attributi, vedere [Contesti di attributi](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vedere anche

[Attributi IDL](idl-attributes.md)<br/>
[Attributi di interfaccia](interface-attributes.md)
