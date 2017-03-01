---
title: Typedef &lt;type_traits&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- false_type
- std::false_type
- type_traits/std::false_type
- xtr1common/std::false_type
- true_type
- std::true_type
- type_traits/std::true_type
- xtr1common/std::true_type
ms.assetid: 8ac040ca-ed2d-4570-adc9-cb5626530053
caps.latest.revision: 13
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 41b445ceeeb1f37ee9873cb55f62d30d480d8718
ms.openlocfilehash: 5f1234e6a88cf9e51555453ec8bf7091f1bc58eb
ms.lasthandoff: 02/24/2017

---
# <a name="lttypetraitsgt-typedefs"></a>Typedef &lt;type_traits&gt;
|||  
|-|-|  
|[false_type Typedef](#false_type_typedef)|[true_type Typedef](#true_type_typedef)|  
  
##  <a name="a-namefalsetypetypedefa--falsetype-typedef"></a><a name="false_type_typedef"></a>  false_type Typedef  
 Include la costante integrale con valore false.  
  
```  
typedef integral_constant<bool, false> false_type;  
```  
  
### <a name="remarks"></a>Note  
 Il tipo è un sinonimo di una specializzazione del modello `integral_constant`.  
  
### <a name="example"></a>Esempio  
  
```cpp  
#include <type_traits>   
#include <iostream>   
  
int main() {   
    std::cout << "false_type == " << std::boolalpha   
        << std::false_type::value << std::endl;   
    std::cout << "true_type == " << std::boolalpha   
        << std::true_type::value << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
false_type == false  
true_type == true  
```  
  
##  <a name="a-nametruetypetypedefa--truetype-typedef"></a><a name="true_type_typedef"></a>  true_type Typedef  
 Include la costante integrale con valore true.  
  
```  
typedef integral_constant<bool, true> true_type;  
```  
  
### <a name="remarks"></a>Note  
 Il tipo è un sinonimo di una specializzazione del modello `integral_constant`.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// std__type_traits__true_type.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
int main() {   
    std::cout << "false_type == " << std::boolalpha   
        << std::false_type::value << std::endl;   
    std::cout << "true_type == " << std::boolalpha   
        << std::true_type::value << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
false_type == false  
true_type == true  
```  
  
## <a name="see-also"></a>Vedere anche  
 [<type_traits>](../standard-library/type-traits.md)


