---
title: '&lt;> seealso (C++ commenti sulla documentazione)'
ms.date: 11/04/2016
f1_keywords:
- <seealso>
- seealso
helpviewer_keywords:
- seealso C++ XML tag
- <seealso> C++ XML tag
ms.assetid: cb33d100-9c50-4485-8d0c-573429eff155
ms.openlocfilehash: 698db2df462f561acd897d0d0e56b3106a915466
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988614"
---
# <a name="ltseealsogt"></a>&lt;seealso&gt;

Il tag \<seealso> consente di specificare il testo da visualizzare in una sezione Vedere anche. Usare [\<see>](see-visual-cpp.md) per specificare un collegamento nel testo.

## <a name="syntax"></a>Sintassi

```
<seealso cref="member"/>
```

#### <a name="parameters"></a>Parametri

*membro*<br/>
Riferimento a un membro o a un campo disponibile per essere chiamato dall'ambiente di compilazione corrente.  Racchiudere il nome tra virgolette singole o doppie.

Il compilatore verifica l'esistenza dell'elemento di codice specificato e risolve `member` nel nome dell'elemento nel file XML di output.  Il compilatore genera un avviso se non trova `member`.

Per informazioni su come creare un riferimento cref a un tipo generico, vedere [\<see>](see-visual-cpp.md).

## <a name="remarks"></a>Note

Compilare con [/doc](doc-process-documentation-comments-c-cpp.md) per elaborare i commenti relativi alla documentazione in un file.

Per un esempio d'uso di \<seealso>, vedere [\<summary>](summary-visual-cpp.md).

Il compilatore MSVC tenterà di risolvere i riferimenti CREF in un passaggio attraverso i commenti della documentazione.  Pertanto, se si utilizzano le regole di ricerca di C++, un simbolo non viene trovato dal compilatore e il riferimento verrà contrassegnato come non risolto.

## <a name="example"></a>Esempio

Nell'esempio seguente un cref fa riferimento a un simbolo non risolto. Il commento XML per il cref a B::Test sarà `<seealso cref="!:B::Test" />`, mentre il riferimento a A::Test è `<seealso cref="M:A.Test" />` ben formato.

```cpp
// xml_seealso_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_seealso_tag.dll

/// Text for class A.
public ref struct A {
   /// <summary><seealso cref="A::Test"/>
   /// <seealso cref="B::Test"/>
   /// </summary>
   void MyMethod(int Int1) {}

   /// text
   void Test() {}
};

/// Text for class B.
public ref struct B {
   void Test() {}
};
```

## <a name="see-also"></a>Vedere anche

[Documentazione di XML](xml-documentation-visual-cpp.md)
