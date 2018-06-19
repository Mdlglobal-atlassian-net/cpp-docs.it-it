---
title: Errore del compilatore C3874 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3874
dev_langs:
- C++
helpviewer_keywords:
- C3874
ms.assetid: fd55fc05-69a7-4237-b3b7-dca1d5400b4f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb1224b1e5b14c0f34e10b7eff972d4014cccdff
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33268255"
---
# <a name="compiler-error-c3874"></a>Errore del compilatore C3874
tipo restituito di 'function' deve essere 'int' anziché 'type'  
  
 Una funzione non presentano il tipo restituito previsto dal compilatore.  
  
 L'esempio seguente genera l'errore C3874:  
  
```  
// C3874b.cpp  
double main()  
{   // C3874  
}  
```