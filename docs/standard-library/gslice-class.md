---
title: Classe gslice
ms.date: 11/04/2016
f1_keywords:
- valarray/std::gslice
- valarray/std::gslice::size
- valarray/std::gslice::start
- valarray/std::gslice::stride
helpviewer_keywords:
- std::gslice [C++]
- std::gslice [C++], size
- std::gslice [C++], start
- std::gslice [C++], stride
ms.assetid: f47cffd0-ea59-4b13-848b-7a5ce1d7e2a3
ms.openlocfilehash: 07c987fb08a213bb66da628bec3021a3bf9ba24a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370628"
---
# <a name="gslice-class"></a>Classe gslice

Classe di utilità per valarray usata per definire subset multidimensionali di valarray. Se valarray viene considerato come matrice multidimensionale con tutti gli elementi in una matrice, la sezione estrae un vettore dalla matrice multidimensionale.

## <a name="remarks"></a>Osservazioni

La classe archivia i parametri che caratterizzano un oggetto di tipo [gslice_array](../standard-library/gslice-array-class.md). Il subset di un oggetto valarray viene costruito indirettamente quando un oggetto della classe gslice viene visualizzato come argomento per un oggetto della classe [valarray](../standard-library/valarray-class.md#op_at)**\<Type>**. I valori archiviati che specificano il subset selezionato da valarray padre includono:

- Indice iniziale.

- Vettore di `valarray<size_t>`lunghezza della classe .

- Vettore passo della `valarray<size_t>`classe .

I due vettori devono avere la stessa lunghezza.

Se il set definito da gslice è il subset di un valarray costante, gslice diventa un nuovo valarray. Se il set definito da gslice è il subset di un valarray non costante, gslice ha una semantica di riferimento al valarray originale. Il meccanismo di valutazione per i valarray non costanti consente di risparmiare tempo e memoria.

Le operazioni sui valarray sono consentite solo se i subset di origine e di destinazione definiti dai gslice sono distinti e tutti gli indici sono validi.

### <a name="constructors"></a>Costruttori

|Costruttore|Descrizione|
|-|-|
|[gslice](#gslice)|Definisce un subset di un `valarray` formato da più sezioni del `valarray`, che iniziano tutte dall'elemento specificato.|

### <a name="member-functions"></a>Funzioni membro

|Funzione membro|Descrizione|
|-|-|
|[Dimensione](#size)|Trova i valori della matrice che specificano il numero di elementi in una sezione generale di un `valarray`.|
|[Iniziare](#start)|Trova l'indice iniziale di una sezione generale di un `valarray`.|
|[Passo](#stride)|Trova la distanza tra gli elementi in una sezione generale di un `valarray`.|

## <a name="requirements"></a>Requisiti

**Intestazione:** \<valarray>

**Spazio dei nomi:** std

## <a name="gslicegslice"></a><a name="gslice"></a>gslice::gslice

Classe di utilità per l'oggetto valarray usato per definire sezioni multidimensionali di un oggetto valarray.

```cpp
gslice();

gslice(
    size_t _StartIndex,
    const valarray<size_t>& _LenArray,
    const valarray<size_t>& _IncArray);
```

### <a name="parameters"></a>Parametri

*_StartIndex*\
Indice valarray del primo elemento del subset.

*_LenArray*\
Matrice che specifica il numero di elementi in ogni sezione.

*_IncArray*\
Matrice che specifica lo stride in ogni sezione.

### <a name="return-value"></a>Valore restituito

Il costruttore predefinito archivia zero per l'indice iniziale e vettori di lunghezza zero per i vettori di lunghezza e stride. Il secondo costruttore archivia *_StartIndex* per l'indice iniziale, *_LenArray* per la matrice di lunghezza e *_IncArray* per la matrice stride.

### <a name="remarks"></a>Osservazioni

**gslice** definisce un subset di un oggetto valarray costituito da più sezioni di tale oggetto, ognuna delle quali inizia in corrispondenza dello stesso elemento specificato. La possibilità di usare matrici per definire più sezioni costituisce l'unica differenza tra `gslice` e [slice::slice](../standard-library/slice-class.md#slice). La prima sezione ha un primo elemento con un indice di *_StartIndex*, un numero di elementi specificati dal primo elemento di *_LenArray*e un passo dato dal primo elemento di *_IncArray*. Nel successivo set di sezioni ortogonali i primi elementi vengono forniti dalla prima sezione. Il secondo elemento di *_LenArray* specifica il numero di elementi. Il passo è dato dal secondo elemento di *_IncArray*. Una terza dimensione delle sezioni usa gli elementi della matrice bidimensionale come elementi iniziali e procede in modo analogo.

### <a name="example"></a>Esempio

```cpp
// gslice_ctor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:" << endl << "(";
   for ( i = 0 ; i < 20 ; i++ )
      cout << " " << va [ i ];
   cout << " )" << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];

   cout << "The valarray for vaGSlice is vaResult:" << endl
        << "va[vaGSlice] = (";

   for ( i = 0 ; i < 8 ; i++ )
      cout << " " << vaResult [ i ];
   cout << ")" << endl;
}
```

```Output
The operand valarray va is:
( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 )
The valarray for vaGSlice is vaResult:
va[vaGSlice] = ( 0 4 8 12 7 11 15 19)
```

## <a name="gslicesize"></a><a name="size"></a>gslice::dimensione

Trova i valori della matrice che specificano il numero di elementi in una sezione generale di un oggetto valarray.

```cpp
valarray<size_t> size() const;
```

### <a name="return-value"></a>Valore restituito

Oggetto valarray che specifica il numero di elementi in ogni sezione di una sezione generale di un oggetto valarray.

### <a name="remarks"></a>Osservazioni

La funzione membro restituisce le lunghezze archiviate delle sezioni.

### <a name="example"></a>Esempio

```cpp
// gslice_size.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t sizeVA;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   sizeVA = va.size ( );
   cout << "The size of the valarray is: "
        << sizeVA << "." << endl << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];
   const valarray <size_t> sizeGS = vaGSlice.size ( );

   cout << "The valarray for vaGSlice is vaResult:"
        << "\n va[vaGSlice] = ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   cout << "The size of vaResult is:"
        << "\n vaGSlice.size ( ) = ( ";
      for ( i = 0 ; i < 2 ; i++ )
         cout << sizeGS[ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The operand valarray va is:
( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ).
The size of the valarray is: 20.

The valarray for vaGSlice is vaResult:
va[vaGSlice] = ( 0 4 8 12 7 11 15 19 ).
The size of vaResult is:
vaGSlice.size ( ) = ( 4 4 ).
```

## <a name="gslicestart"></a><a name="start"></a>gslice::start

Trova l'indice iniziale di una sezione generale di un oggetto valarray.

```cpp
size_t start() const;
```

### <a name="return-value"></a>Valore restituito

Indice iniziale di una sezione generale di un oggetto valarray.

### <a name="example"></a>Esempio

```cpp
// gslice_start.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for (i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];
   size_t vaGSstart = vaGSlice.start ( );

   cout << "The valarray for vaGSlice is vaResult:"
        << "\n va[vaGSlice] = ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   cout << "The index of the first element of vaResult is: "
        << vaGSstart << "." << endl;
}
```

```Output
The operand valarray va is:
( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ).
The valarray for vaGSlice is vaResult:
va[vaGSlice] = ( 0 4 8 12 7 11 15 19 ).
The index of the first element of vaResult is: 0.
```

## <a name="gslicestride"></a><a name="stride"></a>gslice::stride

Trova la distanza tra gli elementi in una sezione generale di un oggetto valarray.

```cpp
valarray<size_t> stride() const;
```

### <a name="return-value"></a>Valore restituito

Oggetto valarray che specifica le distanze tra gli elementi in ogni sezione di una sezione generale di un oggetto valarray.

### <a name="example"></a>Esempio

```cpp
// gslice_stride.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for (i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:\n ( ";
      for (i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];
   const valarray <size_t> strideGS = vaGSlice.stride ( );

   cout << "The valarray for vaGSlice is vaResult:"
        << "\n va[vaGSlice] = ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   cout << "The strides of vaResult are:"
        << "\n vaGSlice.stride ( ) = ( ";
      for ( i = 0 ; i < 2 ; i++ )
         cout << strideGS[ i ] << " ";
   cout << ")." << endl;

}
```

```Output
The operand valarray va is:
( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ).
The valarray for vaGSlice is vaResult:
va[vaGSlice] = ( 0 4 8 12 7 11 15 19 ).
The strides of vaResult are:
vaGSlice.stride ( ) = ( 7 4 ).
```

## <a name="see-also"></a>Vedere anche

[Sicurezza dei filettatura nella libreria standard di C](../standard-library/thread-safety-in-the-cpp-standard-library.md)
