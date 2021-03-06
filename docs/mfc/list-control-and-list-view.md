---
title: Controllo List e visualizzazione elenco
ms.date: 11/04/2016
helpviewer_keywords:
- CListView class [MFC], and CListCtrl
- views [MFC], list and list control
- CListCtrl class [MFC], and CListView
- list views [MFC]
- list controls [MFC], List view
ms.assetid: 7aee1c48-b158-4399-be0b-be366993665e
ms.openlocfilehash: 5c9612a22eab27d568c0dbb86d29ba031fe5985e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62365332"
---
# <a name="list-control-and-list-view"></a>Controllo List e visualizzazione elenco

Per praticità, MFC incapsula il controllo di elenco in due modi. È possibile usare i controlli elenco:

- Diretto, incorporando un [CListCtrl](../mfc/reference/clistctrl-class.md) oggetto in una classe di finestra di dialogo.

- Indirettamente, tramite classi [CListView](../mfc/reference/clistview-class.md).

`CListView` rende più facile l'integrazione di un controllo elenco con l'architettura documento/visualizzazione MFC, che incapsula il controllo in modo analogo a [CEditView](../mfc/reference/ceditview-class.md) incapsula un controllo di modifica: il controllo occupa l'intera area della superficie di visualizzazione MFC. (La visualizzazione *viene* il controllo, eseguire il cast a `CListView`.)

Oggetto `CListView` oggetto eredita da [CCtrlView](../mfc/reference/cctrlview-class.md) e relative classi base e aggiunge una funzione membro per recuperare il controllo elenco sottostante. Usare Visualizza membri per lavorare con la vista come una vista. Usare la [GetListCtrl](../mfc/reference/clistview-class.md#getlistctrl) funzione membro per ottenere l'accesso alle funzioni membro del controllo elenco. Usare questi membri:

- Aggiungere, eliminare o modificare "elementi" nell'elenco.

- Impostare o ottenere attributi del controllo elenco.

Per ottenere un riferimento per la `CListCtrl` sottostante una `CListView`, chiamare `GetListCtrl` dalla classe di visualizzazione elenco:

[!code-cpp[NVC_MFCListView#4](../atl/reference/codesnippet/cpp/list-control-and-list-view_1.cpp)]

Questo argomento descrive entrambe le direzioni per usare il controllo elenco.

## <a name="see-also"></a>Vedere anche

[Uso di CListCtrl](../mfc/using-clistctrl.md)<br/>
[Controlli](../mfc/controls-mfc.md)
