---
title: Compatibilità
description: Viene descritta la compatibilità di Microsoft Universal C Runtime Library (UCRT) con la libreria C standard, POSIX, CRT sicuro e le app dello Store.
ms.date: 12/06/2019
helpviewer_keywords:
- CRT, compatibility
- compatibility, C run-time libraries
- compatibility
ms.assetid: 346709cb-edda-4909-9a19-3d253eddb6b7
ms.openlocfilehash: 39b936acc43243973c2f66ef6fc7306026cc3259
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171047"
---
# <a name="compatibility"></a>Compatibilità

La libreria run-time di C universale (UCRT) supporta la maggior parte delle librerie standard di C necessarie per la conformità a C++. Implementa la libreria C99 (ISO/IEC 9899:1999), con determinate eccezioni: le macro generiche definite in \<tgmath. h > e la compatibilità dei tipi rigorosa in \<Complex. h >. UCRT implementa anche un subset di grandi dimensioni della libreria C POSIX. 1 (ISO/IEC 9945-1:1996, POSIX System Application Program Interface). Tuttavia, non è completamente conforme a uno standard POSIX specifico. UCRT implementa inoltre diverse funzioni e macro specifiche di Microsoft che non fanno parte di uno standard.

Le funzioni specifiche per l'implementazione Microsoft di Visual C++ si trovano nella libreria vcruntime.  Molte di queste funzioni sono per uso interno e non possono essere chiamate dal codice utente. Alcune sono documentate per l'uso durante il debug e per la compatibilità dell'implementazione.

Lo standard C++ riserva all'implementazione i nomi che iniziano con un carattere di sottolineatura nello spazio dei nomi globale. Entrambe le funzioni POSIX e della libreria di runtime specifiche di Microsoft si trovano nello spazio dei nomi globale, ma non fanno parte della libreria di runtime C standard. Questo è il motivo per cui le implementazioni Microsoft preferite di queste funzioni hanno un carattere di sottolineatura leader. Per la portabilità, UCRT supporta anche i nomi predefiniti, ma il compilatore Microsoft C++ genera un avviso di deprecazione quando viene compilato il codice che li usa. Solo i nomi predefiniti sono deprecati, non le funzioni. Per eliminare l'avviso, definire `_CRT_NONSTDC_NO_WARNINGS` prima di includere le intestazioni nel codice che usa i nomi POSIX originali.

Alcune funzioni nella libreria C standard hanno una storia di utilizzi non sicuri a causa di parametri usati in modo improprio e di buffer non controllati. Queste funzioni causano spesso problemi di sicurezza nel codice. Microsoft ha creato un set di versioni più sicure di queste funzioni che verificano l'utilizzo dei parametri. Richiamano il gestore di parametro non valido quando viene rilevato un problema in fase di esecuzione.  Per impostazione predefinita, il compilatore Microsoft C++ genera un avviso di deprecazione quando per una funzione in uso è disponibile una variante più sicura. Quando si compila il codice come C++, è possibile definire `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` come 1 per eliminare la maggior parte degli avvisi. Questa macro consente agli overload di modelli di chiamare le varianti più sicure mantenendo il codice sorgente portatile. Per eliminare l'avviso, definire `_CRT_SECURE_NO_WARNINGS` prima di includere le intestazioni nel codice che usa queste funzioni. Per altre informazioni, vedere [Security Features in the CRT](../c-runtime-library/security-features-in-the-crt.md).

Ad eccezione di quanto indicato nella documentazione per funzioni specifiche, UCRT è compatibile con l'API Windows.  Alcune funzioni non sono supportate nelle app di Windows Store o piattaforma UWP (Universal Windows Platform) ([UWP](/uwp)). Queste funzioni sono elencate in [funzioni CRT non supportate nelle app piattaforma UWP (Universal Windows Platform)](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="related-articles"></a>Articoli correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[App UWP, Windows Runtime e runtime C](../c-runtime-library/windows-store-apps-the-windows-runtime-and-the-c-run-time.md)|Descrive quando le routine UCRT non sono compatibili con le app di Windows universale o le app Microsoft Store.|
|[Conformità ANSI C](../c-runtime-library/ansi-c-compliance.md)|Descrive la denominazione conforme agli standard in UCRT.|
|[UNIX](../c-runtime-library/unix.md)|Fornisce indicazioni per trasferire i programmi su UNIX.|
|[Piattaforme Windows (CRT)](../c-runtime-library/windows-platforms-crt.md)|Elenca i sistemi operativi che CRT supporta.|
|[Compatibilità con le versioni precedenti](../c-runtime-library/backward-compatibility.md)|Descrive come eseguire il mapping dei nomi CRT precedenti ai nuovi.|
|[Funzionalità della libreria CRT](../c-runtime-library/crt-library-features.md)|Fornisce una panoramica sui file della libreria CRT (.lib) e le opzioni del compilatore associate.|
