---
title: Struttura _ATL_BASE_MODULE70 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL::_ATL_BASE_MODULE70
- ATL._ATL_BASE_MODULE70
- _ATL_BASE_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- ATL_BASE_MODULE70 structure
- _ATL_BASE_MODULE70 structure
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d48d863cdbe8e5528824b3ffbad10e1117277e0c
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885340"
---
# <a name="atlbasemodule70-structure"></a>Struttura _ATL_BASE_MODULE70
Usato da qualsiasi progetto che utilizza ATL.  
  
## <a name="syntax"></a>Sintassi  
  
```
struct _ATL_BASE_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInst;
    HINSTANCE m_hInstResource;
    bool m_bNT5orWin98;
    DWORD dwAtlBuildVer;
    GUID* pguidVer;
    CRITICAL_SECTION m_csResource;
    CSimpleArray<HINSTANCE> m_rgResourceInstance;
};
```  
  
## <a name="members"></a>Membri  
 `cbSize`  
 Le dimensioni della struttura, usata per il controllo delle versioni.  
  
 `m_hInst`  
 Il `hInstance` per questo modulo (exe o dll).  
  
 `m_hInstResource`  
 Handle di risorsa istanza predefinita.  
  
 `m_bNT5orWin98`  
 Informazioni sulla versione del sistema operativo. Usato internamente da ATL.  
  
 `dwAtlBuildVer`  
 Archivia la versione di ATL. Attualmente 0x0700.  
  
 `pguidVer`  
 GUID interno ATL.  
  
 `m_csResource`  
 Utilizzato per sincronizzare l'accesso al `m_rgResourceInstance` matrice. Usato internamente da ATL.  
  
 `m_rgResourceInstance`  
 Matrice utilizzata per cercare le risorse in tutte le istanze di risorse di cui è compatibile con ATL. Usato internamente da ATL.  
  
## <a name="remarks"></a>Note  
 [_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module) viene definito come un typedef di _ATL_BASE_MODULE70.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** atlcore  
  
## <a name="see-also"></a>Vedere anche  
 [Classi e struct](../../atl/reference/atl-classes.md)





