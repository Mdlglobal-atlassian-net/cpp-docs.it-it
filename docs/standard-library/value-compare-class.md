---
title: Classe value_compare
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::value_compare
helpviewer_keywords:
- value_compare class
ms.assetid: c306c5b9-3505-4357-aa6b-216451b951ed
ms.openlocfilehash: d64d51869ca8db1ed42e9d33691f59da4473d8d0
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447572"
---
# <a name="value_compare-class"></a>Classe value_compare

Fornisce un oggetto funzione in grado di confrontare gli elementi di un oggetto hash_map comparando i valori delle chiavi per determinarne l'ordine relativo nell'oggetto hash_map.

## <a name="syntax"></a>Sintassi

```cpp
class value_compare
    : std::public binary_function<value_type, value_type, bool>
{
public:
    bool operator()(
        const value_type& left,
        const value_type& right) const
    {
        return (comp(left.first, right.first));
    }

protected:
    value_compare(const key_compare& c) : comp (c) { }
    key_compare comp;
};
```

## <a name="remarks"></a>Osservazioni

I criteri di confronto forniti da value_compare tra `value_types` di tutti gli elementi contenuti in un hash_map sono indotti da un confronto tra le chiavi dei rispettivi elementi dalla costruzione della classe ausiliaria. L'operatore della funzione membro usa l'oggetto `comp` di tipo `key_compare` archiviato nell'oggetto funzione fornito da value_compare per confrontare i componenti della chiave di ordinamento di due elementi.

Per hash_set e hash_multiset, che sono semplici contenitori in cui i valori delle chiavi sono identici ai valori degli elementi, value_compare equivale a `key_compare`. Questo non si applica per gli oggetti di tipo hash_map e hash_multimap, poiché il valore degli elementi di tipo `pair` non è identico al valore della chiave dell'elemento.

## <a name="example"></a>Esempio

Vedere l'esempio relativo ad [hash_map::value_comp](../standard-library/hash-map-class.md#value_comp) per indicazioni su come dichiarare e usare la classe value_compare.

## <a name="requirements"></a>Requisiti

**Intestazione:** \<hash_map >

**Spazio dei nomi:** stdext

## <a name="see-also"></a>Vedere anche

[Struct binary_function](../standard-library/binary-function-struct.md)\
[Sicurezza dei thread nella libreria standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Riferimento per la libreria standard C++](../standard-library/cpp-standard-library-reference.md)
