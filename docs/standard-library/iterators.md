---
title: Iterators
ms.date: 11/04/2016
helpviewer_keywords:
- iterator conventions
- C++ Standard Library, iterator conventions
ms.assetid: 2f746be7-b37d-4bfc-bf05-be4336ca982f
ms.openlocfilehash: ec23cbea63bc6884a361600362fcf0061e927ca6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449967"
---
# <a name="iterators"></a>Iterators

Un iteratore è un oggetto in grado di eseguire l'iterazione sugli elementi di un contenitore della libreria standard C++ e fornire accesso ai singoli elementi. Tutti i contenitori della libreria standard C++ forniscono iteratori che consentono agli algoritmi di accedere ai relativi elementi in maniera standard, senza doversi preoccupare del tipo di contenitore in cui sono archiviati gli elementi.

È possibile utilizzare gli iteratori in modo esplicito utilizzando i membri e `begin()` le `end()` funzioni globali, ad **++** esempio **--** gli operatori e e come e per spostarsi avanti o indietro. È anche possibile usare gli iteratori in modo implicito con un ciclo range-for o (per alcuni tipi di iteratore  **\[** ) l'operatore di indice].

Nella libreria standard C++ l'inizio di una sequenza o di un intervallo corrisponde al primo elemento. La fine di una sequenza o di un intervallo è sempre definita come un elemento dopo l'ultimo elemento. Funzioni `begin` globali e `end` restituiscono iteratori a un contenitore specificato. Il ciclo iteratore esplicito standard su tutti gli elementi in un contenitore è simile al seguente:

```cpp
vector<int> vec{ 0,1,2,3,4 };
for (auto it = begin(vec); it != end(vec); it++)
{
    // Access element using dereference operator
    cout << *it << " ";
}
```

La stessa operazione può essere eseguita in modo più semplice con un ciclo range-for:

```cpp
for (auto num : vec)
{
    // no deference operator
    cout << num << " ";
}
```

Le categorie di iteratori disponibili sono cinque. Per la potenza, le categorie sono riepilogate in ordine crescente come:

- **Output**. Un *iteratore* `X` di output può eseguire l'iterazione su una **++** sequenza usando l'operatore e può scrivere un elemento una sola volta usando __\*__ l'operatore.

- **Input**. Un *iteratore* `X` di input può scorrere in un secondo momento su una sequenza usando l'operatore + + e può leggere un elemento per un numero qualsiasi **&ast;** di volte usando l'operatore. È possibile confrontare gli iteratori di input usando **++** gli operatori and **! =** . Dopo aver incrementato qualsiasi copia di un iteratore di input, non sarà possibile confrontare, dereferenziare o incrementare nessuna delle altre copie in modo sicuro.

- **In avanti**. Un *iteratore* `X` in poi può eseguire l'iterazione su una sequenza usando l'operatore + + ed è in grado di leggere qualsiasi elemento o scrivere elementi non const **&ast;** un numero qualsiasi di volte usando l'operatore. È possibile accedere ai membri degli elementi usando **->** l'operatore e confrontare gli iteratori in secondo **==** uso usando gli operatori and **! =** . È anche possibile eseguire più copie di un iteratore in avanti, ciascuna delle quali può essere dereferenziata e incrementata in modo indipendente. Un iteratore in in poi inizializzato senza riferimento a un contenitore viene chiamato *iteratore in in poi null*. Gli iteratori in avanti null risultano sempre uguali.

- **Bidirezionale**. Un *iteratore* `X` bidirezionale può prendere il posto di un iteratore in avanti. È tuttavia possibile decrementare anche un iteratore bidirezionale, come in `--X`, `X--`o `(V = *X--)`. È possibile accedere ai membri degli elementi e confrontare gli iteratori bidirezionali nello stesso modo degli iteratori in avanti.

- **Accesso casuale**. `X` Un *iteratore ad accesso casuale* può prendere il posto di un iteratore bidirezionale. Con un iteratore di accesso casuale è possibile usare l'operatore  **\[** di indice] per accedere agli elementi. È possibile utilizzare gli **+** operatori **-** **+=** , e **-=** per spostarsi in avanti o indietro di un numero specificato di elementi e per calcolare la distanza tra gli iteratori. È possibile confrontare gli iteratori bidirezionali usando **==** , **! =** , **\<** , **>** , **\< =** e. **>=**

Tutti gli iteratori possono essere assegnati o copiati. Si presuppone che si tratti di oggetti semplici, spesso passati e restituiti per valore, non per riferimento. Si noti anche che nessuna delle operazioni descritte in precedenza può generare un'eccezione quando viene eseguita su un iteratore valido.

La gerarchia di categorie di iteratore può essere riepilogata mostrando tre sequenze. Per accedere a una sequenza in sola scrittura, è possibile usare:

> iteratore di output \
> -> iteratore in poi \
> -> iteratore bidirezionale \
> -> iteratore ad accesso casuale

La freccia destra significa "può essere sostituito da". Qualsiasi algoritmo che chiami un iteratore di output dovrebbe funzionare correttamente, ad esempio, con un iteratore in avanti, ma *non* viceversa.

Per eseguire l'accesso di sola lettura a una sequenza, è possibile usare:

> iteratore di input \
> -> iteratore in poi \
> -> iteratore bidirezionale \
> -> iteratore ad accesso casuale

In questo caso, un iteratore di input è il più debole di tutte le categorie.

Infine, per accedere a una sequenza in lettura/scrittura, è possibile usare:

> iteratore in poi \
> -> iteratore bidirezionale \
> -> iteratore ad accesso casuale

Un puntatore a oggetto può sempre fungere da iteratore ad accesso casuale, quindi può essere usato come qualsiasi categoria di iteratore se supporta l'accesso corretto in lettura/scrittura alla sequenza che definisce.

Un iteratore `Iterator` diverso da un puntatore all'oggetto deve anche definire i tipi di membri necessari per la specializzazione `iterator_traits<Iterator>`. Si noti che questi requisiti possono essere soddisfatti derivando `Iterator` dalla classe di base pubblica [iterator](../standard-library/iterator-struct.md).

È importante comprendere le caratteristiche e le limitazioni di ogni categoria di iteratore per vedere come gli iteratori vengono usati dai contenitori e dagli algoritmi della libreria standard C++.

> [!NOTE]
> È possibile evitare l'utilizzo di iteratori in modo esplicito utilizzando cicli range-for. Per altre informazioni, vedere [istruzione for basata sull'intervallo](../cpp/range-based-for-statement-cpp.md).

Microsoft C++ ora offre iteratori verificati e iteratori di debug per assicurarsi di non sovrascrivere i limiti del contenitore. Per altre informazioni, vedere [Iteratori verificati](../standard-library/checked-iterators.md) e [Supporto degli iteratori di debug](../standard-library/debug-iterator-support.md).

## <a name="see-also"></a>Vedere anche

[Riferimento per la libreria standard C++](../standard-library/cpp-standard-library-reference.md)\
[Thread Safety nella libreria standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
