---
title: File ILK come input del linker
ms.date: 11/04/2016
helpviewer_keywords:
- ILK files
- .ilk files
ms.assetid: 7324c104-9e5d-423d-b268-b59f92607bf2
ms.openlocfilehash: 252c1cd6e17346954fce7ebf16134246da76ba57
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293849"
---
# <a name="ilk-files-as-linker-input"></a>File ILK come input del linker

Quando si collegano in modo incrementale, collegamento Aggiorna il file di stato ilk creato durante il primo collegamento incrementale. Questo file ha lo stesso nome base file .exe o il file con estensione dll e ha l'estensione ilk. Durante i collegamenti incrementali successivi collegamento Aggiorna il file ilk. Se il file ilk è mancante, LINK esegue un collegamento completo e crea un nuovo file ilk. Se il file ILK non è utilizzabile, LINK esegue un collegamento non incrementale. Per informazioni dettagliate su collegamento incrementale, vedere la [collegamento incrementale (/Incremental)](incremental-link-incrementally.md) opzione.

## <a name="see-also"></a>Vedere anche

[File di input LINK](link-input-files.md)<br/>
[Opzioni del linker MSVC](linker-options.md)
