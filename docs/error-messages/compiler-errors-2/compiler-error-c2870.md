---
title: Errore del compilatore C2870
ms.date: 11/04/2016
f1_keywords:
- C2870
helpviewer_keywords:
- C2870
ms.assetid: 80523ee9-1fd3-4dc4-8a77-5083deb99066
ms.openlocfilehash: f61281da23e46236e7fce496a4d89086e5d6c0ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165042"
---
# <a name="compiler-error-c2870"></a>Errore del compilatore C2870

'name': una definizione dello spazio dei nomi deve comparire in ambito file o immediatamente all'interno di un'altra definizione dello spazio dei nomi

È definito lo spazio dei nomi `name` in modo non corretto. Gli spazi dei nomi deve essere definita nell'ambito file (all'esterno di tutti i blocchi e le classi) o immediatamente all'interno di un altro spazio dei nomi.

L'esempio seguente genera l'errore C2870:

```
// C2870.cpp
// compile with: /c
int main() {
   namespace A { int i; };   // C2870
}
```