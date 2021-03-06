---
title: Avviso del compilatore (livello 1) C4929
ms.date: 11/04/2016
f1_keywords:
- C4929
helpviewer_keywords:
- C4929
ms.assetid: 95f8ab4f-4468-4caa-acd5-8f4592f03b3c
ms.openlocfilehash: 8f8f5f9febf762ddff1d35baa2686162ff6653e2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199303"
---
# <a name="compiler-warning-level-1-c4929"></a>Avviso del compilatore (livello 1) C4929

' file ': libreria dei tipi contiene un'Unione. il qualificatore ' embedded_idl ' verrà ignorato

Impossibile applicare l'attributo embedded_idl di [#import](../../preprocessor/hash-import-directive-cpp.md) alla libreria dei tipi perché è presente un'Unione nella libreria dei tipi. Per risolvere il problema, non usare embedded_idl.

## <a name="example"></a>Esempio

Nell'esempio seguente viene definito un componente.

```cpp
// C4929a.cpp
// compile with: /LD /link /TLBOUT:C4929a.tlb
#include <objbase.h>
[module(name="Test")];
[public, switch_type(short)] typedef union _TD_UNION_TYPE   {
   [case(24)]
      float fM;
   [case(25)]
      double dMN;
   [default]
      int x;
} TD_UNION_TYPE;

[export, public] typedef struct _TDW_TYPE {
   [switch_is(sU)] TD_UNION_TYPE w;
      short sU;
} TD_TYPE;

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface I {
   HRESULT f(TD_TYPE*);
};

[coclass, uuid("00000000-0000-0000-0000-000000000002")]
struct C : I {
   HRESULT f(TD_TYPE*) { return 0; }
};
```

## <a name="example"></a>Esempio

L'esempio seguente genera l'C4929.

```cpp
// C4929b.cpp
// compile with: /c /W1
#import "C4929a.tlb" embedded_idl   // C4929
```
