---
title: /Zc:forScope (Imponi conformità nell'ambito di un ciclo For)
ms.date: 03/06/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.ForceConformanceInForLoopScope
- VC.Project.VCCLWCECompilerTool.ForceConformanceInForLoopScope
- /zc:forScope
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: 3031f02d-3b14-4ad0-869e-22b0110c3aed
ms.openlocfilehash: 7f98667d3a771994d1b4e54b429f42cb566c102c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316028"
---
# <a name="zcforscope-force-conformance-in-for-loop-scope"></a>/Zc:forScope (Imponi conformità nell'ambito di un ciclo For)

Permette di implementare il comportamento C++ standard per cicli [for](../../cpp/for-statement-cpp.md) con estensioni Microsoft ([/Ze](za-ze-disable-language-extensions.md)).

## <a name="syntax"></a>Sintassi

> **/Zc:forScope**[**-**]

## <a name="remarks"></a>Note

Il comportamento standard permette all'inizializzatore del ciclo **for** di uscire dall'ambito dopo il ciclo **for** . In **/Zc:forScope-** e [/Ze](za-ze-disable-language-extensions.md)l'inizializzatore del ciclo **for** rimane nell'ambito fino al termine dell'ambito locale.

Il **/Zc: forScope** opzione è attivata per impostazione predefinita. **/Zc: forScope** non influisce quando i [/PERMISSIVE--](permissive-standards-conformance.md) opzione specificata.

L'opzione **/Zc:forScope-** è deprecata e verrà rimossa in una futura versione. L'uso di **/Zc:forScope-** genera l'avviso di deprecazione D9035.

Il codice seguente viene compilato in **/Ze** ma non in **/Za**:

```cpp
// zc_forScope.cpp
// compile by using: cl /Zc:forScope- /Za zc_forScope.cpp
// C2065, D9035 expected
int main() {
    // Compile by using cl /Zc:forScope- zc_forScope.cpp
    // to compile this non-standard code as-is.
    // Uncomment the following line to resolve C2065 for /Za.
    // int i;
    for (int i = 0; i < 1; i++)
        ;
    i = 20;   // i has already gone out of scope under /Za
}
```

Se si usa **/Zc:forScope-**, viene visualizzato l'avviso C4288 (disattivato per impostazione predefinita) se una variabile si trova all'interno dell'ambito a causa di una dichiarazione effettuata in un ambito precedente. Per illustrare questo comportamento, rimuovere i caratteri `//` dal codice di esempio per dichiarare `int i`.

È possibile modificare il comportamento di runtime di **/Zc:forScope** con il pragma [conform](../../preprocessor/conform.md) .

Se si usa **/Zc:forScope-** in un progetto con un file PCH esistente, viene generato un avviso, **/Zc:forScope-** viene ignorato e la compilazione continua con i file PCH esistenti. Se si vuole che venga generato un nuovo file pch, usare [/Yc (Crea precompilati o meno File di intestazione)](yc-create-precompiled-header-file.md).

Per altre informazioni sui problemi di conformità in Visual C++, vedere [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Per impostare l'opzione del compilatore nell'ambiente di sviluppo di Visual Studio

1. Aprire la finestra di dialogo **Pagine delle proprietà** del progetto. Per informazioni dettagliate, vedere [le proprietà del compilatore e compilazione impostare C++ in Visual Studio](../working-with-project-properties.md).

1. Selezionare il **le proprietà di configurazione** > **C/C++** > **lingua** pagina delle proprietà.

1. Modificare la proprietà **Imponi conformità nell'ambito di un ciclo For** .

### <a name="to-set-this-compiler-option-programmatically"></a>Per impostare l'opzione del compilatore a livello di codice

- Vedere <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForceConformanceInForLoopScope%2A>.

## <a name="see-also"></a>Vedere anche

[/Zc (conformità)](zc-conformance.md)<br/>
[/Za, /Ze (disabilita le estensioni del linguaggio)](za-ze-disable-language-extensions.md)<br/>
