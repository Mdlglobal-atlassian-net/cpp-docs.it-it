---
title: Classe error_code
ms.date: 11/04/2016
f1_keywords:
- system_error/std::error_code
- system_error/std::error_code::value_type
- system_error/std::error_code::assign
- system_error/std::error_code::category
- system_error/std::error_code::clear
- system_error/std::error_code::default_error_condition
- system_error/std::error_code::message
- system_error/std::error_code::operator bool
helpviewer_keywords:
- std::error_code
- std::error_code::value_type
- std::error_code::assign
- std::error_code::category
- std::error_code::clear
- std::error_code::default_error_condition
- std::error_code::message
ms.assetid: c09b4a96-cb14-4281-a319-63543f9b2b4a
ms.openlocfilehash: 919a2a81c66de9adf15deeae8cf8ff3dea08762e
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245829"
---
# <a name="error_code-class"></a>Classe error_code

Rappresenta gli errori di sistema di basso livello che sono specifici dell'implementazione.

## <a name="syntax"></a>Sintassi

```cpp
class error_code;
```

## <a name="remarks"></a>Note

Un oggetto di tipo classe `error_code` archivia un valore di codice di errore e un puntatore a un oggetto che rappresenta una [categoria](../standard-library/error-category-class.md) di codici di errore che descrive gli errori di basso livello segnalati.

## <a name="members"></a>Members

### <a name="constructors"></a>Costruttori

