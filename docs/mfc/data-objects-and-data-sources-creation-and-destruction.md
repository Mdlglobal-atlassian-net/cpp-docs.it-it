---
title: 'Oggetti dati e origini dati (OLE): creazione e distruzione'
ms.date: 11/04/2016
helpviewer_keywords:
- destroying data objects [MFC]
- object creation [MFC], data source objects
- data sources [MFC], and data objects
- data source objects [MFC], creating
- destruction [MFC], data sources
- data source objects [MFC], destroying
- data objects [MFC], creating
- data objects [MFC], destroying
- data sources [MFC], role
- data sources [MFC], destroying
- destruction [MFC], data objects
- data sources [MFC], creating
ms.assetid: ac216d54-3ca5-4ce7-850d-cd1f6a90d4f1
ms.openlocfilehash: 58b68ca9597fd2a03cffb2bbab327dbc72d09599
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371209"
---
# <a name="data-objects-and-data-sources-creation-and-destruction"></a>Oggetti dati e origini dati (OLE): creazione e distruzione

Come spiegato nell'articolo [Oggetti dati e origini dati (OLE),](../mfc/data-objects-and-data-sources-ole.md)gli oggetti dati e le origini dati rappresentano entrambi i lati di un trasferimento di dati. Questo articolo descrive quando creare ed eliminare questi oggetti e origini per eseguire i trasferimenti dei dati nel modo corretto, con informazioni su:

