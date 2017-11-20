---
title: Ordine di utilizzo | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c7a74abff7a2971fe66fa2df878078ac95f58fe8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/24/2017
---
# <a name="stack-usage"></a>Utilizzo dello stack
Tutta la memoria oltre l'indirizzo corrente di RSP viene considerata come volatile: il sistema operativo o un debugger, potrà sovrascrivere la memoria durante una sessione di debug di utente o un gestore di interrupt. Di conseguenza, RSP deve sempre essere impostato prima di tentare di leggere o scrivere valori a uno stack frame.  
  
 In questa sezione vengono illustrate l'allocazione di spazio dello stack per le variabili locali e **alloca** intrinseco.  
  
-   [Allocazione nello stack](../build/stack-allocation.md)  
  
-   [Costruzione dinamica dell'area dello stack di parametri](../build/dynamic-parameter-stack-area-construction.md)  
  
-   [Tipi di funzioni](../build/function-types.md)  
  
-   [Allineamento malloc](../build/malloc-alignment.md)  
  
-   [alloca](../build/alloca.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Convenzioni del software x64](../build/x64-software-conventions.md)