---
title: 'Contenitori: funzionalità avanzate'
ms.date: 11/04/2016
helpviewer_keywords:
- links [MFC], to embedded OLE objects
- containers [MFC], links to embedded OLE objects
- containers [MFC], advanced features
- container/server applications [MFC]
- embedded objects [MFC]
- OLE controls [MFC], containers
- OLE containers [MFC], advanced features
- server/container applications [MFC]
- containers [MFC], container applications
ms.assetid: 221fd99c-b138-40fa-ad6a-974e3b3ad1f8
ms.openlocfilehash: cf130bf8dead5c59548821658b979785c4d54726
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376489"
---
# <a name="containers-advanced-features"></a>Contenitori: funzionalità avanzate

In questo articolo vengono descritti i passaggi necessari per incorporare funzionalità avanzate facoltative nelle applicazioni contenitore esistenti. Tali funzionalità sono:

- [Un'applicazione che funge sia da contenitore che da server](#_core_creating_a_container_server_application)

- [Un collegamento OLE a un oggetto incorporato](#_core_links_to_embedded_objects)

## <a name="creating-a-containerserver-application"></a><a name="_core_creating_a_container_server_application"></a>Creazione di un'applicazione contenitore/serverCreating a Container/Server Application

Un'applicazione contenitore/server è un'applicazione che funge sia da contenitore che da server. Microsoft Word per Windows ne è un esempio. È possibile incorporare i documenti di Word per Windows in altre applicazioni ed è inoltre possibile importare elementi nei documenti di Word per Windows. La procedura che consente di trasformare un'applicazione sia in un contenitore che in un server completo (non è possibile creare un'applicazione contenitore/server ridotto) è analoga a quella per la creazione di un server completo.

L'articolo [Server: Implementazione](../mfc/servers-implementing-a-server.md) di un server elenca una serie di attività necessarie per implementare un'applicazione server. Per convertire un'applicazione contenitore in un'applicazione contenitore/server, è necessario eseguire alcune di quelle attività, con l'aggiunta di codice al contenitore. Di seguito vengono elencati i principali aspetti da considerare:

- Il codice del contenitore creato dalla creazione guidata applicazioni inizializza il sottosistema OLE. Non sarà necessario modificare o aggiungere nulla per tale supporto.

- Laddove la classe base di una classe di documento è `COleDocument`, modificare la classe base in `COleServerDoc`.

- Eseguire l'override `COleClientItem::CanActivate` per evitare di modificare gli elementi sul posto quando il server stesso è utilizzato per la modifica sul posto.

   Ad esempio, l'esempio OLE MFC [OCLIENT](../overview/visual-cpp-samples.md) ha incorporato un elemento creato dall'applicazione contenitore/server. Aprire l'applicazione OCLIENT e modificare sul posto l'elemento creato dall'applicazione contenitore/server. Durante la modifica dell'elemento dell'applicazione, si decide di incorporare un elemento creato dall'esempio OLE MFC [HIERSVR](../overview/visual-cpp-samples.md). A tale scopo, non utilizzare l'attivazione sul posto. È necessario aprire completamente HIERSVR per attivare questo elemento. Poiché la libreria MFC non supporta questa funzionalità OLE, l'override di `COleClientItem::CanActivate` consente di verificare questa situazione ed evitare un possibile errore di runtime nell'applicazione.

Se si crea una nuova applicazione e si desidera che funga da applicazione contenitore/server, selezionare tale opzione nella finestra di dialogo Opzioni OLE nella creazione guidata applicazione e tale supporto verrà creato automaticamente. Per ulteriori informazioni, vedere l'articolo [Cenni preliminari: creazione di un contenitore di controlli ActiveX](../mfc/reference/creating-an-mfc-activex-control-container.md). Per informazioni sugli esempi MFC, vedere [Esempi MFC](../overview/visual-cpp-samples.md#mfc-samples).

Notare che non è possibile inserire un'applicazione MDI in se stessa. Un'applicazione contenitore/server non può essere inserita in se stessa a meno che non sia un'applicazione SDI.

## <a name="links-to-embedded-objects"></a><a name="_core_links_to_embedded_objects"></a>Collegamenti a oggetti incorporatiLinks to Embedded Objects

I collegamenti alla funzionalità Oggetti incorporati consentono all'utente di creare un documento con un collegamento OLE a un oggetto incorporato all'interno dell'applicazione contenitore. Ad esempio, è possibile creare un documento in un elaboratore di testo contenente un foglio di calcolo incorporato. Se l'applicazione supporta i collegamenti a oggetti incorporati, è possibile incollare un collegamento al foglio di calcolo contenuto nel documento dell'elaboratore di testo. Questa funzionalità consente all'applicazione di utilizzare le informazioni contenute nel foglio di lavoro senza sapere da dove provenga originariamente.

#### <a name="to-link-to-embedded-objects-in-your-application"></a>Per eseguire il collegamento a oggetti incorporati nell'applicazione

1. Derivare la classe del documento da `COleLinkingDoc` anziché da `COleDocument`.

1. Creare un ID di classe OLE (**CLSID**) per l'applicazione utilizzando il generatore di ID di classe incluso negli strumenti di sviluppo OLE.

1. Registrare l'applicazione con OLE.

1. Creare un oggetto `COleTemplateServer` come membro della classe dell'applicazione.

1. Nella funzione membro `InitInstance` della classe dell'applicazione, effettuare le operazioni seguenti:

   - Connettere l'oggetto `COleTemplateServer` ai modelli di documento chiamando la funzione membro `ConnectTemplate` dell'oggetto.

   - Chiamare `COleTemplateServer::RegisterAll` la funzione membro per registrare tutti gli oggetti di classe con il sistema OLE.

   - Chiamare `COleTemplateServer::UpdateRegistry`. L'unico `UpdateRegistry` parametro da *OAT_CONTAINER* se l'applicazione non viene avviata con l'opzione "/Embedded". In questo modo l'applicazione viene registrata come contenitore in grado di supportare collegamenti a oggetti incorporati.

      Se l'applicazione viene avviata con l'opzione "/Embedded", la finestra principale non dovrebbe venire visualizzata, analogamente a un'applicazione server.

L'esempio OLE MFC [OCLIENT](../overview/visual-cpp-samples.md) implementa questa funzionalità. Per un esempio di come viene `InitInstance` eseguita questa operazione, vedere la funzione in *OCLIENT. CPP* di questa applicazione di esempio.

## <a name="see-also"></a>Vedere anche

[Contenitori](../mfc/containers.md)<br/>
[Server](../mfc/servers.md)
