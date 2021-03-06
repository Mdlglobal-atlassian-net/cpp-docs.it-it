---
title: div, ldiv, lldiv
ms.date: 04/05/2018
api_name:
- div
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
- api-ms-win-crt-utility-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- div
helpviewer_keywords:
- div function
- quotients, computing
- quotients
- dividing integers
- remainder computing
ms.assetid: 8ae80d97-54fd-499e-b14c-e30993b58119
ms.openlocfilehash: 5b40fa0c4cc9cdf0c0de0f6af21da04b0c70369f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/12/2019
ms.locfileid: "70937690"
---
# <a name="div-ldiv-lldiv"></a>div, ldiv, lldiv

Calcola il quoziente e il resto di due Integer.

## <a name="syntax"></a>Sintassi

```C
div_t div(
   int numer,
   int denom
);
ldiv_t ldiv(
   long numer,
   long denom
);
lldiv_t lldiv(
   long long numer,
   long long denom
);
```

```cpp
ldiv_t div(
   long numer,
   long denom
); /* C++ only */
lldiv_t div(
   long long numer,
   long long denom
); /* C++ only */
```

### <a name="parameters"></a>Parametri

*numer*<br/>
Numeratore.

*denom*<br/>
Denominatore.

## <a name="return-value"></a>Valore restituito

**div** chiamato usando gli argomenti di tipo **int** restituisce una struttura di tipo **div_t**, che comprende il quoziente e il resto. Il valore restituito con argomenti di tipo **Long** è **ldiv_t**e il valore restituito con argomenti **di tipo Long** **Long** è **lldiv_t**. **div_t**, **ldiv_t**e **lldiv_t** sono definiti in \<stdlib. h >.

## <a name="remarks"></a>Note

La funzione **div** divide i *numeri* per *Denom* e quindi calcola il quoziente e il resto. La struttura [div_t](../../c-runtime-library/standard-types.md) contiene il quoziente, la **quota**e il resto **REM**. Il segno del quoziente è uguale a quello del quoziente matematico. Il valore assoluto del quoziente è l'intero più grande che è minore del valore assoluto del quoziente matematico. Se il denominatore è 0, il programma termina con un messaggio di errore.

Gli overload di **div** che accettano argomenti di tipo **Long** o **Long** **Long** sono disponibili solo per C++ il codice. I tipi restituiti [ldiv_t](../../c-runtime-library/standard-types.md) e [lldiv_t](../../c-runtime-library/standard-types.md) contengono i membri **quot** e **REM**, che hanno gli stessi significati dei membri di **div_t**.

## <a name="requirements"></a>Requisiti

|Routine|Intestazione obbligatoria|
|-------------|---------------------|
|**div**, **ldiv**, **lldiv**|\<stdlib.h>|

Per altre informazioni sulla compatibilità, vedere [Compatibilità](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Esempio

```C
// crt_div.c
// arguments: 876 13

// This example takes two integers as command-line
// arguments and displays the results of the integer
// division. This program accepts two arguments on the
// command line following the program name, then calls
// div to divide the first argument by the second.
// Finally, it prints the structure members quot and rem.
//

#include <stdlib.h>
#include <stdio.h>
#include <math.h>

int main( int argc, char *argv[] )
{
   int x,y;
   div_t div_result;

   x = atoi( argv[1] );
   y = atoi( argv[2] );

   printf( "x is %d, y is %d\n", x, y );
   div_result = div( x, y );
   printf( "The quotient is %d, and the remainder is %d\n",
           div_result.quot, div_result.rem );
}
```

```Output
x is 876, y is 13
The quotient is 67, and the remainder is 5
```

## <a name="see-also"></a>Vedere anche

[Supporto delle funzioni a virgola mobile](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
