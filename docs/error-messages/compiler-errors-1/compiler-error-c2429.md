---
title: Errore del compilatore C2429
ms.date: 11/16/2017
f1_keywords:
- C2429
helpviewer_keywords:
- C2429
ms.assetid: 57ff6df9-5cf1-49f3-8bd8-4e550dfd65a0
ms.openlocfilehash: a5d1e98e91c541729a93f731eede9b047589c63a
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447976"
---
# <a name="compiler-error-c2429"></a>Errore del compilatore C2429

> «*funzionalità del linguaggio*'richiede l'impostazione del flag del compilatore'*l'opzione del compilatore*»

La funzionalità del linguaggio richiede un'opzione del compilatore specifici per il supporto.

L'errore **C2429: funzionalità del linguaggio 'annidati-namespace-definition' richiede l'impostazione del flag del compilatore ' / std:c++17 + + 17'** viene generato se si tenta di definire una *dello spazio dei nomi composto*, uno spazio dei nomi che contiene uno o più nomi dello spazio dei nomi con ambito annidato, a partire da Visual Studio 2015 Update 5. (In Visual Studio 2017 versione 15.3, il **/std: c + + più recente** opzione è obbligatoria.) Composta dello spazio dei nomi le definizioni non sono consentite in C++ prima di c++17. Il compilatore supporta le definizioni di spazi dei nomi composti quando la [/std: c + + 17](../../build/reference/std-specify-language-standard-version.md) è specificata l'opzione del compilatore:

```cpp
// C2429a.cpp
namespace a::b { int i; } // C2429 starting in Visual Studio 2015 Update 3.
                          // Use /std:c++17 to fix, or do this:
// namespace a { namespace b { int i; }}

int main() {
   a::b::i = 2;
}
```
