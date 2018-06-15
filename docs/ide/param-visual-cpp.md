---
title: '&lt;param&gt; (Visual C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- param
- <param>
dev_langs:
- C++
helpviewer_keywords:
- param C++ XML tag
- <param> C++ XML tag
ms.assetid: 66c1a1c3-4f98-4bcf-8c7d-9a40308982fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 01add77f68ac35b4c669391504461dd516b55d3d
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "33325383"
---
# <a name="ltparamgt-visual-c"></a>&lt;param&gt; (Visual C++)
Il tag \<param> viene usato nel commento di una dichiarazione di metodo per descrivere uno dei parametri del metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<param name='name'>description</param>  
```  
  
#### <a name="parameters"></a>Parametri  
 `name`  
 Nome di un parametro di metodo.  Racchiudere il nome tra virgolette singole o doppie.  Il compilatore genera un avviso se non trova `name`.  
  
 `description`  
 Descrizione del parametro.  
  
## <a name="remarks"></a>Note  
 Il testo del tag \<param> verrà visualizzato in IntelliSense, nel [Visualizzatore oggetti](http://msdn.microsoft.com/en-us/f89acfc5-1152-413d-9f56-3dc16e3f0470) e nel report Web sui commenti del codice.  
  
 Compilare con [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) per elaborare i commenti relativi alla documentazione in un file.  
  
## <a name="example"></a>Esempio  
  
```  
// xml_param_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_param_tag.dll  
/// Text for class MyClass.  
public ref class MyClass {  
   /// <param name="Int1">Used to indicate status.</param>  
   void MyMethod(int Int1) {  
   }  
};  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Documentazione di XML](../ide/xml-documentation-visual-cpp.md)