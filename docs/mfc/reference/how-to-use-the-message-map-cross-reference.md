---
title: 'Procedura: Usare il riferimento incrociato alla mappa messaggi'
ms.date: 11/04/2016
helpviewer_keywords:
- windows [MFC], message maps
ms.assetid: 2e863d23-9e58-45ba-b5e4-a8ceefccd0c8
ms.openlocfilehash: 58659dbf4e4bc817381faaef930334a80f664b03
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/14/2019
ms.locfileid: "65612155"
---
# <a name="how-to-use-the-message-map-cross-reference"></a>Procedura: Usare il riferimento incrociato alla mappa messaggi

Nelle voci con etichettate \<memberFxn >, scrivere una funzione membro per un oggetto derivato [CWnd](../../mfc/reference/cwnd-class.md) classe. Assegnare alla funzione un nome. Altre funzioni, come `OnActivate`, sono funzioni membro della classe `CWnd`. Se chiamate, passano il messaggio alla funzione di Windows `DefWindowProc`. Per elaborare i messaggi di notifica di Windows, eseguire l'override della funzione corrispondente `CWnd` nella classe derivata. La funzione deve chiamare la funzione di cui si è eseguito l'override nella classe base per consentire alla classe base e a Windows di rispondere al messaggio.

In ogni caso, inserire il prototipo della funzione nell'intestazione della classe derivata da `CWnd` e codificare la voce della mappa messaggi come indicato.

Vengono utilizzati i seguenti termini:

|Termine|Definizione|
|----------|----------------|
|ID|Qualsiasi ID elemento menu definito dall'utente (WM_COMMAND (messaggi)) o l'ID di controllo (messaggi di notifica finestra figlio).|
|"message" e "wNotifyCode"|ID messaggi di Windows come definiti in WINDOWS.H.|
|nMessageVariable|Nome di una variabile che contiene il valore restituito dal `RegisterWindowMessage` funzione Windows.|

## <a name="see-also"></a>Vedere anche

[Mappe messaggi](../../mfc/reference/message-maps-mfc.md)
