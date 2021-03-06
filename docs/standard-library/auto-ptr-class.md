---
title: Classe auto_ptr
ms.date: 11/04/2016
f1_keywords:
- memory/std::auto_ptr
- memory/std::auto_ptr::element_type
- memory/std::auto_ptr::get
- memory/std::auto_ptr::release
- memory/std::auto_ptr::reset
helpviewer_keywords:
- std::auto_ptr [C++]
- std::auto_ptr [C++], element_type
- std::auto_ptr [C++], get
- std::auto_ptr [C++], release
- std::auto_ptr [C++], reset
ms.assetid: 7f9108b6-9eb3-4634-b615-cf7aa814f23b
ms.openlocfilehash: 6b429b0e5c734f81216c988e372c02021528cffd
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/21/2019
ms.locfileid: "72690033"
---
# <a name="auto_ptr-class"></a>Classe auto_ptr

Esegue il wrapping di un puntatore di tipo smart intorno a una risorsa, in modo da assicurare che la risorsa venga eliminata definitivamente in modo automatico quando il controllo lascia un blocco.

La classe `unique_ptr` con maggiori capacità prevale su `auto_ptr`. Per altre informazioni, vedere [Classe unique_ptr](../standard-library/unique-ptr-class.md).

Per altre informazioni su `throw()` e sulla gestione delle eccezioni, vedere [Specifiche di eccezioni (generazione)](../cpp/exception-specifications-throw-cpp.md).

## <a name="syntax"></a>Sintassi

```cpp
class auto_ptr {
    typedef Type element_type;
    explicit auto_ptr(Type* ptr = 0) throw();
    auto_ptr(auto_ptr<Type>& right) throw()
        ;
    template <class Other>
    operator auto_ptr<Other>() throw();
    template <class Other>
    auto_ptr<Type>& operator=(auto_ptr<Other>& right) throw();
    template <class Other>
    auto_ptr(auto_ptr<Other>& right);
    auto_ptr<Type>& operator=(auto_ptr<Type>& right);
    ~auto_ptr();
    Type& operator*() const throw();
    Type * operator->()const throw();
    Type *get() const throw();
    Type *release()throw();
    void reset(Type* ptr = 0);
};
```

### <a name="parameters"></a>Parametri

\ a *destra*
`auto_ptr` da cui ottenere una risorsa esistente.

\ *ptr*
Puntatore specificato per sostituire il puntatore archiviato.

## <a name="remarks"></a>Note

Il modello di classe descrive un puntatore intelligente, denominato `auto_ptr`, a un oggetto allocato. Il puntatore deve essere null o designare un oggetto allocato da **New**. `auto_ptr` trasferisce la proprietà se il valore archiviato viene assegnato a un altro oggetto. Sostituisce il valore archiviato dopo un trasferimento con un puntatore null. Il distruttore per `auto_ptr<Type>` Elimina l'oggetto allocato. `auto_ptr<Type>` assicura che un oggetto allocato venga eliminato automaticamente quando il controllo lascia un blocco, anche tramite un'eccezione generata. Non costruire due oggetti `auto_ptr<Type>` proprietari dello stesso oggetto.

È possibile passare un oggetto `auto_ptr<Type>` in base al valore come argomento per una chiamata di funzione. Un `auto_ptr` non può essere un elemento di un contenitore della libreria standard. Non è possibile gestire in modo affidabile una sequenza di oggetti `auto_ptr<Type>` con un contenitore della libreria standard C++.

## <a name="members"></a>Members

### <a name="constructors"></a>Costruttori

