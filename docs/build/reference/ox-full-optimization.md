---
title: /Ox (Abilita la maggior parte delle ottimizzazioni della velocità)
ms.date: 10/18/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.ToolOptimization
- /Ox
- /Oxs
helpviewer_keywords:
- Ox compiler option [C++]
- fast code [C++]
- /Ox compiler option [C++]
- -Ox compiler option [C++]
ms.assetid: 3ad7c30b-c615-428c-b1d0-2e024f81c760
ms.openlocfilehash: e39905608087425fe5a445f4ef88434d73bb2ded
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320097"
---
# <a name="ox-enable-most-speed-optimizations"></a>/Ox (Abilita la maggior parte delle ottimizzazioni della velocità)

Il **/Ox** opzione del compilatore consente una combinazione di ottimizzazioni che ottimizza per velocità. In alcune versioni dell'IDE di Visual Studio e il messaggio della Guida del compilatore, si tratta *ottimizzazione completa*, ma la **/Ox** opzione del compilatore consente solo un subset delle opzioni di ottimizzazione velocità abilitata per **/O2**.

## <a name="syntax"></a>Sintassi

> **/Ox**

## <a name="remarks"></a>Note

Il **/Ox** Abilita opzione del compilatore il **/O** tale priorità alla velocità di opzioni del compilatore. Il **/Ox** l'opzione del compilatore non include l'aggiuntive [/GF (Elimina stringhe Duplicate)](gf-eliminate-duplicate-strings.md) e [/Gy (Attiva collegamento a livello di funzione)](gy-enable-function-level-linking.md) opzioni abilitate dal [/O1 oppure/O2 (Riduci dimensione, Ottimizza velocità)](o1-o2-minimize-size-maximize-speed.md). Le opzioni aggiuntive da applicare **/O1** e **/O2** può causare i puntatori alle stringhe o alle funzioni per condividere un indirizzo di destinazione, che può influire sul debug e della conformità del linguaggio rigorosa. Il **/Ox** opzione è un modo semplice per abilitare la maggior parte delle ottimizzazioni senza includere **/GF** e **/Gy**. Per altre informazioni, vedere le descrizioni del [/GF](gf-eliminate-duplicate-strings.md) e [/Gy](gy-enable-function-level-linking.md) opzioni.

Il **/Ox** opzione del compilatore è equivale a usare le opzioni seguenti in combinazione:

- [/OB (espansione funzioni Inline)](ob-inline-function-expansion.md), dove il parametro option è 2 (**/Ob2**)

- [/Og (ottimizzazioni globali)](og-global-optimizations.md)

- [/Oi (genera funzioni intrinseche)](oi-generate-intrinsic-functions.md)

- [/Ot (Ottimizza per velocità codice)](os-ot-favor-small-code-favor-fast-code.md)

- [/Oy (omissione dei puntatori ai frame)](oy-frame-pointer-omission.md)

**/Ox** si escludono a vicenda da:

- [/ O1 (Riduci dimensione)](o1-o2-minimize-size-maximize-speed.md)

- [/ O2 (Ottimizza velocità)](o1-o2-minimize-size-maximize-speed.md)

- [/Od (disabilita (debug))](od-disable-debug.md)

È possibile annullare la distorsione verso velocità dei **/Ox** se si specifica l'opzione del compilatore **/Oxs.**, che combina il **/Ox** con l'opzione del compilatore [/Os (Ottimizza per dimensione piccola Il codice)](os-ot-favor-small-code-favor-fast-code.md). Le opzioni combinate favorire la riduzione delle dimensioni del codice.  Il **/Oxs.** opzione è esattamente lo stesso effetto **/Ox** **/Os** quando le opzioni vengono visualizzate nell'ordine indicato.

Per applicare tutte le ottimizzazioni a livello di file disponibili nelle build di rilascio, è consigliabile specificare [/O2 (Ottimizza velocità)](o1-o2-minimize-size-maximize-speed.md) anziché **/Ox**, e [/O1 (Riduci dimensione)](o1-o2-minimize-size-maximize-speed.md) invece di **/Oxs**. Per le compilazioni di ottimizzazione ancora più in versione, considerare anche il [/GL (Ottimizzazione intero programma)](gl-whole-program-optimization.md) l'opzione del compilatore e [/LTCG (generazione di codice in fase di collegamento)](ltcg-link-time-code-generation.md) l'opzione del linker.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Per impostare l'opzione del compilatore nell'ambiente di sviluppo di Visual Studio

1. Aprire la finestra di dialogo **Pagine delle proprietà** del progetto. Per informazioni dettagliate, vedere [le proprietà del compilatore e compilazione impostare C++ in Visual Studio](../working-with-project-properties.md).

1. Sotto **le proprietà di configurazione**aprire **C/C++** e quindi scegliere il **ottimizzazione** pagina delle proprietà.

1. Modificare il **ottimizzazione** proprietà.

### <a name="to-set-this-compiler-option-programmatically"></a>Per impostare l'opzione del compilatore a livello di codice

- Vedere <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Vedere anche

[Opzioni /O (ottimizza codice)](o-options-optimize-code.md)<br/>
[Opzioni del compilatore MSVC](compiler-options.md)<br/>
[Sintassi della riga di comando del compilatore MSVC](compiler-command-line-syntax.md)
