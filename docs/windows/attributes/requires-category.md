---
title: requires_category (attributo COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.requires_category
helpviewer_keywords:
- requires_category attribute
ms.assetid: a645fdc6-1ef5-414d-8c56-5fe2686d4687
ms.openlocfilehash: e6621e2cec92eadb0ca4b4ac989b4ca7d578b2ef
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429844"
---
# <a name="requirescategory"></a>requires_category

Specifica le categorie di componenti necessari della classe di destinazione.

## <a name="syntax"></a>Sintassi

```cpp
[ requires_category(
  requires_category) ]
```

### <a name="parameters"></a>Parametri

*requires_category*<br/>
L'ID della categoria obbligatoria.

## <a name="remarks"></a>Note

Il **requires_category** attributo C++ specifica le categorie di componenti necessari per la classe di destinazione. Per altre informazioni, vedere [REQUIRED_CATEGORY](../../atl/reference/category-macros.md#required_category).

Questo attributo richiede che anche l'attributo [coclass](coclass.md), [progid](progid.md)o [vi_progid](vi-progid.md) (o un altro attributo che implica uno di questi) sia applicato allo stesso elemento.

## <a name="example"></a>Esempio

Il codice seguente richiede che l'oggetto implementa la categoria di controllo.

```cpp
// cpp_attr_ref_requires_category.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="MyLibrary")];

[ coclass, requires_category("CATID_Control"),
  uuid("1e1a2436-f3ea-4ff3-80bf-5409370e8144")]
class CMyClass {};
```

## <a name="requirements"></a>Requisiti

### <a name="attribute-context"></a>Contesto attributo

|||
|-|-|
|**Si applica a**|**classe**, **struct**|
|**Ripetibile**|No|
|**Attributi obbligatori**|Uno o più delle operazioni seguenti: `coclass`, `progid`, o `vi_progid`.|
|**Attributi non validi**|nessuno|

Per altre informazioni sui contesti di attributi, vedere [Contesti di attributi](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vedere anche

[Attributi COM](com-attributes.md)<br/>
[implements_category](implements-category.md)