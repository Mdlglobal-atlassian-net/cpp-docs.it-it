---
title: Errore del compilatore di risorse RW2002
ms.date: 11/04/2016
f1_keywords:
- RW2002
helpviewer_keywords:
- RW2002
ms.assetid: b1d1a49b-b50b-4b0b-9f09-c7762e2dbe8f
ms.openlocfilehash: 9c5c2824778a679627bd3008276849890f43ac7e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190690"
---
# <a name="resource-compiler-error-rw2002"></a>Errore del compilatore di risorse RW2002

Errore di analisi

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Per risolvere il problema, verificare le seguenti cause possibili:

1. **Tipo di acceleratore obbligatorio (ASCII o VIRTKEY)**

   Il campo `type` nell'istruzione **ACCELERATORS** deve contenere il valore ASCII o VIRTKEY.

1. **INIZIO previsto nella tabella Accelerator**

   La parola chiave **BEGIN** deve seguire immediatamente la parola chiave **ACCELERATORS** .

1. **INIZIO previsto nella finestra di dialogo**

   La parola chiave **Begin** deve seguire immediatamente la parola chiave **Dialog** .

1. **INIZIO previsto nel menu**

   La parola chiave **BEGIN** deve seguire immediatamente la parola chiave **MENU** .

1. **BEGIN previsto in RCData**

   La parola chiave **BEGIN** deve seguire immediatamente la parola chiave **RCDATA** .

1. **Prevista parola chiave BEGIN nella tabella di stringhe**

   La parola chiave **Begin** deve seguire immediatamente la parola chiave **un'STRINGTABLE** .

1. **Non è possibile riutilizzare le costanti stringa**

   Si sta utilizzando lo stesso valore due volte in un'istruzione **un'STRINGTABLE** . Assicurarsi che non si stiano combinando valori decimali e esadecimali sovrapposti. Ogni ID in una **un'STRINGTABLE** deve essere univoco. Per garantire la massima efficienza, usare costanti contigue che iniziano per un multiplo di 16.

1. **Carattere di controllo non compreso nell'intervallo [^ A-^ Z]**

   Un carattere di controllo nell'istruzione **ACCELERATORS** non è valido. Il carattere che segue l'accento circonflesso ( **^** ) deve essere compreso tra A e Z incluse.

1. **Menu vuoti non consentiti**

   Una parola chiave **end** viene visualizzata prima che tutte le voci di menu siano definite nell'istruzione di **menu** . Il compilatore di risorse non consente menu vuoti. Assicurarsi che non siano presenti virgolette aperte all'interno dell'istruzione di **menu** .

1. **FINE prevista nella finestra di dialogo**

   La parola chiave **end** deve verificarsi alla fine di un'istruzione di **dialogo** . Verificare che non vi siano virgolette aperte rimaste dall'istruzione precedente.

1. **FINE prevista nel menu**

   La parola chiave **END** deve essere specificata alla fine di un'istruzione **MENU** . Verificare che non siano presenti virgolette inglesi aperte o che il numero di istruzioni **BEGIN** corrisponda a quello delle istruzioni **END** .

1. **Prevista virgola nella tabella dei tasti di scelta rapida**

   Il compilatore di risorse richiede una virgola tra i campi `event` e *idvalue* nell'istruzione **ACCELERATORS** .

1. **Previsto nome classe di controllo**

   Il campo `class` di un'istruzione di **controllo** nell'istruzione della **finestra di dialogo** deve essere uno dei seguenti tipi: Button, ComboBox, Edit, ListBox, ScrollBar, static o definito dall'utente. Verificare che la classe sia stata digitata correttamente.

1. **Nome del tipo di carattere previsto**

   Il campo *typeface* dell'opzione FONT nell'istruzione **DIALOG** deve essere una stringa di caratteri ASCII racchiusa tra virgolette doppie. Questo campo specifica il nome di un tipo di carattere.

1. **Previsto valore ID per MenuItem**

   L'istruzione **MENU** deve contenere un campo *menuID* che specifica il nome o il numero che identifica la risorsa di menu.

1. **Prevista stringa di menu**

   Ogni istruzione **MENUITEM** e **POPUP** deve contenere un campo di *testo* che è una stringa racchiusa tra virgolette doppie che specifica il nome della voce di menu o del menu popup. Un'istruzione del **separatore MenuItem** non richiede una stringa racchiusa tra virgolette.

