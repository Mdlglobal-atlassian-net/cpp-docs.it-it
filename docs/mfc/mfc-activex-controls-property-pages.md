---
title: 'Controlli ActiveX MFC: pagine delle proprietà'
ms.date: 11/19/2018
helpviewer_keywords:
- DDP_ functions [MFC]
- MFC ActiveX controls [MFC], properties
- property pages [MFC], MFC ActiveX controls
- DoDataExchange method [MFC]
- OLEIVERB_PROPERTIES
- CPropertyPageDialog class [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 1506f87a-9fd6-4505-8380-0dbc9636230e
ms.openlocfilehash: c31d13e03483f8632f17a526da75ebe8e21bccbf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364572"
---
# <a name="mfc-activex-controls-property-pages"></a>Controlli ActiveX MFC: pagine delle proprietà

Le pagine delle proprietà consentono all'utente di un controllo ActiveX di visualizzare e modificare le proprietà del controllo ActiveX. È possibile accedere a queste proprietà richiamando una finestra di dialogo delle proprietà del controllo, che contiene una o più pagine delle proprietà che forniscono un'interfaccia grafica personalizzata per la visualizzazione e la modifica delle proprietà del controllo.

>[!IMPORTANT]
> ActiveX è una tecnologia legacy che non deve essere utilizzata per il nuovo sviluppo. Per ulteriori informazioni sulle tecnologie moderne che sostituiscono ActiveX, vedere [Controlli ActiveX](activex-controls.md).

Le pagine delle proprietà dei controlli ActiveX vengono visualizzate in due modi:

- Quando viene richiamato il verbo Properties del controllo (**OLEIVERB_PROPERTIES**), il controllo apre una finestra di dialogo delle proprietà modale che contiene le pagine delle proprietà del controllo.

- Il contenitore può visualizzare la propria finestra di dialogo non modale che mostra le pagine delle proprietà del controllo selezionato.

La finestra di dialogo delle proprietà (illustrata nella figura seguente) è costituita da un'area per la visualizzazione della pagina delle proprietà corrente, schede per il passaggio da una pagina delle proprietà all'altra e una raccolta di pulsanti che eseguono attività comuni, ad esempio la chiusura della finestra di dialogo della pagina delle proprietà, l'annullamento delle modifiche apportate o l'applicazione immediata di eventuali modifiche al controllo ActiveX.

![Finestra di dialogo Proprietà per Circ3](../mfc/media/vc373i1.gif "Finestra di dialogo Proprietà per Circ3") <br/>
Finestra di dialogo Proprietà

In questo articolo vengono trattati argomenti relativi all'utilizzo delle pagine delle proprietà in un controllo ActiveX. incluse le seguenti:

- [Implementazione della pagina delle proprietà predefinita per un controllo ActiveXImplementing the default property page for an ActiveX control](#_core_implementing_the_default_property_page)

- [Aggiunta di controlli a una pagina delle proprietà](#_core_adding_controls_to_a_property_page)

- [Personalizzazione della funzione DoDataExchange](#_core_customizing_the_dodataexchange_function)

Per altre informazioni sull'uso delle pagine delle proprietà in un controllo ActiveX, vedere gli articoli seguenti:For more information on using property pages in an ActiveX control, see the following articles:

- [Controlli ActiveX MFC: aggiunta di un'altra pagina delle proprietà personalizzata](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)

- [Controlli ActiveX MFC: utilizzo delle pagine delle proprietà predefinite](../mfc/mfc-activex-controls-using-stock-property-pages.md)

Per informazioni sull'utilizzo delle finestre delle proprietà in un'applicazione MFC diversa da un controllo ActiveX, vedere [Finestre delle proprietà](../mfc/property-sheets-mfc.md).

## <a name="implementing-the-default-property-page"></a><a name="_core_implementing_the_default_property_page"></a>Implementazione della pagina delle proprietà predefinitaImplementing the Default Property Page

Se si utilizza la Creazione guidata controllo ActiveX per creare il progetto di controllo, la Creazione guidata controllo ActiveX fornisce una classe di pagina delle proprietà predefinita per il controllo derivato dalla [classe COlePropertyPage](../mfc/reference/colepropertypage-class.md). Inizialmente, questa pagina delle proprietà è vuota, ma è possibile aggiungervi qualsiasi controllo della finestra di dialogo o un set di controlli. Poiché la Creazione guidata controllo ActiveX crea una sola classe di `COlePropertyPage`pagina delle proprietà per impostazione predefinita, è necessario creare classi di pagine delle proprietà aggiuntive (derivate anche da ) utilizzando Visualizzazione classi. Per ulteriori informazioni su questa procedura, vedere [Controlli ActiveX MFC: aggiunta di un'altra pagina delle proprietà personalizzate](../mfc/mfc-activex-controls-adding-another-custom-property-page.md).

L'implementazione di una pagina delle proprietà (in questo caso, l'impostazione predefinita) è un processo in tre passaggi:Implementing a property page (in this case, the default) is a three-step process:

#### <a name="to-implement-a-property-page"></a>Per implementare una pagina delle proprietàTo implement a property page

1. Aggiungere `COlePropertyPage`una classe derivata da -al progetto di controllo. Se il progetto è stato creato utilizzando la Creazione guidata controllo ActiveX (come in questo caso), la classe della pagina delle proprietà predefinita esiste già.

1. Utilizzare l'editor finestre per aggiungere controlli al modello di pagina delle proprietà.

1. Personalizzare `DoDataExchange` la funzione `COlePropertyPage`della classe derivata per scambiare valori tra il controllo della pagina delle proprietà e il controllo ActiveX.

Ad esempio, le procedure seguenti utilizzano un controllo semplice (denominato "Sample"). L'esempio è stato creato utilizzando la Creazione guidata controllo ActiveX e contiene solo la proprietà predefinita Caption.

## <a name="adding-controls-to-a-property-page"></a><a name="_core_adding_controls_to_a_property_page"></a>Aggiunta di controlli a una pagina delle proprietàAdding Controls to a Property Page

#### <a name="to-add-controls-to-a-property-page"></a>Per aggiungere controlli a una pagina delle proprietàTo add controls to a property page

1. Con il progetto di controllo aperto, aprire Visualizzazione risorse.

1. Fare doppio clic sull'icona della directory **Dialog.**

1. Aprire la finestra di dialogo IDD_PROPPAGE_SAMPLE.

   La Creazione guidata controllo ActiveX aggiunge il nome del progetto alla fine dell'ID della finestra di dialogo, in questo caso Sample.

1. Trascinare il controllo selezionato dalla Casella degli strumenti nell'area della finestra di dialogo.

1. Per questo esempio, un controllo etichetta di testo "Caption :" e un controllo casella di modifica con un identificatore di IDC_CAPTION sono sufficienti.

1. Fare clic su **Salva** sulla barra degli strumenti per salvare le modifiche.

Ora che l'interfaccia utente è stata modificata, è necessario collegare la casella di modifica con il Caption proprietà. Questa operazione viene eseguita nella `CSamplePropPage::DoDataExchange` sezione seguente modificando la funzione.

## <a name="customizing-the-dodataexchange-function"></a><a name="_core_customizing_the_dodataexchange_function"></a>Personalizzazione della funzione DoDataExchange

La funzione [CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) della pagina delle proprietà consente di collegare i valori delle pagine delle proprietà con i valori effettivi delle proprietà nel controllo. Per stabilire i collegamenti, è necessario mappare i campi della pagina delle proprietà appropriati alle rispettive proprietà del controllo.

Questi mapping vengono implementati utilizzando la pagina delle proprietà **DDP_** le funzioni. Le funzioni **DDP_** funzionano come le funzioni **DDX_** utilizzate nelle finestre di dialogo MFC standard, con un'eccezione. Oltre al riferimento a una variabile membro, **DDP_** funzioni accettano il nome della proprietà del controllo. Di seguito è riportata `DoDataExchange` una voce tipica nella funzione per una pagina delle proprietà.

[!code-cpp[NVC_MFC_AxUI#31](../mfc/codesnippet/cpp/mfc-activex-controls-property-pages_1.cpp)]

Questa funzione associa la variabile membro *m_caption* della pagina `DDP_TEXT` delle proprietà alla proprietà Caption, utilizzando la funzione.

Dopo aver inserito il controllo della pagina delle proprietà, è necessario stabilire un collegamento tra il `DDP_Text` controllo della pagina delle proprietà, IDC_CAPTION, e la proprietà effettiva del controllo, Caption, utilizzando la funzione come descritto in precedenza.

[Le pagine delle proprietà](../mfc/reference/property-pages-mfc.md) sono disponibili per altri tipi di controllo finestra di dialogo, ad esempio caselle di controllo, pulsanti di opzione e caselle di riepilogo. La tabella seguente elenca l'intero insieme di **DDP_** le funzioni della pagina delle proprietà e i relativi scopi:

### <a name="property-page-functions"></a>Funzioni della pagina delle proprietà

|Nome della funzione|Utilizzare questa funzione per collegare|
|-------------------|-------------------------------|
|`DDP_CBIndex`|Indice della stringa selezionata in una casella combinata con una proprietà del controllo.|
|`DDP_CBString`|Stringa selezionata in una casella combinata con una proprietà del controllo. La stringa selezionata può iniziare con le stesse lettere del valore della proprietà, ma non deve necessariamente corrispondere completamente.|
|`DDP_CBStringExact`|Stringa selezionata in una casella combinata con una proprietà del controllo. La stringa selezionata e il valore stringa della proprietà devono corrispondere esattamente.|
|`DDP_Check`|Casella di controllo con una proprietà del controllo.|
|`DDP_LBIndex`|Indice della stringa selezionata in una casella di riepilogo con una proprietà del controllo.|
|`DDP_LBString`|Stringa selezionata in una casella di riepilogo con una proprietà del controllo. La stringa selezionata può iniziare con le stesse lettere del valore della proprietà, ma non deve necessariamente corrispondere completamente.|
|`DDP_LBStringExact`|Stringa selezionata in una casella di riepilogo con una proprietà del controllo. La stringa selezionata e il valore stringa della proprietà devono corrispondere esattamente.|
|`DDP_Radio`|Pulsante di opzione con una proprietà del controllo.|
|`DDP_Text`|Testo con una proprietà del controllo.|

## <a name="see-also"></a>Vedere anche

[Controlli ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Classe COlePropertyPage](../mfc/reference/colepropertypage-class.md)
