---
title: _bittest, _bittest64
ms.date: 11/04/2016
f1_keywords:
- _bittest64
- _bittest_cpp
- _bittest64_cpp
- _bittest
helpviewer_keywords:
- _bittest intrinsic
- _bittest64 intrinsic
- bt instruction
ms.assetid: 15e62afb-abea-4ee7-a6b1-13efa2034937
ms.openlocfilehash: 1d29b8bec646bb2da8acfe20479fe0e238db0de5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349173"
---
# <a name="bittest-bittest64"></a>_bittest, _bittest64

**Sezione specifica Microsoft**

Genera l'istruzione `bt`, che esamina il bit in posizione `b` dell'indirizzo `a` e restituisce il valore di tale bit.

## <a name="syntax"></a>Sintassi

```
unsigned char _bittest(
   long const *a,
   long b
);
unsigned char _bittest64(
   __int64 const *a,
   __int64 b
);
```

### <a name="parameters"></a>Parametri

*a*<br/>
[in] Puntatore alla memoria da esaminare.

*b*<br/>
[in] Posizione del bit da testare.

### <a name="return-value"></a>Valore restituito

Bit nella posizione specificata.

## <a name="requirements"></a>Requisiti

|Funzione intrinseca|Architettura|Intestazione|
|---------------|------------------|------------|
|`_bittest`|x86, ARM, x64|\<intrin.h>|
|`_bittest64`|ARM, x64|\<intrin.h>|

## <a name="remarks"></a>Note

Questa routine è disponibile solo come funzione intrinseca.

## <a name="example"></a>Esempio

```cpp
// bittest.cpp
// processor: x86, ARM, x64

#include <stdio.h>
#include <intrin.h>

long num = 78002;

int main()
{
    unsigned char bits[32];
    long nBit;

    printf_s("Number: %d\n", num);

    for (nBit = 0; nBit < 31; nBit++)
    {
        bits[nBit] = _bittest(&num, nBit);
    }

    printf_s("Binary representation:\n");
    while (nBit--)
    {
        if (bits[nBit])
            printf_s("1");
        else
            printf_s("0");
    }
}
```

```Output
Number: 78002
Binary representation:
0000000000000010011000010110010
```

**Fine sezione specifica Microsoft**

## <a name="see-also"></a>Vedere anche

[Intrinseci del compilatore](../intrinsics/compiler-intrinsics.md)