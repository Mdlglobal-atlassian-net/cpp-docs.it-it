---
title: Esportazione di funzioni da una DLL in base al numero ordinale anziché al nome
ms.date: 11/04/2016
helpviewer_keywords:
- exporting functions [C++], ordinal values
- ordinal exports [C++]
- exporting DLLs [C++], ordinal values
- NONAME attribute
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
ms.openlocfilehash: 66e99b18d181e9067e90398c35a61db2da66c301
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328582"
---
# <a name="exporting-functions-from-a-dll-by-ordinal-rather-than-by-name"></a>Esportazione di funzioni da una DLL in base al numero ordinale anziché al nome

Il modo più semplice per esportare le funzioni dalla DLL consiste nell'esportarli in base al nome. Questo è ciò che accade quando si usa **__declspec (dllexport)**, ad esempio. È invece possibile esportare le funzioni in base all'ordinale. Con questa tecnica, è necessario utilizzare un file def anziché **__declspec (dllexport)**. Per specificare il valore ordinale di una funzione, aggiungere il relativo ordinale al nome della funzione nel file def. Per informazioni sulla specifica di ordinali, vedere [esportazione da una dll tramite i file def](exporting-from-a-dll-using-def-files.md).

> [!TIP]
> Se si desidera ottimizzare le dimensioni del file della DLL, utilizzare l'attributo **NoName** in ogni funzione esportata. Con l'attributo **NoName** , i numeri ordinali vengono archiviati nella tabella di esportazione della dll anziché nei nomi di funzione. Questo può essere un notevole risparmio se si esportano diverse funzioni.

## <a name="what-do-you-want-to-do"></a>Per saperne di più

- [Usare un file con estensione def per poter esportare in base all'ordinale](exporting-from-a-dll-using-def-files.md)

- [USA __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

## <a name="see-also"></a>Vedere anche

[Esportazione da una DLL](exporting-from-a-dll.md)