|||
|-|-|
|[auto_ptr](#auto_ptr)|Costruttore per oggetti di tipo `auto_ptr`.|

### <a name="typedefs"></a>Definizioni typedef

|||
|-|-|
|[element_type](#element_type)|Il tipo è un sinonimo del parametro di modello `Type`.|

### <a name="functions"></a>Funzioni

|||
|-|-|
|[get](#get)|La funzione membro restituisce il puntatore `myptr` archiviato.|
|[release](#release)|Il membro sostituisce il puntatore archiviato `myptr` con un puntatore Null e restituisce il puntatore archiviato in precedenza.|
|[reset](#reset)|La funzione membro valuta l'espressione `delete myptr`, ma solo se il valore del puntatore archiviato `myptr` cambia in seguito a una chiamata di funzione. Sostituisce quindi il puntatore archiviato con *ptr*.|

### <a name="operators"></a>Operatori

|||
|-|-|
|[operator=](#op_eq)|Operatore di assegnazione che trasferisce la proprietà da un oggetto `auto_ptr` a un altro.|
|[operator*](#op_star)|Operatore di dereferenziazione per oggetti di tipo `auto_ptr`.|
|[operator->](#op_arrow)|Operatore per consentire l'accesso ai membri.|
|[operator auto_ptr\<Other>](#op_auto_ptr_lt_other_gt)|Esegue il cast da un tipo di `auto_ptr` a un altro tipo di `auto_ptr`.|
|[operator auto_ptr_ref\<Other>](#op_auto_ptr_ref_lt_other_gt)|Esegue il cast da un `auto_ptr` a un `auto_ptr_ref`.|

### <a name="auto_ptr"></a>auto_ptr

Costruttore per oggetti di tipo `auto_ptr`.

```cpp
explicit auto_ptr(Type* ptr  = 0) throw();

auto_ptr(auto_ptr<Type>& right) throw();

auto_ptr(auto _ptr_ref<Type> right) throw();

template <class Other>
auto _ptr(auto _ptr<Other>& right) throw();
```

#### <a name="parameters"></a>Parametri

\ *ptr*
Il puntatore all'oggetto incapsulato da `auto_ptr`.

\ a *destra*
L'oggetto `auto_ptr` che deve essere copiato dal costruttore.

#### <a name="remarks"></a>Note

Il primo costruttore archivia *ptr* in `myptr`, il puntatore archiviato all'oggetto allocato. Il secondo costruttore trasferisce la proprietà del puntatore archiviato a *destra*, archiviando *right*. [versione](#release) in `myptr`.

Il terzo costruttore si comporta come il secondo, ad eccezione del fatto che archivia `right`. `ref` `release` in `myptr`, dove `ref` è il riferimento archiviato in `right`.

Il costruttore di modello si comporta come il secondo costruttore, a condizione che un puntatore a `Other` possa essere convertito in modo implicito in un puntatore a `Type`.

#### <a name="example"></a>Esempio

```cpp
// auto_ptr_auto_ptr.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

class Int
{
public:
   Int(int i)
   {
      cout << "Constructing " << ( void* )this  << endl;
      x = i;
      bIsConstructed = true;
   };
   ~Int( )
   {
      cout << "Destructing " << ( void* )this << endl;
      bIsConstructed = false;
   };
   Int &operator++( )
   {
      x++;
      return *this;
   };
   int x;
private:
   bool bIsConstructed;
};

void function ( auto_ptr<Int> &pi )
{
   ++( *pi );
   auto_ptr<Int> pi2( pi );
   ++( *pi2 );
   pi = pi2;
}

int main( )
{
   auto_ptr<Int> pi ( new Int( 5 ) );
   cout << pi->x << endl;
   function( pi );
   cout << pi->x << endl;
}
```

```Output
Constructing 00311AF8
5
7
Destructing 00311AF8
```

### <a name="element_type"></a>element_type

Il tipo è un sinonimo del parametro di modello `Type`.

```cpp
typedef Type element  _type;
```

### <a name="get"></a>Ottieni

La funzione membro restituisce il puntatore `myptr` archiviato.

```cpp
Type *get() const throw();
```

#### <a name="return-value"></a>Valore restituito

@No__t_0 puntatore archiviato.

#### <a name="example"></a>Esempio

```cpp
// auto_ptr_get.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>
using namespace std;

class Int
{
public:
   Int(int i)
   {
      x = i;
      cout << "Constructing " << ( void* )this  << " Value: " << x << endl;
   };
   ~Int( )
   {
      cout << "Destructing " << ( void* )this << " Value: " << x << endl;
   };

   int x;

};

int main( )
{
   auto_ptr<Int> pi ( new Int( 5 ) );
   pi.reset( new Int( 6 ) );
   Int* pi2 = pi.get ( );
   Int* pi3 = pi.release ( );
   if (pi2 == pi3)
      cout << "pi2 == pi3" << endl;
   delete pi3;
}
```

```Output
Constructing 00311AF8 Value: 5
Constructing 00311B88 Value: 6
Destructing 00311AF8 Value: 5
pi2 == pi3
Destructing 00311B88 Value: 6
```

### <a name="op_eq"></a>operatore =

Operatore di assegnazione che trasferisce la proprietà da un oggetto `auto_ptr` a un altro.

```cpp
template <class Other>
    auto_ptr<Type>& operator=(auto_ptr<Other>& right) throw();
auto_ptr<Type>& operator=(auto_ptr<Type>& right) throw();
auto_ptr<Type>& operator=(auto_ptr_ref<Type> right) throw();
```

#### <a name="parameters"></a>Parametri

\ a *destra*
Oggetto di tipo `auto_ptr`.

#### <a name="return-value"></a>Valore restituito

Riferimento a un oggetto di tipo `auto_ptr<Type>`.

#### <a name="remarks"></a>Note

L'assegnazione valuta l'espressione `delete myptr`, ma solo se il puntatore archiviato `myptr` cambia come risultato dell'assegnazione. Trasferisce quindi la proprietà del puntatore archiviato a *destra*, archiviando *right*. [versione](#release) in `myptr`. La funzione restituisce __\*this__.

#### <a name="example"></a>Esempio

Per un esempio di utilizzo dell'operatore membro, vedere [auto_ptr](#auto_ptr).

### <a name="op_star"></a>operatore

Operatore di dereferenziazione per oggetti di tipo `auto_ptr`.

```cpp
Type& operator*() const throw();
```

#### <a name="return-value"></a>Valore restituito

Riferimento a un oggetto di tipo `Type` di proprietà del puntatore.

#### <a name="remarks"></a>Note

L'operatore di riferimento indiretto restituisce `*`[get](#get). Di conseguenza, il puntatore archiviato non deve essere null.

#### <a name="example"></a>Esempio

Per un esempio di come usare la funzione membro, vedere [auto_ptr](#auto_ptr).

### <a name="op_arrow"></a>operatore-&gt;

Operatore per consentire l'accesso ai membri.

```cpp
Type * operator->() const throw();
```

#### <a name="return-value"></a>Valore restituito

Membro dell'oggetto di cui `auto_ptr` proprietario.

#### <a name="remarks"></a>Note

L'operatore di selezione restituisce [get](#get)`( )`, in modo che l'espressione *ap*-> **member** si comporti come ( *ap*. **get**( ) )-> **member**, dove *ap* è un oggetto di classe `auto_ptr`\< **Type**>. Di conseguenza, il puntatore archiviato non deve essere null e `Type` deve essere una classe, uno struct o un tipo di Unione con un membro di `member`.

#### <a name="example"></a>Esempio

Per un esempio di come usare la funzione membro, vedere [auto_ptr](#auto_ptr).

### <a name="op_auto_ptr_lt_other_gt"></a>operatore auto_ptr &lt;Other &gt;

Esegue il cast da un tipo di `auto_ptr` a un altro tipo di `auto_ptr`.

```cpp
template <class Other>
operator auto _ptr<Other>() throw();
```

#### <a name="return-value"></a>Valore restituito

L'operatore cast di tipo restituisce `auto_ptr` \< **Other**>( **\*this**).

#### <a name="example"></a>Esempio

```cpp
// auto_ptr_op_auto_ptr.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;
int main()
{
   auto_ptr<int> pi ( new int( 5 ) );
   auto_ptr<const int> pc = ( auto_ptr<const int> )pi;
}
```

### <a name="op_auto_ptr_ref_lt_other_gt"></a>operatore auto_ptr_ref &lt;Other &gt;

Esegue il cast da un `auto_ptr` a un `auto_ptr_ref`.

```cpp
template <class Other>
operator auto _ptr  _ref<Other>() throw();
```

#### <a name="return-value"></a>Valore restituito

L'operatore cast di tipo restituisce **auto_ptr_ref**\< **Other**>( **\*this**).

#### <a name="example"></a>Esempio

```cpp
// auto_ptr_op_auto_ptr_ref.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

class C {
public:
    C(int _i) : m_i(_i) {
    }
    ~C() {
        cout << "~C:  " << m_i << "\n";
    }
    C &operator =(const int &x) {
        m_i = x;
        return *this;
    }
    int m_i;
};
void f(auto_ptr<C> arg) {
};
int main()
{
    const auto_ptr<C> ciap(new C(1));
    auto_ptr<C> iap(new C(2));

    // Error: this implies transfer of ownership of iap's pointer
    // f(ciap);
    f(iap); // compiles, but gives up ownership of pointer

            // here, iap owns a destroyed pointer so the following is bad:
            // *iap = 5; // BOOM

    cout << "main exiting\n";
}
```

```Output
~C:  2
main exiting
~C:  1
```

### <a name="release"></a>versione

Il membro sostituisce il puntatore archiviato `myptr` con un puntatore Null e restituisce il puntatore archiviato in precedenza.

```cpp
Type *release() throw();
```

#### <a name="return-value"></a>Valore restituito

Il puntatore archiviato in precedenza.

#### <a name="remarks"></a>Note

Il membro sostituisce il puntatore archiviato `myptr` con un puntatore Null e restituisce il puntatore archiviato in precedenza.

#### <a name="example"></a>Esempio

```cpp
// auto_ptr_release.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>
using namespace std;

class Int
{
public:
    Int(int i)
    {
        x = i;
        cout << "Constructing " << (void*)this << " Value: " << x << endl;
    };
    ~Int() {
        cout << "Destructing " << (void*)this << " Value: " << x << endl;
    };

    int x;

};

int main()
{
    auto_ptr<Int> pi(new Int(5));
    pi.reset(new Int(6));
    Int* pi2 = pi.get();
    Int* pi3 = pi.release();
    if (pi2 == pi3)
        cout << "pi2 == pi3" << endl;
    delete pi3;
}
```

```Output
Constructing 00311AF8 Value: 5
Constructing 00311B88 Value: 6
Destructing 00311AF8 Value: 5
pi2 == pi3
Destructing 00311B88 Value: 6
```

### <a name="reset"></a>reimpostazione

La funzione membro valuta l'espressione `delete myptr`, ma solo se il valore del puntatore archiviato `myptr` cambia in seguito a una chiamata di funzione. Sostituisce quindi il puntatore archiviato con `ptr`.

```cpp
void reset(Type* ptr = 0);
```

#### <a name="parameters"></a>Parametri

\ *ptr*
Puntatore specificato per sostituire il puntatore archiviato `myptr`.

#### <a name="example"></a>Esempio

```cpp
// auto_ptr_reset.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

class Int
{
public:
    Int(int i)
    {
        x = i;
        cout << "Constructing " << (void*)this << " Value: " << x << endl;
    };
    ~Int()
    {
        cout << "Destructing " << (void*)this << " Value: " << x << endl;
    };

    int x;
};

int main()
{
    auto_ptr<Int> pi(new Int(5));
    pi.reset(new Int(6));
    Int* pi2 = pi.get();
    Int* pi3 = pi.release();
    if (pi2 == pi3)
        cout << "pi2 == pi3" << endl;
    delete pi3;
}
```

```Output
Constructing 00311AF8 Value: 5
Constructing 00311B88 Value: 6
Destructing 00311AF8 Value: 5
pi2 == pi3
Destructing 00311B88 Value: 6
```

## <a name="see-also"></a>Vedere anche

[Classe unique_ptr](../standard-library/unique-ptr-class.md)
