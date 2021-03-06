---
title: Archiviazione thread-local (TLS)
ms.date: 08/09/2019
helpviewer_keywords:
- multithreading [C++], Thread Local Storage
- TLS [C++]
- threading [C++], Thread Local Storage
- storing thread-specific data
- thread attribute
- Thread Local Storage [C++]
ms.assetid: 80801907-d792-45ca-b776-df0cf2e9f197
ms.openlocfilehash: 7e308f7ba23503879f8ebbcacde481cf72055229
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510387"
---
# <a name="thread-local-storage-tls"></a>Archiviazione thread-local (TLS)

L'archiviazione thread-local è il metodo attraverso il quale ogni thread incluso in un processo multithreading specifico può allocare posizioni in cui archiviare dati specifici del thread. I dati specifici del thread in fase di esecuzione sono supportati tramite l'API TLS ([TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc). Win32 e il compilatore C++ Microsoft supportano ora i dati associati in modo statico (tempo di caricamento) per thread, oltre all'implementazione API esistente.

## <a name="_core_compiler_implementation_for_tls"></a>Implementazione del compilatore per TLS

**C++11:**  L' `thread_local` identificatore di classe di archiviazione è il metodo consigliato per specificare l'archiviazione locale di thread per oggetti e membri di classe. Per ulteriori informazioni, vedere [classi di archiviazioneC++()](../cpp/storage-classes-cpp.md).

MSVC fornisce anche un attributo specifico di Microsoft, [thread](../cpp/thread.md), come modificatore di classe di archiviazione estesa. Usare la parola chiave **_ _ declspec** per dichiarare una variabile di **thread** . Nel codice seguente, ad esempio, viene dichiarata una variabile locale di thread di tipo integer e quindi inizializzata con un valore:

```C
__declspec( thread ) int tls_i = 1;
```

## <a name="rules-and-limitations"></a>Regole e limitazioni

Le linee guida seguenti devono essere osservate quando si dichiarano variabili e oggetti thread-local associati staticamente. Queste linee guida si applicano sia a [thread](../cpp/thread.md) che a [thread_local](../cpp/storage-classes-cpp.md):

- L'attributo **thread** può essere applicato solo a dichiarazioni e definizioni di classi e dati. Non può essere usato in dichiarazioni o definizioni di funzione. Il codice seguente, ad esempio, genera un errore di compilazione:

    ```C
    __declspec( thread )void func();     // This will generate an error.
    ```

- Il modificatore di **thread** può essere specificato solo in elementi di dati con estensione **statica** . Sono inclusi gli oggetti dati globali (sia **statici** che **extern**), gli oggetti statici locali e i membri dati C++ statici delle classi. Impossibile dichiarare oggetti dati automatici con l'attributo **thread** . Il codice seguente genera errori del compilatore:

    ```C
    void func1()
    {
        __declspec( thread )int tls_i;            // This will generate an error.
    }

    int func2(__declspec( thread )int tls_i )     // This will generate an error.
    {
        return tls_i;
    }
    ```

- Le dichiarazioni e la definizione di un oggetto thread-local devono specificare tutti l'attributo **thread** . Il codice seguente genera ad esempio un errore:

    ```C
    #define Thread  __declspec( thread )
    extern int tls_i;        // This will generate an error, since the
    int __declspec( thread )tls_i;        // declaration and definition differ.
    ```

- L'attributo **thread** non può essere utilizzato come modificatore di tipo. Il codice seguente, ad esempio, genera un errore di compilazione:

    ```C
    char __declspec( thread ) *ch;        // Error
    ```

- Poiché la dichiarazione di C++ oggetti che utilizzano l'attributo **thread** è consentita, i due esempi seguenti sono semanticamente equivalenti:

    ```cpp
    __declspec( thread ) class B
    {
    // Code
    } BObject;  // OK--BObject is declared thread local.

    class B
    {
    // Code
    };
    __declspec( thread ) B BObject;  // OK--BObject is declared thread local.
    ```

- L'indirizzo di un oggetto locale di thread non è considerato costante e qualsiasi espressione che includa tale indirizzo non è considerata un'espressione costante. In C standard, l'effetto è impedire l'utilizzo dell'indirizzo di una variabile thread-local come inizializzatore per un oggetto o un puntatore. Ad esempio, il codice seguente viene contrassegnato come errore dal compilatore C:

    ```C
    __declspec( thread ) int tls_i;
    int *p = &tls_i;       //This will generate an error in C.
    ```

   Questa restrizione non si C++applica a. Poiché C++ permette l'inizializzazione dinamica di tutti gli oggetti, è possibile inizializzare un oggetto usando un'espressione che usa l'indirizzo di una variabile thread-local. Viene eseguita esattamente come la costruzione di oggetti thread-local. Ad esempio, il codice illustrato in precedenza non genera un errore quando viene compilato come file C++ di origine. L'indirizzo di una variabile locale di thread è valido solo se il thread in cui è stato utilizzato l'indirizzo è ancora presente.

- Il linguaggio C standard consente l'inizializzazione di un oggetto o di una variabile con un'espressione che include un riferimento a se stessa, ma solo per oggetti di extent non statici. Sebbene C++ in genere consenta tale inizializzazione dinamica di oggetti con un'espressione che include un riferimento a se stessa, questo tipo di inizializzazione non è consentito con gli oggetti thread-local. Ad esempio:

    ```C
    __declspec( thread )int tls_i = tls_i;                // Error in C and C++
    int j = j;                               // OK in C++, error in C
    __declspec( thread )int tls_i = sizeof( tls_i )       // Legal in C and C++
    ```

   Un' `sizeof` espressione che include l'oggetto in fase di inizializzazione non rappresenta un riferimento a se stessa ed è abilitata C++sia in C sia in.

   C++non consente l'inizializzazione dinamica dei dati di thread a causa di possibili miglioramenti futuri per la funzionalità di archiviazione thread-local.

- Nei sistemi operativi Windows precedenti a Windows Vista `__declspec( thread )` , presenta alcune limitazioni. Se una dll dichiara qualsiasi dato o oggetto come `__declspec( thread )`, può causare un errore di protezione se caricato dinamicamente. Quando la dll viene caricata con [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw), causa un errore di sistema ogni volta che `__declspec( thread )` il codice fa riferimento ai dati. Poiché lo spazio delle variabili globali per un thread viene allocato in fase di esecuzione, le dimensioni di questo spazio sono basate sul calcolo dei requisiti dell'applicazione sommati ai requisiti di tutte le DLL collegate staticamente. Quando si usa `LoadLibrary`, non è possibile estendere questo spazio per consentire le variabili locali di thread dichiarate con. `__declspec( thread )` Usare le API TLS, ad esempio [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc), nella dll per allocare TLS se la dll può essere caricata `LoadLibrary`con.

## <a name="see-also"></a>Vedere anche

[Multithreading con C e Win32](multithreading-with-c-and-win32.md)
