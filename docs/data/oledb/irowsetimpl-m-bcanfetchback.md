---
title: 'IRowsetImpl:: M_bcanfetchback | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IRowsetImpl.m_bCanFetchBack
- ATL::IRowsetImpl::m_bCanFetchBack
- IRowsetImpl.m_bCanFetchBack
- IRowsetImpl::m_bCanFetchBack
- m_bCanFetchBack
dev_langs:
- C++
helpviewer_keywords:
- m_bCanFetchBack
ms.assetid: cfa007b0-7ba5-48a3-9d05-9f1916305fb7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2ea9d8a6f5e36c0ff22dfb01341377658a38e04e
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetimplmbcanfetchback"></a>IRowsetImpl::m_bCanFetchBack
Indica se un provider supporta il recupero di massa con le versioni precedenti.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
unsigned m_bCanFetchBack:1;  
  
```  
  
## <a name="remarks"></a>Note  
 Collegato per il **DBPROP_CANFETCHBACKWARDS** proprietà il **DBPROPSET_ROWSET** gruppo. Il provider deve supportare **DBPROP_CANFETCHBACKWARDS** per **m_bCanFetchBackwards** su true.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** atldb.h  
  
## <a name="see-also"></a>Vedere anche  
 [Classe IRowsetImpl](../../data/oledb/irowsetimpl-class.md)   
 [IRowsetImpl::m_bCanScrollBack](../../data/oledb/irowsetimpl-m-bcanscrollback.md)