---
title: /Qfast_transcendentals (forzare funzioni trascendenti veloci)
ms.date: 11/04/2016
f1_keywords:
- /Qfast_transcendentals
helpviewer_keywords:
- /Qfast_transcendentals
- Force Fast Transcendentals
ms.assetid: 4de24bd1-38e6-49d4-9a05-04c9937d24ac
ms.openlocfilehash: 383a915721d627367ca2ca035957df947996bbe2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319317"
---
# <a name="qfasttranscendentals-force-fast-transcendentals"></a>/Qfast_transcendentals (forzare funzioni trascendenti veloci)

Genera il codice inline per le funzioni trascendenti.

## <a name="syntax"></a>Sintassi

```
/Qfast_transcendentals
```

## <a name="remarks"></a>Note

Questa opzione del compilatore forza funzioni trascendenti da convertire in codice inline per migliorare la velocità di esecuzione. Questa opzione ha effetto solo se abbinato **/fp: tranne** oppure **/fp: precise**. Generazione di codice inline per le funzioni trascendenti è già il comportamento predefinito in **/fp: fast**.

Questa opzione non è compatibile con **/fp: strict**. Visualizzare [/fp (specifica il comportamento della virgola mobile)](fp-specify-floating-point-behavior.md) per altre informazioni sulle opzioni del compilatore a virgola mobile.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Per impostare l'opzione del compilatore nell'ambiente di sviluppo di Visual Studio

1. Aprire la finestra di dialogo **Pagine delle proprietà** del progetto. Per informazioni dettagliate, vedere [le proprietà del compilatore e compilazione impostare C++ in Visual Studio](../working-with-project-properties.md).

1. Fare clic sulla cartella **C/C++** .

1. Fare clic sulla pagina delle proprietà **Riga di comando** .

1. Digitare l'opzione del compilatore nella casella **Opzioni aggiuntive** .

### <a name="to-set-this-compiler-option-programmatically"></a>Per impostare l'opzione del compilatore a livello di codice

- Vedere <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vedere anche

[Opzioni /Q (operazioni di basso livello)](q-options-low-level-operations.md)<br/>
[Opzioni del compilatore MSVC](compiler-options.md)<br/>
[Sintassi della riga di comando del compilatore MSVC](compiler-command-line-syntax.md)
