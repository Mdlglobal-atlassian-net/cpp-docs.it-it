---
title: multiset::make_value (STL/CLR) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::multiset::make_value
dev_langs: C++
helpviewer_keywords: make_value member [STL/CLR]
ms.assetid: 385ded5b-65bf-4806-8c3d-a4129a05f612
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a0da7494efb2bfe2f5fbd4e5e4b9dad18468dd28
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="multisetmakevalue-stlclr"></a>multiset::make_value (STL/CLR)
Costruisce un oggetto valore.  
  
## <a name="syntax"></a>Sintassi  
  
```  
static value_type make_value(key_type key);  
```  
  
#### <a name="parameters"></a>Parametri  
 key  
 Valore della chiave da utilizzare.  
  
## <a name="remarks"></a>Note  
 La funzione membro restituisce un `value_type` oggetto la cui chiave è `key`. Utilizzarla per creare un oggetto può essere utilizzato con diverse altre funzioni membro.  
  
## <a name="example"></a>Esempio  
  
```  
// cliext_multiset_make_value.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(Mymultiset::make_value(L'a'));   
    c1.insert(Mymultiset::make_value(L'b'));   
    c1.insert(Mymultiset::make_value(L'c'));   
  
// display contents " a b c"   
    for each (Mymultiset::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vedere anche  
 [multiset (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [multiset:: KEY_TYPE (STL/CLR)](../dotnet/multiset-key-type-stl-clr.md)   
 [multiset::value_type (STL/CLR)](../dotnet/multiset-value-type-stl-clr.md)