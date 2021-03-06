---
title: /Fd (Nome file database di programma)
ms.date: 11/04/2016
f1_keywords:
- /FD
- VC.Project.VCCLWCECompilerTool.ProgramDataBaseFileName
- VC.Project.VCCLCompilerTool.ProgramDataBaseFileName
helpviewer_keywords:
- /FD compiler option [C++]
- program database file name [C++]
- -FD compiler option [C++]
- PDB files, creating
- program database compiler option [C++]
- .pdb files, creating
- FD compiler option [C++]
ms.assetid: 3977a9ed-f0ac-45df-bf06-01cedd2ba85a
ms.openlocfilehash: c686de7dc9c9c20c404240db558d2ff66078ceb7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292731"
---
# <a name="fd-program-database-file-name"></a>/Fd (Nome file database di programma)

Specifica un nome di file per il file di database (PDB) di programma creato dal [/Z7, /Zi, /ZI (formato informazioni di Debug)](z7-zi-zi-debug-information-format.md).

## <a name="syntax"></a>Sintassi

```
/Fdpathname
```

## <a name="remarks"></a>Note

Senza **/Fd**, valore predefinito è il nome del file PDB VC*x*0.pdb, dove *x* è la versione principale di Visual C++ in uso.

Se si specifica un nome di percorso che non include un nome di file (il percorso termina con una barra rovesciata), il compilatore crea un file con estensione pdb denominato VC*x*0.log pdb nella directory specificata.

Se si specifica un nome di file che non include un'estensione, il compilatore Usa con estensione PDB dell'estensione.

Questa opzione anche il nome del file di stato (con estensione IDB) usato per la compilazione incrementale e ricompilazione minima.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Per impostare l'opzione del compilatore nell'ambiente di sviluppo di Visual Studio

1. Aprire la finestra di dialogo **Pagine delle proprietà** del progetto. Per informazioni dettagliate, vedere [le proprietà del compilatore e compilazione impostare C++ in Visual Studio](../working-with-project-properties.md).

1. Fare clic sulla cartella **C/C++** .

1. Fare clic sulla pagina delle proprietà **File di output** .

1. Modificare il **nome di File di Database di programma** proprietà.

### <a name="to-set-this-compiler-option-programmatically"></a>Per impostare l'opzione del compilatore a livello di codice

- Vedere <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ProgramDataBaseFileName%2A>.

## <a name="example"></a>Esempio

Questa riga di comando crea un file con estensione pdb denominato Prog. pdb e un file con estensione IDB denominato Prog. IDB:

```
CL /DDEBUG /Zi /FdPROG.PDB PROG.CPP
```

## <a name="see-also"></a>Vedere anche

[Opzioni del file di output (/F)](output-file-f-options.md)<br/>
[Opzioni del compilatore MSVC](compiler-options.md)<br/>
[Sintassi della riga di comando del compilatore MSVC](compiler-command-line-syntax.md)<br/>
[Specifica del nome del percorso](specifying-the-pathname.md)
