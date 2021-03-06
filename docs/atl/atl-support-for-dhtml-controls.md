---
title: Supporto ATL per controlli DHTML
ms.date: 11/04/2016
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
- DHTML controls
ms.assetid: 4ba98098-da5d-4362-96ad-8372f816c307
ms.openlocfilehash: dd8ac616d127c3307c1c432c0b3c9bc2ef1d6181
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223292"
---
# <a name="atl-support-for-dhtml-controls"></a>Supporto ATL per controlli DHTML

Usa ATL, è possibile creare un controllo con funzionalità di DHTML (Dynamic HTML). Un controllo DHTML ATL:

- Ospita il controllo WebBrowser.

- Specifica, utilizzare il linguaggio HTML, l'interfaccia utente (UI) del controllo DHTML.

- Accede tramite l'interfaccia, l'oggetto WebBrowser e i relativi metodi [IWebBrowser2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752127\(v=vs.85\)).

- Gestisce la comunicazione tra il codice C++ e HTML.

Un controllo DHTML è simile a qualsiasi altro controllo ATL, ma il controllo DHTML include un'interfaccia dispatch aggiuntiva. Vedere la figura nella [identificazione degli elementi del progetto controllo DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md) per un'illustrazione delle interfacce fornite nel progetto di DHTML predefinito.

È possibile visualizzare il controllo DHTML ATL in un Web browser o altro contenitore, ad esempio ActiveX Control Test Container.

## <a name="in-this-section"></a>In questa sezione

[Identificazione degli elementi del progetto dei controlli DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md)<br/>
Descrive gli elementi di un progetto controllo DHTML.

[Chiamata al codice C++ da DHTML](../atl/calling-cpp-code-from-dhtml.md)<br/>
Fornisce un esempio di chiamata di codice C++ da un controllo DHTML.

[Creazione di un controllo DHTML ATL](../atl/creating-an-atl-dhtml-control.md)<br/>
Elenca i passaggi per la creazione di un controllo DHTML.

[Test del controllo DHTML di ATL](../atl/testing-the-atl-dhtml-control.md)<br/>
Viene illustrato come compilare e testare il progetto controllo DHTML iniziale.

[Modifica del un controllo DHTML ATL](../atl/modifying-the-atl-dhtml-control.md)<br/>
Viene illustrato come aggiungere alcune funzionalità al controllo.

[Test del controllo modificato DHTML ATL](../atl/testing-the-modified-atl-dhtml-control.md)<br/>
Viene illustrato come compilare e testare la funzionalità del controllo aggiunto.

## <a name="related-sections"></a>Sezioni correlate

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Fornisce collegamenti ad argomenti concettuali sulla programmazione con Active Template Library.
