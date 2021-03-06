---
title: emitidl (attributo COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.emitidl
helpviewer_keywords:
- emitidl attribute
ms.assetid: 85b80c56-578e-4392-ac03-8443c74ebb7d
ms.openlocfilehash: 6c4055e0f14bced1e5047fc502a4bf274126f804
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409655"
---
# <a name="emitidl"></a>emitidl

Specifica se tutti gli attributi IDL successivi vengono elaborati e inseriti nel file con estensione IDL generato.

## <a name="syntax"></a>Sintassi

```cpp
[ emitidl(state, defaultimports=boolean) ];
```

### <a name="parameters"></a>Parametri

*state*<br/>
Uno di questi valori possibili: `true`, `false`, `forced`, `restricted`, `push`, o `pop`.

- Se `true`, eventuali attributi IDL presenti categoria rilevati in un file di codice sorgente vengono inseriti nel file con estensione IDL generato. Questo è l'impostazione predefinita per **emitidl**.

- Se `false`, eventuali attributi IDL presenti categoria rilevati in un file di codice sorgente non vengono inseriti nel file con estensione IDL generato.

- Se `restricted`, supporta gli attributi IDL in file senza un [modulo](module-cpp.md) attributo. Il compilatore non genera un file IDL.

- Se `forced`, esegue l'override di una successiva `restricted` attributo, che richiede un file per avere una `module` attributi se sono presenti IDL attributi nel file.

- `push` Consente di salvare l'oggetto corrente **emitidl** le impostazioni per interna **emitidl** stack, e `pop` consente di impostare **emitidl** per qualsiasi valore si trovi all'inizio dell'oggetto interno **emitidl** dello stack.

`defaultimports=`*booleano* \(facoltativo)

- Se *booleana* viene **true**, docobj.idl viene importato in un file con estensione IDL generato. Inoltre, se un file con estensione idl con lo stesso nome di un'estensione h file che si `#include` in origine il codice si trova nella stessa directory del file con estensione h, quindi il file con estensione IDL generato contiene un'istruzione di importazione per il file con estensione idl.

- Se *booleana* viene **false**, docobj.idl non viene importato in file IDL generato. È necessario importare in modo esplicito con i file con estensione idl [importare](import.md).

## <a name="remarks"></a>Note

Dopo il **emitidl** attributo C++ viene rilevato in un file di codice sorgente, attributi IDL categoria vengono inseriti nel file con estensione IDL generato. Se è presente alcun **emitidl** attributi, attributi IDL presenti nel file del codice sorgente vengono restituiti come output nel file con estensione IDL generato.

È possibile avere più **emitidl** attributi in un file di codice sorgente. Se `[emitidl(false)];` viene rilevato in un file senza una successiva `[emitidl(true)];`, quindi non sono presenti attributi vengono elaborati nel file IDL generato.

Ogni volta che il compilatore rileva un nuovo file **emitidl** in modo implicito è impostata su **true**.

## <a name="requirements"></a>Requisiti

### <a name="attribute-context"></a>Contesto attributo

|||
|-|-|
|**Si applica a**|Ovunque|
|**Ripetibile**|No|
|**Attributi obbligatori**|Nessuna|
|**Attributi non validi**|nessuno|

Per altre informazioni, vedere [Contesti di attributi](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vedere anche

[Attributi del compilatore](compiler-attributes.md)<br/>
[Attributi autonomi](stand-alone-attributes.md)
