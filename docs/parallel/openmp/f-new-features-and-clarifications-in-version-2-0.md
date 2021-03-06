---
title: F. Nuovi chiarimenti e funzionalità della versione 2.0
ms.date: 01/22/2019
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
ms.openlocfilehash: 8cd82000992ab957bf2c41f11deccd65e2e6ea8f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215033"
---
# <a name="f-new-features-and-clarifications-in-version-20"></a>F. Nuovi chiarimenti e funzionalità della versione 2.0

In questa appendice vengono riepilogate le principali modifiche apportate allaC++ specifica OpenMP C/in, in passaggio dalla versione 1,0 alla versione 2,0. Gli elementi seguenti sono nuove funzionalità aggiunte alla specifica:

- Nelle [direttive](2-directives.md#21-directive-format)OpenMP sono consentite le virgole.

- Aggiunta della clausola `num_threads`. Questa clausola consente a un utente di richiedere un numero specifico di thread per un [costrutto parallelo](2-directives.md#23-parallel-construct).

- La direttiva [threadprivate](2-directives.md#271-threadprivate-directive) è stata estesa per accettare variabili statiche con ambito blocco.

- Le matrici di lunghezza variabile C99 sono tipi completi e possono essere specificate ovunque siano consentiti tipi completi, ad esempio negli elenchi delle clausole `private`, `firstprivate`e `lastprivate` (vedere la [sezione 2.7.2](2-directives.md#272-data-sharing-attribute-clauses)).

- Una variabile privata in un'area parallela può essere contrassegnata nuovamente come [privata](2-directives.md#2721-private) in una direttiva nidificata.

- È stata aggiunta la clausola `copyprivate`. Fornisce un meccanismo per usare una variabile privata per trasmettere un valore da un membro di un team agli altri membri. Si tratta di un'alternativa all'uso di una variabile condivisa per il valore quando si fornisce una variabile condivisa di questo tipo sarebbe difficile, ad esempio in una ricorsione che richiedeva una variabile diversa a ogni livello. La clausola [copyprivate](2-directives.md#2728-copyprivate) può essere visualizzata solo nella direttiva `single`.

- L'aggiunta di routine temporali [omp_get_wtick](3-run-time-library-functions.md#332-omp_get_wtick-function) e [omp_get_wtime](3-run-time-library-functions.md#331-omp_get_wtime-function) simile alle routine MPI. Queste funzioni sono necessarie per l'esecuzione degli intervalli di clock.

- È stata aggiunta un'appendice con un elenco di [comportamenti definiti dall'implementazione](e-implementation-defined-behaviors-in-openmp-c-cpp.md) in OpenMPC++ C/. Per definire e documentare il proprio comportamento in questi casi, è necessaria un'implementazione.

- Le modifiche seguenti sono utili per chiarire o correggere le funzionalità nella specifica API OpenMP precedente perC++C/:

  - È stato chiarito che il comportamento di [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) e [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) quando `omp_in_parallel` restituisce un valore diverso da zero non è definito.

  - [Annidamento di direttive](2-directives.md#29-directive-nesting) chiarificato quando viene utilizzato un parallelo annidato.

  - Le funzioni di [inizializzazione](3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions) e [distruzione](3-run-time-library-functions.md#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) dei blocchi possono essere chiamate in un'area parallela.

  - Sono stati aggiunti nuovi esempi all' [appendice a](a-examples.md).
