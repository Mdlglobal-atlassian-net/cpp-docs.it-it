---
title: Strumenti del linker LNK1140 errore | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1140
dev_langs:
- C++
helpviewer_keywords:
- LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc0d59589a1882aca4ef2deb419e1e4f1081e52b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1140"></a>Errore degli strumenti del linker LNK1140
Troppi moduli per i database di programma. il collegamento con /PDB: NONE  
  
 Il progetto contiene più di 4096 moduli.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Per correggere il problema, provare le seguenti soluzioni possibili  
  
1.  Ripetere il collegamento utilizzando [/PDB: NONE](../../build/reference/pdb-use-program-database.md).  
  
2.  Compilare alcuni moduli senza informazioni di debug.  
  
3.  Ridurre il numero di moduli.