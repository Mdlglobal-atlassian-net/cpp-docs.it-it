---
title: "CBulkRowset::AddRefRows | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CBulkRowset::AddRefRows"
  - "AddRefRows"
  - "CBulkRowset.AddRefRows"
  - "ATL.CBulkRowset<TAccessor>.AddRefRows"
  - "ATL::CBulkRowset::AddRefRows"
  - "CBulkRowset<TAccessor>::AddRefRows"
  - "ATL.CBulkRowset.AddRefRows"
  - "ATL::CBulkRowset<TAccessor>::AddRefRows"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddRefRows (metodo)"
ms.assetid: 014be991-50f8-4377-ba16-fec80b54b406
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CBulkRowset::AddRefRows
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Chiama [IRowset::AddRefRows](https://msdn.microsoft.com/en-us/library/ms719619.aspx) per incrementare il conteggio dei riferimenti per tutte le righe attualmente recuperate dal rowset di massa.  
  
## Sintassi  
  
```  
  
HRESULT AddRefRows( ) throw( );  
  
```  
  
## Valore restituito  
 Un `HRESULT` standard.  
  
## Requisiti  
 **Intestazione:** atldbcli.h  
  
## Vedere anche  
 [Classe CBulkRowset](../../data/oledb/cbulkrowset-class.md)   
 [CBulkRowset::ReleaseRows](../../data/oledb/cbulkrowset-releaserows.md)