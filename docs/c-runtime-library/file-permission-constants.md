---
title: Costanti di autorizzazione file
ms.date: 11/04/2016
f1_keywords:
- _S_IWRITE
- _S_IREAD
helpviewer_keywords:
- S_IWRITE constant
- constants [C++], file attributes
- S_IREAD constant
- file permissions [C++]
- _S_IWRITE constant
- _S_IREAD constant
ms.assetid: 593cad33-31d1-44d2-8941-8af7d210c88c
ms.openlocfilehash: 7b9d99f8b0fc7daf8f7dc58db999c7f885a3dc8d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648604"
---
# <a name="file-permission-constants"></a>Costanti di autorizzazione file

## <a name="syntax"></a>Sintassi

```

#include <sys/stat.h>

```

## <a name="remarks"></a>Note

Una di queste costanti è necessaria quando `_O_CREAT` (`_open`, `_sopen`) viene specificato.

L'argomento `pmode` specifica le impostazioni di autorizzazione del file come segue.

|Costante|Significato|
|--------------|-------------|
|`_S_IREAD`|Lettura consentita|
|`_S_IWRITE`|Scrittura consentita|
|`_S_IREAD` &#124; `_S_IWRITE`|Lettura e scrittura consentite|

Una volta utilizzato come argomento `pmode` per `_umask`, la costante manifesto imposta l'impostazione di autorizzazione, come illustrato di seguito.

|Costante|Significato|
|--------------|-------------|
|`_S_IREAD`|Scrittura non consentita (file di sola lettura)|
|`_S_IWRITE`|Lettura non consentita (file di sola scrittura)|
|`_S_IREAD` &#124; `_S_IWRITE`|Lettura e scrittura non consentite|

## <a name="see-also"></a>Vedere anche

[_open, _wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_umask](../c-runtime-library/reference/umask.md)<br/>
[Tipi standard](../c-runtime-library/standard-types.md)<br/>
[Costanti globali](../c-runtime-library/global-constants.md)