---
title: Tipi di elenchi immagini
ms.date: 11/04/2016
helpviewer_keywords:
- lists [MFC], image
- image lists [MFC], types of
- CImageList class [MFC], types
ms.assetid: bee5e7c3-78f5-4037-a136-9c50d67cdee5
ms.openlocfilehash: 939aad78b7cf8cca9c940bae11892d23dbb659cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180850"
---
# <a name="types-of-image-lists"></a>Tipi di elenchi immagini

Esistono due tipi di elenchi immagini ([CImageList](../mfc/reference/cimagelist-class.md)): non mascherata e mascherato. Un "elenco di immagine non mascherata" è costituito da una bitmap a colori che contiene una o più immagini. Un "elenco di immagini mascherate" è costituito da due immagini bitmap della stessa dimensione. Il primo è una bitmap a colori che contiene le immagini e la seconda è una bitmap monocromatica che contiene una serie di maschere, ovvero uno per ogni immagine nella bitmap prima.

Uno degli overload del `Create` membro funzione accetta un flag che indica se l'elenco di immagini è mascherato. (Gli altri overload creano elenchi di immagini con maschera.)

Quando viene disegnata un'immagine non mascherata, viene semplicemente copiato nel contesto di dispositivo di destinazione; vale a dire l'oggetto viene disegnato sul colore dello sfondo esistenti del contesto di dispositivo. Quando viene disegnata un'immagine mascherata, i bit dell'immagine vengono combinati con i bit della maschera, che in genere produce aree trasparenti nell'immagine bitmap in cui viene illustrato il colore di sfondo del contesto di dispositivo di destinazione tramite. È possibile specificare diversi stili di disegno quando si disegna un'immagine mascherata. Ad esempio, è possibile specificare che l'immagine di retinatura per indicare un oggetto selezionato.

## <a name="see-also"></a>Vedere anche

[Uso di CImageList](../mfc/using-cimagelist.md)<br/>
[Controlli](../mfc/controls-mfc.md)
