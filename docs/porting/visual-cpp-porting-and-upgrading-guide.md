---
title: Guida C++ al porting e aggiornamento Microsoft
description: Aggiornare il C++ codice Microsoft alla versione più recente di Visual Studio.
ms.date: 11/18/2019
ms.assetid: f5fbcc3d-aa72-41a6-ad9a-a706af2166fb
ms.topic: overview
ms.openlocfilehash: 723879ad03b9b66c7490804e890f07d6d55e9dae
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303345"
---
# <a name="microsoft-c-porting-and-upgrading-guide"></a>Guida C++ al porting e aggiornamento Microsoft

Questo articolo fornisce una guida per l'aggiornamento C++ del codice Microsoft alla versione più recente di Visual Studio. Per i progetti creati in Visual Studio da 2010 a 2015, è sufficiente aprire il progetto in Visual Studio 2019. È possibile aggiornare un progetto Visual Studio 2008 o versione precedente in due passaggi. Usare Visual Studio 2010 per convertire prima il progetto nel formato MSBuild. Aprire quindi il progetto in Visual Studio 2019. Per istruzioni complete, vedere [aggiornamento C++ di progetti da versioni precedenti di Visual Studio](upgrading-projects-from-earlier-versions-of-visual-cpp.md).

I set di strumenti in Visual Studio 2015, Visual Studio 2017 e Visual Studio 2019 sono compatibili con i file binari. A questo punto è possibile eseguire l'aggiornamento a una versione più recente del compilatore senza dover aggiornare le dipendenze della libreria. Per ulteriori informazioni, vedere [ C++ la pagina relativa alla compatibilità binaria 2015-2019](binary-compat-2015-2017.md).

Quando si esegue l'aggiornamento di progetti che usano librerie open source o sono progettati per l'esecuzione su più piattaforme, è consigliabile eseguire la migrazione a un progetto basato su CMake. Per altre informazioni, vedere [progetti CMake in Visual Studio](../build/cmake-projects-in-visual-studio.md)

## <a name="reasons-to-upgrade-c-code"></a>Motivi per aggiornare C++ il codice

Se un'applicazione legacy viene eseguita in modo soddisfacente, in un ambiente protetto e non è in fase di sviluppo attivo, potrebbe non essere molto utile aggiornarla. Tuttavia, si consideri un aggiornamento in questi casi: l'applicazione richiede una manutenzione continua. In alternativa, si sta eseguendo lo sviluppo di nuove funzionalità o si sono apportati miglioramenti alle prestazioni o alla sicurezza. Un aggiornamento offre i vantaggi seguenti:

- Lo stesso codice può essere eseguito più velocemente, perché sono state migliorate le ottimizzazioni del compilatore.

- Le C++ funzionalità moderne e le procedure di programmazione eliminano molte cause comuni dei bug e producono codice molto più facile da gestire rispetto ai precedenti idiomi di tipo C.

- I tempi di compilazione sono più veloci, a causa dei miglioramenti delle prestazioni nel compilatore e nel linker.

- Conformità agli standard migliori. L'opzione del compilatore [/permissive-](../build/reference/permissive-standards-conformance.md) consente di identificare il codice che non è conforme allo standard corrente C++ .

- Migliore sicurezza in fase di esecuzione, incluse le funzionalità della [libreria di runtime C](../c-runtime-library/security-features-in-the-crt.md) più sicure. E, funzionalità del compilatore, ad esempio [Guard checking](../build/reference/guard-enable-guard-checks.md) and address desterilizzator (novità di Visual Studio 2019 versione 16,4).

## <a name="multitargeting-vs-upgrading"></a>Confronto tra più destinazioni e aggiornamento

Forse l'aggiornamento della codebase a un nuovo set di strumenti non è un'opzione. È comunque possibile usare la versione più recente di Visual Studio per compilare e modificare progetti che usano set di strumenti e librerie meno recenti. In Visual Studio 2019 è possibile sfruttare le funzionalità seguenti:

- strumenti di analisi statica moderni, che C++ includono le linee guida di base e i controlli Clang-tidy, per identificare i potenziali problemi nel codice sorgente.

- la formattazione automatica in base alla scelta degli stili moderni può aiutare a rendere il codice legacy molto più leggibile.

Per altre informazioni, vedere [Usare multitargeting nativo in Visual Studio per compilare progetti precedenti](use-native-multi-targeting.md).

## <a name="in-this-section"></a>In questa sezione

|Titolo|Descrizione|
|-----------|-----------------|
|[Aggiornamento C++ di progetti da versioni precedenti di Visual Studio](upgrading-projects-from-earlier-versions-of-visual-cpp.md)|Come aggiornare la codebase a Visual Studio 2019 e V142 del compilatore.|
|[Strumenti IDE per l' C++ aggiornamento del codice](ide-tools-for-upgrading-code.md)|Funzionalità IDE utili che consentono di eseguire il processo di aggiornamento.|
|[C++compatibilità binaria 2015-2019](binary-compat-2015-2017.md)|Utilizzare le librerie V140 e V141 così come sono i progetti V142.|
|[Usare multitargeting nativo in Visual Studio per compilare progetti precedenti](use-native-multi-targeting.md)|Usare Visual Studio 2019 con i compilatori e le librerie precedenti.|
|[Cronologia delle modifiche di Visual C++ dal 2003 al 2015](visual-cpp-change-history-2003-2015.md)|Elenco di tutte le modifiche apportate alle C++ librerie Microsoft e agli strumenti di compilazione da Visual Studio 2003 a 2015 che potrebbero richiedere modifiche al codice.|
|[Visual C++: novità dalla versione 2003 alla 2015](visual-cpp-what-s-new-2003-through-2015.md)|Tutte le informazioni sulle novità per Microsoft C++ da visual Studio 2003 a visual studio 2015.|
|[Porting e aggiornamento: esempi e case study](porting-and-upgrading-examples-and-case-studies.md)|In questa sezione viene illustrato il processo di porting e aggiornamento di vari esempi e applicazioni e vengono descritte le esperienze e i risultati. Questi articoli forniscono un'idea di ciò che è necessario per il processo di porting e aggiornamento. Vengono inoltre presentati suggerimenti e indicazioni per l'aggiornamento e viene descritto come risolvere errori specifici.|
|[Porting to the Universal Windows Platform](porting-to-the-universal-windows-platform-cpp.md) (Conversione in Universal Windows Platform)|Contiene informazioni sul porting di codice a Windows 10|
|[Introduzione a Visual C++ per utenti UNIX](introduction-to-visual-cpp-for-unix-users.md)|Fornisce informazioni per gli utenti UNIX che non hanno familiarità con Visual C++ e vogliono aumentare la produttività con questo linguaggio.|
|[Esecuzione di programmi Linux in Windows](porting-from-unix-to-win32.md)|Illustra le opzioni per la migrazione di applicazioni UNIX a Windows.|

## <a name="see-also"></a>Vedere anche

[C++ in Visual Studio](../overview/visual-cpp-in-visual-studio.md)<br/>
[Novità del compilatore C++ in Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Miglioramenti della conformità di C++ in Visual Studio](../overview/cpp-conformance-improvements.md)<br/>
