---
title: Modelli di funzioni membro
ms.date: 11/04/2016
helpviewer_keywords:
- function templates, member functions
ms.assetid: 83d51835-6a27-40ed-997c-7d90dc9182d8
ms.openlocfilehash: ee36d4f33f3e4216e2ad9c434ac1da4ca3aa83e8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177981"
---
# <a name="member-function-templates"></a>Modelli di funzioni membro

Il termine modello di membro si riferisce sia ai modelli di funzioni membro che ai modelli di classe annidati. I modelli di funzioni membro sono funzioni modello membri di una classe o di un modello di classe.

Le funzioni membro possono essere modelli di funzione in vari contesti. Tutte le funzioni dei modelli di classe sono generiche, ma non vengono definite come modelli di membro o modelli di funzioni membro. Se queste funzioni membro accettano i propri argomenti di modello, vengono considerate come modelli di funzioni membro.

## <a name="example"></a>Esempio

I modelli di funzioni membro delle classi di modelli e non di modelli vengono dichiarati come modelli di funzione con i relativi parametri di modello.

```cpp
// member_function_templates.cpp
struct X
{
   template <class T> void mf(T* t) {}
};

int main()
{
   int i;
   X* x = new X();
   x->mf(&i);
}
```

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un modello di funzione membro di una classe di modello.

```cpp
// member_function_templates2.cpp
template<typename T>
class X
{
public:
   template<typename U>
   void mf(const U &u)
   {
   }
};

int main()
{
}
```

## <a name="example"></a>Esempio

```cpp
// defining_member_templates_outside_class.cpp
template<typename T>
class X
{
public:
   template<typename U>
   void mf(const U &u);
};

template<typename T> template <typename U>
void X<T>::mf(const U &u)
{
}

int main()
{
}
```

## <a name="example"></a>Esempio

Le classi locali non possono avere modelli di membro.

Le funzioni modello di membro non possono essere funzioni virtuali e non possono eseguire l'override delle funzioni virtuali da una classe base quando vengono dichiarate con lo stesso nome di una funzione virtuale di una classe base.

Nell'esempio seguente viene illustrata una conversione definita dall'utente basata su modelli:

```cpp
// templated_user_defined_conversions.cpp
template <class T>
struct S
{
   template <class U> operator S<U>()
   {
      return S<U>();
   }
};

int main()
{
   S<int> s1;
   S<long> s2 = s1;  // Convert s1 using UDC and copy constructs S<long>.
}
```

## <a name="see-also"></a>Vedere anche

[Modelli di funzioni](../cpp/function-templates.md)
