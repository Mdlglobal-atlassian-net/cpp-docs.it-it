---
title: "Le istruzioni &#39;On Error&#39; non sono valide nelle istruzioni &#39;SyncLock&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30752"
  - "vbc30752"
helpviewer_keywords: 
  - "BC30752"
ms.assetid: 5c726627-b0fc-4edf-bd29-a83a0009f44d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le istruzioni &#39;On Error&#39; non sono valide nelle istruzioni &#39;SyncLock&#39;
Le istruzioni `On Error` non possono essere usate nei blocchi `SyncLock` perché interromperebbero la sincronizzazione dei thread.  
  
 **ID errore:** BC30752  
  
### Per correggere l'errore  
  
1.  Inserire le istruzioni `On Error` al di fuori dei blocchi `SyncLock`.  
  
## Vedere anche  
 [On Error Statement](../Topic/On%20Error%20Statement%20\(Visual%20Basic\).md)