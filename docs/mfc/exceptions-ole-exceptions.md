---
title: 'Eccezioni: eccezioni OLE'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE, exceptions
- OLE exceptions [MFC]
- exceptions [MFC], OLE
- exception handling [MFC], OLE
- OLE exceptions [MFC], classes for handling
ms.assetid: 2f8e0161-b94f-48bb-a5a2-6f644b192527
ms.openlocfilehash: 1606a0f5a86996345e12024cf6416afdf6bdc82b
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246702"
---
# <a name="exceptions-ole-exceptions"></a>Eccezioni: eccezioni OLE

Le tecniche e le funzionalità per la gestione delle eccezioni in OLE sono uguali a quelle utilizzate per gestire le altre eccezioni. Per ulteriori informazioni sulla gestione delle eccezioni, vedere l' [articolo C++ procedure consigliate moderne per le eccezioni e la gestione degli errori](../cpp/errors-and-exception-handling-modern-cpp.md).

Tutti gli oggetti eccezione derivano dalla classe base astratta `CException`. MFC fornisce due classi per gestire le eccezioni OLE:

- [COleException](../mfc/reference/coleexception-class.md) Per la gestione delle eccezioni OLE generali.

- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) Per la generazione e la gestione delle eccezioni di invio OLE (automazione).

La differenza tra queste due classi è la quantità di informazioni che forniscono e il punto in cui vengono utilizzate. `COleException` dispone di un membro dati pubblico che contiene il codice di stato OLE per l'eccezione. `COleDispatchException` fornisce ulteriori informazioni, incluse le seguenti:

- Un codice di errore specifico dell'applicazione

- Una descrizione dell'errore, ad esempio "disco pieno"

- Una Guida contestuale attraverso cui l'applicazione può fornire informazioni aggiuntive per l'utente

- Il nome del file della Guida dell'applicazione

- Il nome dell'applicazione che ha generato l'eccezione

`COleDispatchException` fornisce ulteriori informazioni in modo che possano essere utilizzate con prodotti come Microsoft Visual Basic. La descrizione dell'errore verbale può essere utilizzata in una finestra di messaggio o in un'altra notifica; le informazioni della Guida possono essere utilizzate per consentire all'utente di rispondere alle condizioni che hanno causato l'eccezione.

Due funzioni globali corrispondono alle due classi di eccezioni OLE: [AfxThrowOleException](../mfc/reference/exception-processing.md#afxthrowoleexception) e [AfxThrowOleDispatchException](../mfc/reference/exception-processing.md#afxthrowoledispatchexception). Utilizzarle per generare rispettivamente eccezioni OLE generali ed eccezioni OLE dispatch.

## <a name="see-also"></a>Vedere anche

[Gestione delle eccezioni](../mfc/exception-handling-in-mfc.md)
