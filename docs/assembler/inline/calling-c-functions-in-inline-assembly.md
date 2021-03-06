---
title: Chiamare le funzioni C nell'assembly inline
ms.date: 08/30/2018
helpviewer_keywords:
- function calls, C functions
- function calls, in inline assembly
- functions [C], calling in inline assembly
- Visual C, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: f8a8d568-d175-4e23-9b24-36ef60a4cab3
ms.openlocfilehash: 94bbfda3a5fd15885f3d8276d506541418a9489f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169591"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Chiamare le funzioni C nell'assembly inline

**Sezione specifica Microsoft**

Un blocco `__asm` può chiamare le funzioni C, incluse le routine di libreria C. Nell'esempio seguente viene chiamata la routine di libreria `printf`:

```cpp
// InlineAssembler_Calling_C_Functions_in_Inline_Assembly.cpp
// processor: x86
#include <stdio.h>

char format[] = "%s %s\n";
char hello[] = "Hello";
char world[] = "world";
int main( void )
{
   __asm
   {
      mov  eax, offset world
      push eax
      mov  eax, offset hello
      push eax
      mov  eax, offset format
      push eax
      call printf
      //clean up the stack so that main can exit cleanly
      //use the unused register ebx to do the cleanup
      pop  ebx
      pop  ebx
      pop  ebx
   }
}
```

Poiché gli argomenti di funzione vengono passati nello stack, si inseriscono semplicemente gli argomenti necessari, puntatori di stringa nell'esempio precedente, prima di chiamare la funzione. Gli argomenti sono inseriti in ordine inverso, pertanto si staccano dallo stack nell'ordine desiderato. Per emulare l'istruzione C

```cpp
printf( format, hello, world );
```

l'esempio inserisce i puntatori a `world`, `hello` e `format`, in questo ordine, quindi chiamare `printf`.

**Fine sezione specifica Microsoft**

## <a name="see-also"></a>Vedere anche

[Assembler inline](../../assembler/inline/inline-assembler.md)<br/>
