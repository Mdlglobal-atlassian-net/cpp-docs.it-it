---
title: Creazione di un'applicazione contenitore di documenti attivi
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- active document containers [MFC], creating
- MFC COM, active document containment
- applications [MFC], active document container
ms.assetid: 14e2d022-a6c5-4249-8712-706b0f4433f7
ms.openlocfilehash: 965778fd5d17aa416b198c101edc3a445a39580b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152943"
---
# <a name="creating-an-active-document-container-application"></a>Creazione di un'applicazione contenitore di documenti attivi

Il modo più semplice e consigliato per creare un'applicazione contenitore di documenti attivi consiste nel creare un'applicazione contenitore EXE MFC mediante la Creazione guidata applicazione MFC, quindi modificare l'applicazione per supportare il contenimento dei documenti attivi.

#### <a name="to-create-an-active-document-container-application"></a>Per creare un'applicazione contenitore di documenti attivi

1. Dal **File** menu, fare clic su **Project**dal **New** sottomenu.

1. Nel riquadro sinistro, fare clic su **Visual C++** tipo di progetto.

1. Selezionare **applicazione MFC** dal riquadro di destra.

1. Denominare il progetto *MyProj*, fare clic su **OK**.

1. Selezionare il **supporto documenti compositi** pagina.

1. Selezionare il **contenitore** oppure **contenitore/server completo** opzione.

1. Selezionare il **contenitore di documenti attivi** casella di controllo.

1. Scegliere **Fine**.

1. Una volta completata la generazione dell'applicazione tramite la Creazione guidata applicazione MFC, aprire i seguenti file in Esplora soluzioni:

   - *MyProjview.cpp*

1. Nelle *MyProjview. cpp*, apportare le modifiche seguenti:

   - In `CMyProjView::OnPreparePrinting` sostituire il contenuto della funzione con il seguente codice:

     [!code-cpp[NVC_MFCDocView#56](../mfc/codesnippet/cpp/creating-an-active-document-container-application_1.cpp)]

   `OnPreparePrinting` fornisce il supporto di stampa. Questo codice sostituisce `DoPreparePrinting`, ovvero la preparazione predefinita alla stampa.

   Il contenimento del documento attivo fornisce uno schema di stampa avanzato:

   - È possibile chiamare prima il documento attivo tramite relativo `IPrint` interfaccia e ordinargli di eseguire la stampa. Questo comportamento è diverso dal contenimento OLE precedente, in cui il contenitore doveva eseguire il rendering di un'immagine dell'elemento contenuto nella stampante `CDC` oggetto.

   - Se l'operazione fallisce, ordinare all'elemento di contenuto di stampa tramite relativo `IOleCommandTarget` interfaccia

   - Se l'operazione fallisce, eseguire il rendering dell'elemento.

   Le funzioni membro statiche `COleDocObjectItem::OnPrint` e `COleDocObjectItem::OnPreparePrinting`, come implementate nel codice precedente, gestiscono questo schema di stampa avanzato.

1. Aggiungere qualsiasi implementazione personalizzata e compilare l'applicazione.

## <a name="see-also"></a>Vedere anche

[Contenimento dei documenti attivi](../mfc/active-document-containment.md)
