---
title: Pragma hdrstop
ms.date: 08/29/2019
f1_keywords:
- hdrstop_CPP
- vc-pragma.hdrstop
helpviewer_keywords:
- hdrstop pragma
- pragmas, hdrstop
ms.assetid: 5ea8370a-10d1-4538-ade6-4c841185da0e
ms.openlocfilehash: f540f0f01fe654213af15afa8fbf5cbd94e4b7e2
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221024"
---
# <a name="hdrstop-pragma"></a>Pragma hdrstop

Offre un controllo aggiuntivo sui nomi dei file di precompilazione e sul percorso in cui viene salvato lo stato di compilazione.

## <a name="syntax"></a>Sintassi

> **#pragma hdrstop** [("*nomefile*")]

## <a name="remarks"></a>Note

*Filename* è il nome del file di intestazione precompilato da usare o creare (a seconda se è specificato [/Yu](../build/reference/yu-use-precompiled-header-file.md) o [/YC](../build/reference/yc-create-precompiled-header-file.md) ). Se *filename* non contiene una specifica del percorso, si presuppone che il file di intestazione precompilato si trovi nella stessa directory del file di origine.

Se un file C C++ o contiene un pragma **hdrstop** quando viene compilato `/Yc`con, il compilatore salva lo stato della compilazione fino al percorso del pragma. Lo stato compilato di qualsiasi codice che segue il pragma non viene salvato.

Utilizzare *filename* per denominare il file di intestazione precompilato in cui viene salvato lo stato compilato. Uno spazio tra **hdrstop** e *filename* è facoltativo. Il nome file specificato nel pragma **hdrstop** è una stringa ed è quindi soggetto ai vincoli di qualsiasi stringa C o C++ . In particolare, deve essere racchiuso tra virgolette e utilizzare il carattere di escape (barra rovesciata) per specificare i nomi di directory. Ad esempio:

```C
#pragma hdrstop( "c:\\projects\\include\\myinc.pch" )
```

Il nome del file di intestazione precompilata viene determinato in base agli elementi seguenti (in ordine di priorità):

1. Argomento dell'opzione del `/Fp` compilatore

2. Argomento *filename* per`#pragma hdrstop`

3. Il nome di base del file di origine con una estensione PCH

Per le `/Yc` opzioni `/Yu` e, se nessuna delle due opzioni di compilazione né il pragma **hdrstop** specifica un nome di file, il nome di base del file di origine viene usato come nome di base del file di intestazione precompilato.

È inoltre possibile utilizzare i comandi di pre-elaborazione per eseguire la sostituzione delle macro come indicato di seguito:

```C
#define INCLUDE_PATH "c:\\progra~`1\\devstsu~1\\vc\\include\\"
#define PCH_FNAME "PROG.PCH"
.
.
.
#pragma hdrstop( INCLUDE_PATH PCH_FNAME )
```

Le regole seguenti determinano la posizione in cui è possibile collocare il pragma **hdrstop** :

- Deve trovarsi all'esterno di eventuali dati o dichiarazione o definizione di funzione.

- Deve essere specificato nel file di origine, non all'interno di un file di intestazione.

## <a name="example"></a>Esempio

```C
#include <windows.h>                 // Include several files
#include "myhdr.h"

__inline Disp( char *szToDisplay )   // Define an inline function
{
    // ...                           // Some code to display string
}
#pragma hdrstop
```

In questo esempio, il pragma **hdrstop** viene visualizzato dopo che sono stati inclusi due file ed è stata definita una funzione inline. Questo percorso può sembrare inizialmente un posizionamento dispari per il pragma. Si consideri, tuttavia, che utilizzando le opzioni `/Yc` di precompilazione manuali e `/Yu`, con il pragma hdrstop, è possibile precompilare interi file di origine, anche il codice inline. Il compilatore Microsoft non limita l'utente alla precompilazione delle sole dichiarazioni di dati.

## <a name="see-also"></a>Vedere anche

[Direttive pragma e parola chiave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
