---
title: Routines _ismbc
ms.date: 11/04/2016
api_location:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ismbc
helpviewer_keywords:
- ismbc routines
- _ismbc routines
ms.assetid: b8995391-7857-4ac3-9a1e-de946eb4464d
ms.openlocfilehash: 6dc14f269cafa8ccc343c5403ab0e23d319c71c3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940158"
---
# <a name="_ismbc-routines"></a>Routines _ismbc

Ogni test della routine **_ismbc** verifica un carattere multibyte `c` per una determinata condizione.

|||
|-|-|
|[_ismbcalnum, _ismbcalnum_l, _ismbcalpha, _ismbcalpha_l, _ismbcdigit, _ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|[_ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2, _ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|
|[_ismbcgraph, _ismbcgraph_l, _ismbcprint, _ismbcprint_l, _ismbcpunct, _ismbcpunct_l, _ismbcblank, _ismbcblank_l, _ismbcspace, _ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|[_ismbclegal, _ismbclegal_l, _ismbcsymbol, _ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|
|[_ismbchira, _ismbchira_l, _ismbckata, _ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|[_ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|

## <a name="remarks"></a>Note

Il risultato del test di ogni routine **_ismbc** dipende dalla tabella codici multibyte attiva. Le tabelle codici multibyte contengono caratteri alfabetici a un byte. Per impostazione predefinita, la tabella codici multibyte viene impostata sulla tabella codici ANSI predefinita del sistema, ottenuta dal sistema operativo all'avvio del programma. È possibile eseguire una query o modificare la tabella codici multibyte in uso, rispettivamente con [_getmbcp](../c-runtime-library/reference/getmbcp.md) o [_setmbcp](../c-runtime-library/reference/setmbcp.md).

Il valore di output è interessato dall'impostazione della categoria `LC_CTYPE` delle impostazioni locali. Vedere [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) per altre informazioni. Le versioni di queste funzioni senza il suffisso **_l** usano le impostazioni locali correnti per questo comportamento dipendente dalle impostazioni locali. Le versioni con il suffisso **_l** sono identiche, ma usano il parametro passato alle impostazioni locali.

|Routine|Condizione di test|Esempio della tabella codici 932|
|-------------|--------------------|---------------------------|
|[_ismbcalnum, _ismbcalnum_l](../c-runtime-library/reference/ismbcalnum-functions.md)|Carattere alfanumerico|Restituisce un valore diverso da zero se e solo se `c` è una rappresentazione a byte singolo di una lettera ASCII dell'alfabeto inglese: vedere esempi per `_ismbcdigit` e `_ismbcalpha`.|
|[_ismbcalpha, _ismbcalpha_l](../c-runtime-library/reference/ismbcalnum-functions.md)|Carattere alfabetico|Restituisce un valore diverso da zero se e solo se `c` è una rappresentazione a byte singolo di una lettera ASCII dell'alfabeto inglese: vedere esempi per `_ismbcupper` e `_ismbclower` oppure un simbolo dell'alfabeto katakana: 0xA6<=`c`<=0xDF.|
|[_ismbcdigit, _ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|Carattere numerico|Restituisce un valore diverso da zero se e solo se `c` è una rappresentazione a byte singolo di una cifra ASCII: 0x30<=`c`<=0x39.|
|[_ismbcgraph, _ismbcgraph_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Graphic|Restituisce un valore diverso da zero se e solo se `c` è una rappresentazione a byte singolo di qualsiasi carattere stampabile ASCII o katakana, ad eccezione dello spazio ( ). Vedere gli esempi per `_ismbcdigit`, `_ismbcalpha` e `_ismbcpunct`.|
|[_ismbclegal, _ismbclegal_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Carattere multibyte valido|Restituisce un valore diverso da zero se e solo se il primo byte di `c` è compreso negli intervalli 0x81 - 0x9F o 0xE0 - 0xFC, mentre il secondo byte è compreso negli intervalli 0x40 - 0x7E o 0x80 - FC.|
|[_ismbclower, _ismbclower_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Carattere alfabetico minuscolo|Restituisce un valore diverso da zero se e solo se `c` è una rappresentazione a byte singolo di una lettera minuscola ASCII dell'alfabeto inglese: 0x61<=`c`<=0x7A.|
|[_ismbcprint, _ismbcprint_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Carattere stampabile|Restituisce un valore diverso da zero se e solo se `c` è una rappresentazione a byte singolo di qualsiasi carattere stampabile ASCII o katakana, incluso lo spazio ( ): vedere esempi per `_ismbcspace`, `_ismbcdigit`, `_ismbcalpha` e `_ismbcpunct`.|
|[_ismbcpunct, _ismbcpunct_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Punctuation|Restituisce un valore diverso da zero se e solo se `c` è una rappresentazione a byte singolo di qualsiasi carattere di punteggiatura ASCII o katakana.|
|[_ismbcblank, _ismbcblank_l,](../c-runtime-library/reference/ismbcgraph-functions.md)|Spazio o tabulazione orizzontale|Restituisce un valore diverso da zero se e solo se `c` è una rappresentazione a un byte di uno spazio o un carattere di tabulazione orizzontale: `c`= 0x20 o `c`= 0x09.|
|[_ismbcspace, _ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Whitespace|Restituisce un valore diverso da zero se e solo se `c` è uno spazio vuoto: `c`=0x20 o 0x09<=`c`<=0x0D.|
|[_ismbcsymbol, _ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Simbolo multibyte|Restituisce un valore diverso se e solo se 0x8141<=`c`<=0x81AC.|
|[_ismbcupper, _ismbcupper_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Carattere alfabetico maiuscolo|Restituisce un valore diverso da zero se e solo se `c` è una rappresentazione a byte singolo di una lettera maiuscola ASCII dell'alfabeto inglese: 0x41<=`c`<=0x5A.|

**Specifiche per la tabella codici 932**

Le routine seguenti sono specifiche per la tabella codici 932.

|Routine|Condizione di test (solo per la tabella codici 932)|
|-------------|-------------------------------------------|
|[_ismbchira, _ismbchira_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Hiragana a byte doppio: 0x829F<=`c`<=0x82F1.|
|[_ismbckata, _ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Katakana a byte doppio: 0x8340<=`c`<=0x8396.|
|[_ismbcl0, _ismbcl0_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS non Kanji: 0x8140<=`c`<=0x889E.|
|[_ismbcl1, _ismbcl1_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS livello 1: 0x889F<=`c`<=0x9872.|
|[_ismbcl2, _ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS livello 2: 0x989F<=`c`<=0xEA9E.|

`_ismbcl0`, `_ismbcl1` e `_ismbcl2` verificano che il valore `c` specificato corrisponda alle condizioni di test descritte nella tabella precedente, ma non verifica se `c` è un carattere multibyte valido. Se il byte più basso è compreso tra 0x00 - 0x3F, 0x7F, o 0xFD - 0xFF, queste funzioni restituiscono un valore diverso da zero, indicando che il carattere soddisfa la condizione di test. Usare [_ismbbtrail, _ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md) per verificare se il carattere multibyte è definito.

**Specifiche per la tabella codici 932 END**

## <a name="see-also"></a>Vedere anche

[Classificazione di caratteri](../c-runtime-library/character-classification.md)<br/>
[Routine is, isw](../c-runtime-library/is-isw-routines.md)<br/>
[Routine _ismbb](../c-runtime-library/ismbb-routines.md)
