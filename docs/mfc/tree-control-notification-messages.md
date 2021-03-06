---
title: Messaggi di notifica del controllo Tree
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], tree controls
- messages [MFC], notification
- CTreeCtrl class [MFC], notifications
- notifications [MFC], CTreeCtrl
- tree controls [MFC], notification messages
ms.assetid: ac7013b4-91dd-4668-bd75-439ca0680ef9
ms.openlocfilehash: 90e2e112d7862dfed7d8af31cfb72ff45633a2c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62181639"
---
# <a name="tree-control-notification-messages"></a>Messaggi di notifica del controllo Tree

Un controllo albero ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) invia i messaggi di notifica seguente come WM_NOTIFY messaggi:

|Messaggio di notifica|Descrizione|
|--------------------------|-----------------|
|TVN_BEGINDRAG|Segnala l'avvio di un'operazione di trascinamento e rilascio|
|TVN_BEGINLABELEDIT|Segnala l'avvio della modifica dell'etichetta sul posto|
|TVN_BEGINRDRAG|Segnala l'avvio di un'operazione di trascinamento e rilascio, usando il pulsante destro del mouse|
|TVN_DELETEITEM|Segnala l'eliminazione di un elemento specifico|
|TVN_ENDLABELEDIT|Segnala la fine della modifica dell'etichetta|
|TVN_GETDISPINFO|Richiede le informazioni che richiede il controllo albero per visualizzare un elemento|
|TVN_ITEMEXPANDED|Segnala che un elemento padre dell'elenco di elementi figlio è stato espanso o compresso|
|TVN_ITEMEXPANDING|Segnala che un elemento padre dell'elenco di elementi figlio sta per essere espansi o compressi|
|TVN_KEYDOWN|Segnala un evento della tastiera|
|TVN_SELCHANGED|Segnala che la selezione è stato modificato da un elemento a un altro|
|TVN_SELCHANGING|Segnala che la selezione sta per essere modificato da un elemento in un altro|
|TVN_SETDISPINFO|Notifica per aggiornare le informazioni memorizzate per un elemento|

## <a name="see-also"></a>Vedere anche

[Uso di CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Controlli](../mfc/controls-mfc.md)
