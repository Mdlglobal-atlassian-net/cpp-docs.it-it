---
title: remainder, remainderf, remainderl
ms.date: 4/2/2020
api_name:
- remainderl
- remainder
- remainderf
- _o_remainder
- _o_remainderf
- _o_remainderl
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- remainderf
- remainder
- remainderl
helpviewer_keywords:
- remainderf
- remainderl
- remainder
ms.assetid: 5f721fb3-8b78-4597-9bc0-ca9bcd1f1d0e
ms.openlocfilehash: 6b2a1a94fa39f9e9474f7bc3da3150bf4134d35f
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917855"
---
# <a name="remainder-remainderf-remainderl"></a>remainder, remainderf, remainderl

Calcola il resto del quoziente di due valori a virgola mobile, arrotondati al valore integrale più vicino.

## <a name="syntax"></a>Sintassi

```C
double remainder( double x, double y );
float remainderf( float x, float y );
long double remainderl( long double x, long double y );
```

```cpp
float remainder( float x, float y ); /* C++ only */
long double remainder( long double x, long double y ); /* C++ only */
```

### <a name="parameters"></a>Parametri

*x*<br/>
Numeratore.

*y*<br/>
Denominatore.

## <a name="return-value"></a>Valore restituito

Resto a virgola mobile di *x* / *y*. Se il valore di *y* è 0,0, **resto** restituisce un valore NaN non interattiva. Per informazioni sulla rappresentazione di un valore NaN non interattivo da parte della famiglia **printf** , vedere [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Osservazioni

Le funzioni **resto** calcolano il resto a virgola mobile *r* di *x* / *y* in modo che *x* = *n* \* *y* + *r*, dove *n*è il numero intero più vicino al valore *x* / *y* e *n*è anche ogni volta che &#124; *n* - *x* / *y* &#124; = 1/2. Quando *r* = 0, *r* ha lo stesso segno di *x*.

Poiché C++ consente l'overload, è possibile chiamare gli overload di **resto** che accettano e restituiscono valori **float** o **Long** **Double** . In un programma C il **resto** accetta sempre due argomenti **doppi** e restituisce un **valore Double**.

Per impostazione predefinita, lo stato globale di questa funzione ha come ambito l'applicazione. Per modificare questa situazione, vedere [stato globale in CRT](../global-state.md).

## <a name="requirements"></a>Requisiti

|Function|Intestazione obbligatoria (C)|Intestazione obbligatoria (C++)|
|--------------|---------------------|-|
|**resto**, **remainderf**, **restol**|\<math.h>|\<cmath> o \<math.h>|

Per informazioni sulla compatibilità, vedere [Compatibilità](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Esempio

```C
// crt_remainder.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;

   z = remainder(w, x);
   printf("The remainder of %.2f / %.2f is %f\n", w, x, z);
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
```

## <a name="see-also"></a>Vedere anche

[Supporto a virgola mobile](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[remquo, remquof, remquol](remquo-remquof-remquol.md)<br/>
