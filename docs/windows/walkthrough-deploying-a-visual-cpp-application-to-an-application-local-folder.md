---
title: Distribuire un'applicazione Visual C++ in una cartella locale di un'app
ms.date: 04/23/2019
helpviewer_keywords:
- deploying Visual C++ applications
ms.assetid: 47a81c47-9dbe-47c6-96cc-fbb2fda5e6ad
ms.openlocfilehash: b05dcc47aa7c0b75943f0db69797b7bf6fb55df7
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877342"
---
# <a name="walkthrough-deploying-a-visual-c-application-to-an-application-local-folder"></a>Procedura dettagliata: Distribuzione di un'applicazione Visual C++ in una cartella dell'applicazione locale

Viene descritto come distribuire un'applicazione Visual C++ copiando i file nella cartella corrispondente.

## <a name="prerequisites"></a>Prerequisiti

- Un computer in cui è installato Visual Studio.

- Un altro computer che non dispone delle librerie Visual C++.

### <a name="to-deploy-an-application-to-an-application-local-folder"></a>Per distribuire un'applicazione Visual C++ in una cartella locale di un'applicazione

1. Creare e compilare un'applicazione MFC seguendo i passaggi descritti in [Procedura dettagliata: Distribuzione di un'applicazione Visual C++ tramite un progetto di installazione](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).

1. Copiare i file di libreria di runtime C (CRT) e MFC appropriati dalla directory di installazione di Visual Studio nella cartella \\VC\\redist\\*versione* e quindi incollarli nella cartella \Release\ del progetto MFC. Per altre informazioni sui file aggiuntivi che può essere necessario copiare, vedere [Determinazione delle DLL da ridistribuire](determining-which-dlls-to-redistribute.md).

1. Eseguire l'applicazione MFC in un secondo computer che non dispone delle librerie Visual C++.

   1. Copiare il contenuto della cartella \Release\ e incollarlo nella cartella dell'applicazione nel secondo computer.

   1. Eseguire l'applicazione nel secondo computer.

   L'applicazione viene eseguita correttamente perché le librerie Visual C++ sono disponibili nella cartella locale dell'applicazione.

## <a name="see-also"></a>Vedere anche

[Esempi di distribuzione](deployment-examples.md)<br/>