- [Creazione di oggetti dati](#_core_creating_data_objects)

- [Eliminazione di oggetti dati](#_core_destroying_data_objects)

- [Creazione di origini dati](#_core_creating_data_sources)

- [Eliminazione delle origini dati](#_core_destroying_data_sources)

## <a name="creating-data-objects"></a><a name="_core_creating_data_objects"></a>Creazione di oggetti datiCreating Data Objects

Gli oggetti dati vengono usati dall'applicazione di destinazione, ovvero il client o il server. Un oggetto dati nell'applicazione di destinazione è un'estremità di una connessione tra l'applicazione di origine e quella di destinazione. Un oggetto dati nell'applicazione di destinazione viene usato per accedere ai dati nell'origine dati e per interagirvi.

Un oggetto dati è necessario in due situazioni comuni. La prima situazione è quella in cui nell'applicazione vengono rilasciati dati usando il trascinamento della selezione. La seconda situazione è quella in cui si sceglie Incolla o Incolla speciale dal menu Modifica.

In una situazione che prevede il trascinamento della selezione non è necessario creare un oggetto dati. Un puntatore a un oggetto dati esistente verrà passato alla funzione `OnDrop`. Questo oggetto dati viene creato dal framework come parte dell'operazione di trascinamento e rilascio e verrà anche eliminato dal framework. Questo non sempre avviene quando l'operazione Incolla viene eseguita con un altro metodo. Per ulteriori informazioni, vedere [Eliminazione di oggetti dati](#_core_destroying_data_objects).

Se l'applicazione esegue un'operazione Incolla o Incolla speciale, è consigliabile creare un oggetto `COleDataObject` e chiamarne la funzione membro `AttachClipboard`. In questo modo, l'oggetto dati viene associato ai dati negli Appunti. È quindi possibile usare questo oggetto dati nella funzione Incolla.

## <a name="destroying-data-objects"></a><a name="_core_destroying_data_objects"></a>Eliminazione di oggetti dati

Se si segue lo schema descritto in [Creazione di oggetti dati](#_core_creating_data_objects), l'eliminazione degli oggetti dati è un aspetto semplice dei trasferimenti di dati. L'oggetto dati creato nella funzione Incolla verrà eliminato definitivamente da MFC quando viene restituita la funzione Incolla.

Se si segue un altro metodo per gestire le operazioni Incolla, assicurarsi che l'oggetto dati venga eliminato al termine dell'operazione Incolla. Fino a quando l'oggetto dati non viene eliminato definitivamente, sarà impossibile per qualsiasi applicazione copiare correttamente dati negli Appunti.

## <a name="creating-data-sources"></a><a name="_core_creating_data_sources"></a>Creazione di origini datiCreating Data Sources

Le origini dati vengono usate dall'origine del trasferimento dei dati, che può essere il lato client o il lato server del trasferimento. Un'origine dati nell'applicazione di origine è un'estremità di una connessione tra l'applicazione di origine e quella di destinazione. Un oggetto dati nell'applicazione di destinazione viene usato per interagire con i dati nell'origine dati.

Le origini dati vengono create quando un'applicazione deve copiare dati negli Appunti. Ecco uno scenario tipico:

1. L'utente seleziona alcuni dati.

1. L'utente sceglie **Copia** (o **Taglia)** dal menu **Modifica** o avvia un'operazione di trascinamento della selezione.

1. A seconda della progettazione del programma, l'applicazione crea un oggetto `COleDataSource` o un oggetto da una classe derivata da `COleDataSource`.

1. I dati selezionati vengono inseriti nell'origine dati chiamando una delle funzioni nel gruppo `COleDataSource::CacheData` o `COleDataSource::DelayRenderData`.

1. L'applicazione chiama la funzione membro `SetClipboard` (o la funzione membro `DoDragDrop` se si tratta di un'operazione di trascinamento della selezione) che appartiene all'oggetto creato nel passaggio 3.

1. Se si tratta di `DoDragDrop` un'operazione **Taglia** o restituisce **DROPEFFECT_MOVE**, i dati selezionati nel passaggio 1 vengono eliminati dal documento.

Questo scenario viene implementato dagli esempi OLE MFC [OCLIENT](../overview/visual-cpp-samples.md) e [HIERSVR](../overview/visual-cpp-samples.md). Esaminare l'origine per ogni classe derivata da `CView` dell'applicazione per tutte le funzioni tranne `GetClipboardData` e `OnGetClipboardData`. Queste due funzioni si trovano nelle implementazioni delle classi derivate da `COleClientItem` o `COleServerItem`. Questi programmi di esempio offrono un buon esempio dell'implementazione di questi concetti.

Un'altra situazione in cui si potrebbe voler creare un oggetto `COleDataSource` si verifica quando si modifica il comportamento predefinito di un'operazione di trascinamento e rilascio. Per altre informazioni, vedere l'articolo [Trascinamento della selezione OLE: Personalizzare il trascinamento della selezione.](../mfc/drag-and-drop-ole.md#customize-drag-and-drop)

## <a name="destroying-data-sources"></a><a name="_core_destroying_data_sources"></a>Eliminazione delle origini dati

Le origini dati devono essere eliminate definitivamente dall'applicazione che ne è attualmente responsabile. Nelle situazioni in cui si passa l'origine dati a OLE, ad esempio la `pDataSrc->InternalRelease`chiamata a [COleDataSource::DoDragDrop](../mfc/reference/coledatasource-class.md#dodragdrop), è necessario chiamare . Ad esempio:

[!code-cpp[NVC_MFCListView#1](../atl/reference/codesnippet/cpp/data-objects-and-data-sources-creation-and-destruction_1.cpp)]

Se l'origine dati non è stata passata a OLE, si è responsabili della sua eliminazione definitiva, come per tutti i normali oggetti C++.

Per ulteriori informazioni, vedere [Trascinamento della selezione,](../mfc/drag-and-drop-ole.md) [Appunti](../mfc/clipboard.md)e [Modifica di oggetti dati e origini dati](../mfc/data-objects-and-data-sources-manipulation.md).

## <a name="see-also"></a>Vedere anche

[Oggetti dati e origini dati (OLE)](../mfc/data-objects-and-data-sources-ole.md)<br/>
[Classe COleDataObject](../mfc/reference/coledataobject-class.md)<br/>
[Classe COleDataSource](../mfc/reference/coledatasource-class.md)
