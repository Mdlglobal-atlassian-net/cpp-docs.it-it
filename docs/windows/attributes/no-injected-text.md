---
title: no_injected_text (C++ attributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.no_injected_text
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
ms.openlocfilehash: 5f98be3478b2e1eeb4b464f1784f3f4ece22d8a4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166614"
---
# <a name="no_injected_text"></a>no_injected_text

Impedisce al compilatore di inserire codice come risultato dell'utilizzo dell'attributo.

## <a name="syntax"></a>Sintassi

```cpp
[ no_injected_text(boolean) ];
```

### <a name="parameters"></a>Parametri

*boolean*<br/>
Opzionale **true** se non si desidera inserire codice, **false** per consentire l'inserimento del codice. il valore predefinito è **true** .

## <a name="remarks"></a>Osservazioni

L'uso più comune dell'attributo **no_injected_text** C++ è l'opzione del compilatore [/FX](../../build/reference/fx-merge-injected-code.md) , che inserisce l'attributo **no_injected_text** nel file. mrg.

## <a name="requirements"></a>Requisiti

### <a name="attribute-context"></a>Contesto attributo

|||
|-|-|
|**Si applica a**|Ovunque|
|**Ripetibile**|No|
|**Attributi obbligatori**|nessuno|
|**Attributi non validi**|nessuno|

Per altre informazioni sui contesti di attributi, vedere [Contesti di attributi](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vedere anche

[Attributi del compilatore](compiler-attributes.md)
