---
title: Esportazione da una DLL tramite __declspec(dllexport)
ms.date: 05/06/2019
f1_keywords:
- dllexport
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- names [C++], DLL exports by
- export directives [C++]
- exporting DLLs [C++], __declspec(dllexport) keyword
ms.assetid: a35e25e8-7263-4a04-bad4-00b284458679
ms.openlocfilehash: 075962758773660085ae0b98b668c264524cc6aa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328586"
---
# <a name="exporting-from-a-dll-using-__declspecdllexport"></a>Esportazione da una DLL tramite __declspec(dllexport)

È possibile esportare dati, funzioni, classi o funzioni membro di classe da una DLL usando la parola chiave **__declspec (dllexport)** . **__declspec (dllexport)** aggiunge la direttiva export al file oggetto, in modo che non sia necessario utilizzare un file def.

Questa praticità è molto evidente quando si tenta di esportare i nomi di funzione C++ decorati. Poiché non esiste alcuna specifica standard per la decorazione del nome, il nome di una funzione esportata potrebbe variare tra le versioni del compilatore. Se si utilizza **__declspec (dllexport)**, la ricompilazione della dll e dei file exe dipendenti è necessaria solo per tenere conto di eventuali modifiche alle convenzioni di denominazione.

Molte direttive Export, ad esempio ordinali, NoName e PRIVATE, possono essere eseguite solo in un file def e non è possibile specificare questi attributi senza un file def. Tuttavia, l'utilizzo di **__declspec (dllexport)** oltre all'utilizzo di un file def non provoca errori di compilazione.

Per esportare le funzioni, la parola chiave **__declspec (dllexport)** deve apparire a sinistra della parola chiave della convenzione di chiamata, se è specificata una parola chiave. Ad esempio:

```
__declspec(dllexport) void __cdecl Function1(void);
```

Per esportare tutti i membri dati pubblici e le funzioni membro in una classe, la parola chiave deve apparire a sinistra del nome della classe come indicato di seguito:

```
class __declspec(dllexport) CExampleExport : public CObject
{ ... class definition ... };
```

> [!NOTE]
> `__declspec(dllexport)`non può essere applicato a una funzione con `__clrcall` la convenzione di chiamata.

Quando si compila la DLL, si crea in genere un file di intestazione che contiene i prototipi di funzione e/o le classi da esportare e si aggiunge **__declspec (dllexport)** alle dichiarazioni nel file di intestazione. Per rendere il codice più leggibile, definire una macro per **__declspec (dllexport)** e usare la macro con ogni simbolo da esportare:

```
#define DllExport   __declspec( dllexport )
```

**__declspec (dllexport)** archivia i nomi di funzione nella tabella di esportazione della dll. Se si desidera ottimizzare le dimensioni della tabella, vedere [esportazione di funzioni da una dll in base al numero ordinale anziché al nome](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

## <a name="what-do-you-want-to-do"></a>Per saperne di più

- [Esportazione da una DLL tramite i file def](exporting-from-a-dll-using-def-files.md)

- [Esportare e importare utilizzando AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Esportare le funzioni C++ per l'utilizzo in eseguibili in linguaggio C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Esportare le funzioni C per l'utilizzo in eseguibili in linguaggio C o C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Determinare il metodo di esportazione da utilizzare](determining-which-exporting-method-to-use.md)

- [Importare in un'applicazione tramite __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Inizializzare una DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Scegliere l'argomento su cui visualizzare maggiori informazioni

- [Parola chiave __declspec](../cpp/declspec.md)

- [Importazione ed esportazione di funzioni inline](importing-and-exporting-inline-functions.md)

- [Importazioni reciproche](mutual-imports.md)

## <a name="see-also"></a>Vedere anche

[Esportazione da una DLL](exporting-from-a-dll.md)
