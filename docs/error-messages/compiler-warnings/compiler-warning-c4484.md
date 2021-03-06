---
title: Avviso del compilatore C4484
ms.date: 11/04/2016
f1_keywords:
- C4484
helpviewer_keywords:
- C4484
ms.assetid: 3d30e5b3-2297-45b7-a37a-1360056fdd0e
ms.openlocfilehash: c168c91f8259b744ed10dd72701d34fd60b98681
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165158"
---
# <a name="compiler-warning-c4484"></a>Avviso del compilatore C4484

' override_function ': corrisponde al metodo della classe di riferimento di base ' base_class_function ', ma non è contrassegnato ' Virtual ',' New ' o ' override '; si presuppone ' New ' (e non ' Virtual ')

Quando si compila con **/CLR**, il compilatore non esegue l'override implicito di una funzione della classe base, il che significa che la funzione otterrà un nuovo slot in vtable. Per risolvere il errore, specificare in modo esplicito se una funzione è un override.

Per altre informazioni, vedere:

- [/clr (compilazione Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [override](../../extensions/override-cpp-component-extensions.md)

- [new (nuovo slot in vtable)](../../extensions/new-new-slot-in-vtable-cpp-component-extensions.md)

C4484 viene sempre emesso come un errore. Usare il pragma [warning](../../preprocessor/warning.md) per disattivare C4484.

## <a name="example"></a>Esempio

L'esempio seguente genera l'C4484.

```cpp
// C4484.cpp
// compile with: /clr
ref struct A {
   virtual void Test() {}
};

ref struct B : A {
   void Test() {}   // C4484
};

// OK
ref struct C {
   virtual void Test() {}
   virtual void Test2() {}
};

ref struct D : C {
   virtual void Test() new {}
   virtual void Test2() override {}
};
```
