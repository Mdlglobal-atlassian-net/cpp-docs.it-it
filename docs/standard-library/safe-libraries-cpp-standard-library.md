---
title: 'Librerie protette: libreria standard C++'
ms.date: 11/04/2016
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
ms.assetid: 3993340f-1f29-4d81-b3f5-52a52bc8e148
ms.openlocfilehash: e352489ca12b5815aab5517defc72571abe177fb
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446091"
---
# <a name="safe-libraries-c-standard-library"></a>Librerie protette: libreria standard C++

Sono stati apportati diversi miglioramenti alle librerie fornite con Microsoft C++, inclusa la C++ libreria standard, per renderle più sicure.

Nella libreria standard C++ vari metodi sono stati identificati come potenzialmente non sicuri perché potrebbero causare un sovraccarico buffer o altri problemi relativi al codice. L'uso di questi metodi è sconsigliato, mentre sono stati creati in sostituzione metodi nuovi e più sicuri. Questi metodi terminano tutti in `_s`.

Sono stati apportati anche vari miglioramenti per rendere gli iteratori e gli algoritmi più sicuri. Per altre informazioni, vedere [Iteratori verificati](../standard-library/checked-iterators.md), [Supporto degli iteratori di debug](../standard-library/debug-iterator-support.md) e [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

## <a name="remarks"></a>Osservazioni

La tabella seguente elenca i metodi della libreria standard C++ potenzialmente non sicuri, nonché il relativo equivalente più sicuro:

|Metodo potenzialmente non sicuro|Equivalente più sicuro|
|-------------------------------|----------------------|
|[copy](../standard-library/basic-string-class.md#copy)|[basic_string::_Copy_s](../standard-library/basic-string-class.md#copy_s)|
|[copy](../standard-library/char-traits-struct.md#copy)|[char_traits::_Copy_s](../standard-library/char-traits-struct.md#copy_s)|

Se si chiama uno dei metodi potenzialmente non sicuri elencati qui sopra o se si usano gli iteratori in modo non corretto, il compilatore genererà l'[Avviso del compilatore (livello 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Per informazioni su come disabilitare questi avvisi, vedere [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

## <a name="in-this-section"></a>Contenuto della sezione

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)

[_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)

[Iteratori verificati](../standard-library/checked-iterators.md)

[Supporto degli iteratori di debug](../standard-library/debug-iterator-support.md)

## <a name="see-also"></a>Vedere anche

[Panoramica sulla libreria standard C++](../standard-library/cpp-standard-library-overview.md)
