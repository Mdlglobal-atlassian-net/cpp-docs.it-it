---
title: L'invio e ricezione di messaggi | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows messages [MFC], handling in MFC
- control-notification messages [MFC]
- messages [MFC], receiving
- messages [MFC], MFC
- MFC, messages
- messages [MFC], sending
ms.assetid: 9ce189cb-b259-4c3b-b6f2-9cfbed18b98b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0c587e3b84ae7afd7869a5c1405d8ddc4ab417b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="message-sending-and-receiving"></a>Invio e ricezione di messaggi
Prendere in considerazione la parte del processo e modalità di risposta il framework di invio.  
  
 La maggior parte dei risultati di messaggi dall'interazione dell'utente con il programma. I comandi vengono generati tramite clic del mouse nelle voci di menu o pulsanti della barra degli strumenti o tramite i tasti di scelta rapida. L'utente genera inoltre messaggi di Windows, ad esempio, spostare o ridimensionare una finestra. Quando si verificano eventi, ad esempio l'avvio del programma o la chiusura, come windows di ottenere o perde lo stato attivo e così via, vengono inviati altri messaggi di Windows. Clic del mouse o altre interazioni utente con un controllo, ad esempio un controllo pulsante o una casella di elenco in una finestra di dialogo vengono generati messaggi di notifica del controllo.  
  
 Il **eseguire** funzione membro di classe `CWinApp` recupera i messaggi e li invia alla finestra appropriata. La maggior parte dei messaggi di comando vengono inviati alla finestra cornice principale dell'applicazione. Il `WindowProc` predefiniti da classe libreria Ottiene i messaggi e li instrada in modo diverso, a seconda della categoria del messaggio ricevuto.  
  
 Si consideri ora la parte del processo di ricezione.  
  
 Il destinatario di un messaggio iniziale deve essere un oggetto window. I messaggi di Windows sono in genere gestiti direttamente da tale oggetto finestra. I messaggi di comando, in genere originari finestra cornice principale dell'applicazione, vengono indirizzati alla catena di destinazione comando descritto in [comandi (Routing)](../mfc/command-routing.md).  
  
 Ogni oggetto in grado di ricevere messaggi o comandi ha il proprio messaggio mapping che abbina un messaggio o un comando con il nome del gestore.  
  
 Quando un oggetto destinazione comando riceve un messaggio o un comando, viene cercato propria mappa messaggi per trovare una corrispondenza. Se viene rilevato un gestore per il messaggio, chiama il gestore. Per ulteriori informazioni sulla modalità con cui vengono eseguita la ricerca di mappe messaggi, vedere [come il Framework ricerche mappe messaggi](../mfc/how-the-framework-searches-message-maps.md). Vedere la figura [comandi nel Framework](../mfc/user-interface-objects-and-command-ids.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Chiamata di un gestore dal framework](../mfc/how-the-framework-calls-a-handler.md)
