---
title: Trascinamento di file in una finestra cornice
ms.date: 11/04/2016
helpviewer_keywords:
- drag and drop [MFC], files
- drag and drop [MFC], File Manager
- Windows Explorer [MFC]
- File Manager drag and drop support [MFC]
- files [MFC], drag and drop
- frame windows [MFC], dragging and dropping files in
- drag and drop [MFC], Windows Explorer
ms.assetid: 85560fe9-121b-4105-bd7b-216b966e19fa
ms.openlocfilehash: 0129b939e0fe2afd5dd29623bb44418bfd16c20d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240660"
---
# <a name="dragging-and-dropping-files-in-a-frame-window"></a>Trascinamento di file in una finestra cornice

La finestra cornice gestisce sia una relazione con Esplora File o File Manager.

Dall'aggiunta di inizializzazione di alcuni chiama nell'override della `CWinApp` funzione membro `InitInstance`, come descritto in [CWinApp: La classe dell'applicazione](../mfc/cwinapp-the-application-class.md), è possibile avere indirettamente aprire i file trascinati da Esplora File o File Manager vengono nella finestra cornice di finestra cornice. Visualizzare [gestione File trascinamento della selezione](../mfc/special-cwinapp-services.md).

## <a name="see-also"></a>Vedere anche

[Uso di finestre cornice](../mfc/using-frame-windows.md)
