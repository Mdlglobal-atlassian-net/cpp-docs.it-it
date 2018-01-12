---
title: Eventi di compilazione remoti (Linux C++) | Microsoft Docs
ms.custom: 
ms.date: 9/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 165d3690-5bd8-4b0b-bc66-8b699d85a61b
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 25e51a7df39c649ec8425f4aee332086acc408d6
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/03/2018
---
# <a name="build-event-properties-linux-c"></a>Proprietà di un evento di compilazione (Linux C++) 

## <a name="pre-build-event"></a>Evento di pre-compilazione

Proprietà | Descrizione
--- | ---
Riga di comando | Specifica una riga di comando per l'esecuzione dello strumento Evento di pre-compilazione.
Descrizione | Consente di specificare una descrizione che verrà visualizzata dallo strumento Evento di pre-compilazione.
Usa in compilazione | Consente di specificare se questo evento di compilazione è escluso dalla compilazione per la configurazione corrente.
Altri file da copiare | Consente di specificare i file aggiuntivi da copiare nel sistema remoto. Facoltativamente è possibile specificare l'elenco come coppie di mapping da percorso locale a percorso remoto usando una sintassi simile a percorsolocalecompleto1:=percorsoremotocompleto1;percorsolocalecompleto2:=percorsoremotocompleto2, che consente di copiare un file locale nel percorso remoto specificato nel sistema remoto.

## <a name="pre-link-event"></a>Evento di pre-collegamento

Proprietà | Descrizione
--- | ---
Riga di comando | Specifica una riga di comando per l'esecuzione dello strumento Evento di pre-collegamento.
Descrizione | Specifica una descrizione che verrà visualizzata dallo strumento Evento di pre-collegamento.
Usa in compilazione | Consente di specificare se questo evento di compilazione è escluso dalla compilazione per la configurazione corrente.
Altri file da copiare | Consente di specificare i file aggiuntivi da copiare nel sistema remoto. Facoltativamente è possibile specificare l'elenco come coppie di mapping da percorso locale a percorso remoto usando una sintassi simile a percorsolocalecompleto1:=percorsoremotocompleto1;percorsolocalecompleto2:=percorsoremotocompleto2, che consente di copiare un file locale nel percorso remoto specificato nel sistema remoto.

## <a name="post-build-event"></a>Evento di post-compilazione

Proprietà | Descrizione
--- | ---
Riga di comando | Specifica una riga di comando per l'esecuzione dello strumento Evento di post-compilazione.
Descrizione | Specifica una descrizione che verrà visualizzata dallo strumento Evento di post-compilazione.
Usa in compilazione | Consente di specificare se questo evento di compilazione è escluso dalla compilazione per la configurazione corrente.
Altri file da copiare | Consente di specificare i file aggiuntivi da copiare nel sistema remoto. Facoltativamente è possibile specificare l'elenco come coppie di mapping da percorso locale a percorso remoto usando una sintassi simile a percorsolocalecompleto1:=percorsoremotocompleto1;percorsolocalecompleto2:=percorsoremotocompleto2, che consente di copiare un file locale nel percorso remoto specificato nel sistema remoto.

## <a name="remote-pre-build-event"></a>Evento di pre-compilazione remota

Proprietà | Descrizione
--- | ---
Riga di comando | Consente di specificare una riga di comando per lo strumento Evento di pre-compilazione da eseguire nel sistema remoto.
Descrizione | Consente di specificare una descrizione che verrà visualizzata dallo strumento Evento di pre-compilazione.
Usa in compilazione | Consente di specificare se questo evento di compilazione è escluso dalla compilazione per la configurazione corrente.
Altri file da copiare | Consente di specificare i file aggiuntivi da copiare dal sistema remoto. Facoltativamente è possibile specificare l'elenco come coppie di mapping da percorso remoto a percorso locale usando una sintassi simile a percorsoremotocompleto1:=percorsolocalecompleto1;percorsoremotocompleto2:=percorsolocalecompleto2, che consente di copiare un file remoto nel percorso specificato nel computer locale.

## <a name="remote-pre-link-event"></a>Evento di pre-collegamento remoto

Proprietà | Descrizione
--- | ---
Riga di comando | Consente di specificare una riga di comando per lo strumento Evento di pre-collegamento da eseguire nel sistema remoto.
Descrizione | Specifica una descrizione che verrà visualizzata dallo strumento Evento di pre-collegamento.
Usa in compilazione | Consente di specificare se questo evento di compilazione è escluso dalla compilazione per la configurazione corrente.
Altri file da copiare | Consente di specificare i file aggiuntivi da copiare dal sistema remoto. Facoltativamente è possibile specificare l'elenco come coppie di mapping da percorso remoto a percorso locale usando una sintassi simile a percorsoremotocompleto1:=percorsolocalecompleto1;percorsoremotocompleto2:=percorsolocalecompleto2, che consente di copiare un file remoto nel percorso specificato nel computer locale.

## <a name="remote-post-build-event"></a>Evento di post-compilazione remota

Proprietà | Descrizione
--- | ---
Riga di comando | Consente di specificare una riga di comando per lo strumento Evento di post-compilazione da eseguire nel sistema remoto.
Descrizione | Specifica una descrizione che verrà visualizzata dallo strumento Evento di post-compilazione.
Usa in compilazione | Consente di specificare se questo evento di compilazione è escluso dalla compilazione per la configurazione corrente.
Altri file da copiare | Consente di specificare i file aggiuntivi da copiare dal sistema remoto. Facoltativamente è possibile specificare l'elenco come coppie di mapping da percorso remoto a percorso locale usando una sintassi simile a percorsoremotocompleto1:=percorsolocalecompleto1;percorsoremotocompleto2:=percorsolocalecompleto2, che consente di copiare un file remoto nel percorso specificato nel computer locale.