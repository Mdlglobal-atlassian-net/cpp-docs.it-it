---
title: Spostarsi all'interno del codice C++ in Visual Studio
description: Usare vari strumenti in Visual Studio per esplorare la codebase di C++.
ms.date: 05/28/2019
ms.openlocfilehash: 932694db70019924557259d4defe802b53ef0f89
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079083"
---
# <a name="navigate-c-code-in-visual-studio"></a>Spostarsi all'interno del codice C++ in Visual Studio

Visual Studio offre una suite di strumenti che consentono di esplorare la codebase in modo rapido ed efficiente.

## <a name="open-an-included-file"></a>Aprire un file incluso

Fare clic con il pulsante destro del mouse su una direttiva `#include` e quindi scegliere **Passa al documento**. In alternativa, selezionare **F12** con il cursore sulla riga per aprire il file.

![C&#43; &#43; passare all'opzione di menu Document](../ide/media/go-to-document.png "Vai al documento")

## <a name="toggle-headercode-file"></a>Attiva/disattiva file di codice/intestazione

È possibile spostarsi tra un file di intestazione e il file di origine corrispondente. Fare clic con il pulsante destro del mouse in un punto qualsiasi nel file e scegliere **Attiva/disattiva file di codice/intestazione**. In alternativa, è possibile selezionare **CTRL+K**, **CTRL+O**.

## <a name="go-to-definitiondeclaration"></a>Vai a definizione/Vai a dichiarazione

È possibile passare alla definizione di un simbolo di codice facendo clic con il pulsante destro del mouse nell'editor e scegliendo **Vai a definizione** o premendo **F12**. È possibile passare a una dichiarazione in modo analogo usando il menu di scelta rapida visualizzato facendo clic con il pulsante destro del mouse oppure premendo **CTRL+F12**.

![C&#43; &#43; Vai a definizione](../ide/media/go-to-def.png "Vai a definizione")

## <a name="go-to"></a>Vai a

**Vai a** fa riferimento a un set di funzionalità di navigazione ognuna delle quali genera un determinato tipo di risultato in base ai filtri specificati.

È possibile aprire **Vai a** con **CTRL+,** . Questa azione crea una casella di ricerca sul documento che si sta modificando.

![C&#43; &#43; Vai a](../ide/media/go-to-cpp.png "Vai a")

**Vai a** include questi filtri di ricerca:

- **Vai alla riga** (**CTRL + G**): passa rapidamente a una riga diversa del documento corrente.
- **Vai a tutti** (**CTRL +,** ) o (**CTRL + T**): i risultati della ricerca includono tutti gli elementi seguenti.
- **Vai al file** (**CTRL 1, F**): consente di cercare i file nella soluzione.
- **Vai al tipo** (**CTRL 1, T**): i risultati della ricerca includono:
  - Classi, struct ed enumerazioni.
  - Interfacce e delegati (solo codice gestito).
- **Vai al membro** (**CTRL 1, M**): i risultati della ricerca includono:
  - Variabili globali e funzioni globali.
  - Variabili membro di classe e funzioni membro.
  - Costanti.
  - Elementi di enumerazione.
  - Proprietà ed eventi.
- **Vai al simbolo** (**CTRL 1, S**): i risultati della ricerca includono:
  - Risultati di Vai al tipo e Vai al membro.
  - Tutti i costrutti di linguaggio C++ rimanenti, comprese le macro.

Quando si richiama per la prima volta **Vai a** con **CTRL+** , **Vai a tutti** viene attivato senza filtri sui risultati della ricerca. È quindi possibile selezionare il filtro desiderato usando i pulsanti accanto alla casella di ricerca. Richiamare un filtro specifico usando i tasti di scelta rapida corrispondenti. Questa operazione apre la casella di ricerca **Vai a** con il filtro preselezionato. Tutti i tasti di scelta rapida sono configurabili.

Per applicare un filtro di testo, avviare la query di ricerca con il carattere corrispondente del filtro seguito da uno spazio. (**Vai alla riga** può facoltativamente omettere lo spazio). Questi filtri di testo sono disponibili:

- Vai a tutti: (nessun filtro testo)
- Vai alla riga numero: :
- Vai al file: f
- Vai al tipo: t
- Vai al membro: m
- Vai al simbolo: #

L'esempio seguente mostra i risultati di un'operazione *Vai al file* con il filtro "f":

![&#43; &#43; Menu Vai a](../ide/media/vs2017-go-to-results.png "Menu Vai a")

Per vedere l'elenco dei filtri testo digitare ? seguito da uno spazio. È anche possibile accedere ai comandi **Vai a** con il menu **Modifica**. Si tratta di un altro modo per rammentarsi dei principali tasti di scelta rapida di **Vai a**.

![&#43; &#43; Menu Vai a](../ide/media/go-to-menu-cpp.png "Menu Vai a")

## <a name="find-or-find-in-files"></a>Trova o Cerca nei file

È possibile eseguire una ricerca di testo per qualsiasi elemento nella soluzione con **Trova** (**CTRL+F**) o **Cerca nei file** (**CTRL+SHIFT+F**).

**Trova** può essere applicato a una selezione, al documento corrente, a tutti i documenti aperti, al progetto corrente o all'intera soluzione. È possibile usare espressioni regolari e testo normale. Evidenzia automaticamente, inoltre, tutte le corrispondenze nell'IDE.

![C&#43; &#43; Find](../ide/media/find-cpp.png "Find")

**Cerca nei file** è una versione più potente di **Trova** che consente di visualizzare i risultati nella finestra **Risultati ricerca**. È possibile cercare le dipendenze del codice esterne, filtrare per tipi di file e altro ancora.

![C&#43; &#43; ricerca nei file](../ide/media/find-in-files-cpp.png "Cerca nei file")

È possibile organizzare i risultati di **Cerca nei file** in due finestre e accodare insieme i risultati di più ricerche. Selezionare un risultato per passare alla posizione corrispondente nel file.

![C&#43; &#43; ricerca nei file](../ide/media/vs2017-find-in-files-results.png "Cerca nei file")

Per altre informazioni, vedere [Cerca nei file](/visualstudio/ide/find-in-files) nella documentazione di Visual Studio.

## <a name="find-all-references"></a>Trova tutti i riferimenti

Per trovare tutti gli utilizzi di un simbolo nella codebase, posizionare il cursore sul simbolo o subito dopo, fare clic con il pulsante destro del mouse e quindi scegliere **Trova tutti i riferimenti**. È possibile filtrare, ordinare o raggruppare i risultati in molti modi diversi. I risultati vengono popolati in modo incrementale. Sono classificati come letture o scritture per aiutare a distinguere che cosa fa parte della soluzione rispetto a cosa appartiene a intestazioni di sistema o altre librerie.

![C&#43; &#43; trova tutti i riferimenti](../ide/media/find-all-references-results-cpp.png "Trova tutti i riferimenti")

I risultati sono raggruppati in base alle categorie seguenti:

- Progetto, quindi definizione
- Solo definizione
- Definizione, quindi progetto
- Definizione, quindi percorso
- Definizione, progetto, quindi percorso

#### <a name="filter-results"></a>Filtrare i risultati

Per filtrare i risultati, passare il mouse su una colonna e selezionare l'icona del filtro che viene visualizzata. È possibile filtrare i risultati dalla prima colonna per nascondere elementi quali i riferimenti a stringhe e commenti che non è necessario visualizzare.

![C&#43; &#43; trova tutti i filtri dei riferimenti](../ide/media/find-all-references-filters-cpp.png "Filtri trova tutti i riferimenti")

- **Risultati confermati**: riferimenti al codice effettivo al simbolo cercato. La ricerca di una funzione membro denominata `Size`, ad esempio, restituisce tutti i riferimenti a `Size` che corrispondono all'ambito della classe che definisce `Size`.

- **Risultati non confermati**: questo filtro è disattivato per impostazione predefinita perché Mostra i simboli il cui nome corrisponde a, ma non i riferimenti effettivi al simbolo che si sta cercando. Se si dispone di due classi ognuna delle quali definisce una funzione membro denominata `Size`, ad esempio, e si esegue una ricerca di `Size` su un riferimento da un oggetto `Class1`, tutti i riferimenti a `Size` provenienti da `Class2` verranno visualizzati come non confermati.

- **Risultati non elaborati**: le operazioni **Find All References** possono richiedere tempo per essere completate su codebase più grandi, quindi nell'elenco dei risultati vengono visualizzati i risultati "non elaborati". Per i risultati non elaborati la corrispondenza al nome del simbolo cercato è stata confermata, ma non è stato ancora appurato se si tratta di riferimenti effettivi. È possibile attivare questo filtro per ottenere risultati più rapidi. Tenere semplicemente presente che alcuni risultati potrebbero non essere riferimenti effettivi.

#### <a name="sort-results"></a>Ordinare i risultati

È possibile ordinare i risultati in base a qualsiasi colonna selezionando la colonna. Per passare dall'ordine crescente all'ordine decrescente e viceversa, selezionare di nuovo la colonna.

## <a name="navigation-bar"></a>Barra di spostamento

È possibile passare alla definizione di un tipo in un file o ai membri del tipo usando la **barra di spostamento** che si trova sopra la finestra dell'editor.

![Barra&#43; &#43; di spostamento C](../ide/media/navbar-cpp.png "Barra di spostamento")

## <a name="see-also"></a>Vedere anche

- [Leggere e comprendere il codice C++](read-and-understand-code-cpp.md)</br>
- [Scrittura e refactoring del codice (C++)](read-and-understand-code-cpp.md)</br>
- [Collaborare con Live Share per C++](live-share-cpp.md)
