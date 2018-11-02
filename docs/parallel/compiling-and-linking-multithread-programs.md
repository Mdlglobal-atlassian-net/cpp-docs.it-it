---
title: Compilazione e collegamento di programmi multithread
ms.date: 11/04/2016
helpviewer_keywords:
- compiling multithreaded programs
- multithreading [C++], linking programs
- threading [C++], linking programs
- multithreading [C++], compiled programs
- threading [C++], compiled programs
- compiling source code [C++], multithread programs
- linking [C++], multithread programs
ms.assetid: 27589afc-daf2-4f26-b868-a99de5c9dfec
ms.openlocfilehash: 3d98f5341de1374c9119e2a4303c94fcfb005e29
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558886"
---
# <a name="compiling-and-linking-multithread-programs"></a>Compilazione e collegamento di programmi multithread

Il programma di Bounce. c è stato introdotto in [C programma Multithread di esempio](sample-multithread-c-program.md).

Vengono compilati i programmi con multithreading per impostazione predefinita.

### <a name="to-compile-and-link-the-multithread-program-bouncec-from-within-the-development-environment"></a>Per compilare e collegare il programma multithread Bounce. c all'interno dell'ambiente di sviluppo

1. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.

1. Nel **tipi di progetto** riquadro, fare clic su **Win32**.

1. Nel **modelli** riquadro, fare clic su **applicazione Console Win32**e quindi denominare il progetto.

1. Aggiungere il file contenente il codice sorgente C per il progetto.

1. Nel **compilare** dal menu Compila il progetto facendo clic la **compilazione** comando.

### <a name="to-compile-and-link-the-multithread-program-bouncec-from-the-command-line"></a>Per compilare e collegare il programma multithread Bounce. c dalla riga di comando

1. Compilare e collegare il programma:

    ```
    CL BOUNCE.C
    ```

## <a name="see-also"></a>Vedere anche

[Multithreading con C e Win32](multithreading-with-c-and-win32.md)