---
title: Stili per il controllo Progress
ms.date: 11/19/2018
helpviewer_keywords:
- PBS_SMOOTH style
- progress controls [MFC], styles
- PBS_VERTICAL style
- CProgressCtrl class [MFC], styles
ms.assetid: 39eb8081-bc20-4552-91b9-e7cdd1b7d8ae
ms.openlocfilehash: 3adbd32456b1375bd2dc8574220e083ca3d83ee9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306814"
---
# <a name="styles-for-the-progress-control"></a>Stili per il controllo Progress

Quando si crea inizialmente il controllo progress ([CProgressCtrl:: Create](../mfc/reference/cprogressctrl-class.md#create)), utilizzare il *dwStyle* parametro per specificare gli stili desiderati della finestra per il controllo di stato. Nell'elenco seguente sono illustrati in maniera dettagliata gli stili applicabili alla finestra. Il controllo ignora qualsiasi stile della finestra diverso da quelli elencati di seguito. Si consiglia di creare sempre il controllo come finestra figlio, in genere di una finestra di dialogo padre.

|Stile di finestra|Effetto|
|------------------|------------|
|WS_BORDER|Crea un bordo intorno alla finestra.|
|WS_CHILD|Crea una finestra figlio (deve sempre essere utilizzato per `CProgressCtrl`).|
|WS_CLIPCHILDREN|Esclude l'area occupata dalle finestre figlio quando si disegna nella finestra padre. Utilizzato quando si crea la finestra padre.|
|WS_CLIPSIBLINGS|Taglia le finestre figlio le une rispetto alle altre.|
|WS_DISABLED|Crea una finestra che inizialmente è disabilitata.|
|WS_VISIBLE|Crea una finestra che inizialmente è visibile.|
|WS_TABSTOP|Specifica che il controllo può ricevere lo stato attivo quando l'utente preme il tasto TAB per passare ad esso.|

Inoltre, è possibile specificare due stili che si applicano solo al controllo di stato, PBS_VERTICAL e PBS_SMOOTH.

Usare PBS_VERTICAL per orientare il controllo verticalmente anziché in orizzontale. Usare PBS_SMOOTH per riempire il controllo completamente anziché visualizzare quadratini separati che riempiono gradualmente il controllo.

Senza PBS_SMOOTH (stile):

![Stile della barra di stato standard](../mfc/media/vc4ruw1.gif "stile della barra di stato Standard")

Con gli stili PBS_SMOOTH e PBS_VERTICAL:

![Stato di avanzamento stile, uniforme e verticale](../mfc/media/vc4ruw2.gif "stile, uniforme e verticale dell'indicatore di stato")

Per altre informazioni, vedere [stili Window](../mfc/reference/styles-used-by-mfc.md#frame-window-styles-mfc) nel *riferimento MFC*.

## <a name="see-also"></a>Vedere anche

[Uso di CProgressCtrl](../mfc/using-cprogressctrl.md)
