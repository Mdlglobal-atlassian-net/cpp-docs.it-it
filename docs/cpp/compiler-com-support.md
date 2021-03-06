---
title: Supporto COM del compilatore
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
ms.openlocfilehash: 6ab697e5a090158b034a385e60978cff4a73f488
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857580"
---
# <a name="compiler-com-support"></a>Supporto COM del compilatore

**Sezione specifica Microsoft**

Il compilatore C++ Microsoft può leggere direttamente le librerie dei tipi COM (Component Object Model) e traslare C++ il contenuto nel codice sorgente che può essere incluso nella compilazione. Le estensioni del linguaggio sono disponibili per semplificare la programmazione COM sul lato client per le applicazioni desktop.

Utilizzando la direttiva per il [preprocessore #import](../preprocessor/hash-import-directive-cpp.md), il compilatore è in grado di leggere una libreria dei tipi C++ e di convertirla in un file di intestazione che descrive le interfacce com come classi. È disponibile un set di attributi `#import` per il controllo utente del contenuto dei file di intestazione delle librerie dei tipi risultanti.

È possibile usare l'attributo esteso [__declspec](../cpp/declspec.md) [uuid](../cpp/uuid-cpp.md) per assegnare un identificatore univoco globale (GUID) a un oggetto COM. È possibile utilizzare la parola chiave [__uuidof](../cpp/uuidof-operator.md) per estrarre il GUID associato a un oggetto com. Un altro **__declspec** attributo, [Property](../cpp/property-cpp.md), può essere utilizzato per specificare i metodi `get` e `set` per un membro dati di un oggetto com.

Viene fornito un set di classi e funzioni globali del supporto COM per supportare i tipi `VARIANT` e `BSTR`, implementare i puntatori intelligenti e incapsulare l'oggetto Error generato da `_com_raise_error`:

- [Funzioni globali COM del compilatore](../cpp/compiler-com-global-functions.md)

- [_bstr_t](../cpp/bstr-t-class.md)

- [_com_error](../cpp/com-error-class.md)

- [_com_ptr_t](../cpp/com-ptr-t-class.md)

- [_variant_t](../cpp/variant-t-class.md)

**Fine sezione specifica Microsoft**

## <a name="see-also"></a>Vedere anche

[Classi di supporto COM del compilatore](../cpp/compiler-com-support-classes.md)<br/>
[Funzioni globali COM del compilatore](../cpp/compiler-com-global-functions.md)
