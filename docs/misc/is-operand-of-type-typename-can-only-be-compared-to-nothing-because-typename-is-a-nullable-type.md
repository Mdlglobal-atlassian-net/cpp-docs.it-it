---
title: "&#200; possibile confrontare l&#39;operando &#39;Is&#39; del tipo &#39;typename&#39; solo con &#39;Nothing&#39; perch&#233; &#39;typename&#39; &#232; un tipo nullable | Microsoft Docs"
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
  - "vbc32127"
  - "bc32127"
helpviewer_keywords: 
  - "BC32127"
ms.assetid: 68b745b5-8605-4bf3-a6ec-69e67b3cff2d
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#200; possibile confrontare l&#39;operando &#39;Is&#39; del tipo &#39;typename&#39; solo con &#39;Nothing&#39; perch&#233; &#39;typename&#39; &#232; un tipo nullable
Una variabile dichiarata come nullable è stata confrontata con un'espressione diversa da `Nothing` mediante l'operatore `Is`.  
  
 **ID errore:** BC32127  
  
### Per correggere l'errore  
  
1.  Per confrontare un tipo nullable con un'espressione diversa da `Nothing` usando l'operatore `Is`, chiamare il metodo `GetType` sul tipo nullable e confrontare il risultato con l'espressione, come mostrato nell'esempio seguente.  
  
    ```vb#  
    Dim number? As Integer = 5 If number IsNot Nothing Then If number.GetType() Is Type.GetType("System.Int32") Then End If End If  
    ```  
  
## Vedere anche  
 [Nullable Value Types](../Topic/Nullable%20Value%20Types%20\(Visual%20Basic\).md)   
 [Is Operator](../Topic/Is%20Operator%20\(Visual%20Basic\).md)