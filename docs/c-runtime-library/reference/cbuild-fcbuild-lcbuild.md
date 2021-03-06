---
title: _Cbuild, _FCbuild, _LCbuild
ms.date: 03/30/2018
api_name:
- _Cbuild
- _FCbuild
- _LCbuild
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _Cbuild
- _FCbuild
- _LCbuild
- complex/_Cbuild
- complex/_FCbuild
- complex/_LCbuild
helpviewer_keywords:
- _Cbuild function
- _FCbuild function
- _LCbuild function
ms.openlocfilehash: b0ae50f40f0ca0a926e1eef586c6610a04b6ea7a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943220"
---
# <a name="_cbuild-_fcbuild-_lcbuild"></a>_Cbuild, _FCbuild, _LCbuild

Costruisce un numero complesso da parti reali e immaginarie.

## <a name="syntax"></a>Sintassi

```C
_Dcomplex _Cbuild( double real, double imaginary );
_Fcomplex _FCbuild( float real, float imaginary );
_Lcomplex _LCbuild( long double real, long double imaginary );
```

### <a name="parameters"></a>Parametri

*real*<br/>
Parte reale del numero complesso da costruire.

*imaginary*<br/>
Parte immaginaria del numero complesso da costruire.

## <a name="return-value"></a>Valore restituito

Struttura **_Dcomplex**, **_Fcomplex**o **_Lcomplex** che rappresenta il numero complesso \* (*reale*, *immaginario* i) per i valori del tipo a virgola mobile specificato.

## <a name="remarks"></a>Note

Le funzioni **_Cbuild**, **_FCbuild**e **_LCbuild** semplificano la creazione di tipi complessi. Usare le funzioni [CREAL, crealf, Creall](creal-crealf-creall.md) e [Cimag, cimagf, cimagl](cimag-cimagf-cimagl.md) per recuperare le parti reali e immaginarie dei numeri complessi rappresentati.

## <a name="requirements"></a>Requisiti

|Routine|Intestazione C|Intestazione C++|
|-------------|--------------|------------------|
|**_Cbuild**, **_FCbuild**, **_LCbuild**|\<complex.h>|\<ccomplex>|

Queste funzioni sono specifiche di Microsoft. I tipi **_Dcomplex**, **_Fcomplex**e **_Lcomplex** sono equivalenti specifici di Microsoft ai tipi nativi C99 non implementati **Double _Complex**, **float _Complex**e **long double _Complex**, rispettivamente. Per altre informazioni sulla compatibilità, vedere [Compatibilità](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vedere anche

[Riferimento alfabetico alle funzioni](crt-alphabetical-function-reference.md)<br/>
[_Cmulcc, _FCmulcc, _LCmulcc](cmulcc-fcmulcc-lcmulcc.md)<br/>
[_Cmulcr, _FCmulcr, _LCmulcr](cmulcr-fcmulcr-lcmulcr.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
