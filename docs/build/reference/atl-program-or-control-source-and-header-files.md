---
title: File di intestazione e di origine di un controllo o programma ATL
ms.date: 11/04/2016
helpviewer_keywords:
- file types [C++], ATL source and headers
ms.assetid: cb65372f-4880-4007-b582-a52eaa568fd1
ms.openlocfilehash: 5c1e5fc111b38fc9e4173598f11fbad7a658d755
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707502"
---
# <a name="atl-program-or-control-source-and-header-files"></a>File di intestazione e di origine di un controllo o programma ATL

I file seguenti vengono creati quando si crea un progetto ATL in Visual Studio, a seconda delle opzioni selezionate per il progetto creato.

Tutti questi file si trovano nella directory *Projname* e anche nella cartella File di intestazione (file con estensione h) oppure nella cartella File di origine (file con estensione cpp) in Esplora soluzioni.

|Nome file|Description|
|---------------|-----------------|
|*Projname*.h|File di inclusione principale contenente le definizioni di interfaccia di C++ e le dichiarazioni di GUID degli elementi definiti in ATLSample.idl. Viene rigenerato da MIDL durante la compilazione.|
|*Projname*.cpp|File di origine principale del programma. Contiene l'implementazione delle esportazioni di DLL per un server in-process e l'implementazione di `WinMain` per un server locale. Per un servizio, implementa anche tutte le funzioni di gestione del servizio.|
|Resource.h|File di intestazione per il file di risorse.|
|StdAfx.cpp|Include i file StdAfx.h e Atlimpl.cpp.|
|StdAfx.h|Include i file di intestazione ATL.|

## <a name="see-also"></a>Vedere anche

[Tipi di file creati per i progetti di Visual Studio C++](file-types-created-for-visual-cpp-projects.md)<br>
[File di intestazione e di origine di un controllo o programma MFC](mfc-program-or-control-source-and-header-files.md)<br>
[Progetti CLR](files-created-for-clr-projects.md)
