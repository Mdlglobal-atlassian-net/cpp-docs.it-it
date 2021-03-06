---
title: Struct forward_iterator_tag
ms.date: 11/04/2016
f1_keywords:
- xutility/std::forward_iterator_tag
helpviewer_keywords:
- forward_iterator_tag struct
- forward_iterator_tag class
ms.assetid: 68b633ac-b135-4e9e-837d-14248a262ec5
ms.openlocfilehash: 687e39ce752bc0d4d289421887570dea6870f8f3
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457130"
---
# <a name="forward_iterator_tag-struct"></a>Struct forward_iterator_tag

Classe che fornisce un tipo restituito per la funzione **iterator_category** che rappresenta un iteratore in avanti.

## <a name="syntax"></a>Sintassi

```cpp
struct forward_iterator_tag    : public input_iterator_tag {};
```

## <a name="remarks"></a>Note

Le classi di tag di categoria vengono usate come tag di compilazione per la selezione dell'algoritmo. La funzione modello deve individuare la categoria più specifica dell'argomento iteratore in modo da usare l'algoritmo più efficiente in fase di compilazione. Per ogni iteratore di tipo `Iterator`, è necessario definire `iterator_traits`< `Iterator`>  **::iterator_category** come il tag di categoria più specifico che descrive il comportamento dell'iteratore.

Il tipo è uguale a **iterator**\< **Iter**>  **::iterator_category** quando **Iter** descrive un oggetto che può essere usato come iteratore in avanti.

## <a name="example"></a>Esempio

Per un esempio di come usare i tag **iterator_tag**, vedere [iterator_traits](../standard-library/iterator-traits-struct.md) o [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md).

## <a name="requirements"></a>Requisiti

**Intestazione:** \<iterator>

**Spazio dei nomi:** std

## <a name="see-also"></a>Vedere anche

[Struct input_iterator_tag](../standard-library/input-iterator-tag-struct.md)\
[Sicurezza dei thread nella libreria standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Riferimento per la libreria standard C++](../standard-library/cpp-standard-library-reference.md)
