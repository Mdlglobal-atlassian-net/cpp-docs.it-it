---
title: Funzioni intrinseche _InterlockedCompareExchange128
ms.date: 09/02/2019
f1_keywords:
- _InterlockedCompareExchange128_cpp
- _InterlockedCompareExchange128
- _InterlockedCompareExchange128_acq
- _InterlockedCompareExchange128_nf
- _InterlockedCompareExchange128_np
- _InterlockedCompareExchange128_rel
helpviewer_keywords:
- cmpxchg16b instruction
- _InterlockedCompareExchange128 intrinsic
ms.assetid: f05918fc-716a-4f6d-b746-1456d6b96c56
ms.openlocfilehash: 6f6b36b238945f7d46e9817cdc85977d666e1e9b
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077622"
---
# <a name="_interlockedcompareexchange128-intrinsic-functions"></a>Funzioni intrinseche _InterlockedCompareExchange128

**Sezione specifica Microsoft**

Esegue un confronto e uno scambio Interlocked a 128 bit.

## <a name="syntax"></a>Sintassi

```C
unsigned char _InterlockedCompareExchange128(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_acq(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_nf(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_np(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_rel(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
```

### <a name="parameters"></a>Parametri

\ di *destinazione*
[in, out] Puntatore alla destinazione, ovvero una matrice di interi a 2 64 bit considerata come un campo a 128 bit. Per evitare un errore di protezione generale, i dati di destinazione devono essere allineati a 16 byte.

\ *ExchangeHigh*
in Intero a 64 bit che può essere scambiato con la parte superiore della destinazione.

\ *ExchangeLow*
in Intero a 64 bit che può essere scambiato con la parte bassa della destinazione.

\ *ComparandResult*
[in, out] Puntatore a una matrice di interi a 2 64 bit (considerato come campo a 128 bit) da confrontare con la destinazione.  Nell'output questa matrice viene sovrascritta con il valore originale della destinazione.

## <a name="return-value"></a>Valore restituito

1 se il comparand a 128 bit corrisponde al valore originale della destinazione. `ExchangeHigh` e `ExchangeLow` sovrascrivono la destinazione a 128 bit.

0 se comparand non è uguale al valore originale della destinazione. Il valore della destinazione è invariato e il valore di comparand viene sovrascritto con il valore della destinazione.

## <a name="requirements"></a>Requisiti

|Intrinsic|Architecture|
|---------------|------------------|
|`_InterlockedCompareExchange128`|x64, ARM64|
|`_InterlockedCompareExchange128_acq`, `_InterlockedCompareExchange128_nf`, `_InterlockedCompareExchange128_rel`|ARM64|
|`_InterlockedCompareExchange128_np`|x64|

**File di intestazione** \<intrin. h >

## <a name="remarks"></a>Osservazioni

Il `_InterlockedCompareExchange128` intrinseco genera l'istruzione `cmpxchg16b` (con il prefisso `lock`) per eseguire un confronto e uno scambio bloccati a 128 bit. Le prime versioni dell'hardware AMD a 64 bit non supportano questa istruzione. Per verificare il supporto hardware per l'istruzione `cmpxchg16b`, chiamare il `__cpuid` intrinseco con `InfoType=0x00000001 (standard function 1)`. Il bit 13 di `CPUInfo[2]` (ECX) è 1 se l'istruzione è supportata.

> [!NOTE]
> Il valore di `ComparandResult` viene sempre sovrascritto. Dopo l'istruzione `lock`, questa funzione intrinseca copia immediatamente il valore iniziale di `Destination` in `ComparandResult`. Per questo motivo, `ComparandResult` e `Destination` devono puntare a posizioni di memoria separate per evitare comportamenti imprevisti.

Sebbene sia possibile utilizzare `_InterlockedCompareExchange128` per la sincronizzazione dei thread di basso livello, non è necessario eseguire la sincronizzazione su 128 bit se è invece possibile utilizzare funzioni di sincronizzazione più piccole, ad esempio gli altri `_InterlockedCompareExchange` intrinseci. Utilizzare `_InterlockedCompareExchange128` se si desidera l'accesso atomico a un valore a 128 bit in memoria.

Se si esegue codice che usa la funzione intrinseca su hardware che non supporta l'istruzione `cmpxchg16b`, i risultati sono imprevedibili.

Sulle piattaforme ARM usare le funzioni intrinseche con i suffissi `_acq` e `_rel` per la semantica di acquisizione e di rilascio, ad esempio all'inizio e alla fine di una sezione critica. Le funzioni intrinseche ARM con un suffisso `_nf` ("No Fence") non fungono da barriera di memoria.

Le funzioni intrinseche con suffisso `_np` ("nessuna prelettura") impediscono l'inserimento di una possibile operazione di prelettura da parte del compilatore.

Questa routine è disponibile solo come funzione intrinseca.

## <a name="example"></a>Esempio

Questo esempio USA `_InterlockedCompareExchange128` per sostituire la parola alta di una matrice di interi a 2 64 bit con la somma delle parole alta e bassa e per incrementare la parola bassa. L'accesso alla matrice `BigInt.Int` è atomico, ma in questo esempio viene utilizzato un singolo thread e il blocco viene ignorato per semplicità.

```cpp
// cmpxchg16b.c
// processor: x64
// compile with: /EHsc /O2
#include <stdio.h>
#include <intrin.h>

typedef struct _LARGE_INTEGER_128 {
    __int64 Int[2];
} LARGE_INTEGER_128, *PLARGE_INTEGER_128;

volatile LARGE_INTEGER_128 BigInt;

// This AtomicOp() function atomically performs:
//   BigInt.Int[1] += BigInt.Int[0]
//   BigInt.Int[0] += 1
void AtomicOp ()
{
    LARGE_INTEGER_128 Comparand;
    Comparand.Int[0] = BigInt.Int[0];
    Comparand.Int[1] = BigInt.Int[1];
    do {
        ; // nothing
    } while (_InterlockedCompareExchange128(BigInt.Int,
                                            Comparand.Int[0] + Comparand.Int[1],
                                            Comparand.Int[0] + 1,
                                            Comparand.Int) == 0);
}

// In a real application, several threads contend for the value
// of BigInt.
// Here we focus on the compare and exchange for simplicity.
int main(void)
{
   BigInt.Int[1] = 23;
   BigInt.Int[0] = 11;
   AtomicOp();
   printf("BigInt.Int[1] = %d, BigInt.Int[0] = %d\n",
      BigInt.Int[1],BigInt.Int[0]);
}
```

```Output
BigInt.Int[1] = 34, BigInt.Int[0] = 12
```

**Fine sezione specifica Microsoft**

## <a name="see-also"></a>Vedere anche

[Intrinseci del compilatore](../intrinsics/compiler-intrinsics.md)\
[Funzioni intrinseche _InterlockedCompareExchange](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)\
[Conflitti con il compilatore x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
