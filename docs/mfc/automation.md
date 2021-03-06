---
title: Automazione
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers, about Automation servers
- clients, Automation
- programmatic control [MFC]
- properties [MFC], Automation
- MFC, COM support
- OLE Automation
- Automation
- servers [MFC], Automation
- Automation clients
- sample applications [MFC], Automation
- methods [MFC]
- passing parameters, Automation
- Automation method [MFC]
- Automation, passing parameters
- Automation property [MFC]
- MFC COM, Automation
- methods [MFC], Automation
ms.assetid: 329117f0-c1aa-4680-a901-bfb71277dfba
ms.openlocfilehash: e9320ccf7a21c6110c51366fa8af96596512a4a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370820"
---
# <a name="automation"></a>Automazione

L'automazione (precedentemente nota come automazione OLE) fa sì che un'applicazione possa modificare oggetti implementati in un'altra applicazione o esporli in modo che possano essere modificati.

Un [server di automazione](../mfc/automation-servers.md) è un'applicazione (un tipo di server COM) che espone le proprie funzionalità tramite interfacce COM ad altre applicazioni, chiamate [client di automazione](../mfc/automation-clients.md). L'esposizione consente ai client di automazione di automatizzare determinate funzioni accedendo direttamente agli oggetti e utilizzando i servizi che essi forniscono.

I server e i client di automazione utilizzano le interfacce COM che derivano sempre da `IDispatch` e accettano e restituiscono uno specifico set di tipi di dati denominati tipi di automazione. È possibile automatizzare qualsiasi oggetto che espone un'interfaccia di automazione, fornendo i metodi e le proprietà a cui è possibile accedere da altre applicazioni. L'automazione è disponibile sia per gli oggetti OLE che per gli oggetti COM. L'oggetto automatizzato potrebbe essere locale o remoto (in un altro computer a cui si accede attraverso una rete), quindi esistono due categorie di automazione:

- Automazione (locale).

- Automazione remota (su una rete, utilizzando Distributed COM o DCOM).

L'esposizione degli oggetti è utile quando le applicazioni forniscono funzionalità utili per altre applicazioni. Ad esempio, un controllo ActiveX è un tipo di server di automazione; l'applicazione che contiene il controllo ActiveX è il client di automazione del controllo.

Ad esempio, un elaboratore di testo potrebbe esporre la propria funzionalità di controllo ortografico ad altri programmi. L'esposizione degli oggetti consente ai fornitori di migliorare le proprie applicazioni sfruttando funzionalità preconfezionate di altre applicazioni. In questo modo, l'automazione applica alcuni dei principi della programmazione orientata a oggetti, ad esempio la possibilità di riutilizzo e l'incapsulamento, a livello delle stesse applicazioni.

Più importante è il supporto che l'automazione fornisce agli utenti e ai provider di soluzioni. Esponendo la funzionalità dell'applicazione tramite un'interfaccia comune e definita chiaramente, l'automazione consente di compilare soluzioni complete in un unico linguaggio di programmazione generale, come ad esempio Microsoft Visual Basic, anziché in diversi macro linguaggi specifici per applicazione.

Molte applicazioni commerciali, quali Microsoft Excel e Microsoft Visual C++, permettono di automatizzare gran parte delle funzionalità che offrono. Ad esempio, in Visual C++, è possibile scrivere macro VBScript per automatizzare compilazioni, aspetti della modifica di codice o attività di debug.

## <a name="passing-parameters-in-automation"></a><a name="_core_passing_parameters_in_automation"></a> Passaggio di parametri nell'automazione

Una difficoltà nel creare metodi di automazione consiste nel contribuire a fornire un meccanismo "sicuro" uniforme per passare dati tra i server e i client di automazione. L'automazione utilizza il tipo **VARIANT** per passare i dati. Il tipo **VARIANT** è un'unione contrassegnata. Contiene un membro dati per il valore (si tratta di un'unione anonima C++) e un membro dati che indica il tipo di informazioni archiviate nell'unione. Il tipo **VARIANT** supporta numerosi tipi di dati standard: interi a 2 e a 4 byte, numeri in virgola mobile a 4 e a 8 byte, stringhe e valori Boolean. Inoltre, supporta i tipi **HRESULT** (codici di errore OLE), **CURRENCY** (un tipo numerico a virgola fissa) `IUnknown` e `IDispatch` **DATE** (data e ora assoluta), nonché puntatori a e interfacce.

Il tipo **VARIANT** è incapsulato nella classe [COleVariant](../mfc/reference/colevariant-class.md) . Le classi **CURRENCY** e **DATE** di supporto sono incapsulate nelle classi [COleCurrency](../mfc/reference/colecurrency-class.md) e [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) .

## <a name="automation-samples"></a>Esempi di automazione

- [AUTOCLIK](../overview/visual-cpp-samples.md) Utilizzare questo esempio per apprendere le tecniche di automazione e come base per l'apprendimento dell'automazione remota.

- [ACDUAL](../overview/visual-cpp-samples.md) Aggiunge interfacce duali a un'applicazione server di automazione.

- [CALCDRIV](../overview/visual-cpp-samples.md) Applicazione client di automazione che controlla MFCCALC.

- [INPROC](../overview/visual-cpp-samples.md) Mostra un'applicazione server di automazione in-process.

- [IPDRIVE](../overview/visual-cpp-samples.md) Applicazione client di automazione che controlla INPROC.

- [MFCCALC](../overview/visual-cpp-samples.md) Mostra un'applicazione client di automazione.

## <a name="what-do-you-want-to-know-more-about"></a>Cosa vuoi sapere di più su

- [Client di automazione](../mfc/automation-clients.md)

- [Server di automazione](../mfc/automation-servers.md)

- [OLE](../mfc/ole-in-mfc.md)

- [tecnologia Active](../mfc/mfc-com.md)

## <a name="what-do-you-want-to-do"></a>Cosa vuoi fare

- [Aggiungere una classe di automazione](../mfc/automation-servers.md)

- [Utilizzare le librerie dei tipi](../mfc/automation-clients-using-type-libraries.md)

- [Accedere a server di automazione](../mfc/automation-servers.md)

- [Scrivere client di automazione in C++](../mfc/automation-clients.md)

## <a name="see-also"></a>Vedere anche

[MFC COM](../mfc/mfc-com.md)
