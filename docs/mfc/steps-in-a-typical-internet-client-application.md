---
title: Passaggi in un'applicazione client Internet tipica
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], general table
- WinInet classes [MFC], programming
- Internet applications [MFC], client applications
ms.assetid: 7aba135c-7c15-4e2f-8c34-bbaf792c89a6
ms.openlocfilehash: 9762e762680e2ac530b87baeac7afdea77ef6f14
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306938"
---
# <a name="steps-in-a-typical-internet-client-application"></a>Passaggi in un'applicazione client Internet tipica

Nella tabella seguente illustra la procedura che è possibile eseguire in un'applicazione client Internet tipica.

|Obiettivo|Azioni da effettuare|Effetti|
|---------------|----------------------|-------------|
|Avviare una sessione di Internet.|Creare un [CInternetSession](../mfc/reference/cinternetsession-class.md) oggetto.|Inizializza WinInet e si connette al server.|
|Impostare un'opzione di query Internet (limite di timeout o un numero di tentativi, ad esempio).|Uso [CInternetSession:: SetOption](../mfc/reference/cinternetsession-class.md#setoption).|Restituisce FALSE se l'operazione non è riuscita.|
|Definire una funzione di callback per monitorare lo stato della sessione.|Uso [CInternetSession:: EnableStatusCallback](../mfc/reference/cinternetsession-class.md#enablestatuscallback).|Stabilisce un callback [CInternetSession:: OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback). Eseguire l'override `OnStatusCallback` per creare una propria routine di callback.|
|Connettersi a un server Internet, intranet server o file locale.|Uso [CInternetSession:: OpenURL](../mfc/reference/cinternetsession-class.md#openurl).|Analizza l'URL e apre una connessione al server specificato. Restituisce un [CStdioFile](../mfc/reference/cstdiofile-class.md) (se si passa `OpenURL` un nome di file locale). Si tratta dell'oggetto tramite cui si accede ai dati recuperati dal server o file.|
|Lettura dal file.|Uso [CInternetFile:: Read](../mfc/reference/cinternetfile-class.md#read).|Legge il numero specificato di byte usando un buffer che è fornire.|
|Gestire le eccezioni.|Usare la [CInternetException](../mfc/reference/cinternetexception-class.md) classe.|Gestisce tutti i tipi di eccezioni comuni di Internet.|
|Terminare la sessione di Internet.|Smaltire la [CInternetSession](../mfc/reference/cinternetsession-class.md) oggetto.|Effettua la pulizia automatica degli handle e delle connessioni del file aperto.|

## <a name="see-also"></a>Vedere anche

[Estensioni Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Prerequisiti per le classi client Internet](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[Scrittura di un'applicazione client Internet con classi WinInet MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
