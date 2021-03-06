---
title: vi_progid (C++ attributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.vi_progid
helpviewer_keywords:
- vi_progid attribute
ms.assetid: a52449be-b93e-4111-b883-44bb8da53261
ms.openlocfilehash: fbf5ab2bc4263356a1cfcf789865a3f7e286ccd7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514863"
---
# <a name="vi_progid"></a>vi_progid

Specifica una forma indipendente dalla versione del ProgID.

## <a name="syntax"></a>Sintassi

```cpp
[ vi_progid(name) ];
```

### <a name="parameters"></a>Parametri

*name*<br/>
ProgID indipendente dalla versione che rappresenta l'oggetto.

I ProgID presentano una versione leggibile dell'identificatore di classe (CLSID) utilizzato per identificare gli oggetti COM/ActiveX.

## <a name="remarks"></a>Note

L'attributo **vi_progid** C++ consente di specificare un ProgID indipendente dalla versione per un oggetto com. Un ProgID ha il formato *name1. name2. Version*. Un ProgID indipendente dalla versione non dispone di una *versione*. È possibile specificare sia `progid` gli attributi che **vi_progid** in un oggetto. `coclass` Se non si specifica **vi_progid**, il ProgID indipendente dalla versione è il valore specificato dall'attributo [ProgID](progid.md) .

**vi_progid** implica l' `coclass` attributo, ovvero se si specifica **vi_progid**, equivale a specificare gli `coclass` attributi e **vi_progid** .

L'attributo **vi_progid** fa sì che una classe venga registrata automaticamente con il nome specificato. Il file IDL generato non visualizzerà il valore ProgID.

Nei progetti ATL, se è presente anche l'attributo [coclass](coclass.md) , il ProgID specificato viene usato dalla `GetVersionIndependentProgID` funzione `coclass` (inserita dall'attributo).

## <a name="example"></a>Esempio

Vedere l'esempio di [coclasse](coclass.md) per un uso di esempio di **vi_progid**.

## <a name="requirements"></a>Requisiti

### <a name="attribute-context"></a>Contesto attributo

|||
|-|-|
|**Si applica a**|**classe**, **struct**|
|**Ripetibile**|No |
|**Attributi obbligatori**|Nessuna|
|**Attributi non validi**|Nessuna|

Per altre informazioni sui contesti di attributi, vedere [Contesti di attributi](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vedere anche

[Attributi IDL](idl-attributes.md)<br/>
[Attributi Typedef, Enum, Union e Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Attributi di classe](class-attributes.md)<br/>
[Chiave ProgID](/windows/win32/com/-progid--key)
