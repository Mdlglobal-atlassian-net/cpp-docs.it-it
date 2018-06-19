---
title: L'impostazione di un tasto di scelta rapida | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3987ddee98ae35e02a181e38cd71f181801aeb61
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379645"
---
# <a name="setting-a-hot-key"></a>Impostazione di un tasto di scelta rapida
L'applicazione può utilizzare le informazioni fornite da un tasto di scelta rapida ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) controllo in uno dei due modi:  
  
-   Impostare un tasto di scelta rapida globale per l'attivazione di una finestra non figlio inviando un [messaggio WM_SETHOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646284) messaggio nella finestra di attivazione.  
  
-   Impostare un tasto di scelta rapida specifici di thread chiamando la funzione Windows [RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309).  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [Controlli](../mfc/controls-mfc.md)

