---
title: "Metodo ClassFactory::Release | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::ClassFactory::Release"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Release (metodo)"
ms.assetid: 49da2002-f9d6-4d7f-8a65-48c20b1bf99f
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# Metodo ClassFactory::Release
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Decrementa il conteggio dei riferimenti per l'oggetto ClassFactory corrente.  
  
## Sintassi  
  
```  
STDMETHOD_(  
   ULONG,  
   Release  
)();  
```  
  
## Valore restituito  
 S\_OK se ha avuto successo, in caso contrario un HRESULT, che descrive perchè l'operazione è fallita.  
  
## Requisiti  
 **Header:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## Vedere anche  
 [Classe ClassFactory](../windows/classfactory-class.md)