---
title: Classe concurrent_unordered_set
ms.date: 11/04/2016
f1_keywords:
- concurrent_unordered_set
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::concurrent_unordered_set
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::hash_function
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::insert
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::key_eq
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::swap
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::unsafe_erase
helpviewer_keywords:
- concurrent_unordered_set class
ms.assetid: c61f9a9a-4fd9-491a-9251-e300737ecf4b
ms.openlocfilehash: 0671a3c1996ca85a9c2cf5a386821c3d52c1bf50
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143149"
---
# <a name="concurrent_unordered_set-class"></a>Classe concurrent_unordered_set

La classe `concurrent_unordered_set` è un contenitore indipendente dalla concorrenza che controlla una sequenza di lunghezza variabile di elementi di tipo K. La sequenza viene rappresentata in un modo che Abilita le operazioni di Accodamento, accesso elementi, accesso iteratori e attraversamento iteratori in modo indipendente dalla concorrenza. In tal caso, i puntatori o gli iteratori sono sempre validi. Non si tratta di una garanzia di inizializzazione di elementi o di un ordine di attraversamento specifico.

## <a name="syntax"></a>Sintassi

```cpp
template <typename K,
    typename _Hasher = std::hash<K>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<K>
>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<K>> class concurrent_unordered_set : public details::_Concurrent_hash<details::_Concurrent_unordered_set_traits<K,
    details::_Hash_compare<K,
_Hasher,
    key_equality>,
_Allocator_type,
    false>>;
```

### <a name="parameters"></a>Parametri

*K*<br/>
Tipo di chiave.

*_Hasher*<br/>
Tipo di oggetto della funzione hash. Questo argomento è facoltativo e il valore predefinito è `std::hash<K>`.

*key_equality*<br/>
Tipo di oggetto della funzione di confronto di uguaglianza. Questo argomento è facoltativo e il valore predefinito è `std::equal_to<K>`.

*_Allocator_type*<br/>
Tipo che rappresenta l'oggetto allocatore archiviato che incapsula i dettagli relativi all'allocazione e alla deallocazione della memoria per il set non ordinato simultaneo. Questo argomento è facoltativo e il valore predefinito è `std::allocator<K>`.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedef pubblici

|Nome|Descrizione|
|----------|-----------------|
|`allocator_type`|Tipo di un allocatore per gestire l'archiviazione.|
|`const_iterator`|Tipo di un iteratore costante per la sequenza controllata.|
|`const_local_iterator`|Tipo di un iteratore di bucket costante per la sequenza controllata.|
|`const_pointer`|Tipo di un puntatore costante a un elemento.|
|`const_reference`|Tipo di un riferimento costante a un elemento.|
|`difference_type`|Tipo di una distanza Signed tra due elementi.|
|`hasher`|Tipo della funzione hash.|
|`iterator`|Tipo di un iteratore per la sequenza controllata.|
|`key_equal`|Tipo della funzione di confronto.|
|`key_type`|Tipo di una chiave di ordinamento.|
|`local_iterator`|Tipo di un iteratore di bucket per la sequenza controllata.|
|`pointer`|Tipo di un puntatore a un elemento.|
|`reference`|Tipo di un riferimento a un elemento.|
|`size_type`|Tipo di una distanza Unsigned tra due elementi.|
|`value_type`|Tipo di un elemento.|

### <a name="public-constructors"></a>Costruttori pubblici

