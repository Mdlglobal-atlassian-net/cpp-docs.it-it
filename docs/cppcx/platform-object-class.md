---
title: Classe Platform::Object
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Object::Object
- VCCORLIB/Platform::Object::Equals
- VCCORLIB/Platform::Object::GetHashCode
- VCCORLIB/Platform::Object::ReferenceEquals
- VCCORLIB/Platform::ToString
- VCCORLIB/Platform::GetType
helpviewer_keywords:
- Object class
ms.assetid: 709e84a8-0bff-471b-bc14-63e424080b5a
ms.openlocfilehash: 8300ec484bdb58919ce8e450b706dd07c275ceee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363691"
---
# <a name="platformobject-class"></a>Classe Platform::Object

Fornisce il comportamento comune per le classi di riferimento e gli struct di riferimento nelle app di Windows Runtime. Tutte le istanze delle classi e degli struct di riferimento sono implicitamente convertibili a Platform::Object^ e possono eseguire l'override del relativo metodo ToString virtuale.

## <a name="syntax"></a>Sintassi

```cpp
public ref class Object : Object
```

### <a name="members"></a>Membri

### <a name="public-constructors"></a>Costruttori pubblici

|Nome|Descrizione|
|----------|-----------------|
|[Object::Object](#ctor)|Inizializza una nuova istanza della classe Object.|

### <a name="public-methods"></a>Metodi pubblici

|Nome|Descrizione|
|----------|-----------------|
|[Object::Equals](#equals)|Determina se l'oggetto specificato è uguale all'oggetto corrente.|
|[Object::GetHashCode](#gethashcode)|Restituisce il codice hash relativo a questa istanza.|
|[Object::ReferenceEquals](#referenceequals)|Determina se le istanze di Object specificate rappresentano la stessa istanza.|
|[ToString](#tostring)|Restituisce una stringa che rappresenta l'oggetto corrente. È possibile eseguirne l'override.|
|[GetType](#gettype)|Ottiene un oggetto [Platform::Type](../cppcx/platform-type-class.md) che descrive l'istanza corrente.|

## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà

`Object`

`Object`

### <a name="requirements"></a>Requisiti

**Intestazione:** vccorlib.h

**Spazio dei nomi:** Platform

## <a name="objectequals-method"></a><a name="equals"></a>Metodo Object::Equals

Determina se l'oggetto specificato è uguale all'oggetto corrente.

### <a name="syntax"></a>Sintassi

```cpp
bool Equals(
    Object^ obj
)
```

### <a name="parameters"></a>Parametri

*obj*<br/>
Oggetto da confrontare.

### <a name="return-value"></a>Valore restituito

**true** se gli oggetti sono uguali, in caso contrario **false**.

## <a name="objectgethashcode-method"></a><a name="gethashcode"></a>Metodo Object::GetHashCodeObject::GetHashCode Method

Restituisce il valore di identità `IUnknown`* per questa istanza se è un oggetto COM, oppure un valore hash calcolato se non è un oggetto COM.

### <a name="syntax"></a>Sintassi

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>Valore restituito

Valore numerico che identifica in modo univoco l'oggetto.

### <a name="remarks"></a>Osservazioni

Puoi usare GetHashCode per creare chiavi per gli oggetti nella mappa. È possibile confrontare i codici hash utilizzando [Object::Equals](#equals). Se il percorso del codice è estremamente critico e `GetHashCode` e `Equals` non sono sufficientemente veloci, puoi passare al livello COM sottostante ed effettuare confronti tra puntatori `IUnknown` nativi.

## <a name="objectgettype-method"></a><a name="gettype"></a>Metodo Object::GetType

Restituisce un oggetto [Platform::Type](../cppcx/platform-type-class.md) che descrive il tipo di runtime di un oggetto.

### <a name="syntax"></a>Sintassi

```cpp
Object::GetType();
```

### <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito

Oggetto [Platform::Type](../cppcx/platform-type-class.md) che descrive il tipo di runtime dell'oggetto.

### <a name="remarks"></a>Osservazioni

Il valore statico [Type::GetTypeCode](../cppcx/platform-type-class.md#gettypecode) può essere utilizzato per ottenere un valore di [enumerazione Platform::TypeCode](../cppcx/platform-typecode-enumeration.md) che rappresenta il tipo corrente. Questa funzionalità è particolarmente utile per i tipi predefiniti. Il codice del tipo per qualsiasi classe di riferimento oltre [a Platform::String](../cppcx/platform-string-class.md) è Object (1).

La classe [Windows::UI::Xaml::Interop::TypeName](/uwp/api/windows.ui.xaml.interop.typename) viene usata nelle API di Windows come modalità indipendente dal linguaggio per passare informazioni sul tipo tra componenti e app di Windows.The Windows::UI::Xaml::Interop::TypeName class is used in the Windows APIs as a language-independent way of passing type information between Windows components and apps. La classe T[Platform::Type](../cppcx/platform-type-class.md) dispone `Type` di `TypeName`operatori per la conversione tra e .

Usa l'operatore [typeid](../extensions/typeid-cpp-component-extensions.md) per restituire un `Platform::Type` oggetto per un nome di classe, ad esempio quando ti spogli tra le pagine XAML:

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

## <a name="objectobject-constructor"></a><a name="ctor"></a>Costruttore Object::Object

Inizializza una nuova istanza della classe Object.

### <a name="syntax"></a>Sintassi

```cpp
public:Object();
```

## <a name="objectreferenceequals-method"></a><a name="referenceequals"></a>Metodo Object::ReferenceEqualsObject::ReferenceEquals Method

Determina se le istanze di Object specificate rappresentano la stessa istanza.

### <a name="syntax"></a>Sintassi

```cpp
public:static bool ReferenceEquals(  Object^ obj1,   Object^ obj2);
```

### <a name="parameters"></a>Parametri

*obj1*<br/>
Primo oggetto da confrontare.

*obj2*<br/>
Secondo oggetto da confrontare.

### <a name="return-value"></a>Valore restituito

**true** se i due oggetti sono uguali; in caso contrario, **false**.

## <a name="objecttostring-method-ccx"></a><a name="tostring"></a>Metodo Object::ToString (C/CX)

Restituisce una stringa che rappresenta l'oggetto corrente.

### <a name="syntax"></a>Sintassi

```cpp
public:
virtual String^ ToString();
```

### <a name="return-value"></a>Valore restituito

Stringa che rappresenta l'oggetto corrente. Puoi eseguire l'override di questo metodo per fornire un messaggio stringa personalizzato in ref class o struct:

```cpp
public ref class Tree sealed
{
public:
    Tree(){}
    virtual Platform::String^ ToString() override
    {
      return "I’m a Tree";
    };
};
```

## <a name="see-also"></a>Vedere anche

[Spazio dei nomi della piattaforma](platform-namespace-c-cx.md)<br/>
[Classe Platform::Type](platform-type-class.md)<br/>
[Sistema di tipi](type-system-c-cx.md)
