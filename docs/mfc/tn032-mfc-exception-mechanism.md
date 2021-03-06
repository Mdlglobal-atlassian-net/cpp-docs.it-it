---
title: 'TN032: Meccanismo di eccezioni MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- TN032
- MFC, exceptions
- CException class [MFC], using
ms.assetid: 0271f0aa-82cb-47a2-b7ea-e88126fc7e43
ms.openlocfilehash: 5b419fdcc4f20579b1a809dd8a5cf6a93f4fe835
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611421"
---
# <a name="tn032-mfc-exception-mechanism"></a>TN032: Meccanismo di eccezioni MFC

Le versioni precedenti di Visual C++ non supportavano il meccanismo delle eccezioni C++ standard e MFC forniva macro **TRY/CATCH/THROW** che sono stati usati invece. Questa versione di Visual C++ supporta pienamente le eccezioni C++. In questa nota venivano trattati alcuni dettagli di implementazione avanzata delle precedenti macro, incluso come pulire automaticamente gli oggetti basati su stack. Dal momento che le eccezioni C++ supportano la rimozione dello stack per impostazione predefinita, questa nota tecnica non è più necessaria.

Fare riferimento a [alle eccezioni: Utilizzo delle macro MFC ed eccezioni C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) per altre informazioni sulle differenze tra le macro MFC e le nuove parole chiave C++.

## <a name="see-also"></a>Vedere anche

[Note tecniche per numero](../mfc/technical-notes-by-number.md)<br/>
[Note tecniche per categoria](../mfc/technical-notes-by-category.md)
