---
title: Classi Document-Template
ms.date: 11/04/2016
helpviewer_keywords:
- document templates [MFC], classes
ms.assetid: 901749e9-8048-44a0-b5e2-361554650a73
ms.openlocfilehash: 82b9ce4c242df7c85ada0722b2c1e993a0cf3f81
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446909"
---
# <a name="document-template-classes"></a>Classi Document-Template

Gli oggetti modello di documento coordinano la creazione di oggetti finestra di documento, visualizzazione e cornice quando viene creato un nuovo documento o vista.

[CDocTemplate](../mfc/reference/cdoctemplate-class.md)<br/>
Classe base per i modelli di documento. Questa classe non verrà mai utilizzata direttamente. usare invece una delle altre classi modello documento derivate da questa classe.

[CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)<br/>
Modello per i documenti nell'interfaccia a documenti multipli (MDI). Le applicazioni MDI possono avere più documenti aperti alla volta.

[CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md)<br/>
Modello per i documenti nell'interfaccia a documento singolo (SDI). Per le applicazioni SDI è aperto un solo documento alla volta.

## <a name="related-class"></a>Classe correlata

[CCreateContext](../mfc/reference/ccreatecontext-structure.md)<br/>
Struttura passata da un modello di documento alle funzioni di creazione di finestre per coordinare la creazione di oggetti documento, visualizzazione e finestra cornice.

## <a name="see-also"></a>Vedere anche

[Panoramica della classe](../mfc/class-library-overview.md)
