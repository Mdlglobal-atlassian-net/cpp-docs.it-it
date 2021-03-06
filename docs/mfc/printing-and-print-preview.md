---
title: Stampa e anteprima di stampa
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC]
- previewing printing
- printing [MFC]
- print preview
- printing [MFC], print preview
ms.assetid: d15059cd-32de-4450-95f7-e73aece238f6
ms.openlocfilehash: 70740922ec7f2030d14eebee72144a373550aacc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62218716"
---
# <a name="printing-and-print-preview"></a>Stampa e anteprima di stampa

MFC supporta la stampa e anteprima di stampa per i documenti del programma tramite la classe [CView](../mfc/reference/cview-class.md). Per la stampa di base e l'anteprima di stampa, è sufficiente eseguire l'override della classe di visualizzazione [OnDraw](../mfc/reference/cview-class.md#ondraw) funzione membro, che è necessario fare comunque. Tale funzione può disegnare la visualizzazione sullo schermo, per un contesto di dispositivo stampante per una stampante effettivo, o a un contesto di dispositivo che simula la stampante sullo schermo.

È anche possibile aggiungere codice per la gestione di anteprima, impaginare i documenti stampati di aggiungervi intestazioni e piè di pagina e la stampa di documenti con più pagine.

Questa serie di articoli viene illustrato come la stampa viene implementata in Microsoft Foundation classe libreria (MFC) e come sfruttare i vantaggi dell'architettura di stampa già incorporato in framework. Gli articoli illustrano anche come MFC supporta facile implementazione della funzionalità di anteprima di stampa e come è possibile usare e modificare tale funzionalità.

## <a name="what-do-you-want-to-know-more-about"></a>Ciò che si desidera saperne di più

- [Stampa](../mfc/printing.md)

- [Architettura dell'anteprima di stampa](../mfc/print-preview-architecture.md)

- [Esempio](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>Vedere anche

[Elementi dell'interfaccia utente](../mfc/user-interface-elements-mfc.md)
