---
title: Più classi base
ms.date: 11/19/2018
helpviewer_keywords:
- base classes [C++], multiple
- derived classes [C++], multiple bases
- multiple inheritance, class declaration
- multiple base classes [C++]
ms.assetid: a30c69fe-401c-4a87-96a0-e0da70c7c740
ms.openlocfilehash: 7cac70da5dd7093ce3e9c1cf3d2350d780c6b391
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353725"
---
# <a name="multiple-base-classes"></a>Più classi base

Una classe può essere derivata da più di una classe base. In un modello a ereditarietà multipla (in cui le classi derivano da più di una classe di base), le classi di base vengono specificate utilizzando l'elemento di grammatica *dell'elenco* di base. Ad esempio, la dichiarazione di classe per `CollectionOfBook`, derivata da `Collection` e `Book`, può essere specificata come segue:

```cpp
// deriv_MultipleBaseClasses.cpp
// compile with: /LD
class Collection {
};
class Book {};
class CollectionOfBook : public Book, public Collection {
    // New members
};
```

L'ordine in cui vengono specificate le classi base non è significativo, tranne in alcuni casi, quando vengono richiamati i costruttori e i distruttori. In questi casi, l'ordine in cui le classi base vengono specificate influisce su quanto segue:

- L'ordine con cui viene eseguita l'inizializzazione per costruttore. Se il codice si basa sul presupposto che la parte `Book` di `CollectionOfBook` sia inizializzata prima della parte `Collection`, l'ordine di specifica è significativo. L'inizializzazione viene eseguita nell'ordine in cui le classi sono specificate *nell'elenco di base*.

- L'ordine con cui vengono richiamati i distruttori per eseguire la pulizia. Anche in questo caso, se una "parte" specifica della classe deve essere presente mentre l'altra parte viene eliminata definitivamente, l'ordine è significativo. I distruttori vengono chiamati nell'ordine inverso delle classi specificate *nell'elenco di base*.

    > [!NOTE]
    >  L'ordine di specifica delle classi base può influire sul layout di memoria della classe. Non prendere decisioni relative alla programmazione in base all'ordine dei membri base nella memoria.

Quando si specifica *l'elenco di base*, non è possibile specificare più di una volta lo stesso nome di classe. Tuttavia, è possibile che una classe costituisca più volte una base indiretta per una classe derivata.

## <a name="virtual-base-classes"></a>Classi di base virtuali

Poiché una classe può rappresentare più di una volta una classe base indiretta per una classe derivata, in C++ è possibile ottimizzare l'utilizzo di tali classi base. Le classi base virtuali consentono di risparmiare spazio e di evitare ambiguità in gerarchie di classi in cui viene utilizzata l'ereditarietà multipla.

Ogni oggetto non virtuale contiene una copia dei membri dati definiti nella classe base. Questa duplicazione determina uno spreco di spazio e richiede di specificare la copia dei membri della classe base desiderata ogni volta che vi si accede.

Quando una classe base viene specificata come base virtuale, può essere utilizzata più volte come base indiretta senza duplicazione dei membri dati. Una sola copia dei membri dati viene condivisa da tutte le classi base che la utilizzano come base virtuale.

Quando si dichiara una classe base virtuale, la parola chiave **virtual** viene visualizzata negli elenchi di base delle classi derivate.

Si consideri la gerarchia di classi nella figura seguente, che illustra un oggetto Lunch-Line simulato.

![Rappresentazione grafica di oggetto Lunch-Line simulato](../cpp/media/vc38xp1.gif "Rappresentazione grafica di oggetto Lunch-Line simulato") <br/>
Simulazione del grafico a linee del pranzo

Nella figura `Queue` è la classe base sia per `CashierQueue` che per `LunchQueue`. Tuttavia, quando entrambe le classi vengono combinate per formare `LunchCashierQueue`, si verifica il problema seguente: la nuova classe contiene due oggetti secondari di tipo `Queue`, uno da `CashierQueue` e l'altro da `LunchQueue`. Nella figura seguente viene illustrato il layout di memoria concettuale (il layout di memoria effettivo può essere ottimizzato).

