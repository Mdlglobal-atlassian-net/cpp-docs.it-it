---
title: Finestra di progettazione della barra multifunzione (MFC)
ms.date: 11/19/2018
f1_keywords:
- vc.editors.ribbon.F1
helpviewer_keywords:
- Ribbon Designer (MFC)
- MFC Ribbon Designer
ms.assetid: 0806dfd6-7d11-471a-99e1-4072852231f9
ms.openlocfilehash: 8b66ff0f19392eb1685f8632a3fc4d9e90094304
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372794"
---
# <a name="ribbon-designer-mfc"></a>Finestra di progettazione della barra multifunzione (MFC)

La finestra di progettazione della barra multifunzione permette di creare e personalizzare barre multifunzione in applicazioni MFC. Una barra multifunzione è un elemento dell'interfaccia utente che organizza i comandi in gruppi logici. Questi gruppi sono visualizzati in schede separate in una striscia che occupa tutta la parte superiore della finestra. La barra multifunzione sostituisce la barra dei menu e le barre degli strumenti. Una barra multifunzione può migliorare significativamente l'usabilità delle applicazioni. Per ulteriori informazioni, vedere [Barre multifunzione](/windows/win32/uxguide/cmd-ribbons). La figura seguente mostra una barra multifunzione.

![Controllo della risorsa della barra multifunzione MFC](../mfc/media/ribbon_no_callouts.png "Controllo della risorsa della barra multifunzione MFC")

Nelle versioni precedenti di Visual Studio, le barre multifunzione dovevano essere create scrivendo codice che utilizza le classi della barra multifunzione MFC, ad esempio [CMFCRibbonBar Class](../mfc/reference/cmfcribbonbar-class.md). In Visual Studio 2010 e versioni successive, la finestra di progettazione della barra multifunzione fornisce un metodo alternativo per la creazione di barre multifunzione. Prima di tutto, creare e personalizzare una barra multifunzione come risorsa. Caricare quindi la risorsa barra multifunzione dal codice nell'applicazione MFC. È anche possibile usare risorse barra multifunzione e classi Ribbon MFC insieme. Ad esempio, è possibile creare una risorsa barra multifunzione e quindi aggiungervi più elementi a livello di codice al runtime.

## <a name="understanding-the-ribbon-designer"></a>Informazioni sulla finestra di progettazione della barra multifunzione

La finestra di progettazione della barra multifunzione crea e archivia la barra multifunzione come risorsa. Quando si crea una risorsa barra multifunzione, la finestra di progettazione della barra multifunzione esegue tre operazioni:

- Aggiunge una voce nello script di definizione delle risorse del progetto (*.rc). Nell'esempio seguente, IDR_RIBBON è il nome univoco che identifica la risorsa della barra multifunzione, RT_RIBBON_XML è il tipo di risorsa e ribbon.mfcribbon-ms è il nome del file di risorse.

```cpp
    IDR_RIBBON RT_RIBBON_XML      "res\\ribbon.mfcribbon-ms"
```

- Aggiunge le definizioni degli ID comando a resource.h.

```
#define IDR_RIBBON            307
```

- Crea un file di risorse della barra multifunzione (*.mfcribbon-ms) che contiene il codice XML che definisce i pulsanti, i controlli e gli attributi della barra multifunzione. Le modifiche apportate alla barra multifunzione nella finestra di progettazione della barra multifunzione vengono archiviate come XML nel file di risorse. Nell'esempio di codice riportato \*di seguito viene illustrata una parte del contenuto di un file con estensione mfcribbon-ms:

```
<RIBBON_BAR>
<ELEMENT_NAME>RibbonBar</ELEMENT_NAME>
<IMAGE>
<ID>
<NAME>IDB_BUTTONS</NAME>
<VALUE>113</VALUE>
</ID>
```

Per utilizzare la risorsa barra multifunzione nell'applicazione MFC, caricare la risorsa chiamando [CMFCRibbonBar::LoadFromResource](../mfc/reference/cmfcribbonbar-class.md#loadfromresource).

## <a name="creating-a-ribbon-by-using-the-ribbon-designer"></a>Creazione di una barra multifunzione mediante la finestra di progettazione della barra multifunzione

È possibile aggiungere una risorsa barra multifunzione al progetto MFC in due modi diversi:

- Creare un'applicazione MFC e configurare la Creazione guidata progetto MFC in modo da creare la barra multifunzione. Per ulteriori informazioni, vedere [Procedura dettagliata: creazione di un'applicazione della barra multifunzione tramite MFC](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md).

