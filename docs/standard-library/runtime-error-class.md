---
title: Classe runtime_error
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::runtime_error
helpviewer_keywords:
- runtime_error class
ms.assetid: 4d0227bf-847b-45a2-a320-2351ebf98368
ms.openlocfilehash: c4c4436c32f5f23c6bea119e95b165631384f583
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451125"
---
# <a name="runtimeerror-class"></a>Classe runtime_error

La classe funge da classe di base per tutte le eccezioni generate per segnalare errori presumibilmente rilevabili solo quando il programma viene eseguito.

## <a name="syntax"></a>Sintassi

```cpp
class runtime_error : public exception {
public:
    explicit runtime_error(const string& message);

    explicit runtime_error(const char *message);

};
```

## <a name="remarks"></a>Note

Il valore restituito dalla [classe exception](../standard-library/exception-class.md) è una copia di **message**`.`[data](../standard-library/basic-string-class.md#data).

## <a name="example"></a>Esempio

```cpp
// runtime_error.cpp
// compile with: /EHsc /GR
#include <iostream>

using namespace std;

int main( )
{
// runtime_error
   try
   {
      locale loc( "test" );
   }
   catch ( exception &e )
   {
      cerr << "Caught " << e.what( ) << endl;
      cerr << "Type " << typeid( e ).name( ) << endl;
   };
}
/* Output:
Caught bad locale name
Type class std::runtime_error
*/
```

## <a name="requirements"></a>Requisiti

**Intestazione:** \<stdexcept>

**Spazio dei nomi:** std

## <a name="see-also"></a>Vedere anche

[Classe Exception](../standard-library/exception-class.md)\
[Thread Safety nella libreria standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
