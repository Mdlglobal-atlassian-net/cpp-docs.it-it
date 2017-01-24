---
title: "&#39;End AddHandler&#39; deve essere preceduto da una dichiarazione &#39;AddHandler&#39; corrispondente | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31124"
  - "vbc31124"
helpviewer_keywords: 
  - "BC31124"
ms.assetid: c667fecb-163a-49ca-b416-e1070f4fab1d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End AddHandler&#39; deve essere preceduto da una dichiarazione &#39;AddHandler&#39; corrispondente
Un'istruzione `End AddHandler` si verifica senza un'istruzione `AddHandler` corrispondente.`End AddHandler` deve essere preceduto da un'istruzione `AddHandler` corrispondente.  
  
 **ID errore:** BC31124  
  
### Per correggere l'errore  
  
-   Verificare che l'istruzione `AddHandler` precedente sia valida e sia stata digitata correttamente.  
  
## Vedere anche  
 [AddHandler Statement](../Topic/AddHandler%20Statement.md)   
 [Event Statement](../Topic/Event%20Statement.md)