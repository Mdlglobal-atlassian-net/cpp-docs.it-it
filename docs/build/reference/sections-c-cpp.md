---
title: SECTIONS (C/C++)
ms.date: 11/04/2016
f1_keywords:
- SECTIONS
helpviewer_keywords:
- SECTIONS .def file statement
ms.assetid: 7b974366-9ef5-4e57-bbcc-73a1df6f8857
ms.openlocfilehash: 5125b09675969c784aafe375faf1fdbc36d8c5d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318628"
---
# <a name="sections-cc"></a>SECTIONS (C/C++)

Introduce una sezione di uno o più `definitions` che sono identificatori di accesso sulle sezioni nel file di output del progetto.

```
SECTIONS
definitions
```

## <a name="remarks"></a>Note

Ogni definizione deve essere riportata in una riga separata. Il `SECTIONS` parola chiave può essere sulla stessa riga della prima definizione o su una riga precedente. Il file con estensione DEF può contenere uno o più `SECTIONS` istruzioni.

Ciò `SECTIONS` istruzione imposta gli attributi per uno o più sezioni nel file di immagine e può essere utilizzato per eseguire l'override gli attributi predefiniti per ogni tipo di sezione.

Il formato per `definitions` è:

`.section_name specifier`

in cui `.section_name` è il nome di una sezione dell'immagine del programma e `specifier` corrisponde a uno o più dei seguenti modificatori di accesso:

|Modificatore|Descrizione|
|--------------|-----------------|
|`EXECUTE`|La sezione non eseguibile|
|`READ`|Consente operazioni di lettura sui dati|
|`SHARED`|Condivide la sezione tra tutti i processi che caricano l'immagine|
|`WRITE`|Consente operazioni di scrittura sui dati|

Separare i nomi degli identificatori con uno spazio. Ad esempio:

```
SECTIONS
.rdata READ WRITE
```

`SECTIONS` Contrassegna l'inizio di un elenco di sezione `definitions`. Ogni `definition` deve essere su una riga separata. Il `SECTIONS` parola chiave può essere sulla stessa riga del primo `definition` o su una riga precedente. Il file con estensione DEF può contenere uno o più `SECTIONS` istruzioni. Il `SEGMENTS` parola chiave viene supportata come un sinonimo `SECTIONS`.

Versioni precedenti di Visual C++ supportano:

```
section [CLASS 'classname'] specifier
```

Il `CLASS` (parola chiave) è supportato per la compatibilità, ma viene ignorato.

È un modo equivalente per specificare gli attributi di sezione con il [/Section](section-specify-section-attributes.md) opzione.

## <a name="see-also"></a>Vedere anche

[Regole relative alle istruzioni di definizione dei moduli](rules-for-module-definition-statements.md)
