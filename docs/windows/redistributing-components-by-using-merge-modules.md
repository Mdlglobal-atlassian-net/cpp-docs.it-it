---
title: Ridistribuzione di componenti tramite modelli merge
ms.date: 11/04/2016
helpviewer_keywords:
- merge modules, using
- redistributing applications, using merge modules
ms.assetid: 93b84211-bf9b-4a78-9f22-474ac2ef7840
ms.openlocfilehash: 36dc115987b051f117264991927c2599a88deda6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514766"
---
# <a name="redistributing-components-by-using-merge-modules"></a>Ridistribuzione di componenti tramite modelli merge

Visual Studio include [modelli unione](/windows/win32/Msi/about-merge-modules) per ogni componente di Visual C++ concesso in licenza per la ridistribuzione con un'applicazione. Quando un modello merge viene compilato in un file di installazione di Windows Installer, consente una distribuzione di DLL specifiche in computer con una determinata piattaforma. Nel file di installazione specificare che i modelli unione sono prerequisiti dell'applicazione. Quando si installa Visual Studio, i modelli unione vengono installati in \Programmi\Common Files\Merge Modules\\. È possibile ridistribuire solo versioni non di debug delle DLL di Visual C++. Per altre informazioni e un collegamento a un elenco di modelli unione concessi in licenza per la ridistribuzione, vedere [Ridistribuzione di file Visual C++](redistributing-visual-cpp-files.md).

È possibile usare modelli unione per consentire l'installazione delle DLL ridistribuibili di Visual C++ nella cartella %SYSTEMROOT%\system32\. Questa tecnica è usata da Visual Studio stesso. L'installazione in questa cartella può tuttavia essere completata solo se l'utente che la esegue ha diritti di amministratore.

Non è consigliabile utilizzare i modelli unione, tranne quando non è necessario eseguire la manutenzione dell'applicazione e non esistono dipendenze da più di una versione delle DLL. Non è possibile includere in un programma di installazione modelli unione per versioni diverse della stessa DLL. Inoltre, i modelli unione rendono difficile la manutenzione delle DLL in modo indipendente dall'applicazione. È invece consigliabile installare Visual C++ Redistributable Package.

## <a name="see-also"></a>Vedere anche

[Ridistribuzione di file Visual C++](redistributing-visual-cpp-files.md)
