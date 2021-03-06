---
title: /BASE (indirizzo di base)
ms.date: 09/05/2018
f1_keywords:
- /base
- VC.Project.VCLinkerTool.BaseAddress
helpviewer_keywords:
- base addresses [C++]
- programs [C++], preventing relocation
- semicolon [C++], specifier
- -BASE linker option
- key address size
- environment variables [C++], LIB
- programs [C++], base address
- LIB environment variable
- BASE linker option
- DLLs [C++], linking
- /BASE linker option
- '@ symbol for base address'
- executable files [C++], base address
- at sign symbol for base address
ms.assetid: 00b9f6fe-0bd2-4772-a69c-7365eb199069
ms.openlocfilehash: dc6380903af0be2e6696ca3589813c249f71dd05
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341016"
---
# <a name="base-base-address"></a>/BASE (indirizzo di base)

Specifica l'indirizzo di base per un programma.

## <a name="syntax"></a>Sintassi

> **/BASE:**{*address*[**,**<em>size</em>] | **\@**<em>filename</em>**,**<em>key</em>}

## <a name="remarks"></a>Note

> [!NOTE]
> Per motivi di sicurezza, Microsoft consiglia di utilizzare il [/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md) opzione invece di specificare gli indirizzi di base per i file eseguibili. Questo genera un'immagine eseguibile che può essere riassegnata in modo casuale in fase di caricamento usando la funzionalità indirizzi dello spazio layout randomization (ASLR) di Windows. L'opzione /DYNAMICBASE è attiva per impostazione predefinita.

Il/opzione di BASE consente di impostare un indirizzo di base per il programma, il percorso predefinito per un .exe o un file DLL viene sottoposto a override. L'indirizzo di base predefinito per un file .exe è 0x400000 per immagini a 32 bit o 0x140000000 per le immagini a 64 bit. Per una DLL, l'indirizzo di base predefinita è 0x10000000 per immagini a 32 bit o 0x180000000 per le immagini a 64 bit. Nei sistemi operativi che non supportano ASLR (ASLR) o quando è stata impostata l'opzione /DYNAMICBASE: No, il sistema operativo innanzitutto tenta di caricare un programma relativo specifico o un indirizzo di base predefinito. Se non è presente disponibile spazio sufficiente, il sistema consente di rilocare il programma. Per impedire la rilocazione, utilizzare il [/fixed](fixed-fixed-base-address.md) opzione.

Il linker genera un errore se *indirizzo* non è un multiplo di 64 K. È facoltativamente possibile specificare le dimensioni del programma; il linker genera un avviso se il programma non rientra nelle dimensioni specificate.

Nella riga di comando, un altro modo per specificare l'indirizzo di base consiste nell'usare un file di risposta di indirizzo di base. Un file di risposta di indirizzo di base è un file di testo che contiene indirizzi di base e dimensioni facoltative di tutte le DLL che verrà usato il programma e una chiave di testo univoco per ogni indirizzo di base. Per specificare un indirizzo di base usando un file di risposta, utilizzare un simbolo di chiocciola (**\@**) seguito dal nome del file di risposta, *nomefile*, seguito da una virgola, quindi il *chiave*valore per l'indirizzo di base da utilizzare nel file. Il linker cerca *filename* del percorso specificato, o se viene specificato alcun percorso, nelle directory specificate nella variabile di ambiente LIB. In ogni riga *filename* rappresenta una DLL e presenta la sintassi seguente:

> *key* *address* [*size*] **;** *comment*

Il *chiave* è una stringa di caratteri alfanumerici e non viene fatta distinzione tra maiuscole e minuscole. In genere è il nome di una DLL, ma non è necessario. Il *key* è seguita da una base *indirizzo* in notazione del linguaggio C, esadecimale o decimale e un valore massimo *dimensioni*. Tutti i tre argomenti sono separati da spazi o tabulazioni. Il linker genera un avviso se l'oggetto specificato *dimensioni* è minore di spazio degli indirizzi virtuali richiesto dal programma. Oggetto *commento* specificato da un punto e virgola (**;**) e possono essere nello stesso o in una riga separata. Il linker Ignora tutto il testo da punto e virgola alla fine della riga. Questo esempio Mostra parte di tale file:

```
main   0x00010000    0x08000000    ; for PROJECT.exe
one    0x28000000    0x00100000    ; for DLLONE.DLL
two    0x28100000    0x00300000    ; for DLLTWO.DLL
```

Se il file che contiene le righe seguenti viene chiamato DLLs. txt, il comando seguente si applica queste informazioni:

```
link dlltwo.obj /dll /base:@dlls.txt,two
```

Un altro modo per impostare l'indirizzo di base consiste nell'usare la *BASE* argomento in un [nome](name-c-cpp.md) oppure [libreria](library.md) istruzione. Opzione /BASE e [/DLL](dll-build-a-dll.md) equivale al **libreria** istruzione.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Per impostare questa opzione del linker nell'ambiente di sviluppo di Visual Studio

1. Aprire la finestra di dialogo **Pagine delle proprietà** del progetto. Per informazioni dettagliate, vedere [le proprietà del compilatore e compilazione impostare C++ in Visual Studio](../working-with-project-properties.md).

1. Selezionare il **le proprietà di configurazione** > **Linker** > **avanzate** pagina delle proprietà.

1. Modificare il **indirizzo di Base** proprietà.

### <a name="to-set-this-linker-option-programmatically"></a>Per impostare l'opzione del linker a livello di codice

- Vedere <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.BaseAddress%2A>.

## <a name="see-also"></a>Vedere anche

[Informazioni di riferimento sul linker MSVC](linking.md)<br/>
[Opzioni del linker MSVC](linker-options.md)
