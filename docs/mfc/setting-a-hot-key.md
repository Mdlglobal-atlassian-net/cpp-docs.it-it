---
title: Impostazione di un tasto di scelta rapida
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
ms.openlocfilehash: ebaddb4a64a4d9d47b82fd36f118c74527554e53
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893224"
---
# <a name="setting-a-hot-key"></a>Impostazione di un tasto di scelta rapida

L'applicazione può usare le informazioni fornite da un tasto di scelta rapida ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) controllo in uno dei due modi:

- Configurare un tasto di scelta rapida globale per l'attivazione di una finestra non figlio mediante l'invio di un [messaggio WM_SETHOTKEY](/windows/desktop/inputdev/wm-sethotkey) messaggio nella finestra di attivazione.

- Configurare un tasto di scelta rapida specifici di thread chiamando la funzione di Windows [RegisterHotKey](/windows/desktop/api/winuser/nf-winuser-registerhotkey).

## <a name="see-also"></a>Vedere anche

[Uso di CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Controlli](../mfc/controls-mfc.md)

