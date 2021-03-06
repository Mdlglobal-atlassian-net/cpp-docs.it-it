---
title: 'Procedura: Usare la classe transformer in una pipeline di dati'
ms.date: 11/04/2016
helpviewer_keywords:
- transformer class, example
- data pipelines, using transformer [Concurrency Runtime]
- using transformer in data pipelines [Concurrency Runtime]
ms.assetid: ca49cb3f-4dab-4b09-a9c9-d3a109ae4c29
ms.openlocfilehash: c8cf1801d0262e3a2995d520604374ea22352fa0
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141890"
---
# <a name="how-to-use-transformer-in-a-data-pipeline"></a>Procedura: Usare la classe transformer in una pipeline di dati

Questo argomento contiene un esempio di base che illustra come usare la classe [Concurrency:: Transformer](../../parallel/concrt/reference/transformer-class.md) in una pipeline di dati. Per un esempio più completo che usa una pipeline di dati per eseguire l'elaborazione di immagini, vedere [procedura dettagliata: creazione di una rete per l'elaborazione di immagini](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

Il *pipelining dei dati* è un modello comune nella programmazione simultanea. Una pipeline di dati è costituita da una serie di fasi in cui ogni fase esegue il lavoro e quindi passa il risultato di tale operazione alla fase successiva. Il `transformer` classe un componente chiave nelle pipeline di dati perché riceve un valore di input, esegue operazioni su tale valore e quindi produce un risultato per l'uso da parte di un altro componente.

## <a name="example"></a>Esempio

Questo esempio usa la pipeline di dati seguente per eseguire una serie di trasformazioni in base a un valore di input iniziale:

1. Nella prima fase viene calcolato il valore assoluto dell'input.

1. La seconda fase calcola la radice quadrata dell'input.

1. La terza fase calcola il quadrato del relativo input.

1. La fase Forth nega l'input.

1. La Quinta fase scrive il risultato finale in un buffer dei messaggi.

Infine, nell'esempio viene stampato il risultato della pipeline sulla console.

[!code-cpp[concrt-data-pipeline#1](../../parallel/concrt/codesnippet/cpp/how-to-use-transformer-in-a-data-pipeline_1.cpp)]

Nell'esempio viene prodotto l'output seguente:

```Output
The result is -42.
```

Una fase di una pipeline di dati è comune per l'output di un valore il cui tipo differisce dal valore di input. In questo esempio, la seconda fase accetta un valore di tipo `int` come input e produce la radice quadrata del valore (un `double`) come output.

> [!NOTE]
> La pipeline di dati in questo esempio è illustrata. Poiché ogni operazione di trasformazione esegue un po' di lavoro, l'overhead necessario per eseguire il passaggio dei messaggi può superare i vantaggi derivanti dall'utilizzo di una pipeline di dati.

## <a name="compiling-the-code"></a>Compilazione del codice

Copiare il codice di esempio e incollarlo in un progetto di Visual Studio oppure incollarlo in un file denominato `data-pipeline.cpp`, quindi eseguire il comando seguente in una finestra del prompt dei comandi di Visual Studio.

> **CL. exe/EHsc data-pipeline. cpp**

## <a name="see-also"></a>Vedere anche

[Libreria di agenti asincroni](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Blocchi dei messaggi asincroni](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Procedura dettagliata: creazione di una rete per l'elaborazione di immagini](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)
