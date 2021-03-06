---
title: Pragma execution_character_set
ms.date: 08/29/2019
f1_keywords:
- execution_character_set
- vc-pragma.execution_character_set
helpviewer_keywords:
- pragma execution_character_set
ms.assetid: 32248cbc-7c92-4dca-8442-230c052b53ad
ms.openlocfilehash: 0c2c812f27634f397af91eace7a41c0e71c1eb99
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218633"
---
# <a name="execution_character_set-pragma"></a>Pragma execution_character_set

Specifica il set di caratteri di esecuzione usato per i valori letterali stringa e carattere. Questa direttiva non è necessaria per i valori letterali contrassegnati `u8` con il prefisso.

## <a name="syntax"></a>Sintassi

> **#pragma execution_character_set (** "*target*" **)**

### <a name="parameters"></a>Parametri

*destinazione*\
Specifica il set di caratteri di esecuzione di destinazione. Attualmente l'unico set di esecuzioni di destinazione supportato è "UTF-8".

## <a name="remarks"></a>Note

Questa direttiva del compilatore è obsoleta a partire da Visual Studio 2015 Update 2. Si consiglia di usare le opzioni `/execution-charset:utf-8` del `/utf-8` compilatore o insieme al prefisso per `u8` i valori letterali stringa e carattere Narrow che contengono caratteri estesi. Per altre informazioni sul `u8` prefisso, vedere [valori letterali stringa e carattere](../cpp/string-and-character-literals-cpp.md). Per ulteriori informazioni sulle opzioni del compilatore, vedere [/Execution-CharSet (set Execution character set)](../build/reference/execution-charset-set-execution-character-set.md) e [/UTF-8 (set Source and executable character sets to UTF-8)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md).

La `#pragma execution_character_set("utf-8")` direttiva indica al compilatore di codificare valori letterali di tipo carattere e Narrow String nel codice sorgente come UTF-8 nell'eseguibile. Questa codifica di output è indipendente dalla codifica del file di origine usata.

Per impostazione predefinita, il compilatore codifica i caratteri narrow e le stringhe strette usando la tabella codici corrente come set di caratteri di esecuzione. Ciò significa che i caratteri Unicode o DBCS in un valore letterale che non rientrano nell'intervallo della tabella codici corrente vengono convertiti nel carattere di sostituzione predefinito nell'output. I caratteri Unicode e DBCS vengono troncati al byte di ordine inferiore. Questo è quasi certamente quello che si intende fare. È possibile specificare la codifica UTF-8 per i valori letterali nel file di origine `u8` usando un prefisso. Il compilatore passa le stringhe con codifica UTF-8 all'output senza modifiche. I valori letterali carattere Narrow con prefisso U8 devono contenere un byte, oppure vengono troncati nell'output.

Per impostazione predefinita, Visual Studio usa la tabella codici corrente come set di caratteri di origine usato per interpretare il codice sorgente per l'output. Quando un file viene letto, in Visual Studio viene interpretato in base alla tabella codici corrente a meno che non sia stata impostata la tabella codici del file oppure, a meno che non vengano rilevati i caratteri BOM (Byte Order Mark) o UTF-16 all'inizio del file. Poiché UTF-8 non può essere impostato come tabella codici corrente, quando il rilevamento automatico rileva i file di origine codificati come UTF-8 senza un BOM, Visual Studio presuppone che siano codificati usando la tabella codici corrente. I caratteri nel file di origine che non rientrano nell'intervallo della tabella codici specificata o rilevata automaticamente possono causare errori e avvisi del compilatore.

## <a name="see-also"></a>Vedere anche

[Direttive pragma e \_ \_parola chiave pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[/Execution-CharSet (imposta il set di caratteri di esecuzione)](../build/reference/execution-charset-set-execution-character-set.md)\
[/utf/8 (imposta i set di caratteri eseguibili e di origine su UTF/8)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)
