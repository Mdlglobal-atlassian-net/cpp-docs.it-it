---
title: Classe enable_shared_from_this
ms.date: 11/04/2016
f1_keywords:
- memory/std::enable_shared_from_this
helpviewer_keywords:
- enable_shared_from_this class
- enable_shared_from_this
ms.assetid: 9237603d-22e2-421f-b070-838ac006baf5
ms.openlocfilehash: 152a5e0433f2eab5160fbdedde8f18f42f2303e6
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245858"
---
# <a name="enablesharedfromthis-class"></a>Classe enable_shared_from_this

Consente di generare un `shared_ptr`.

## <a name="syntax"></a>Sintassi

```cpp
class enable_shared_from_this {
public:
    shared_ptr<Ty>
        shared_from_this();
    shared_ptr<const Ty> shared_from_this() const;
    weak_ptr<T> weak_from_this() noexcept;
    weak_ptr<T const> weak_from_this() const noexcept;
protected:
    enable_shared_from_this();
    enable_shared_from_this(const enable_shared_from_this&);
    enable_shared_from_this& operator=(const enable_shared_from_this&);
    ~enable_shared_from_this();
};
```

### <a name="parameters"></a>Parametri

*Ty*\
Tipo controllato dal puntatore condiviso.

## <a name="remarks"></a>Note

Gli oggetti derivati da `enable_shared_from_this` possono usare i metodi `shared_from_this` nelle funzioni membro per creare proprietari [shared_ptr](../standard-library/shared-ptr-class.md) dell'istanza che condividono la proprietà con proprietari `shared_ptr` esistenti. In caso contrario, se si crea una nuova `shared_ptr` usando **ciò**, è diverso dai esistente `shared_ptr` proprietari, che possono portare a riferimenti non validi o l'oggetto deve essere eliminato più di una volta.

I costruttori, il distruttore e l'operatore di assegnazione sono protetti per evitare un uso improprio accidentale. Il tipo di argomento di modello *Ty* deve essere il tipo della classe derivata.

Per un esempio di utilizzo, vedere [enable_shared_from_this::shared_from_this](#shared_from_this).

## <a name="shared_from_this"></a> shared_from_this

Genera un `shared_ptr` che condivide la proprietà dell'istanza con i proprietari `shared_ptr` esistenti.

```cpp
shared_ptr<T> shared_from_this();
shared_ptr<const T> shared_from_this() const;
```

### <a name="remarks"></a>Note

Quando si derivano oggetti dalla classe di base `enable_shared_from_this`, le funzioni membro del modello `shared_from_this` restituiscono un oggetto [classe shared_ptr](../standard-library/shared-ptr-class.md) che condivide la proprietà di questa istanza con i proprietari `shared_ptr` esistenti. In caso contrario, se si crea una nuova `shared_ptr` dal **ciò**, è diverso dai esistente `shared_ptr` proprietari, che possono portare a riferimenti non validi o l'oggetto deve essere eliminato più di una volta. Il comportamento sarà indefinito se si chiama `shared_from_this` in un'istanza che non è già di proprietà di un oggetto `shared_ptr`.

### <a name="example"></a>Esempio

```cpp
// std_memory_shared_from_this.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

struct base : public std::enable_shared_from_this<base>
{
    int val;
    shared_ptr<base> share_more()
    {
        return shared_from_this();
    }
};

int main()
{
    auto sp1 = make_shared<base>();
    auto sp2 = sp1->share_more();

    sp1->val = 3;
    cout << "sp2->val == " << sp2->val << endl;
    return 0;
}
```

```Output
sp2->val == 3
```

## <a name="weak_from_this"></a> weak_from_this

```cpp
weak_ptr<T> weak_from_this() noexcept;
weak_ptr<T const> weak_from_this() const noexcept;
```
