---
title: Spazi dei nomi (C++)
ms.date: 08/30/2017
f1_keywords:
- namespace_CPP
- using_CPP
helpviewer_keywords:
- namespaces [C++]
ms.assetid: d1a5a9ab-1cad-47e6-a82d-385bb77f4188
ms.openlocfilehash: 4957ec5a5face860d2e39861eddc8f7e5abe9370
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367906"
---
# <a name="namespaces-c"></a>Spazi dei nomi (C++)

Uno spazio dei nomi è un'area dichiarativa che fornisce un ambito per gli identificatori (nomi di tipi, funzioni, variabili e così via) al suo interno. Gli spazi dei nomi vengono usati per organizzare il codice in gruppi logici e per evitare conflitti tra nomi, che si possono verificare in particolare quando la codebase include più librerie. Tutti gli identificatori nell'ambito dello spazio dei nomi sono visibili tra loro senza qualifica. Gli identificatori esterni allo spazio dei nomi possono accedere ai `std::vector<std::string> vec;`membri utilizzando il nome completo per`using std::string`ogni identificatore, ad esempio , oppure tramite una [dichiarazione using](../cpp/using-declaration.md) per un singolo identificatore ( ) o una [direttiva using](../cpp/namespaces-cpp.md#using_directives) per tutti gli identificatori nello spazio dei nomi (`using namespace std;`). È consigliabile che il codice nel file di intestazione usi sempre il nome completo dello spazio dei nomi.

L'esempio seguente illustra una dichiarazione dello spazio dei nomi e tre modi in cui il codice esterno allo spazio dei nomi può accedere ai rispettivi membri.

```cpp
namespace ContosoData
{
    class ObjectManager
    {
    public:
        void DoSomething() {}
    };
    void Func(ObjectManager) {}
}
```

Mediante il nome completo:

```cpp
ContosoData::ObjectManager mgr;
mgr.DoSomething();
ContosoData::Func(mgr);
```

Mediante una dichiarazione using  per portare nell'ambito un identificatore:

```cpp
using ContosoData::ObjectManager;
ObjectManager mgr;
mgr.DoSomething();
```

Mediante una direttiva using per portare nell'ambito qualsiasi elemento dello spazio dei nomi:

```cpp
using namespace ContosoData;

ObjectManager mgr;
mgr.DoSomething();
Func(mgr);
```

## <a name="using-directives"></a><a id="using_directives"></a>utilizzando le direttive

La direttiva **using** consente di utilizzare tutti i nomi in uno **spazio dei nomi** senza *namespace-name* come qualificatore esplicito. Utilizzare una direttiva using in un file di implementazione (ad esempio, con estensione cpp) se si utilizzano diversi identificatori diversi in uno spazio dei nomi. Se si usano solo uno o due identificatori, prendere in considerazione una dichiarazione using per inserire solo tali identificatori nell'ambito e non tutti gli identificatori nello spazio dei nomi. Se una variabile locale ha lo stesso nome di una variabile dello spazio dei nomi, quest'ultima è nascosta. Se una variabile dello spazio dei nomi ha lo stesso nome di una variabile globale, viene generato un errore.

> [!NOTE]
> È possibile posizionare una direttiva using all'inizio di un file con estensione cpp (nell'ambito del file) o all'interno di una definizione di classe o di funzione.
>
> In genere, è consigliabile evitare di inserire le direttive using nei file di intestazione (*.h), poiché qualsiasi file che include l'intestazione porterà nell'ambito tutti gli elementi dello spazio dei nomi e ciò può provocare problemi di nomi nascosti e conflitti tra i nomi, il cui debug è molto difficile. Usare sempre nomi qualificati in un file di intestazione. Se tali nomi risultano troppo lunghi, è possibile usare un alias di spazio dei nomi per abbreviarli, come illustrato più avanti.

## <a name="declaring-namespaces-and-namespace-members"></a>Dichiarazione di spazi dei nomi e di membri dello spazio dei nomi

In genere, si dichiara uno spazio dei nomi in un file di intestazione. Se le implementazioni delle funzioni si trovano in un file separato, qualificare i nomi delle funzioni, come illustrato in questo esempio.

```cpp
//contosoData.h
#pragma once
namespace ContosoDataServer
{
    void Foo();
    int Bar();
}
```

