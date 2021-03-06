---
title: restrict
ms.date: 02/09/2018
f1_keywords:
- restrict_cpp
helpviewer_keywords:
- __declspec keyword [C++], restrict
- restrict __declspec keyword
ms.assetid: f39cf632-68d8-4362-a497-2d4c15693689
ms.openlocfilehash: 40c1c05ca72f639829f2d3658497b0e9f3199640
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403373"
---
# <a name="restrict"></a>restrict

**Sezione specifica Microsoft**

Quando applicato a una definizione che restituisce un tipo di puntatore, o dichiarazione di funzione **limitare** indica al compilatore che la funzione restituisce un oggetto che non è *aliasing*, vale a dire, cui viene fatto riferimento da altri puntatori. In questo modo il compilatore di eseguire ulteriori ottimizzazioni.

## <a name="syntax"></a>Sintassi

> **__declspec(restrict)** *pointer_return_type* *function*();

## <a name="remarks"></a>Note

Il compilatore propaga **__declspec(restrict)**. Ad esempio, la libreria CRT `malloc` funzione ha un **__declspec(restrict)** decoration e conseguenza, il compilatore presuppone che i puntatori inizializzati in posizioni di memoria da `malloc` non sono inoltre associato un alias da in precedenza ai puntatori esistenti.

Il compilatore non verifica che il puntatore restituito non è effettivamente un alias. È responsabilità dello sviluppatore assicurarsi che il programma non alias non un puntatore contrassegnato con il **limitare declspec** modificatore.

Per una semantica simile nelle variabili, vedere [Restrict](../cpp/extension-restrict.md).

Per un'altra annotazione che viene applicato l'aliasing all'interno di una funzione, vedere [__declspec(noalias)](../cpp/noalias.md).

Per informazioni sul **limitare** parola chiave che fa parte di C++ AMP, vedere [limitare (C++ AMP)](../cpp/restrict-cpp-amp.md).

## <a name="example"></a>Esempio

L'esempio seguente illustra l'uso della **__declspec(restrict)**.

Quando **__declspec(restrict)** viene applicato a una funzione che restituisce un puntatore, ciò indica al compilatore che la memoria a cui punta il valore restituito non è associato un alias. In questo esempio, i puntatori `mempool` e `memptr` sono globali, in modo che il compilatore non può essere certi che la memoria fanno riferimento non è associato un alias. Ma vengono usati all'interno `ma` e il controllo al chiamante `init` in modo che la memoria che non in caso contrario, viene fatto riferimento dal programma, quindi restituisce **__decslpec(restrict)** viene usato per l'utilità di ottimizzazione. Ciò è simile al modo in cui le intestazioni CRT decorano funzioni di allocazione, ad esempio `malloc` usando **__declspec(restrict)** per indicare che restituiscono sempre la memoria che non può essere associato un alias esistente i puntatori.

```C
// declspec_restrict.c
// Compile with: cl /W4 declspec_restrict.c
#include <stdio.h>
#include <stdlib.h>

#define M 800
#define N 600
#define P 700

float * mempool, * memptr;

__declspec(restrict) float * ma(int size)
{
    float * retval;
    retval = memptr;
    memptr += size;
    return retval;
}

__declspec(restrict) float * init(int m, int n)
{
    float * a;
    int i, j;
    int k=1;

    a = ma(m * n);
    if (!a) exit(1);
    for (i=0; i<m; i++)
        for (j=0; j<n; j++)
            a[i*n+j] = 0.1f/k++;
    return a;
}

void multiply(float * a, float * b, float * c)
{
    int i, j, k;

    for (j=0; j<P; j++)
        for (i=0; i<M; i++)
            for (k=0; k<N; k++)
                c[i * P + j] =
                          a[i * N + k] *
                          b[k * P + j];
}

int main()
{
    float * a, * b, * c;

    mempool = (float *) malloc(sizeof(float) * (M*N + N*P + M*P));

    if (!mempool)
    {
        puts("ERROR: Malloc returned null");
        exit(1);
    }

    memptr = mempool;
    a = init(M, N);
    b = init(N, P);
    c = init(M, P);

    multiply(a, b, c);
}
```

**Fine sezione specifica Microsoft**

## <a name="see-also"></a>Vedere anche

[Parole chiave](../cpp/keywords-cpp.md)<br/>
[__declspec](../cpp/declspec.md)<br/>
[__declspec(noalias)](../cpp/noalias.md)