|Nome|Descrizione|
|----------|-----------------|
|[concurrent_unordered_set](#ctor)|Di overload. Costruisce un set non ordinato simultaneo.|

### <a name="public-methods"></a>Metodi pubblici

|Nome|Descrizione|
|----------|-----------------|
|[hash_function](#hash_function)|Restituisce l'oggetto della funzione hash archiviato.|
|[insert](#insert)|Di overload. Aggiunge elementi all'oggetto `concurrent_unordered_set`.|
|[key_eq](#key_eq)|Restituisce l'oggetto della funzione di confronto di uguaglianza archiviato.|
|[swap](#swap)|Scambia il contenuto di due oggetti `concurrent_unordered_set`. Questo metodo non è indipendente dalla concorrenza.|
|[unsafe_erase](#unsafe_erase)|Di overload. Rimuove gli elementi dal `concurrent_unordered_set` nelle posizioni specificate. Questo metodo non è indipendente dalla concorrenza.|

### <a name="public-operators"></a>Operatori pubblici

|Nome|Descrizione|
|----------|-----------------|
|[operator=](#operator_eq)|Di overload. Assegna il contenuto di un altro `concurrent_unordered_set` oggetto a questo. Questo metodo non è indipendente dalla concorrenza.|

## <a name="remarks"></a>Osservazioni

Per informazioni dettagliate sulla classe `concurrent_unordered_set`, vedere [contenitori e oggetti paralleli](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà

`_Traits`

`_Concurrent_hash`

`concurrent_unordered_set`

## <a name="requirements"></a>Requisiti

**Intestazione:** concurrent_unordered_set. h

**Spazio dei nomi:** Concurrency

## <a name="begin"></a>iniziare

Restituisce un iteratore che punta al primo elemento nel contenitore simultaneo. Questo metodo è sicuro per la concorrenza.

```cpp
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>Valore restituito

Iteratore per il primo elemento nel contenitore simultaneo.

## <a name="cbegin"></a>cbegin

Restituisce un iteratore const che punta al primo elemento nel contenitore simultaneo. Questo metodo è sicuro per la concorrenza.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Valore restituito

Iteratore const al primo elemento nel contenitore simultaneo.

## <a name="cend"></a>cend

Restituisce un iteratore const che punta alla posizione successiva all'ultimo elemento nel contenitore simultaneo. Questo metodo è sicuro per la concorrenza.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Valore restituito

Iteratore const alla posizione successiva all'ultimo elemento nel contenitore simultaneo.

## <a name="clear"></a>deselezionare

Cancella tutti gli elementi nel contenitore simultaneo. Questa funzione non è sicura per la concorrenza.

```cpp
void clear();
```

## <a name="ctor"></a>concurrent_unordered_set

Costruisce un set non ordinato simultaneo.

```cpp
explicit concurrent_unordered_set(
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_set(
    const allocator_type& _Allocator);

template <typename _Iterator>
concurrent_unordered_set(_Iterator first,
    _Iterator last,
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_set(
    const concurrent_unordered_set& _Uset);

concurrent_unordered_set(
    const concurrent_unordered_set& _Uset,
    const allocator_type& _Allocator);

concurrent_unordered_set(
    concurrent_unordered_set&& _Uset);
```

### <a name="parameters"></a>Parametri

*_Iterator*<br/>
Tipo di iteratore di input.

*_Number_of_buckets*<br/>
Numero iniziale di bucket per questo set non ordinato.

*_Hasher*<br/>
Funzione hash per questo set non ordinato.

*key_equality*<br/>
Funzione di confronto di uguaglianza per questo set non ordinato.

*_Allocator*<br/>
Allocatore per questo set non ordinato.

*first*<br/>
*last*<br/>
*_Uset*<br/>
Oggetto `concurrent_unordered_set` di origine da cui copiare o spostare elementi.

### <a name="remarks"></a>Osservazioni

Tramite tutti i costruttori viene archiviato un oggetto allocatore `_Allocator` e viene inizializzato il set non ordinato.

Tramite il primo costruttore viene specificato un set iniziale vuoto e vengono indicati in modo esplicito il numero di bucket, la funzione hash, la funzione di uguaglianza e il tipo di allocatore da utilizzare.

Tramite il secondo costruttore viene specificato un allocatore per il set non ordinato.

Il terzo costruttore specifica i valori forniti dall'intervallo dell'iteratore [`_Begin`, `_End`).

Tramite il quarto e il quinto costruttore viene specificata una copia del set non ordinato simultaneo `_Uset`.

Tramite l'ultimo costruttore viene specificato uno spostamento del set non ordinato simultaneo `_Uset`.

## <a name="count"></a>conteggio

Conta il numero di elementi corrispondenti a una chiave specificata. Questa funzione è sicura per la concorrenza.

```cpp
size_type count(const key_type& KVal) const;
```

### <a name="parameters"></a>Parametri

*KVal*<br/>
Chiave da ricercare.

### <a name="return-value"></a>Valore restituito

Il numero di volte in cui la chiave viene visualizzata nel contenitore.

## <a name="empty"></a>vuoto

Verifica se sono presenti o meno degli elementi. Questo metodo è sicuro per la concorrenza.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valore restituito

**true** se il contenitore simultaneo è vuoto; in caso contrario, **false** .

### <a name="remarks"></a>Osservazioni

In presenza di inserimenti simultanei, se il contenitore simultaneo è vuoto può cambiare immediatamente dopo la chiamata a questa funzione, prima che venga letto anche il valore restituito.

## <a name="end"></a>fine

Restituisce un iteratore che punta alla posizione successiva all'ultimo elemento nel contenitore simultaneo. Questo metodo è sicuro per la concorrenza.

```cpp
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>Valore restituito

Un iteratore alla posizione successiva all'ultimo elemento nel contenitore simultaneo.

## <a name="equal_range"></a>equal_range

Trova un intervallo che corrisponde a una chiave specificata. Questa funzione è sicura per la concorrenza.

```cpp
std::pair<iterator,
    iterator> equal_range(
    const key_type& KVal);

std::pair<const_iterator,
    const_iterator> equal_range(
    const key_type& KVal) const;
```

### <a name="parameters"></a>Parametri

*KVal*<br/>
Valore chiave da cercare.

### <a name="return-value"></a>Valore restituito

Una [coppia](../../../standard-library/pair-structure.md) in cui il primo elemento è un iteratore all'inizio e il secondo elemento è un iteratore alla fine dell'intervallo.

### <a name="remarks"></a>Osservazioni

È possibile che gli inserimenti simultanei causino l'inserimento di chiavi aggiuntive dopo l'iteratore Begin e prima dell'iteratore finale.

## <a name="find"></a>trovare

Trova un elemento che corrisponde a una chiave specificata. Questa funzione è sicura per la concorrenza.

```cpp
iterator find(const key_type& KVal);

const_iterator find(const key_type& KVal) const;
```

### <a name="parameters"></a>Parametri

*KVal*<br/>
Valore chiave da cercare.

### <a name="return-value"></a>Valore restituito

Iteratore che punta alla posizione del primo elemento che corrisponde alla chiave fornita oppure l'iteratore `end()` se tale elemento non esiste.

## <a name="get_allocator"></a>get_allocator

Restituisce l'oggetto allocatore archiviato per il contenitore simultaneo. Questo metodo è sicuro per la concorrenza.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Valore restituito

Oggetto allocatore archiviato per il contenitore simultaneo.

## <a name="hash_function"></a>hash_function

Restituisce l'oggetto della funzione hash archiviato.

```cpp
hasher hash_function() const;
```

### <a name="return-value"></a>Valore restituito

Oggetto della funzione hash archiviato.

## <a name="insert"></a>inserire

Aggiunge elementi all'oggetto `concurrent_unordered_set`.

```cpp
std::pair<iterator,
    bool> insert(
    const value_type& value);

iterator insert(
    const_iterator _Where,
    const value_type& value);

template<class _Iterator>
void insert(_Iterator first,
    _Iterator last);

template<class V>
std::pair<iterator,
    bool> insert(
    V&& value);

template<class V>
typename std::enable_if<!std::is_same<const_iterator,
    typename std::remove_reference<V>::type>::value,
    iterator>::type insert(
    const_iterator _Where,
    V&& value);
```

### <a name="parameters"></a>Parametri

*_Iterator*<br/>
Tipo di iteratore utilizzato per l'inserimento.

*V*<br/>
Tipo del valore inserito nel set.

*value*<br/>
Valore da inserire.

*_Where*<br/>
Posizione iniziale in corrispondenza della quale cercare un punto di inserimento.

*first*<br/>
Inizio dell'intervallo da inserire.

*last*<br/>
Fine dell'intervallo da inserire.

### <a name="return-value"></a>Valore restituito

Coppia che contiene un iteratore e un valore booleano. Per altre informazioni, vedere le sezione Osservazioni.

### <a name="remarks"></a>Osservazioni

La prima funzione membro determina se un elemento X è presente nella sequenza la cui chiave ha un ordinamento equivalente a quella di `value`. In caso contrario, crea tale elemento X e lo inizializza con `value`. La funzione determina quindi l'iteratore `where` che designa X. Se si è verificato un inserimento, la funzione restituisce `std::pair(where, true)`. In caso contrario, viene restituito `std::pair(where, false)`.

La seconda funzione membro restituisce Insert (`value`), usando `_Where` come punto di partenza all'interno della sequenza controllata per cercare il punto di inserimento.

La terza funzione membro inserisce la sequenza di valori di elemento dall'intervallo [`first`, `last`).

Il comportamento delle ultime due funzioni membro è uguale a quello delle prime due, con la differenza che `value` viene utilizzato per costruire il valore inserito.

## <a name="key_eq"></a>key_eq

Restituisce l'oggetto della funzione di confronto di uguaglianza archiviato.

```cpp
key_equal key_eq() const;
```

### <a name="return-value"></a>Valore restituito

Oggetto della funzione di confronto di uguaglianza archiviato.

## <a name="load_factor"></a>load_factor

Calcola e restituisce il fattore di carico corrente del contenitore. Il fattore di carico è il numero di elementi nel contenitore diviso per il numero di bucket.

```cpp
float load_factor() const;
```

### <a name="return-value"></a>Valore restituito

Il fattore di carico per il contenitore.

## <a name="max_load_factor"></a>max_load_factor

Ottiene o imposta il fattore di carico massimo del contenitore. Il fattore di carico massimo è il maggior numero di elementi che possono essere presenti in qualsiasi bucket prima che il contenitore cresca la tabella interna.

```cpp
float max_load_factor() const;

void max_load_factor(float _Newmax);
```

### <a name="parameters"></a>Parametri

`_Newmax`

### <a name="return-value"></a>Valore restituito

La prima funzione membro restituisce il fattore di carico massimo archiviato. La seconda funzione membro non restituisce un valore, ma genera un'eccezione [out_of_range](../../../standard-library/out-of-range-class.md) se il fattore di carico fornito non è valido.

## <a name="max_size"></a>max_size

Restituisce la dimensione massima del contenitore simultaneo, determinato dall'allocatore. Questo metodo è sicuro per la concorrenza.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Valore restituito

Numero massimo di elementi che possono essere inseriti in questo contenitore simultaneo.

### <a name="remarks"></a>Osservazioni

Questo valore limite superiore può essere effettivamente superiore rispetto a quello che il contenitore può effettivamente contenere.

## <a name="operator_eq"></a>operatore =

Assegna il contenuto di un altro `concurrent_unordered_set` oggetto a questo. Questo metodo non è indipendente dalla concorrenza.

```cpp
concurrent_unordered_set& operator= (const concurrent_unordered_set& _Uset);

concurrent_unordered_set& operator= (concurrent_unordered_set&& _Uset);
```

### <a name="parameters"></a>Parametri

*_Uset*<br/>
Oggetto `concurrent_unordered_set` di origine.

### <a name="return-value"></a>Valore restituito

Riferimento a questo oggetto `concurrent_unordered_set`.

### <a name="remarks"></a>Osservazioni

Dopo l'eliminazione di tutti gli elementi esistenti in un set non ordinato simultaneo, tramite `operator=` il contenuto di `_Uset` viene copiato o spostato nel set non ordinato simultaneo.

## <a name="rehash"></a>rehash

Ricompila la tabella hash.

```cpp
void rehash(size_type _Buckets);
```

### <a name="parameters"></a>Parametri

*_Buckets*<br/>
Numero desiderato di bucket.

### <a name="remarks"></a>Osservazioni

La funzione membro modifica il numero di bucket in modo da essere almeno pari a `_Buckets` e ricompila la tabella hash in base alle esigenze. Il numero di bucket deve essere una potenza di 2. Se non è una potenza di 2, verrà arrotondata per eccesso alla successiva potenza di 2.

Genera un'eccezione [out_of_range](../../../standard-library/out-of-range-class.md) se il numero di bucket non è valido (0 o maggiore del numero massimo di bucket).

## <a name="size"></a>dimensioni

Restituisce il numero di elementi in questo contenitore simultaneo. Questo metodo è sicuro per la concorrenza.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Valore restituito

Numero di elementi presenti nel contenitore.

### <a name="remarks"></a>Osservazioni

In presenza di operazioni di inserimento simultanee, il numero di elementi presenti nel contenitore simultaneo potrebbe cambiare immediatamente dopo la chiamata a questa funzione, prima che il valore restituito venga letto.

## <a name="swap"></a>scambio

Scambia il contenuto di due oggetti `concurrent_unordered_set`. Questo metodo non è indipendente dalla concorrenza.

```cpp
void swap(concurrent_unordered_set& _Uset);
```

### <a name="parameters"></a>Parametri

*_Uset*<br/>
Oggetto `concurrent_unordered_set` con cui eseguire lo scambio.

## <a name="unsafe_begin"></a>unsafe_begin

Restituisce un iteratore al primo elemento in questo contenitore per un bucket specifico.

```cpp
local_iterator unsafe_begin(size_type _Bucket);

const_local_iterator unsafe_begin(size_type _Bucket) const;
```

### <a name="parameters"></a>Parametri

*_Bucket*<br/>
Indice del bucket.

### <a name="return-value"></a>Valore restituito

Iteratore che punta all'inizio del bucket.

## <a name="unsafe_bucket"></a>unsafe_bucket

Restituisce l'indice del bucket a cui viene mappata una chiave specifica in questo contenitore.

```cpp
size_type unsafe_bucket(const key_type& KVal) const;
```

### <a name="parameters"></a>Parametri

*KVal*<br/>
Chiave dell'elemento cercata.

### <a name="return-value"></a>Valore restituito

Indice del bucket per la chiave in questo contenitore.

## <a name="unsafe_bucket_count"></a>unsafe_bucket_count

Restituisce il numero corrente di bucket in questo contenitore.

```cpp
size_type unsafe_bucket_count() const;
```

### <a name="return-value"></a>Valore restituito

Numero corrente di bucket in questo contenitore.

## <a name="unsafe_bucket_size"></a>unsafe_bucket_size

Restituisce il numero di elementi in un bucket specifico di questo contenitore.

```cpp
size_type unsafe_bucket_size(size_type _Bucket);
```

### <a name="parameters"></a>Parametri

*_Bucket*<br/>
Bucket da ricercare.

### <a name="return-value"></a>Valore restituito

Numero corrente di bucket in questo contenitore.

## <a name="unsafe_cbegin"></a>unsafe_cbegin

Restituisce un iteratore al primo elemento in questo contenitore per un bucket specifico.

```cpp
const_local_iterator unsafe_cbegin(size_type _Bucket) const;
```

### <a name="parameters"></a>Parametri

*_Bucket*<br/>
Indice del bucket.

### <a name="return-value"></a>Valore restituito

Iteratore che punta all'inizio del bucket.

## <a name="unsafe_cend"></a>unsafe_cend

Restituisce un iteratore alla posizione successiva all'ultimo elemento in un bucket specifico.

```cpp
const_local_iterator unsafe_cend(size_type _Bucket) const;
```

### <a name="parameters"></a>Parametri

*_Bucket*<br/>
Indice del bucket.

### <a name="return-value"></a>Valore restituito

Iteratore che punta all'inizio del bucket.

## <a name="unsafe_end"></a>unsafe_end

Restituisce un iteratore all'ultimo elemento in questo contenitore per un bucket specifico.

```cpp
local_iterator unsafe_end(size_type _Bucket);

const_local_iterator unsafe_end(size_type _Bucket) const;
```

### <a name="parameters"></a>Parametri

*_Bucket*<br/>
Indice del bucket.

### <a name="return-value"></a>Valore restituito

Iteratore che punta alla fine del bucket.

## <a name="unsafe_erase"></a>unsafe_erase

Rimuove gli elementi dal `concurrent_unordered_set` nelle posizioni specificate. Questo metodo non è indipendente dalla concorrenza.

```cpp
iterator unsafe_erase(
    const_iterator _Where);

size_type unsafe_erase(
    const key_type& KVal);

iterator unsafe_erase(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Parametri

*_Where*<br/>
Posizione dell'iteratore da cui cancellare.

*KVal*<br/>
Valore chiave da cancellare.

*first*<br/>
*last*<br/>
Iteratori.

### <a name="return-value"></a>Valore restituito

Le prime due funzioni membro restituiscono un iteratore che definisce il primo elemento rimanente oltre gli eventuali elementi rimossi o [end](#end)() se tale elemento non esiste. La terza funzione membro restituisce il numero di elementi che rimuove.

### <a name="remarks"></a>Osservazioni

La prima funzione membro rimuove l'elemento a cui punta `_Where`. La seconda funzione membro rimuove gli elementi compresi nell'intervallo [`_Begin``_End`).

La terza funzione membro rimuove gli elementi nell'intervallo delimitato da [equal_range](#equal_range)(KVal).

## <a name="unsafe_max_bucket_count"></a>unsafe_max_bucket_count

Restituisce il numero massimo di bucket in questo contenitore.

```cpp
size_type unsafe_max_bucket_count() const;
```

### <a name="return-value"></a>Valore restituito

Numero massimo di bucket in questo contenitore.

## <a name="see-also"></a>Vedere anche

[Spazio dei nomi concurrency](concurrency-namespace.md)<br/>
[Contenitori e oggetti paralleli](../../../parallel/concrt/parallel-containers-and-objects.md)