Le implementazioni di funzioni in contosodata.cpp devono utilizzare il nome completo, anche se si inserisce una direttiva **using** all'inizio del file:

```cpp
#include "contosodata.h"
using namespace ContosoDataServer;

void ContosoDataServer::Foo() // use fully-qualified name here
{
   // no qualification needed for Bar()
   Bar();
}

int ContosoDataServer::Bar(){return 0;}
```

Uno spazio dei nomi può essere dichiarato in più blocchi di un singolo file e in più file. Il compilatore riunisce le parti durante la pre-elaborazione e lo spazio dei nomi risultante include tutti i membri dichiarati in tutte le parti. Un esempio è costituito dallo spazio dei nomi std, dichiarato in ogni file di intestazione della libreria standard.

I membri di uno spazio dei nomi possono essere definiti all'esterno dello spazio dei nomi in cui sono dichiarati da qualifica esplicita del nome definito. La definizione deve tuttavia apparire dopo la posizione della dichiarazione di uno spazio dei nomi che racchiude lo spazio dei nomi della dichiarazione stessa. Ad esempio:

```cpp
// defining_namespace_members.cpp
// C2039 expected
namespace V {
    void f();
}

void V::f() { }        // ok
void V::g() { }        // C2039, g() is not yet a member of V

namespace V {
    void g();
}
```

Questo errore si può verificare quando i membri dello spazio dei nomi vengono dichiarati in più file di intestazione e tali intestazioni non sono state incluse nell'ordine corretto.

## <a name="the-global-namespace"></a>Spazio dei nomi globale

Se un identificatore non viene dichiarato in uno spazio dei nomi esplicito, farà parte dello spazio dei nomi globale implicito. In generale, cercare di evitare di eseguire dichiarazioni in ambito globale quando possibile, ad eccezione del punto di ingresso [main Function](../c-language/main-function-and-program-execution.md), che deve essere nello spazio dei nomi globale. Per qualificare in modo esplicito un identificatore globale, usare l'operatore di risoluzione dell'ambito senza nome, ad esempio `::SomeFunction(x);`. Ciò permetterà di contraddistinguere l'identificatore da eventuali elementi con lo stesso nome in qualsiasi altro spazio dei nomi e semplificherà anche la comprensione del codice da parte di altri utenti.

## <a name="the-std-namespace"></a>Spazio dei nomi standard

Tutti i tipi di libreria standard e `std` le funzioni di `std`C, vengono dichiarati nello spazio dei nomi o negli spazi dei nomi annidati all'interno di .

## <a name="nested-namespaces"></a>Spazi dei nomi annidati

Gli spazi dei nomi possono essere annidati. Uno spazio dei nomi annidato ordinario ha accesso non qualificato ai membri del padre, ma i membri padre non hanno accesso non qualificato allo spazio dei nomi annidato (a meno che non sia dichiarato come inline), come illustrato nell'esempio seguente:An ordinary nested namespace has unqualified access to its parent's members, but the parent members do not have unqualified access to the nested namespace (unless it is declared as inline), as shown in the following example:

```cpp
namespace ContosoDataServer
{
    void Foo();

    namespace Details
    {
        int CountImpl;
        void Ban() { return Foo(); }
    }

    int Bar(){...};
    int Baz(int i) { return Details::CountImpl; }
}
```

Gli spazi dei nomi annidati normali possono essere usati per incapsulare dettagli di implementazione interni, che non fanno parte dell'interfaccia pubblica dello spazio dei nomi padre.

## <a name="inline-namespaces-c-11"></a>Spazi dei nomi inline (C++ 11)

A differenza di uno spazio dei nomi annidato normale, i membri di uno spazio dei nomi inline vengono considerati come membri dello spazio dei nomi padre. Questa caratteristica permette il funzionamento della ricerca dipendente dall'argomento su funzioni con overload per funzioni con overload in uno spazio dei nomi padre e in uno spazio dei nomi inline annidato. Permette anche di dichiarare una specializzazione in uno spazio dei nomi padre per un modello dichiarato nello spazio dei nomi inline. L'esempio seguente illustra il modo in cui viene eseguito il binding di codice esterno allo spazio dei nomi inline per impostazione predefinita:

