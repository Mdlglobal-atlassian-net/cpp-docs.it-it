---
title: Passaggi in un'applicazione client FTP tipica per eliminare un file
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], FTP delete
- WinInet classes [MFC], FTP
- FTP (File Transfer Protocol) [MFC], client applications
- Internet applications [MFC], FTP client applications
ms.assetid: 2c347a96-c0a4-4827-98fe-668406e552bc
ms.openlocfilehash: 6d2a920d3053a920638dd20a23e1c2334745bbc3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307055"
---
# <a name="steps-in-a-typical-ftp-client-application-to-delete-a-file"></a>Passaggi in un'applicazione client FTP tipica per eliminare un file

Nella tabella seguente vengono mostrati i passaggi che è possibile eseguire in una tipica applicazione client FTP per eliminare un file.

|Obiettivo|Azioni da effettuare|Effetti|
|---------------|----------------------|-------------|
|Avviare una sessione FTP.|Creare un [CInternetSession](../mfc/reference/cinternetsession-class.md) oggetto.|Inizializza WinInet e si connette al server.|
|Connettersi a un server FTP.|Uso [CInternetSession:: GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection).|Restituisce un [CFtpConnection](../mfc/reference/cftpconnection-class.md) oggetto.|
|Assicurarsi di trovarsi nella directory corretta nel server FTP.|Uso [CFtpConnection:: GetCurrentDirectory](../mfc/reference/cftpconnection-class.md#getcurrentdirectory) oppure [CFtpConnection:: Getcurrentdirectoryasurl](../mfc/reference/cftpconnection-class.md#getcurrentdirectoryasurl).|Restituisce il nome o l'URL della directory a cui si è attualmente connessi sul server, a seconda della funzione membro selezionata.|
|Passare a una nuova directory FTP sul server.|Uso [CFtpConnection:: SetCurrentDirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory).|Modifica la directory a cui si è attualmente connessi sul server.|
|Individuare il primo file nella directory FTP.|Uso [CFtpFileFind:: FindFile](../mfc/reference/cftpfilefind-class.md#findfile).|Trova il primo file. Restituisce FALSE se non viene trovato alcun file.|
|Individuare il file successivo nella directory FTP.|Uso [CFtpFileFind:: FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile).|Individua il file successivo. Restituisce FALSE se il file non viene trovato.|
|Eliminare il file è stato trovato dal `FindFile` o `FindNextFile`.|Uso [CFtpConnection:: Remove](../mfc/reference/cftpconnection-class.md#remove), usando il nome del file restituito da `FindFile` o `FindNextFile`.|Elimina il file sul server per la lettura o la scrittura.|
|Gestire le eccezioni.|Usare la [CInternetException](../mfc/reference/cinternetexception-class.md) classe.|Gestisce tutti i tipi di eccezioni comuni di Internet.|
|Terminare la sessione FTP.|Smaltire la [CInternetSession](../mfc/reference/cinternetsession-class.md) oggetto.|Effettua la pulizia automatica degli handle e delle connessioni del file aperto.|

## <a name="see-also"></a>Vedere anche

[Estensioni Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Prerequisiti per le classi client Internet](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[Scrittura di un'applicazione client Internet con classi WinInet MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
