---
title: Classe unary_negate
ms.date: 02/21/2019
f1_keywords:
- functional/std::unary_negate
helpviewer_keywords:
- unary_negate class
ms.assetid: e3b86eec-3205-49b9-ab83-f55225af4e0c
ms.openlocfilehash: 2d9f0bedd9e541e65f04ac20375f16f41413cf03
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/21/2019
ms.locfileid: "72684438"
---
# <a name="unary_negate-class"></a>Classe unary_negate

Modello di classe che fornisce una funzione membro che nega il valore restituito di una funzione unaria specificata. Deprecato in C++ 17 a favore di [not_fn](functional-functions.md#not_fn).

## <a name="syntax"></a>Sintassi

```cpp
template <class Predicate>
class unary_negate
    : public unaryFunction<typename Predicate::argument_type, bool>
{
    explicit unary_negate(const Predicate& Func);
    bool operator()(const typename Predicate::argument_type& left) const;
};
```

### <a name="parameters"></a>Parametri

@No__t_1 *Func*
La funzione unaria da negare.

\ a *sinistra*
Operando della funzione unaria da negare.

## <a name="return-value"></a>Valore restituito

Negazione della funzione unaria.

## <a name="remarks"></a>Note

Il modello di classe archivia una copia di un oggetto funzione unaria *\_Func*. Definisce la funzione membro `operator()` come restituito `!_Func(left)`.

Il costruttore di `unary_negate` viene usato di rado in modo diretto. La funzione di supporto [not1](../standard-library/functional-functions.md#not1) costituisce un modo più semplice per dichiarare e usare il predicato adattatore **binary_negator**.

## <a name="example"></a>Esempio

```cpp
// functional_unary_negate.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 7; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    vector<int>::iterator::difference_type result1;
    // Count the elements greater than 10
    result1 = count_if(v1.begin(), v1.end(), bind2nd(greater<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;

    vector<int>::iterator::difference_type result2;
    // Use the negator to count the elements less than or equal to 10
    result2 = count_if(v1.begin(), v1.end(),
        unary_negate<binder2nd <greater<int> > >(bind2nd(greater<int>(),10)));

    // The following helper function not1 also works for the above line
    // not1(bind2nd(greater<int>(), 10)));

    cout << "The number of elements in v1 not greater than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 30 35 )
The number of elements in v1 greater than 10 is: 5.
The number of elements in v1 not greater than 10 is: 3.
```
