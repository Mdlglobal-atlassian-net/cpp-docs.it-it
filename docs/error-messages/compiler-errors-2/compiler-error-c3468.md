---
title: Errore del compilatore C3468
ms.date: 11/04/2016
f1_keywords:
- C3468
helpviewer_keywords:
- C3468
ms.assetid: cfd320db-2f6e-4e0d-ba02-e79ece87e1e0
ms.openlocfilehash: e4a507dad1d795e703e8db7f8704aad959c95b6f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757307"
---
# <a name="compiler-error-c3468"></a>Errore del compilatore C3468

'type': i tipi possono essere inoltrati solo a un assembly:

'`file`' non è un assembly

È possibile inoltrare solo i tipi in un assembly.

Per ulteriori informazioni, vedere [tipo di invio (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="example"></a>Esempio

L'esempio seguente crea un modulo.

```cpp
// C3468.cpp
// compile with: /LN /clr
public ref class R {};
```

## <a name="example"></a>Esempio

L'esempio seguente genera l'errore C3468.

```cpp
// C3468_b.cpp
// compile with: /clr /c
#using "C3468.netmodule"
[ assembly:TypeForwardedTo(R::typeid) ];   // C3468
```
