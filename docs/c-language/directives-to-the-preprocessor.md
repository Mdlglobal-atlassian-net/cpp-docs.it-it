---
title: Direttive al preprocessore
ms.date: 11/04/2016
ms.assetid: adc6251e-cf6b-4508-bdbb-55f446c838d3
ms.openlocfilehash: 520d181c3a58ee2c626678a3afd9126f1ef183cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234140"
---
# <a name="directives-to-the-preprocessor"></a>Direttive al preprocessore

Una "direttiva" indica al preprocessore C di eseguire un'azione specifica nel testo del programma prima della compilazione. Le [direttive per il preprocessore](../preprocessor/preprocessor-directives.md) sono descritte dettagliatamente nel *Riferimento al preprocessore*. In questo esempio viene utilizzata la direttiva per il preprocessore `#define`:

```
#define MAX 100
```

Questa istruzione indica al compilatore di sostituire tutte le occorrenze di `MAX` con `100` prima della compilazione. Le direttive per il preprocessore del compilatore C sono:

|#define|#endif|#ifdef|#line|
|--------------|-------------|-------------|------------|
|`#elif`|`#error`|**#ifndef**|**#pragma**|
|`#else`|`#if`|`#include`|`#undef`|

## <a name="see-also"></a>Vedere anche

[File e programmi di origine](../c-language/source-files-and-source-programs.md)
