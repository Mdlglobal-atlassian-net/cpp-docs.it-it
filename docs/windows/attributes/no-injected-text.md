---
title: no_injected_text (attributo COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.no_injected_text
dev_langs:
- C++
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a9289c1b8f28b90dd5a3a4a437d3e2a5870e8468
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2018
ms.locfileid: "48791797"
---
# <a name="noinjectedtext"></a>no_injected_text

Impedisce al compilatore di inserire codice in seguito a uso dell'attributo.

## <a name="syntax"></a>Sintassi

```cpp
[ no_injected_text(boolean) ];
```

### <a name="parameters"></a>Parametri

*Valore booleano*<br/>
(Facoltativo) **true** se si desidera che nessun codice inserito, **false** per consentire al codice da inserire. **true** è il valore predefinito.

## <a name="remarks"></a>Note

L'uso più comune del **no_injected_text** consiste nell'attributo C++ il [/Fx](../../build/reference/fx-merge-injected-code.md) opzione del compilatore, che consente di inserire il **no_injected_text** attributo nel file mrg.

## <a name="requirements"></a>Requisiti

### <a name="attribute-context"></a>Contesto attributo

|||
|-|-|
|**Si applica a**|Ovunque|
|**Ripetibile**|No|
|**Attributi obbligatori**|Nessuna|
|**Attributi non validi**|nessuno|

Per altre informazioni sui contesti di attributi, vedere [contesti di attributi](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vedere anche

[Attributi del compilatore](compiler-attributes.md)  