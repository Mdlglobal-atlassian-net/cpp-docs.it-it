---
title: raise
ms.date: 4/2/2020
api_name:
- raise
- _o_raise
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- Raise
helpviewer_keywords:
- signals, sending to executing programs
- raise function
- signals
- programs [C++], sending signals to executing programs
ms.openlocfilehash: 81b92404603820948a384b6ad33421251a27c13c
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919555"
---
# <a name="raise"></a>raise

Invia un segnale al programma in esecuzione.

> [!NOTE]
> Non usare questo metodo per arrestare un'app Microsoft Store, tranne che negli scenari di test o di debug. I metodi a livello di codice o dell'interfaccia utente per chiudere un'app dello Store non sono consentiti in base ai [criteri Microsoft Store](/legal/windows/agreements/store-policies). Per altre informazioni, vedere ciclo di vita dell' [app UWP](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Sintassi

```C
int raise(
   int sig
);
```

### <a name="parameters"></a>Parametri

*sig*<br/>
Segnale da inviare.

## <a name="return-value"></a>Valore restituito

In caso di esito positivo, **raise** restituisce 0. In caso contrario, viene restituito un valore diverso da zero.

## <a name="remarks"></a>Osservazioni

La funzione **raise** invia *sig* al programma in esecuzione. Se una chiamata precedente a **signal** ha installata una funzione di gestione del segnale per *sig*, **raise** esegue tale funzione. Se non è stata installata alcuna funzione di gestione, viene eseguita l'azione predefinita associata al valore di segnale *sig*, come indicato di seguito.

|Segnale|Significato|Predefinito|
|------------|-------------|-------------|
|**SIGABRT**|Terminazione anomala|Termina il programma chiamante con codice di uscita 3|
|**SIGFPE**|Errore di virgola mobile|Termina il programma chiamante|
|**SIGILL**|Istruzione non valida|Termina il programma chiamante|
|**SIGINT**|Interrupt CTRL+C|Termina il programma chiamante|
|**SIGSEGV**|Accesso all'archiviazione non valido|Termina il programma chiamante|
|**SIGTERM**|Richiesta di terminazione inviata al programma|Ignora il segnale|

Se l'argomento non è un segnale valido come sopra specificato, viene richiamato il gestore di parametri non validi, come descritto in [Convalida dei parametri](../../c-runtime-library/parameter-validation.md). Se non gestito, la funzione imposta **errno** su **EINVAL** e restituisce un valore diverso da zero.

Per impostazione predefinita, lo stato globale di questa funzione ha come ambito l'applicazione. Per modificare questa situazione, vedere [stato globale in CRT](../global-state.md).

## <a name="requirements"></a>Requisiti

|Routine|Intestazione obbligatoria|
|-------------|---------------------|
|**raise**|\<signal.h>|

Per altre informazioni sulla compatibilità, vedere [Compatibilità](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vedere anche

[Process and Environment Control](../../c-runtime-library/process-and-environment-control.md) (Controllo processo e ambiente)<br/>
[interruzione](abort.md)<br/>
[signal](signal.md)<br/>