![Simulazione dell'oggetto&#45;di linee per il pranzo](../cpp/media/vc38xp2.gif "Simulazione dell'oggetto&#45;di linee per il pranzo") <br/>
Oggetto Lunch-Line simulato

Si noti che sono presenti due oggetti secondari `Queue` nell'oggetto `LunchCashierQueue`. Nel codice seguente `Queue` viene dichiarato come una classe base virtuale:

```cpp
// deriv_VirtualBaseClasses.cpp
// compile with: /LD
class Queue {};
class CashierQueue : virtual public Queue {};
class LunchQueue : virtual public Queue {};
class LunchCashierQueue : public LunchQueue, public CashierQueue {};
```

La parola chiave **virtual** garantisce che `Queue` sia inclusa una sola copia dell'oggetto secondario (vedere la figura seguente).

![Simulazione di pranzo&#45;oggetto linea, classi base virtuali](../cpp/media/vc38xp3.gif "Simulazione di pranzo&#45;oggetto linea, classi base virtuali") <br/>
Oggetto lunch-line simulato con classi base virtuali

Alla classe possono essere associati sia un componente virtuale che uno non virtuale di un tipo specifico. Ciò si verifica in condizioni illustrate nella figura seguente.

![Componenti virtuali e non virtuali di una classeVirtual and non&#45;virtual components of a class](../cpp/media/vc38xp4.gif "Componenti virtuali e non virtuali di una classeVirtual and non&#45;virtual components of a class") <br/>
Componenti virtuali e non virtuali della stessa classe

Nella figura `CashierQueue` e `LunchQueue` usano `Queue` come classe base virtuale. Tuttavia, `TakeoutQueue` specifica `Queue` come classe base, non come classe base virtuale. Di conseguenza, `LunchTakeoutCashierQueue` dispone di due oggetti secondari di tipo `Queue`: uno dal percorso di ereditarietà che include `LunchCashierQueue` e uno dal percorso che include `TakeoutQueue`. Questa situazione viene illustrata nella figura seguente.

![Ereditarietà virtuale virtuale & virtuale nel layout di oggettoVirtual & non&#45;virtual inheritance in object layout](../cpp/media/vc38xp5.gif "Ereditarietà virtuale virtuale & virtuale nel layout di oggettoVirtual & non&#45;virtual inheritance in object layout") <br/>
Layout degli oggetti con ereditarietà virtuale e non virtualeObject layout with virtual and non-virtual inheritance

> [!NOTE]
> L'ereditarietà virtuale offre vantaggi significativi in termini di dimensione se paragonata all'ereditarietà non virtuale. Può introdurre tuttavia un ulteriore sovraccarico di elaborazione.

Se una classe derivata esegue l'override di una funzione virtuale che eredita da una classe base virtuale e se un costruttore o un distruttore per la classe base derivata chiama tale funzione utilizzando un puntatore alla classe base virtuale, il compilatore può introdurre campi vtordisp nelle classi con basi virtuali. L'opzione `/vd0` del compilatore elimina l'aggiunta del membro nascosto di spostamento costruttore/distruttore vtordisp. L'opzione `/vd1` del compilatore, l'impostazione predefinita, li abilita dove sono necessari. Disattivare vtordisps solo se si è certi che tutti i costruttori e distruttori di classe chiamino virtualmente le funzioni virtuali.

L'opzione `/vd` del compilatore influisce su un intero modulo di compilazione. Utilizzare `vtordisp` il pragma per sopprimere e quindi riattivare i `vtordisp` campi in base alla classe:

```cpp
#pragma vtordisp( off )
class GetReal : virtual public { ... };
\#pragma vtordisp( on )
```

## <a name="name-ambiguities"></a>Ambiguità di nomi

L'ereditarietà multipla introduce la possibilità che i nomi vengano ereditati attraverso più di un percorso. In tali percorsi, i nomi dei membri di classe non sono necessariamente univoci. Questi conflitti di nomi sono denominati "ambiguità."

Qualsiasi espressione che fa riferimento a un membro di classe deve creare un riferimento non ambiguo. Nell'esempio che segue viene illustrato come si sviluppano le ambiguità:

```cpp
// deriv_NameAmbiguities.cpp
// compile with: /LD
// Declare two base classes, A and B.
class A {
public:
    unsigned a;
    unsigned b();
};

class B {
public:
    unsigned a();  // Note that class A also has a member "a"
    int b();       //  and a member "b".
    char c;
};

// Define class C as derived from A and B.
class C : public A, public B {};
```

Date le dichiarazioni di classe precedenti, un codice come il seguente è ambiguo, perché non è chiaro se `b` faccia riferimento alla `b` presente in `A` o in `B`:

```cpp
C *pc = new C;

pc->b();
```

Se consideri l'esempio precedente. Poiché il nome `a` è un membro di entrambe le classi `A` e `B`, il compilatore non è in grado di discernere quale `a` definisce la funzione da chiamare. L'accesso a un membro è ambiguo se può fare riferimento a più funzioni, oggetti, tipi o enumeratori.

Il compilatore rileva le ambiguità eseguendo dei test nell'ordine seguente:

1. Se l'accesso al nome è ambiguo, secondo quanto appena descritto, viene generato un messaggio di errore.

1. Se le funzioni in overload non sono ambigue, vengono risolte.

1. Se l'accesso al nome viola le autorizzazioni di accesso ai membri, viene generato un messaggio di errore. Per ulteriori informazioni, vedere [Controllo di accesso ai](../cpp/member-access-control-cpp.md)membri.

Quando un'espressione produce ambiguità attraverso l'ereditarietà, è possibile risolverla manualmente qualificando il nome in questione con il relativo nome di classe. Per fare in modo che l'esempio precedente venga compilato correttamente e senza ambiguità, utilizzare codice analogo al seguente:

```cpp
C *pc = new C;

pc->B::a();
```

> [!NOTE]
> Quando `C` viene dichiarata, è possibile che la stessa generi errori, quando si fa riferimento a `B` nell'ambito di `C`. In ogni caso, fino a quando un riferimento non qualificato a `B` non venga effettivamente utilizzato nell'ambito di `C`, non viene generato alcun errore.

### <a name="dominance"></a>Dominanza

È possibile che più nomi (funzione, oggetto o enumeratore) vengano raggiunti mediante un grafico di ereditarietà. Questi casi sono considerati ambigui con le classi base non virtuali. Sono anche ambigui con le classi base virtuali, a meno che uno dei nomi "domini" sugli altri.

Un nome domina un altro nome se è definito in entrambe le classi e una classe è derivata dall'altra. Il nome dominante è il nome nella classe derivata; questo nome viene utilizzato quando sarebbe altrimenti sorta una certa ambiguità, come mostrato nell'esempio seguente:

```cpp
// deriv_Dominance.cpp
// compile with: /LD
class A {
public:
    int a;
};

class B : public virtual A {
public:
    int a();
};

class C : public virtual A {};

class D : public B, public C {
public:
    D() { a(); } // Not ambiguous. B::a() dominates A::a.
};
```

### <a name="ambiguous-conversions"></a>Conversioni ambigue

Le conversioni esplicite e implicite da puntatori o riferimenti ai tipi di classe possono causare ambiguità. Nella figura seguente, conversione ambigua dei puntatori alle classi base, viene illustrato quanto segue:

- Dichiarazione di un oggetto di tipo `D`.

- Effetto dell'applicazione dell'operatore**&** address-of ( ) a tale oggetto. Si noti che l'operatore address-of fornisce sempre l'indirizzo di base dell'oggetto.

- Effetto della conversione esplicita del puntatore ottenuto usando l'operatore address-of in un tipo `A` della classe base. Si noti che l'assegnazione dell'indirizzo dell'oggetto al tipo `A*` non fornisce sempre il compilatore con informazioni sufficienti come quale oggetto secondario di tipo `A` è da selezionare; in questo caso, esistono due oggetti secondari.

![Conversione ambigua di puntatori a classi di base](../cpp/media/vc38xt1.gif "Conversione ambigua di puntatori a classi di base") <br/>
Conversione ambigua di puntatori a classi di base

La conversione nel tipo `A*` (puntatore a `A`) è ambigua poiché non è possibile discernere quale oggetto secondario di tipo `A` è quello corretto. Si noti che è possibile evitare l'ambiguità in modo esplicito specificando quale oggetto secondario si intende usare, come segue:

```cpp
(A *)(B *)&d       // Use B subobject.
(A *)(C *)&d       // Use C subobject.
```

### <a name="ambiguities-and-virtual-base-classes"></a>Ambiguità e classi base virtuali

Se si usano le classi base virtuali, è possibile passare a funzioni, oggetti, tipi ed enumeratori mediante i percorsi di ereditarietà multipla. Poiché è disponibile una sola istanza della classe base, non esiste ambiguità quando si accede a questi nomi.

La figura seguente mostra come vengono composti gli oggetti mediante l'ereditarietà virtuale e non virtuale.

![Derivazione virtuale e derivazione virtuale non&#45;](../cpp/media/vc38xr1.gif "Derivazione virtuale e derivazione virtuale non&#45;") <br/>
Derivazione virtuale e non virtuale

Nella figura l'accesso a qualsiasi membro della classe `A` tramite le classi base non virtuali causa ambiguità; il compilatore non dispone di informazioni che spieghino se utilizzare l'oggetto secondario associato a `B` o l'oggetto secondario associato a `C`. Tuttavia, quando `A` è specificato come classe base virtuale, non esiste alcuna ambiguità sull'oggetto secondario a cui viene eseguito l'accesso.

## <a name="see-also"></a>Vedere anche

[Ereditarietà](../cpp/inheritance-cpp.md)