```cpp
//Header.h
#include <string>

namespace Test
{
    namespace old_ns
    {
        std::string Func() { return std::string("Hello from old"); }
    }

    inline namespace new_ns
    {
        std::string Func() { return std::string("Hello from new"); }
    }
}

#include "header.h"
#include <string>
#include <iostream>

int main()
{
    using namespace Test;
    using namespace std;

    string s = Func();
    std::cout << s << std::endl; // "Hello from new"
    return 0;
}
```

L'esempio seguente illustra come dichiarare una specializzazione nel padre di un modello dichiarato in uno spazio dei nomi inline:

```cpp
namespace Parent
{
    inline namespace new_ns
    {
         template <typename T>
         struct C
         {
             T member;
         };
    }
     template<>
     class C<int> {};
}
```

È possibile usare gli spazi dei nomi inline come meccanismo di controllo delle versioni per gestire le modifiche all'interfaccia pubblica di una libreria. Ad esempio, è possibile creare un singolo spazio dei nomi padre e incapsulare ogni versione dell'interfaccia nel proprio spazio dei nomi annidato nel padre. Lo spazio dei nomi che include la versione più recente o preferita viene qualificato come inline e viene quindi esposto come se fosse un membro diretto dello spazio dei nomi padre. Il codice client che richiama Parent::Class verrà associato automaticamente al nuovo codice. I client che preferiscono usare la versione meno recente potranno comunque accedere a tale versione usando il percorso completo per lo spazio dei nomi annidato che include il codice corrispondente.

La parola chiave inline deve essere applicata alla prima dichiarazione dello spazio dei nomi in un'unità di compilazione.

L'esempio seguente illustra due versioni di un'interfaccia, ognuna in uno spazio dei nomi annidato. Lo spazio dei nomi `v_20` presenta alcune modifiche rispetto all'interfaccia `v_10` ed è contrassegnato come inline. Il codice client che usa la nuova libreria e chiama `Contoso::Funcs::Add` richiamerà la versione v_20. Il codice che tenta di chiamare `Contoso::Funcs::Divide` otterrà ora un errore in fase di compilazione. Se tale funzione è davvero necessaria, sarà comunque possibile accedere alla versione `v_10` chiamando esplicitamente `Contoso::v_10::Funcs::Divide`.

```cpp
namespace Contoso
{
    namespace v_10
    {
        template <typename T>
        class Funcs
        {
        public:
            Funcs(void);
            T Add(T a, T b);
            T Subtract(T a, T b);
            T Multiply(T a, T b);
            T Divide(T a, T b);
        };
    }

    inline namespace v_20
    {
        template <typename T>
        class Funcs
        {
        public:
            Funcs(void);
            T Add(T a, T b);
            T Subtract(T a, T b);
            T Multiply(T a, T b);
            std::vector<double> Log(double);
            T Accumulate(std::vector<T> nums);
      };
    }
}
```

## <a name="namespace-aliases"></a><a id="namespace_aliases"></a>Alias dello spazio dei nomiNamespace aliases

I nomi degli spazi dei nomi devono essere univoci e ciò significa che spesso non sono molto brevi. Se la lunghezza di un nome rende il codice difficile da leggere o è noioso digitare in un file di intestazione in cui le direttive using non possono essere utilizzate, è possibile creare un alias dello spazio dei nomi che funge da abbreviazione per il nome effettivo. Ad esempio:

```cpp
namespace a_very_long_namespace_name { class Foo {}; }
namespace AVLNN = a_very_long_namespace_name;
void Bar(AVLNN::Foo foo){ }
```

## <a name="anonymous-or-unnamed-namespaces"></a>Spazi dei nomi anonimi o senza nome

È possibile creare uno spazio dei nomi esplicito ma non specificare un nome per tale spazio dei nomi:

```cpp
namespace
{
    int MyFunc(){}
}
```

Questo è chiamato uno spazio dei nomi anonimo o senza nome ed è utile quando si desidera rendere le dichiarazioni di variabili invisibili al codice in altri file (ad esempio, fornire loro collegamento interno) senza dover creare uno spazio dei nomi denominato. Tutto il codice nello stesso file può vedere gli identificatori in uno spazio dei nomi senza nome, ma gli identificatori, insieme allo spazio dei nomi stesso, non sono visibili all'esterno di tale file o, più precisamente, all'esterno dell'unità di conversione.

## <a name="see-also"></a>Vedere anche

[Dichiarazioni e definizioni](declarations-and-definitions-cpp.md)
