---
title: ref (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.ref
dev_langs:
- C++
helpviewer_keywords:
- ref attribute
ms.assetid: 67e82d3e-07d9-4ef8-bf2b-0a4491d12557
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 04eb49d0b0f5cb78f0dcd893ca97586e9a16e9cb
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2018
ms.locfileid: "40010758"
---
# <a name="ref-c"></a>ref (C++)
Identifica un puntatore di riferimento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
[ref]  
```  
  
## <a name="remarks"></a>Note  
 Il **ref** attributi di C++ ha la stessa funzionalità come la [ref](http://msdn.microsoft.com/library/windows/desktop/aa367153) attributo MIDL.  
  
## <a name="example"></a>Esempio  
 Il codice seguente viene illustrato come utilizzare il **ref** attributo:  
  
```cpp  
// cpp_attr_ref_ref.cpp  
// compile with: /LD  
#include <windows.h>   
[module(name="ATLFIRELib")];  
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl  
{  
   [id(1), unique] char * GetFirstName([in, ref] char * pszFullName );   
};  
```  
  
## <a name="requirements"></a>Requisiti  
  
### <a name="attribute-context"></a>Contesto attributo  
  
|||  
|-|-|  
|**Si applica a**|**typedef**, parametro di interfaccia, metodo di interfaccia|  
|**Ripetibile**|No|  
|**Attributi obbligatori**|Nessuna|  
|**Attributi non validi**|nessuno|  
  
 Per altre informazioni sui contesti di attributi, vedere [Contesti di attributi](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attributi IDL](../windows/idl-attributes.md)   
 [TypeDef, Enum, Union e struct (attributi)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Attributi di parametro](../windows/parameter-attributes.md)   