---
title: Abilitazione e disabilitazione dei servizi OLE DB
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 445f97eb-32a8-41c2-ad26-1169f78a074f
ms.openlocfilehash: 3016126d09b39ec74f4acb758a2176be05052648
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210964"
---
# <a name="enabling-and-disabling-ole-db-services"></a>Abilitazione e disabilitazione dei servizi OLE DB

Il gestore dei componenti del servizio OLE DB Confronta le proprietà specificate dal consumer con quelle supportate dal provider per determinare se i singoli componenti del servizio possono essere utilizzati per soddisfare la funzionalità estesa richiesta dal consumer. Se, ad esempio, un'applicazione richiede un cursore scorrevole e il provider supporta solo un cursore di sola trasmissione, Gestione componenti del servizio utilizzerà il componente del servizio del motore di cursori client per fornire funzionalità scorrevoli. Se l'applicazione si basa sulla funzionalità estesa supportata per impostazione predefinita nel set di righe del provider e l'applicazione non imposta in modo esplicito le proprietà per richiedere tale funzionalità, è possibile che la funzionalità non venga visualizzata nel set di righe restituito dal client Motore di cursore. Per essere interoperabile, le applicazioni devono impostare sempre le proprietà per richiedere in modo esplicito le funzionalità estese, se necessario.

In alcuni casi, potrebbe essere necessario disabilitare i singoli servizi di OLE DB per funzionare correttamente con le applicazioni esistenti che fanno supposizioni sulle caratteristiche di un provider. I servizi OLE DB offrono la possibilità di disabilitare singoli servizi, o tutti i servizi, in modalità connessione per connessione o per tutte le applicazioni che utilizzano un singolo provider.

## <a name="see-also"></a>Vedere anche

[Servizi e pooling di risorse OLE DB](../../data/oledb/ole-db-resource-pooling-and-services.md)
