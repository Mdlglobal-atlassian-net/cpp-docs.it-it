---
title: Avviso del compilatore (livello 1) C4659
ms.date: 11/04/2016
f1_keywords:
- C4659
helpviewer_keywords:
- C4659
ms.assetid: e29ba8db-7917-43f6-8e34-868b752279ae
ms.openlocfilehash: 1766cb285fa33d384d57e89c7243fc35022ae006
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175636"
---
# <a name="compiler-warning-level-1-c4659"></a>Avviso del compilatore (livello 1) C4659

\#pragma ' pragma ': l'uso del segmento riservato ' segment ' presenta un comportamento non definito. usare #pragma comment (linker,...)

È stata usata l'opzione. drectve per passare un'opzione al linker. Usare invece il [Commento](../../preprocessor/comment-c-cpp.md) pragma per passare un'opzione del linker.

```cpp
// C4659.cpp
// compile with: /W1 /LD
#pragma code_seg(".drectve")   // C4659
```