|||
|-|-|
|[error_code](#error_code)|Costruisce un oggetto di tipo `error_code`.|

### <a name="typedefs"></a>Definizioni typedef

|||
|-|-|
|[value_type](#value_type)|Tipo che rappresenta il valore del codice di errore archiviato.|

### <a name="functions"></a>Funzioni

|||
|-|-|
|[assign](#assign)|Assegna un valore di codice di errore e una categoria a un codice di errore.|
|[category](#category)|Restituisce la categoria dell'errore.|
|[clear](#clear)|Cancella il valore del codice di errore e la categoria.|
|[default_error_condition](#default_error_condition)|Restituisce la condizione di errore predefinita.|
|[message](#message)|Restituisce il nome del codice di errore.|

### <a name="operators"></a>Operatori

|||
|-|-|
|[operator==](#op_eq_eq)|Verifica l'uguaglianza tra oggetti `error_code`.|
|[operator!=](#op_neq)|Verifica la disuguaglianza tra oggetti `error_code`.|
|[operator<](#op_lt)|Verifica se l'oggetto `error_code` è più piccolo dell'oggetto `error_code` passato per il confronto.|
|[operator=](#op_eq)|Assegna un nuovo valore di enumerazione all'oggetto `error_code`.|
|[operator bool](#op_bool)|Crea una variabile di tipo `error_code`.|

### <a name="assign"></a> assegnare

Assegna un valore di codice di errore e una categoria a un codice di errore.

```cpp
void assign(value_type val, const error_category& _Cat);
```

#### <a name="parameters"></a>Parametri

*Val*\
Il valore del codice di errore da archiviare nell'`error_code`.

*Servizio*\
La categoria dell'errore da archiviare nell'`error_code`.

#### <a name="remarks"></a>Note

La funzione membro Archivia *val* come valore del codice di errore e un puntatore a *servizio*.

### <a name="category"></a> Categoria

Restituisce la categoria dell'errore.

```cpp
const error_category& category() const;
```

#### <a name="remarks"></a>Note

### <a name="clear"></a> Cancella

Cancella il valore del codice di errore e la categoria.

```cpp
clear();
```

#### <a name="remarks"></a>Note

La funzione membro archivia un valore del codice di errore zero e un puntatore all'oggetto [generic_category](../standard-library/system-error-functions.md#generic_category).

### <a name="default_error_condition"></a> default_error_condition

Restituisce la condizione di errore predefinita.

```cpp
error_condition default_error_condition() const;
```

#### <a name="return-value"></a>Valore restituito

La [error_condition](../standard-library/error-condition-class.md) specificata dalla [default_error_condition](../standard-library/error-category-class.md#default_error_condition).

#### <a name="remarks"></a>Note

Questa funzione membro restituisce `category().default_error_condition(value())`.

### <a name="error_code"></a> error_code

Costruisce un oggetto di tipo `error_code`.

```cpp
error_code();

error_code(value_type val, const error_category& _Cat);

template <class _Enum>
error_code(_Enum _Errcode,
    typename enable_if<is_error_code_enum<_Enum>::value,
    error_code>::type* = 0);
```

#### <a name="parameters"></a>Parametri

*Val*\
Il valore del codice di errore da archiviare nell'`error_code`.

*Servizio*\
La categoria dell'errore da archiviare nell'`error_code`.

*_Errcode*\
Il valore di enumerazione da archiviare nell'`error_code`.

#### <a name="remarks"></a>Note

Il primo costruttore archivia un valore del codice di errore zero e un puntatore alla [generic_category](../standard-library/system-error-functions.md#generic_category).

Il secondo costruttore Archivia *val* come valore del codice di errore e un puntatore a [error_category](../standard-library/error-category-class.md).

Il terzo costruttore archivia `(value_type)_Errcode` come valore del codice di errore e un puntatore alla [generic_category](../standard-library/system-error-functions.md#generic_category).

### <a name="message"></a> Messaggio

Restituisce il nome del codice di errore.

```cpp
string message() const;
```

#### <a name="return-value"></a>Valore restituito

`string` che rappresenta il nome del codice di errore.

#### <a name="remarks"></a>Note

Questa funzione membro restituisce `category().message(value())`.

### <a name="op_eq_eq"></a> operator==

Verifica l'uguaglianza tra oggetti `error_code`.

```cpp
bool operator==(const error_code& right) const;
```

#### <a name="parameters"></a>Parametri

*Ok*\
Oggetto di cui verificare l'uguaglianza.

#### <a name="return-value"></a>Valore restituito

**true** se gli oggetti sono uguali; in caso contrario, **false**.

#### <a name="remarks"></a>Note

L'operatore membro restituisce `category() == right.category() && value == right.value()`.

### <a name="op_neq"></a> operatore! =

Verifica la disuguaglianza tra oggetti `error_code`.

```cpp
bool operator!=(const error_code& right) const;
```

#### <a name="parameters"></a>Parametri

*Ok*\
Oggetto di cui verificare la disuguaglianza.

#### <a name="return-value"></a>Valore restituito

**true** se il `error_code` non è uguale all'oggetto il `error_code` oggetto passato in *a destra*; in caso contrario **false**.

#### <a name="remarks"></a>Note

L'operatore membro restituisce `!(*this == right)`.

### <a name="op_lt"></a> Operatore&lt;

Verifica se l'oggetto `error_code` è più piccolo dell'oggetto `error_code` passato per il confronto.

```cpp
bool operator<(const error_code& right) const;
```

#### <a name="parameters"></a>Parametri

*Ok*\
L'oggetto error_code da confrontare.

#### <a name="return-value"></a>Valore restituito

**true** se l'oggetto `error_code` è più piccolo dell'oggetto `error_code` passato per il confronto; in caso contrario **false**.

#### <a name="remarks"></a>Note

L'operatore membro restituisce `category() < right.category() || category() == right.category() && value < right.value()`.

### <a name="op_eq"></a> operator=

Assegna un nuovo valore di enumerazione all'oggetto `error_code`.

```cpp
template <class _Enum>
typename enable_if<is_error_code_enum<_Enum>::value, error_code>::type&
    operator=(_Enum _Errcode);
```

#### <a name="parameters"></a>Parametri

*_Errcode*\
Il valore di enumerazione da assegnare all'oggetto `error_code`.

#### <a name="return-value"></a>Valore restituito

Un riferimento all'oggetto `error_code` a cui viene assegnato il nuovo valore di enumerazione dalla funzione membro.

#### <a name="remarks"></a>Note

L'operatore membro archivia `(value_type)_Errcode` come valore del codice di errore e un puntatore alla [generic_category](../standard-library/system-error-functions.md#generic_category). Restituisce `*this`.

### <a name="op_bool"></a> operator bool

Crea una variabile di tipo `error_code`.

```cpp
explicit operator bool() const;
```

#### <a name="return-value"></a>Valore restituito

Il valore booleano dell'oggetto `error_code`.

#### <a name="remarks"></a>Note

L'operatore restituisce un valore convertibile in **true** solo se [valore](#value) non è uguale a zero. Il tipo restituito è convertibile solo in **bool**, non in `void *` o altri tipi scalari noti.

### <a name="value"></a> Valore

Restituisce il valore del codice di errore archiviato.

```cpp
value_type value() const;
```

### <a name="return-value"></a>Valore restituito

Il valore del codice di errore archiviato di tipo [value_type](#value_type).

### <a name="value_type"></a> value_type

Tipo che rappresenta il valore del codice di errore archiviato.

```cpp
typedef int value_type;
```

#### <a name="remarks"></a>Note

Definizione del tipo è un sinonimo **int**.