1. **Previsto valore del comando numerico**

   Nel compilatore di risorse era previsto un campo numerico *idValue* nell'istruzione **Accelerators** . Assicurarsi di aver usato una costante `#define` per specificare il valore e che la costante sia stata digitata correttamente.

1. **Prevista costante numerica nella tabella di stringhe**

   Una costante numerica, definita in un'istruzione `#define` , deve seguire immediatamente la parola chiave **BEGIN** in un'istruzione **STRINGTABLE** .

1. **Dimensioni previste per i punti numerici**

   Il campo *pointsize* dell'opzione FONT nell'istruzione **DIALOG** deve essere un valore di dimensione in punti integer.

1. **Prevista costante finestra di dialogo numerica**

   Un'istruzione della **finestra di dialogo** richiede valori integer per i campi *x, y, larghezza*e *altezza* . Verificare che questi valori siano inclusi dopo la parola chiave **Dialog** e che non siano negativi.

1. **Prevista stringa in un'STRINGTABLE**

   È prevista una stringa dopo ogni valore *stringid* in un'istruzione **STRINGTABLE** .

1. **Prevista stringa o comando costante Accelerator**

   Il compilatore di risorse non è riuscito a determinare il tipo di tasto configurato per il tasto di scelta rapida. Il campo `event` nell'istruzione **ACCELERATORS** potrebbe non essere valido.

1. **Previsto numero per ID**

   Previsto un numero per il campo `id` di un'istruzione di controllo nell'istruzione della **finestra di dialogo** . Assicurarsi di disporre di un numero o di un'istruzione `#define` per l'ID del controllo.

1. **Prevista stringa tra virgolette nella classe della finestra di dialogo**

   Il campo `class` dell'opzione CLASS nell'istruzione **DIALOG** deve essere un numero intero o una stringa racchiusa tra virgolette doppie.

1. **Prevista stringa tra virgolette nel titolo della finestra di dialogo**

   Il campo `captiontext` dell'opzione CAPTION nell'istruzione **DIALOG** deve essere una stringa di caratteri ASCII racchiusa tra virgolette doppie.

1. **Impossibile trovare il file: nomefile**

   Non è stato trovato il file specificato nella riga di comando del compilatore di risorse. Verificare che il file non sia stato spostato in un'altra directory e che il nome del file o il percorso sia stato digitato correttamente. I file vengono cercati usando la variabile di ambiente **include** o l'impostazione di Visual Studio, se disponibile.

1. **I nomi dei tipi di carattere devono essere numeri ordinali**

   Il campo *pointsize* nell'istruzione font deve essere un numero intero, non una stringa.

1. **Acceleratore non valido**

   Un campo `event` nell'istruzione **ACCELERATORS** non è stato riconosciuto o contiene più di due caratteri.

1. **Tipo di acceleratore non valido (ASCII o VIRTKEY)**

   Il campo `type` nell'istruzione **ACCELERATORS** deve contenere il valore ASCII o VIRTKEY.

1. **Carattere di controllo non valido**

   Un carattere di controllo nell'istruzione **ACCELERATORS** non è valido. Un carattere di controllo valido è costituito da una sola lettera (solo) dopo un accento circonflesso (^).

1. **Tipo di controllo non valido**

   Ogni istruzione di controllo in un'istruzione **Dialog** deve essere una delle seguenti: CheckBox, ComboBox, Control, CTEXT, DEFPUSHBUTTON, EDITTEXT, GroupBox, Icon, ListBox, LTEXT, pulsante, RadioButton, RTEXT, ScrollBar. Verificare che le istruzioni di controllo siano digitate correttamente.

1. **Tipo non valido**

   Il tipo di risorsa non è tra i tipi definiti nel file WINDOWS. h.

1. **Stringa di testo o ordinale previsto nel controllo**

   Il campo di *testo* di un'istruzione di **controllo** nell'istruzione **Dialog** deve essere una stringa di testo o un riferimento ordinale al tipo di controllo. Se si usa un ordinale, assicurarsi di avere un'istruzione `#define` per il controllo.

1. **Parentesi non corrispondenti**

   Assicurarsi di aver chiuso ogni parentesi aperta nell'istruzione della **finestra di dialogo** .

1. **Valore imprevisto in RCData**

   I valori *raw-data* nell'istruzione **RCDATA** devono essere stringhe o numeri interi separati da una virgola. Assicurarsi di non aver escluso una virgola o una virgoletta da una stringa.

1. **Sottotipo di menu sconosciuto**

   Il campo *definizione elemento* dell'istruzione di **menu** può contenere solo istruzioni **MenuItem** e **popup** .
