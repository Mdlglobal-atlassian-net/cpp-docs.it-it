---
title: /Og (Ottimizzazioni globali)
ms.date: 09/22/2017
f1_keywords:
- VC.Project.VCCLCompilerTool.GlobalOptimizations
- /og
helpviewer_keywords:
- -Og compiler option [C++]
- global optimizations compiler option [C++]
- automatic register allocation
- /Og compiler option [C++]
- loop structures, optimizing
- common subexpression elimination
- Og compiler option [C++]
ms.assetid: d10630cc-b9cf-4e97-bde3-8d7ee79e9435
ms.openlocfilehash: 5e45273b6b609f1bf78504a519c1fb98e2147f76
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320292"
---
# <a name="og-global-optimizations"></a>/Og (Ottimizzazioni globali)

Deprecato. Fornisce le ottimizzazioni globali e locali, allocazione del registro automatica e ottimizzazione del ciclo. È consigliabile usare uno [/O1 (Riduci dimensione)](o1-o2-minimize-size-maximize-speed.md) oppure [/O2 (Ottimizza velocità)](o1-o2-minimize-size-maximize-speed.md) invece.

## <a name="syntax"></a>Sintassi

> /Og

## <a name="remarks"></a>Note

**/Og** è deprecata. Queste ottimizzazioni a livello generale sono ora abilitate per impostazione predefinita. Per altre informazioni sui tipi di ottimizzazione, vedere [/O1, / O2 (riduce dimensione, Ottimizza velocità)](o1-o2-minimize-size-maximize-speed.md) oppure [/Ox (Abilita più ottimizzazioni della velocità)](ox-full-optimization.md).

Le ottimizzazioni seguenti sono disponibili nel **/Og**:

- Eliminazione di sottoespressioni comuni globali e locali

   In questa ottimizzazione, il valore di una sottoespressione comune viene calcolato una sola volta. Nell'esempio seguente, se i valori della `b` e `c` non cambiano tra tre espressioni, il compilatore può assegnare il calcolo delle `b + c` a una variabile temporanea e sostituire la variabile per `b + c`:

    ```C
    a = b + c;
    d = b + c;
    e = b + c;
    ```

   Per l'ottimizzazione delle sottoespressioni comuni locale, il compilatore esamina brevi sezioni di codice di sottoespressioni comuni. Per l'ottimizzazione delle sottoespressioni comuni globali, il compilatore cerca funzioni intere di sottoespressioni comuni.

- Allocazione del registro automatica

   Questa ottimizzazione consente al compilatore di variabili di uso più frequente di archiviazione e sottoespressioni nei registri. il `register` (parola chiave) viene ignorato.

- Ottimizzazione del ciclo

   Questa ottimizzazione rimuove sottoespressioni invariante dal corpo di un ciclo. Un ciclo ottimale contiene solo le espressioni con valori cambiano in ogni esecuzione del ciclo. Nell'esempio seguente, l'espressione `x + y` rimane invariato nel corpo del ciclo:

    ```C
    i = -100;
    while( i < 0 ) {
        i += x + y;
    }
    ```

   Dopo l'ottimizzazione, `x + y` viene calcolata una sola volta anziché ogni volta che viene eseguito il ciclo:

    ```C
    i = -100;
    t = x + y;
    while( i < 0 ) {
        i += t;
    }
    ```

   Ottimizzazione del ciclo è molto più efficace quando il compilatore non può presupporre Nessun alias, che è impostata con [Restrict](../../cpp/extension-restrict.md), [noalias](../../cpp/noalias.md), o [limitare](../../cpp/restrict.md).

   > [!NOTE]
   > È possibile abilitare o disabilitare l'ottimizzazione globale in una funzione dalla base usando la `optimize` pragma assieme i `g` opzione.

Per informazioni correlate, vedere [/Oi (genera funzioni intrinseche)](oi-generate-intrinsic-functions.md) e [/Ox (Abilita più ottimizzazioni della velocità)](ox-full-optimization.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Per impostare l'opzione del compilatore nell'ambiente di sviluppo di Visual Studio

1. Aprire la finestra di dialogo **Pagine delle proprietà** del progetto. Per informazioni dettagliate, vedere [le proprietà del compilatore e compilazione impostare C++ in Visual Studio](../working-with-project-properties.md).

1. Fare clic sulla cartella **C/C++** .

1. Fare clic sulla pagina delle proprietà **Riga di comando** .

1. Immettere l'opzione del compilatore nel **opzioni aggiuntive** casella.

### <a name="to-set-this-compiler-option-programmatically"></a>Per impostare l'opzione del compilatore a livello di codice

- Vedere <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vedere anche

[Sintassi della riga di comando del compilatore MSVC](compiler-command-line-syntax.md)
