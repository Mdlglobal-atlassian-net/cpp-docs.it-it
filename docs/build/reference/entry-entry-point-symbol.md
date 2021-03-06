---
title: /ENTRY (Simbolo del punto di ingresso)
ms.date: 11/04/2016
f1_keywords:
- /entry
- VC.Project.VCLinkerTool.EntryPointSymbol
helpviewer_keywords:
- starting address
- -ENTRY linker option
- /ENTRY linker option
- ENTRY linker option
ms.assetid: 26c62ba2-4f52-4882-a7bd-7046a0abf445
ms.openlocfilehash: 0f3604ef75ce10928463c088e423615886555eda
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293212"
---
# <a name="entry-entry-point-symbol"></a>/ENTRY (Simbolo del punto di ingresso)

```
/ENTRY:function
```

## <a name="arguments"></a>Argomenti

*function*<br/>
Una funzione che specifica un avvio definite dall'utente l'indirizzo di un file .exe o DLL.

## <a name="remarks"></a>Note

L'opzione /ENTRY specifica una funzione di punto di ingresso come indirizzo iniziale per un file .exe o DLL.

La funzione deve essere definita per l'utilizzo di `__stdcall` convenzione di chiamata. I parametri e il valore restituito variano a seconda se il programma è un'applicazione console, un'applicazione windows o una DLL. È consigliabile consentire al linker di impostare il punto di ingresso in modo che la libreria run-time di C viene inizializzata correttamente e i costruttori di C++ per gli oggetti statici vengono eseguiti.

Per impostazione predefinita, l'indirizzo iniziale è il nome di una funzione della libreria di runtime C. Il linker viene selezionato in base agli attributi del programma, come illustrato nella tabella seguente.

|Nome funzione|Valore predefinito per|
|-------------------|-----------------|
|**mainCRTStartup** (o **wmainCRTStartup**)|Un'applicazione che usa /SUBSYSTEM: console; le chiamate `main` (o `wmain`)|
|**WinMainCRTStartup** (o **wWinMainCRTStartup**)|Un'applicazione che usa /SUBSYSTEM:**WINDOWS**; le chiamate `WinMain` (o `wWinMain`), che deve essere definito da usare `__stdcall`|
|**_DllMainCRTStartup**|UNA DLL. le chiamate `DllMain` se presente, che deve essere definito da usare `__stdcall`|

Se il [/DLL](dll-build-a-dll.md) oppure [/SUBSYSTEM](subsystem-specify-subsystem.md) viene omesso, il linker un sottosistema e punto di ingresso a seconda che la selezione `main` o `WinMain` è definito.

Le funzioni `main`, `WinMain`, e `DllMain` rappresentano le tre forme del punto di ingresso definito dall'utente.

Quando si crea un'immagine gestita, la funzione specificata a /ENTRY deve avere una firma di (LPVOID *var1*, valore DWORD *var2*, LPVOID *var3*).

Per informazioni su come definire il proprio `DllMain` punto di ingresso, vedere [Visual C++ e DLL comportamento libreria run-time](../run-time-library-behavior.md) .

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Per impostare questa opzione del linker nell'ambiente di sviluppo di Visual Studio

1. Aprire la finestra di dialogo **Pagine delle proprietà** del progetto. Per informazioni dettagliate, vedere [le proprietà del compilatore e compilazione impostare C++ in Visual Studio](../working-with-project-properties.md).

1. Scegliere il **Linker** cartella.

1. Scegliere il **avanzate** pagina delle proprietà.

1. Modificare il **punto di ingresso** proprietà.

### <a name="to-set-this-linker-option-programmatically"></a>Per impostare l'opzione del linker a livello di codice

- Vedere <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EntryPointSymbol%2A>.

## <a name="see-also"></a>Vedere anche

[Informazioni di riferimento sul linker MSVC](linking.md)<br/>
[Opzioni del linker MSVC](linker-options.md)
