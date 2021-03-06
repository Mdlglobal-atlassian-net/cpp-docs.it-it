---
title: Funzioni &lt;thread&gt;
ms.date: 11/04/2016
f1_keywords:
- thread/std::get_id
- thread/std::sleep_for
- thread/std::sleep_until
- thread/std::swap
- thread/std::yield
ms.assetid: bb1aa1ef-fe3f-4e2c-8b6e-e22dbf2f5a19
helpviewer_keywords:
- std::get_id [C++]
- std::sleep_for [C++]
- std::sleep_until [C++]
- std::swap [C++]
- std::yield [C++]
ms.openlocfilehash: bb0a0a12ec2882701447804f9c88d1776a196cb7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375847"
---
# <a name="ltthreadgt-functions"></a>Funzioni &lt;thread&gt;

||||
|-|-|-|
|[get_id](#get_id)|[sleep_for](#sleep_for)|[sleep_until](#sleep_until)|
|[Swap](#swap)|[yield](#yield)|

## <a name="get_id"></a><a name="get_id"></a>get_id

Identifica in modo univoco il thread di esecuzione corrente.

```cpp
thread::id this_thread::get_id() noexcept;
```

### <a name="return-value"></a>Valore restituito

Oggetto di tipo [thread::id](../standard-library/thread-class.md) che identifica in modo univoco il thread di esecuzione corrente.

## <a name="sleep_for"></a><a name="sleep_for"></a>sleep_for

Blocca il thread chiamante.

```cpp
template <class Rep,
class Period>
inline void sleep_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parametri

*Rel_time*\
Oggetto [duration](../standard-library/duration-class.md) che specifica un intervallo di tempo.

### <a name="remarks"></a>Osservazioni

La funzione blocca il thread chiamante per almeno il tempo specificato da *Rel_time*. Questa funzione non genera eccezioni.

## <a name="sleep_until"></a><a name="sleep_until"></a>sleep_until

La funzione blocca il thread chiamante almeno fino all'ora specificata.

```cpp
template <class Clock, class Duration>
void sleep_until(const chrono::time_point<Clock, Duration>& Abs_time);

void sleep_until(const xtime *Abs_time);
```

### <a name="parameters"></a>Parametri

*Abs_time*\
Rappresenta un punto nel tempo.

### <a name="remarks"></a>Osservazioni

Questa funzione non genera eccezioni.

## <a name="swap"></a><a name="swap"></a>Swap

Scambia gli stati di due oggetti **thread.**

```cpp
void swap(thread& Left, thread& Right) noexcept;
```

### <a name="parameters"></a>Parametri

*Sinistra*\
Oggetto **thread** sinistro.

*va bene*\
Oggetto **filettatura** destro.

### <a name="remarks"></a>Osservazioni

La funzione chiama `Left.swap(Right)`.

## <a name="yield"></a><a name="yield"></a>Rendimento

Segnala al sistema operativo di eseguire altri thread, anche se in genere l'esecuzione del thread corrente dovrebbe continuare.

```cpp
inline void yield() noexcept;
```

## <a name="see-also"></a>Vedere anche

[\<>di filettatura](../standard-library/thread.md)
