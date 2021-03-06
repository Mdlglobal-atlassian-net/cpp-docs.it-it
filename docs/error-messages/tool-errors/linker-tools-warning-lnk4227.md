---
title: Avviso degli strumenti del linker LNK4227
ms.date: 11/04/2016
f1_keywords:
- LNK4227
helpviewer_keywords:
- LNK4227
ms.assetid: 941a0414-9964-4e02-8487-f9daa42ef7f9
ms.openlocfilehash: 7b75cff4f03370951245bde1b485d538ffdb4007
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182942"
---
# <a name="linker-tools-warning-lnk4227"></a>Avviso degli strumenti del linker LNK4227

> avviso di operazione sui metadati (*HRESULT*): *warning_message*

Il linker ha rilevato differenze dei metadati durante l'Unione:

- Uno o più assembly a cui si fa riferimento con l'assembly in fase di compilazione.

- Uno o più file di codice sorgente in una compilazione.

Ad esempio, LNK4227 può essere causato da due funzioni globali con lo stesso nome ma le informazioni sui parametri dichiarate in modo diverso (ovvero, le dichiarazioni non sono coerenti in tutti moduli). Utilizzare Ildasm. exe/TEXT/METADATA *object_file* in ogni file con estensione obj per vedere il modo in cui i tipi sono diversi.

LNK4227 viene usato anche per segnalare i problemi che hanno origine con un altro strumento. Per ulteriori informazioni, cercare il messaggio di avviso.

È necessario correggere i problemi relativi ai metadati per risolvere l'avviso.

## <a name="example"></a>Esempio

LNK4227 viene generato quando un assembly a cui si fa riferimento è stato firmato in modo diverso rispetto all'assembly a cui fa riferimento.

L'esempio seguente genera l'LNK4227:

```cpp
// LNK4227.cpp
// compile with: /clr
using namespace System::Reflection;

[assembly:AssemblyDelaySignAttribute(false)];

int main() {}
```

E poi

```cpp
// LNK4227b.cpp
// compile with: /clr LNK4227.cpp /FeLNK4227b.exe
using namespace System::Reflection;
using namespace System::Runtime::CompilerServices;

[assembly:AssemblyDelaySignAttribute(true)];
// Try the following line instead
// [assembly:AssemblyDelaySignAttribute(false)];

ref class MyClass
{
};
```

## <a name="example"></a>Esempio

LNK4227 può essere generato anche quando i numeri di versione nel formato errato vengono passati agli attributi dell'assembly.  La notazione "*" è specifica del `AssemblyVersionAttribute`.  Per risolvere il problema, usare solo i numeri negli attributi di versione diversi da `AssemblyVersionAttribute`.

L'esempio seguente genera l'LNK4227:

```cpp
// LNK4227e.cpp
// compile with: /clr /LD /W1
using namespace System::Reflection;
[assembly:AssemblyVersionAttribute("2.3.*")];   // OK
[assembly:AssemblyFileVersionAttribute("2.3.*")];   // LNK4227
// try the following line instead
// [assembly:AssemblyFileVersionAttribute("2.3")];
```
