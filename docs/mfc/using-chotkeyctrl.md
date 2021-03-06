---
title: Utilizzo di CHotKeyCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- keys, hot and CHotKeyCtrl
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: 9b207117-d848-4224-8888-c3d197bb0c95
ms.openlocfilehash: e2002d96a1eba913e260fa92281f730355a83ca5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447237"
---
# <a name="using-chotkeyctrl"></a>Utilizzo di CHotKeyCtrl

Un controllo tasto di scelta, rappresentato dalla classe [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md), è una finestra in cui viene visualizzata una rappresentazione testuale della combinazione di tasti a cui sono associati i tipi di utente, ad esempio CTRL + MAIUSC + Q. Mantiene inoltre una rappresentazione interna di questa chiave sotto forma di codice di chiave virtuale e di un set di flag che rappresentano lo stato di spostamento. Il controllo del tasto di scelta non imposta effettivamente il tasto di scelta, operazione che corrisponde al programma. Per un elenco di codici chiave virtuali standard, vedere Winuser. h.

Utilizzare un controllo tasto di scelta rapida per ottenere l'input di un utente per il quale tasto di scelta da associare a una finestra o a un thread. I controlli tasto di scelta vengono spesso usati nelle finestre di dialogo, ad esempio quando si chiede all'utente di assegnare un tasto di scelta. È responsabilità del programma recuperare i valori che descrivono il tasto di scelta dal controllo del tasto di scelta e chiamare le funzioni appropriate per associare il tasto di scelta a una finestra o a un thread.

## <a name="what-do-you-want-to-know-more-about"></a>Che cosa si vuole sapere

- [Uso di un controllo tasto di scelta rapida](../mfc/using-a-hot-key-control.md)

- [Impostazione di un tasto di scelta rapida](../mfc/setting-a-hot-key.md)

- [Tasti di scelta rapida globali](../mfc/global-hot-keys.md)

- [Tasti di scelta rapida specifici di thread](../mfc/thread-specific-hot-keys.md)

## <a name="see-also"></a>Vedere anche

[Controlli](../mfc/controls-mfc.md)
