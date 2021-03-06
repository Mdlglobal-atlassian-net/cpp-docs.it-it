---
title: Utilizzo di librerie di importazione e file di esportazione
ms.date: 11/04/2016
helpviewer_keywords:
- LIB [C++], /DEF option
- import libraries
- LIB [C++], import libraries and export files
- export files
- import libraries, creating
ms.assetid: d8175596-9773-4c2f-959d-b05b065a5161
ms.openlocfilehash: 6f6f2d5c48c63ba6d8a8a7f67a98b949b32a8afa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316522"
---
# <a name="working-with-import-libraries-and-export-files"></a>Utilizzo di librerie di importazione e file di esportazione

È possibile utilizzare LIB con l'opzione /DEF per creare una libreria di importazione e un file di esportazione. COLLEGAMENTO viene utilizzato il file di esportazione per compilare un programma che contiene esportazioni (in genere un collegamento dinamico (DLL)) e Usa la libreria di importazione per risolvere i riferimenti a queste esportazioni in altri programmi.

Si noti che se si crea la libreria di importazione in un passaggio preliminare, prima di creare la DLL, è necessario passare lo stesso set di file oggetto quando si compila il file DLL, come è stato passato quando si compila la libreria di importazione.

Nella maggior parte dei casi, non occorre usare LIB per creare la libreria di importazione. Quando si collega un programma (un file eseguibile o una DLL) che contiene esportazioni, verrà creata automaticamente una libreria di importazione che descrive le esportazioni. In un secondo momento, quando si collega un programma che fa riferimento a queste esportazioni, specificare la libreria di importazione.

Tuttavia, quando si esporta un programma che importa anche da una DLL, se direttamente o indirettamente, è necessario utilizzare LIB per creare una delle librerie di importazione. Quando LIB crea una libreria di importazione, crea anche un file di esportazione. Durante il collegamento di una DLL, è necessario usare il file di esportazione.

## <a name="see-also"></a>Vedere anche

[Riferimento a LIB](lib-reference.md)
