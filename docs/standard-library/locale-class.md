---
title: Classe locale
ms.date: 03/19/2019
f1_keywords:
- xlocale/std::locale
- xlocale/std::locale::category
- xlocale/std::locale::combine
- xlocale/std::locale::name
- xlocale/std::locale::classic
- xlocale/std::locale::global
- xlocale/std::locale::operator( )
- xlocale/std::locale::facet
- xlocale/std::locale::id
helpviewer_keywords:
- std::locale [C++]
- std::locale [C++], category
- std::locale [C++], combine
- std::locale [C++], name
- std::locale [C++], classic
- std::locale [C++], global
- std::locale [C++], facet
- std::locale [C++], id
ms.assetid: 7dd6d271-472d-4750-8fb5-ea8f55fbef62
ms.openlocfilehash: 2581c5cdacc9e542f5d911860128dcf5526621ef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367307"
---
# <a name="locale-class"></a>Classe locale

Classe che descrive un oggetto delle impostazioni locali che incapsula le informazioni specifiche delle impostazioni locali come set di facet che definiscono collettivamente un ambiente localizzato specifico.

## <a name="syntax"></a>Sintassi

```cpp
class locale;
```

## <a name="remarks"></a>Osservazioni

Un facet è un puntatore a un oggetto di una classe derivata dalla classe [facet](#facet_class) con un oggetto pubblico nel formato seguente:

```cpp
static locale::id id;
```

È possibile definire un set aperto di tali facet. È inoltre possibile costruire un oggetto delle impostazioni locali che indica un numero arbitrario di facet.

I gruppi predefiniti di questi facet rappresentano le [categorie di impostazioni locali](#category) tradizionalmente gestite nella libreria C standard dalla funzione `setlocale`.

Categoria `collate` (LC_COLLATE) include i facet:

```cpp
collate<char>
collate<wchar_t>
```

Categoria `ctype` (LC_CTYPE) include i facet:

```cpp
ctype<char>
ctype<wchar_t>
codecvt<char, char, mbstate_t>
codecvt<wchar_t, char, mbstate_t>
codecvt<char16_t, char, mbstate_t>
codecvt<char32_t, char, mbstate_t>
```

Categoria `monetary` (LC_MONETARY) include i facet:

```cpp
moneypunct<char, false>
moneypunct<wchar_t, false>
moneypunct<char, true>
moneypunct<wchar_t, true>
money_get<char, istreambuf_iterator<char>>
money_get<wchar_t, istreambuf_iterator<wchar_t>>
money_put<char, ostreambuf_iterator<char>>
money_put<wchar_t, ostreambuf_iterator<wchar_t>>
```

Categoria `numeric` (LC_NUMERIC) include i facet:

```cpp
num_get<char, istreambuf_iterator<char>>
num_get<wchar_t, istreambuf_iterator<wchar_t>>
num_put<char, ostreambuf_iterator<char>>
num_put<wchar_t, ostreambuf_iterator<wchar_t>>
numpunct<char>
numpunct<wchar_t>
```

Categoria `time` (LC_TIME) include i facet:

```cpp
time_get<char, istreambuf_iterator<char>>
time_get<wchar_t, istreambuf_iterator<wchar_t>>
time_put<char, ostreambuf_iterator<char>>
time_put<wchar_t, ostreambuf_iterator<wchar_t>>
```

Categoria `messages` (LC_MESSAGES) include i facet:

```cpp
messages<char>
messages<wchar_t>
```

(L'ultima categoria è richiesta da POSIX, ma non lo standard C.)

Alcuni di questi facet predefiniti vengono `iostream` utilizzati dalle classi, per controllare la conversione di valori numerici in e da sequenze di testo.

Un oggetto delle impostazioni locali della classe consente inoltre di archiviare un nome delle impostazioni locali come oggetto della classe [string](../standard-library/string-typedefs.md#string). L'uso di un nome delle impostazioni locali non valido per costruire un facet o un oggetto delle impostazioni locali genera un oggetto della classe [runtime_error](../standard-library/runtime-error-class.md). Il nome delle `"*"` impostazioni locali archiviate è se l'oggetto delle impostazioni locali non può essere certo che le impostazioni locali di tipo C corrispondano esattamente a quella rappresentata dall'oggetto. In caso contrario, è possibile stabilire impostazioni locali `locale_object`corrispondenti `setlocale(LC_ALL , locale_object.`all'interno della libreria C standard, per un oggetto delle impostazioni locali , chiamando [nome](#name)`().c_str())`.

In questa implementazione è inoltre possibile chiamare la funzione membro statica:

```cpp
static locale empty();
```

per costruire un oggetto delle impostazioni locali privo di facet. È anche un locale trasparente. Se il modello funziona [has_facet](../standard-library/locale-functions.md#has_facet) e [use_facet](../standard-library/locale-functions.md#use_facet) non riesce a trovare il facet richiesto in un'impostazione internazionale trasparente, consulta noto alle impostazioni locali globali e quindi, se questo è trasparente, le impostazioni locali classiche. Così, si può scrivere:

```cpp
cout.imbue(locale::empty());
```

Gli inserimenti [`cout`](../standard-library/iostream.md#cout) successivi a sono mediati dallo stato corrente delle impostazioni locali globali. È anche possibile scrivere:

```cpp
locale loc(locale::empty(),
    locale::classic(),
    locale::numeric);

cout.imbue(loc);
```

Le regole di formattazione numerica per gli inserimenti successivi a `cout` rimangono uguali a quelle delle impostazione locali C, anche quando le impostazioni locali globali forniscono regole mutevoli per l'inserimento di date e importi monetari.

### <a name="constructors"></a>Costruttori

|Costruttore|Descrizione|
|-|-|
|[Impostazioni internazionali](#locale)|Crea le impostazioni locali o una copia delle impostazioni locali oppure una copia delle impostazioni locali in cui un facet o una categoria è stata sostituita da un facet o da una categoria di altre impostazioni locali.|

### <a name="typedefs"></a>Typedef

|Nome tipo|Descrizione|
|-|-|
|[Categoria](#category)|Tipo Integer che fornisce i valori della maschera di bit per indicare le famiglie di facet standard.|

### <a name="member-functions"></a>Funzioni membro

|Funzione membro|Descrizione|
|-|-|
|[Combinare](#combine)|Inserisce un facet delle impostazioni locali specificate nelle impostazioni locali di destinazione.|
|[name](#name)|Restituisce il nome delle impostazioni locali archiviate.|

### <a name="static-functions"></a>Funzioni statiche

|||
|-|-|
|[Classico](#classic)|La funzione membro statica restituisce un oggetto delle impostazioni locali che rappresenta le impostazioni locali C classiche.|
|[Globale](#global)|Reimposta le impostazioni locali predefinite per il programma.|

### <a name="operators"></a>Operatori

|Operatore|Descrizione|
|-|-|
|[operatore di comando](#op_eq)|Assegna un'impostazione locale.|
|[operatore!](#op_neq)|Verifica l'ineguaglianza di due impostazioni locali.|
|[operator( )](#op_call)|Confronta due oggetti `basic_string`.|
|[operatore di comando](#op_eq_eq)|Verifica l'uguaglianza di due impostazioni locali.|

### <a name="classes"></a>Classi

|Classe|Descrizione|
|-|-|
|[Facet](#facet_class)|Classe utilizzata come classe base per tutti i facet delle impostazioni locali.|
|[`id`](#id_class)|La classe di membro fornisce un'identificazione dei facet univoca utilizzata come indice per cercare i facet nelle impostazioni locali.|

## <a name="requirements"></a>Requisiti

**Intestazione:** \<locale>

**Spazio dei nomi:** std

## <a name="localecategory"></a><a name="category"></a>locale::categoria

Tipo Integer che fornisce i valori della maschera di bit per indicare le famiglie di facet standard.

```cpp
typedef int category;
static const int collate = LC_COLLATE;
static const int ctype = LC_CTYPE;
static const int monetary = LC_MONETARY;
static const int numeric = LC_NUMERIC;
static const int time = LC_TIME;
static const int messages = LC_MESSAGES;
static const int all = LC_ALL;
static const int none = 0;
```

### <a name="remarks"></a>Osservazioni

Il tipo è un sinonimo di un tipo **int** che può rappresentare un gruppo di elementi distinti di un tipo di maschera di bit locale alle impostazioni locali della classe o può essere utilizzato per rappresentare una qualsiasi delle categorie delle impostazioni locali C corrispondenti. Gli elementi sono i seguenti:

- `collate`, corrispondente alla categoria C LC_COLLATE

- `ctype`, corrispondente alla categoria C LC_CTYPE

- `monetary`, corrispondente alla categoria C LC_MONETARY

- `numeric`, corrispondente alla categoria C LC_NUMERIC

- `time`, corrispondente alla categoria C LC_TIME

- `messages`, corrispondente alla categoria POSIX LC_MESSAGES

Altri due valori utili sono:

- `none`, corrispondente a nessuna delle categorie C

- `all`, corrispondente all'unione C di tutte le categorie LC_ALL

È possibile rappresentare un gruppo `OR` arbitrario di categorie `monetary` utilizzando `time`con queste costanti, come in &#124; .

## <a name="localeclassic"></a><a name="classic"></a>locale::classico

La funzione membro statica restituisce un oggetto delle impostazioni locali che rappresenta le impostazioni locali C classiche.

```cpp
static const locale& classic();
```

### <a name="return-value"></a>Valore restituito

Riferimento alle impostazioni locali C.

### <a name="remarks"></a>Osservazioni

Le impostazioni locali C classiche sono le impostazioni ASCII inglesi degli Stati Uniti all'interno della libreria C standard. Sono le impostazioni locali che vengono utilizzate in modo implicito nei programmi che non sono internazionalizzati.

### <a name="example"></a>Esempio

```cpp
// locale_classic.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "german" );
   locale loc2 = locale::global( loc1 );
   cout << "The name of the previous locale is: " << loc2.name( )
        << "." << endl;
   cout << "The name of the current locale is: " << loc1.name( )
        << "." << endl;

   if (loc2 == locale::classic( ) )
      cout << "The previous locale was classic." << endl;
   else
      cout << "The previous locale was not classic." << endl;

   if (loc1 == locale::classic( ) )
      cout << "The current locale is classic." << endl;
   else
      cout << "The current locale is not classic." << endl;
}
```

```Output
The name of the previous locale is: C.
The name of the current locale is: German_Germany.1252.
The previous locale was classic.
The current locale is not classic.
```

## <a name="localecombine"></a><a name="combine"></a>locale::combinare

Inserisce un facet delle impostazioni locali specificate nelle impostazioni locali di destinazione.

```cpp
template <class Facet>
locale combine(const locale& source_locale) const;
```

### <a name="parameters"></a>Parametri

*source_locale*\
Impostazioni locali contenenti il facet da inserire nelle impostazioni locali di destinazione.

### <a name="return-value"></a>Valore restituito

La funzione membro restituisce un oggetto impostazioni locali `Facet` che sostituisce o aggiunge a ** \*questo** il facet elencato in *source_locale*.

### <a name="example"></a>Esempio

```cpp
// locale_combine.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main() {
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("Das ist wei\x00dfzz."); // \x00df is the German sharp-s; it comes before z in the German alphabet
   _TCHAR * s2 = _T("Das ist weizzz.");
   int result1 = use_facet<collate<_TCHAR> > ( loc ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc ) << result1 << endl;

   locale loc2 ( "C" );
   int result2 = use_facet<collate<_TCHAR> > ( loc2 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc2 )  << result2 << endl;

   locale loc3 = loc2.combine<collate<_TCHAR> > (loc);
   int result3 = use_facet<collate<_TCHAR> > ( loc3 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc3 ) << result3 << endl;
}
```

## <a name="facet-class"></a><a name="facet_class"></a>Facet (classe)

Classe utilizzata come classe base per tutti i facet delle impostazioni locali.

```cpp
class facet {
protected:
    explicit facet(size_t references = 0);
    virtual ~facet();
private:
    facet(const facet&) // not defined
    void operator=(const facet&) // not defined
};
```

### <a name="remarks"></a>Osservazioni

Non è possibile copiare o `facet`assegnare un oggetto di classe . È possibile creare e distruggere oggetti derivati dalla classe `locale::facet` ma non oggetti della classe di base proper. In genere, si `_Myfac` costruisce `facet` un oggetto `locale`derivato da quando si costruisce un , come in`locale loc(locale::classic(), new _Myfac);`

In questi casi, il costruttore per la classe `facet` base deve avere un argomento zero *riferimenti.* Quando l'oggetto non è più necessario, viene eliminato, pertanto si fornisce un argomento *riferimenti* diversi da zero solo nei rari casi in cui si assume la responsabilità per la durata dell'oggetto.

## <a name="localeglobal"></a><a name="global"></a>locale::globale

Reimposta le impostazioni locali predefinite per il programma. Questa chiamata ha effetto sulle impostazioni locali globali sia per il linguaggio C che per il linguaggio C.

```cpp
static locale global(const locale& new_default_locale);
```

### <a name="parameters"></a>Parametri

*new_default_locale*\
Impostazioni locali che devono essere usate come predefinite dal programma.

### <a name="return-value"></a>Valore restituito

Impostazioni locali precedenti alla reimpostazione delle impostazioni locali predefinite.

### <a name="remarks"></a>Osservazioni

All'avvio del programma, le impostazioni locali globali coincidono con le impostazioni locali classiche. La funzione `global()` chiama `setlocale( LC_ALL, loc.name. c_str())` per definire delle impostazioni locali corrispondenti nella libreria C standard.

### <a name="example"></a>Esempio

```cpp
// locale_global.cpp
// compile by using: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( )
{
   locale loc ( "German_germany" );
   locale loc1;
   cout << "The initial locale is: " << loc1.name( ) << endl;
   locale loc2 = locale::global ( loc );
   locale loc3;
   cout << "The current locale is: " << loc3.name( ) << endl;
   cout << "The previous locale was: " << loc2.name( ) << endl;
}
```

```Output
The initial locale is: C
The current locale is: German_Germany.1252
The previous locale was: C
```

## <a name="id-class"></a><a name="id_class"></a>classe id

La classe di membro fornisce un'identificazione dei facet univoca utilizzata come indice per cercare i facet nelle impostazioni locali.

```cpp
class id
{
   protected:    id();
   private:      id(const id&)
   void operator=(const id&)  // not defined
};
```

### <a name="remarks"></a>Osservazioni

La classe membro descrive l'oggetto membro statico richiesto da ciascun facet delle impostazioni locali univoco. Non è possibile copiare o `id`assegnare un oggetto di classe .

## <a name="localelocale"></a><a name="locale"></a>locale::locale

Crea le impostazioni locali o una copia delle impostazioni locali oppure una copia delle impostazioni locali in cui un facet o una categoria è stata sostituita da un facet o da una categoria di altre impostazioni locali. Include anche un distruttore.

```cpp
locale();

explicit locale(const char* locale_name, category new_category = all);
explicit locale(const string& locale_name);
locale(const locale& from_locale);
locale(const locale& from_locale, const locale& Other, category new_category);
locale(const locale& from_locale, const char* locale_name, category new_category);

template <class Facet>
locale(const locale& from_locale, const Facet* new_facet);

~locale();
```

### <a name="parameters"></a>Parametri

*locale_name*\
Nome delle impostazioni locali.

*from_locale*\
Impostazioni locali che devono essere copiate per la costruzione delle nuove impostazioni locali.

*Altro*\
Impostazioni locali da cui selezionare una categoria.

*new_category*\
Categoria da sostituire nelle impostazioni locali costruite.

*new_facet*\
Facet da sostituire nelle impostazioni locali costruite.

### <a name="remarks"></a>Osservazioni

Il primo costruttore inizializza l'oggetto in modo che corrisponda alle impostazioni locali globali. Il secondo e il terzo costruttore inizializzano tutte le categorie di impostazioni locali in modo che abbiano un comportamento coerente con il nome delle impostazioni locali *locale_name*. I costruttori rimanenti copiano *from_locale*, con le eccezioni indicate:

`locale(const locale& from_locale, const locale& Other, category new_category);`

sostituisce da *Altri* facet corrispondenti a una categoria C per la quale c & *new_category* è diversa da zero.

`locale(const locale& from_locale, const char* locale_name, category new_category);`

`locale(const locale& from_locale, const string& locale_name, category new_category);`

sostituisce `locale(locale_name, all)` da quei facet corrispondenti a `replace_category & new_category` una categoria *replace_category* per cui è diversa da zero.

`template<class Facet> locale(const locale& from_locale, Facet* new_facet);`

sostituisce in (o aggiunge a) *from_locale* facet *new_facet*, se *new_facet* non è un puntatore null.

Se il nome delle impostazioni locali *locale_name* è un puntatore null o non è valido, la funzione genera [runtime_error](../standard-library/runtime-error-class.md).

### <a name="example"></a>Esempio

```cpp
// locale_locale.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( ) {

   // Second constructor
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("Das ist wei\x00dfzz."); // \x00df is the German sharp-s, it comes before z in the German alphabet
   _TCHAR * s2 = _T("Das ist weizzz.");
   int result1 = use_facet<collate<_TCHAR> > ( loc ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc ) << result1 << endl;

   // The first (default) constructor
   locale loc2;
   int result2 = use_facet<collate<_TCHAR> > ( loc2 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc2 )  << result2 << endl;

   // Third constructor
   locale loc3 (loc2,loc, _M_COLLATE );
   int result3 = use_facet<collate<_TCHAR> > ( loc3 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc3 ) << result3 << endl;

   // Fourth constructor
   locale loc4 (loc2, "German_Germany", _M_COLLATE );
   int result4 = use_facet<collate<_TCHAR> > ( loc4 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc4 ) << result4 << endl;
}
```

## <a name="localename"></a><a name="name"></a>locale::nome

Restituisce il nome delle impostazioni locali archiviate.

```cpp
string name() const;
```

### <a name="return-value"></a>Valore restituito

Stringa che fornisce il nome delle impostazioni locali.

### <a name="example"></a>Esempio

```cpp
// locale_name.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "german" );
   locale loc2 = locale::global( loc1 );
   cout << "The name of the previous locale is: "
        << loc2.name( ) << "." << endl;
   cout << "The name of the current locale is: "
        << loc1.name( ) << "." << endl;
}
```

```Output
The name of the previous locale is: C.
The name of the current locale is: German_Germany.1252.
```

## <a name="localeoperator"></a><a name="op_eq"></a>locale::operatore

Assegna un'impostazione locale.

```cpp
const locale& operator=(const locale& other) noexcept;
```

## <a name="localeoperator"></a><a name="op_neq"></a>locale::operator!

Verifica l'ineguaglianza di due impostazioni locali.

```cpp
bool operator!=(const locale& right) const;
```

### <a name="parameters"></a>Parametri

*va bene*\
Una delle impostazioni locali di cui verificare la disuguaglianza.

### <a name="return-value"></a>Valore restituito

Valore booleano che è **true** se le impostazioni locali non sono copie delle stesse impostazioni locali. È **false** se le impostazioni locali sono copie delle stesse impostazioni locali.

### <a name="remarks"></a>Osservazioni

Due impostazioni locali sono uguali se sono le stesse impostazioni locali, se una è una copia dell'altra o se hanno nomi identici.

### <a name="example"></a>Esempio

```cpp
// locale_op_ne.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "German_Germany" );
   locale loc2( "German_Germany" );
   locale loc3( "English" );

   if ( loc1 != loc2 )
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc2 (" << loc2.name( ) << ") are not equal." << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc2 (" << loc2.name( ) << ") are equal." << endl;

   if ( loc1 != loc3 )
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc3 (" << loc3.name( ) << ") are not equal." << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc3 (" << loc3.name( ) << ") are equal." << endl;
}
```

```Output
locales loc1 (German_Germany.1252) and
loc2 (German_Germany.1252) are equal.
locales loc1 (German_Germany.1252) and
loc3 (English_United States.1252) are not equal.
```

## <a name="localeoperator"></a><a name="op_call"></a>locale::operator()

Confronta due oggetti `basic_string`.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator()(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right) const;
```

### <a name="parameters"></a>Parametri

*Sinistra*\
Stringa sinistra.

*va bene*\
Stringa destra.

### <a name="return-value"></a>Valore restituito

La funzione membro restituisce:

- - 1 se la prima sequenza ottiene un risultato inferiore nel confronto con la seconda sequenza.

- +1 se la seconda sequenza ottiene un risultato inferiore nel confronto con la prima sequenza.

- 0 se le sequenze sono equivalenti.

### <a name="remarks"></a>Osservazioni

La funzione membro gestisce in modo efficace quanto segue:

```cpp
const collate<CharType>& fac = use_fac<collate<CharType>>(*this);

return (fac.compare(left.begin(), left.end(), right.begin(), right.end()) < 0);
```

Ciò significa che è possibile utilizzare un oggetto impostazioni locali come oggetto funzione.

### <a name="example"></a>Esempio

```cpp
// locale_op_compare.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

int main( )
{
   using namespace std;
   wchar_t *sa = L"ztesting";
   wchar_t *sb = L"\0x00DFtesting";
   basic_string<wchar_t> a( sa );
   basic_string<wchar_t> b( sb );

   locale loc( "German_Germany" );
   cout << loc( a,b ) << endl;

   const collate<wchar_t>& fac = use_facet<collate<wchar_t> >( loc );
   cout << ( fac.compare( sa, sa + a.length( ),
       sb, sb + b.length( ) ) < 0) << endl;
}
```

```Output
0
0
```

## <a name="localeoperator"></a><a name="op_eq_eq"></a>locale::operatore

Verifica l'uguaglianza di due impostazioni locali.

```cpp
bool operator==(const locale& right) const;
```

### <a name="parameters"></a>Parametri

*va bene*\
Una delle impostazioni locali di cui verificare l'uguaglianza.

### <a name="return-value"></a>Valore restituito

Valore booleano che è **true** se le impostazioni locali sono copie delle stesse impostazioni locali. È **false** se le impostazioni locali non sono copie delle stesse impostazioni locali.

### <a name="remarks"></a>Osservazioni

Due impostazioni locali sono uguali se sono le stesse impostazioni locali, se una è una copia dell'altra o se hanno nomi identici.

### <a name="example"></a>Esempio

```cpp
// locale_op_eq.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "German_Germany" );
   locale loc2( "German_Germany" );
   locale loc3( "English" );

   if ( loc1 == loc2 )
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc2 (" << loc2.name( ) << ") are equal."
      << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc2 (" << loc2.name( ) << ") are not equal."
      << endl;

   if ( loc1 == loc3 )
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc3 (" << loc3.name( ) << ") are equal."
      << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc3 (" << loc3.name( ) << ") are not equal."
      << endl;
}
```

```Output
locales loc1 (German_Germany.1252)
and loc2 (German_Germany.1252) are equal.
locales loc1 (German_Germany.1252)
and loc3 (English_United States.1252) are not equal.
```

## <a name="see-also"></a>Vedere anche

[\<>delle impostazioni locali](../standard-library/locale.md)\
[Tabelle codici](../c-runtime-library/code-pages.md)\
[Nomi delle impostazioni locali, lingue e stringhe di paese/area geografica](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[Sicurezza dei filettatura nella libreria standard di C](../standard-library/thread-safety-in-the-cpp-standard-library.md)
