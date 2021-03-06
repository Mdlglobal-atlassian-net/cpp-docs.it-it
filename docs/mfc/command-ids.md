---
title: ID comandi
ms.date: 11/04/2016
helpviewer_keywords:
- command IDs, MFC
- command IDs
ms.assetid: e0171a2b-45b9-41fa-945d-ec2f7602ded0
ms.openlocfilehash: 76071105e72f1ca4a851b9cdb76d5f1a96f44edb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219899"
---
# <a name="command-ids"></a>ID comandi

Un comando è descritto dal relativo ID di comando da solo (con codifica nel **WM_COMMAND** messaggio). Questo ID viene assegnato all'oggetto di interfaccia utente che genera il comando. In genere, gli ID sono denominati per le funzionalità dell'oggetto dell'interfaccia utente a che sono assegnati.

Ad esempio, un elemento Cancella tutto del menu Modifica potrebbe essere assegnato un ID, ad esempio **ID_EDIT_CLEAR_ALL**. La libreria di classi sono disponibili alcuni ID, in particolare per i comandi che il framework gestisce se stesso, ad esempio **ID_EDIT_CLEAR_ALL** oppure **ID_FILE_OPEN**. Si creeranno altri ID di comando manualmente.

Quando si creano i proprio menu nell'oggetto visivo C++ editor dei menu, è consigliabile seguire la libreria di classi di convenzione di denominazione come illustrato **ID_FILE_OPEN**. [Comandi standard](../mfc/standard-commands.md) illustra i comandi standard definiti dalla libreria di classi.

## <a name="see-also"></a>Vedere anche

[Oggetti dell'interfaccia utente e ID comando](../mfc/user-interface-objects-and-command-ids.md)
