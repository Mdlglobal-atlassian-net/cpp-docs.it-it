---
title: Avviso del compilatore (livello 1) C4650
ms.date: 11/04/2016
f1_keywords:
- C4650
helpviewer_keywords:
- C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
ms.openlocfilehash: e57f1d9acba4a8734339f3b8e538120abe542efc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199568"
---
# <a name="compiler-warning-level-1-c4650"></a>Avviso del compilatore (livello 1) C4650

informazioni di debug non presenti nell'intestazione precompilata; saranno disponibili solo i simboli globali dell'intestazione

Il file di intestazione precompilato non è stato compilato con le informazioni di debug simbolico Microsoft.

Quando viene collegato, il file eseguibile o libreria a collegamento dinamico risultante non includerà le informazioni di debug per i simboli locali contenuti nell'intestazione precompilata.

Questo avviso può essere evitato ricompilando il file di intestazione precompilata con l'opzione della riga di comando [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) .
