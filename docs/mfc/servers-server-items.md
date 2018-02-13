---
title: 'Server: Elementi Server | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- server items, implementing
- servers [MFC], server items
- architecture [MFC], server-item
- server items
- OLE server applications [MFC], server items
ms.assetid: 28ba81a1-726a-4728-a52d-68bc7efd5a3c
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2fe196eb561c336e45402de6c390146a0d77bea4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="servers-server-items"></a>Server: elementi server
Quando un contenitore avvia un server in modo che l'utente possa modificare un elemento OLE incorporato o collegato, l'applicazione server crea un "elemento server". L'elemento server, ovvero un oggetto di una classe derivata da `COleServerItem`, fornisce un'interfaccia tra il documento server e l'applicazione contenitore.  
  
 La classe `COleServerItem` definisce diverse funzioni membro di cui è possibile eseguire l'override che vengono chiamate da OLE, in genere in risposta alle richieste del contenitore. Gli elementi server possono rappresentare una parte o l'intero documento server. Quando un elemento OLE è incorporato nel documento contenitore, l'elemento server rappresenta l'intero documento server. Quando l'elemento OLE è collegato, l'elemento server può rappresentare una parte del documento server o l'intero documento, a seconda che il collegamento sia verso una parte o l'intero documento.  
  
 Nel [HIERSVR](../visual-cpp-samples.md) di esempio, ad esempio, la classe dell'elemento server, **CServerItem**, dispone di un membro che è un puntatore a un oggetto della classe **CServerNode**. Il **CServerNode** oggetto è un nodo nel documento dell'applicazione HIERSVR, ovvero una struttura ad albero. Quando il **CServerNode** oggetto è il nodo radice, il **CServerItem** oggetto rappresenta l'intero documento. Quando il **CServerNode** oggetto è un nodo figlio, il **CServerItem** oggetto rappresenta una parte del documento. Vedere l'esempio OLE MFC [HIERSVR](../visual-cpp-samples.md) per un esempio di questa interazione.  
  
##  <a name="_core_implementing_server_items"></a>Implementazione di elementi Server  
 Se si utilizza la creazione guidata applicazione per scrivere il codice "di avvio" dell'applicazione, per includere gli elementi server nel codice di avvio è sufficiente scegliere una delle opzioni server dalla pagina Opzioni OLE. Se si aggiungono elementi server a un'applicazione esistente, attenersi ai passaggi indicati di seguito:  
  
#### <a name="to-implement-a-server-item"></a>Per implementare un elemento server  
  
1.  Derivare una classe da `COleServerItem`.  
  
2.  Nella classe derivata, eseguire l'override della funzione membro `OnDraw`.  
  
     Il framework chiama `OnDraw` per eseguire il rendering dell'elemento OLE in un metafile. L'applicazione contenitore utilizza tale metafile per eseguire il rendering dell'elemento. La classe di visualizzazione dell'applicazione dispone inoltre di una funzione membro `OnDraw`, utilizzata per eseguire il rendering dell'elemento quando l'applicazione server è attiva.  
  
3.  Implementare un override di `OnGetEmbeddedItem` per la classe documento server. Per ulteriori informazioni, vedere l'articolo [server: implementazione di documenti Server](../mfc/servers-implementing-server-documents.md) e l'esempio OLE MFC [HIERSVR](../visual-cpp-samples.md).  
  
4.  Implementare la funzione membro `OnGetExtent` della classe dell'elemento server. Il framework chiama questa funzione per recuperare la dimensione dell'elemento. L'implementazione predefinita non esegue alcuna operazione.  
  
##  <a name="_core_a_tip_for_server.2d.item_architecture"></a>Un suggerimento per l'architettura dell'elemento Server  
 Come indicato nella [implementazione di elementi Server](#_core_implementing_server_items), le applicazioni server devono essere in grado di eseguire il rendering di elementi nella visualizzazione del server e nel metafile utilizzato dall'applicazione contenitore. In applicazione, la classe di visualizzazione dell'architettura della libreria Microsoft Foundation classe `OnDraw` funzione membro esegue il rendering l'elemento quando viene modificato (vedere [CView:: OnDraw](../mfc/reference/cview-class.md#ondraw) nel *riferimenti alla libreria di classi* ). L'elemento server `OnDraw` esegue il rendering l'elemento in un metafile in tutti gli altri casi (vedere [COleServerItem:: OnDraw](../mfc/reference/coleserveritem-class.md#ondraw)).  
  
 È possibile evitare la duplicazione del codice scrivendo funzioni di supporto nella classe del documento server e chiamandole dalle funzioni `OnDraw` nelle classi dell'elemento server e di visualizzazione. L'esempio OLE MFC [HIERSVR](../visual-cpp-samples.md) utilizza questa strategia: le funzioni **CServerDoc** e **CServerItem:: OnDraw** entrambi chiamano **CServerView**  per il rendering dell'elemento.  
  
 La visualizzazione e l'elemento hanno entrambi funzioni membro `OnDraw`, perché eseguono il disegno in circostanze diverse. La visualizzazione deve considerare fattori quali lo zoom, la dimensione e l'ambito di selezione, il ritaglio e gli elementi dell'interfaccia utente quali le barre di scorrimento. L'elemento server, invece, disegna sempre l'intero oggetto OLE.  
  
 Per ulteriori informazioni, vedere [CView:: OnDraw](../mfc/reference/cview-class.md#ondraw), [COleServerItem](../mfc/reference/coleserveritem-class.md), [COleServerItem:: OnDraw](../mfc/reference/coleserveritem-class.md#ondraw), e [COleServerDoc:: OnGetEmbeddedItem](../mfc/reference/coleserverdoc-class.md#ongetembeddeditem)nel *riferimenti alla libreria di classe*.  
  
## <a name="see-also"></a>Vedere anche  
 [Server](../mfc/servers.md)
