---
title: Creazione di un provider OLE DB
ms.date: 10/13/2018
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: f73017c3-c89f-41a6-a306-ea992cf6092c
ms.openlocfilehash: 3e46e87b0d5d538a0f9fd7e231debfef3fa95210
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62361893"
---
# <a name="creating-an-ole-db-provider"></a>Creazione di un provider OLE DB

Il metodo consigliato per creare un provider OLE DB è usare le procedure guidate per creare un progetto ATL COM e un provider e quindi modificare i file usando i modelli OLE DB. Quando si personalizza il provider, è possibile commento indesiderato delle proprietà e aggiungere le interfacce facoltative.

I passaggi di base sono descritti di seguito:

1. Usare la **Creazione guidata progetto ATL** per creare i file di progetto di base e il **Creazione guidata Provider OLEDB ATL** per creare il provider (selezionare **Provider OLEDB ATL** dal **Installed** > **Visual C++** > **ATL** cartella **Aggiungi nuovo elemento**).

   > [!NOTE]
   > Il progetto deve includere il supporto MFC prima di aggiungere un **Provider OLEDB ATL**.

1. Modificare il codice nel `Execute` nel metodo [CCustomRowset(CustomRS.h)](cmyproviderrowset-myproviderrs-h.md). Per un esempio, vedere [durante la lettura di stringhe in un Provider OLE DB](../../data/oledb/reading-strings-into-the-ole-db-provider.md).

1. Modifica la proprietà è mappata nel [CustomDS.h](cmyprovidersource-myproviderds-h.md), [CustomSess.h](cmyprovidersession-myprovidersess-h.md), e [CustomRS.h](cmyproviderrowset-myproviderrs-h.md). La procedura guidata consente di creare mappe delle proprietà che contengono tutte le proprietà che è possibile implementare un provider. Scorrere le mappe delle proprietà e rimuovere o rimuovere i commenti per le proprietà che non è necessario che il provider di supporto.

1. Aggiornare PROVIDER_COLUMN_MAP, che è reperibile nel [CCustomRowset(CustomRS.h)](cmyproviderrowset-myproviderrs-h.md). Per un esempio, vedere [memorizzazione di stringhe In un Provider OLE DB](../../data/oledb/storing-strings-in-the-ole-db-provider.md).

1. Quando si è pronti per testare il provider, è possibile eseguirne il test quando si tenta di trovare il provider in un'enumerazione di provider. Per esempi di codice di test che consente di trovare un provider in un'enumerazione, vedere la [CATDB](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/catdb) e [DBVIEWER](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer) oppure l'esempio nella [implementazione di un Consumer semplice](../../data/oledb/implementing-a-simple-consumer.md).

1. Aggiungere eventuali interfacce aggiuntive desiderate. Per un esempio, vedere [miglioramento di un Provider semplice in sola lettura](../../data/oledb/enhancing-the-simple-read-only-provider.md).

   > [!NOTE]
   > Per impostazione predefinita, le procedure guidate di generano il codice al livello 0 conforme a OLE DB. Per assicurarsi che l'applicazione a livello 0 conforme, non rimuovere una delle interfacce generate dalla procedura guidata dal codice.

## <a name="see-also"></a>Vedere anche

[Esempio: CatDB Visualizzazione dello Schema di origine dati](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/catdb)<br/>
[Esempio DBViewer: Database Browser](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer)