- In un progetto MFC esistente creare una risorsa barra multifunzione e caricarla. Per ulteriori informazioni, vedere [Procedura dettagliata: aggiornamento dell'applicazione scribble MFC (parte 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md).

Se il progetto contiene già una barra multifunzione codificata manualmente, MFC include funzioni che permettono di convertire la barra multifunzione esistente in una risorsa barra multifunzione. Per ulteriori informazioni, vedere [Procedura: convertire una barra multifunzione MFC esistente in una risorsa della barra multifunzione](../mfc/how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource.md).

> [!NOTE]
> Le barre multifunzione non possono essere create in applicazioni basate su finestra di dialogo. Per ulteriori informazioni, vedere [Tipo di applicazione, Creazione guidata applicazione MFC](../mfc/reference/application-type-mfc-application-wizard.md).

## <a name="customizing-ribbons"></a>Personalizzazione di barre multifunzione

Per aprire una barra multifunzione nella finestra di progettazione della barra multifunzione, fare doppio clic sulla risorsa barra multifunzione in Visualizzazione risorse. Nella finestra di progettazione è possibile aggiungere, rimuovere e personalizzare gli elementi sulla barra multifunzione, il pulsante dell'applicazione o la barra di accesso rapido. È anche possibile collegare eventi, ad esempio eventi di selezione di pulsanti ed eventi di menu, a un metodo nell'applicazione.

La figura seguente mostra i diversi componenti presenti nella finestra di progettazione della barra multifunzione.

![Finestra di progettazione della barra multifunzione MFC](../mfc/media/ribbon_designer.png "Finestra di progettazione della barra multifunzione MFC")

- **Casella degli strumenti:** Contiene controlli che possono essere trascinati nell'area di progettazione.

- **Superficie di progettazione:** Contiene la rappresentazione visiva della risorsa della barra multifunzione.

- ** [Creazione guidata classe](reference/mfc-class-wizard.md):** Elenca gli attributi dell'elemento selezionato nell'area di progettazione.

- **Finestra Visualizzazione risorse:** Visualizza le risorse che includono le risorse della barra multifunzione nel progetto.

- **Barra degli strumenti dell'editor della barra multifunzione:** Contiene comandi che consentono di visualizzare in anteprima la barra multifunzione e modificarne il tema visivo.

Gli argomenti seguenti descrivono come usare le funzionalità della finestra di progettazione della barra multifunzione:

- [Procedura: personalizzare il pulsante dell'applicazione](../mfc/how-to-customize-the-application-button.md)

- [Procedura: Personalizzare la barra di accesso rapido](../mfc/how-to-customize-the-quick-access-toolbar.md)

- [Procedura: aggiungere controlli Ribbon e gestori eventi](../mfc/how-to-add-ribbon-controls-and-event-handlers.md)

- [Procedura: caricare una risorsa Ribbon da un'applicazione MFC](../mfc/how-to-load-a-ribbon-resource-from-an-mfc-application.md)

## <a name="definitions-of-ribbon-elements"></a>Definizioni degli elementi della barra multifunzione

![Barra multifunzione MFC](../mfc/media/ribbon.png "Barra multifunzione MFC")

- **Pulsante dell'applicazione:** Pulsante visualizzato nell'angolo superiore sinistro di una barra multifunzione. Il pulsante dell'applicazione sostituisce il menu File ed è visibile anche quando la barra multifunzione è ridotta a icona. Quando si fa clic su questo pulsante, viene visualizzato un menu che contiene un elenco di comandi.

- **Barra degli strumenti Accesso rapido:** Una piccola barra degli strumenti personalizzabile che visualizza i comandi utilizzati di frequente.

- **Categoria**: Raggruppamento logico che rappresenta il contenuto di una scheda della barra multifunzione.

- **Pulsante Predefinito categoria:** Pulsante visualizzato sulla barra multifunzione quando la barra multifunzione è ridotta a icona. Quando si fa clic su questo pulsante, la categoria viene visualizzata di nuovo come menu.

- **Pannello:** Area della barra multifunzione che visualizza un gruppo di controlli correlati. Ogni categoria della barra multifunzione contiene uno o più pannelli della barra multifunzione.

- **Elementi della barra multifunzione:** Controlli nei pannelli, ad esempio pulsanti e caselle combinate. Per visualizzare i vari controlli che possono essere ospitati in una barra multifunzione, vedere [RibbonGadgets Sample: Ribbon Gadgets Application](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Vedere anche

[Elementi dell'interfaccia utente](../mfc/user-interface-elements-mfc.md)<br/>
[Uso di file di risorse](../windows/working-with-resource-files.md)
