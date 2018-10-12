---
title: TypeDef, Enum, Union e struct (attributi) (COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- union attributes
- attributes [C++/CLI], reference topics
ms.assetid: f8a4fe94-dc02-4aed-bc31-3e500d42f4c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 89e1511df2aeabe7cbd63549a1dca6e53944fbe2
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2018
ms.locfileid: "48791428"
---
# <a name="typedef-enum-union-and-struct-attributes"></a>Attributi Typedef, Enum, Union e Struct

Gli attributi seguenti si applicano per la [typedef](../../cpp/aliases-and-typedefs-cpp.md), [struct](../../cpp/struct-cpp.md), e [enum](../../cpp/enumerations-cpp.md) parole chiave C++.

### <a name="typedef"></a>typedef

|Attributo|Descrizione|
|---------------|-----------------|
|[case](case-cpp.md)|Utilizzato con il [switch_type](switch-type.md) dell'attributo un **union**.|
|[custom](custom-cpp.md)|È possibile definire un attributo personalizzato.|
|[export](export.md)|Fa sì che una struttura di dati da inserire nel file IDL.|
|[first_is](first-is.md)|Specifica l'indice del primo elemento della matrice deve essere trasmesso.|
|[helpcontext](helpcontext.md)|Specifica un ID di contesto che consente all'utente di visualizzare informazioni sull'elemento corrente nel file della Guida.|
|[helpfile](helpfile.md)|Imposta il nome del file della Guida per una libreria dei tipi.|
|[helpstring](helpstring.md)|Specifica una stringa di caratteri usata per descrivere l'elemento a cui viene applicata.|
|[library_block](library-block.md)|Inserisce un costrutto nel blocco di libreria del file con estensione idl.|
|[ptr](ptr.md)|Definisce un puntatore come puntatore completo.|
|[public](public-cpp-attributes.md)|Assicura che un typedef entra in libreria dei tipi anche se non è presente all'interno del file con estensione idl.|
|[ref](ref-cpp.md)|Identifica un puntatore di riferimento.|
|[switch_is](switch-is.md)|Specifica l'espressione o un identificatore che agisce come l'unione discriminante che consente di selezionare il membro dell'unione.|
|[switch_type](switch-type.md)|Identifica il tipo della variabile utilizzata come l'unione discriminante.|
|[unique](unique-cpp.md)|Specifica un puntatore univoco.|
|[wire_marshal](wire-marshal.md)|Specifica un tipo di dati che verrà usato per la trasmissione anziché un tipo di dati specifici dell'applicazione.|

### <a name="enum"></a>enum

|Attributo|Descrizione|
|---------------|-----------------|
|[custom](custom-cpp.md)|È possibile definire un attributo personalizzato.|
|[export](export.md)|Fa sì che una struttura di dati da inserire nel file IDL.|
|[uuid](uuid-cpp-attributes.md)|Specifica l'ID univoco per una classe o interfaccia.|
|[v1_enum](v1-enum.md)|Indica che il tipo enumerato specificato deve essere trasmessi come un'entità a 32 bit, anziché il valore predefinito di 16 bit.|

### <a name="union"></a>union

|Attributo|Descrizione|
|---------------|-----------------|
|[custom](custom-cpp.md)|È possibile definire un attributo personalizzato.|
|[export](export.md)|Fa sì che una struttura di dati da inserire nel file IDL.|
|[first_is](first-is.md)|Specifica l'indice del primo elemento della matrice deve essere trasmesso.|
|[last_is](last-is.md)|Specifica l'indice dell'ultimo elemento di matrice deve essere trasmesso.|
|[length_is](length-is.md)|Specifica il numero di elementi della matrice deve essere trasmesso.|
|[max_is](max-is.md)|Definisce il valore massimo per un indice di matrice valida.|
|[size_is](size-is.md)|Specifica le dimensioni della memoria allocata per i puntatori con dimensioni, ridimensionati i puntatori ai puntatori a dimensioni e unidimensionali o le matrici multidimensionali.|
|[unique](unique-cpp.md)|Specifica un puntatore univoco.|
|[uuid](uuid-cpp-attributes.md)|Specifica l'ID univoco per una classe o interfaccia.|

### <a name="nonencapsulated-union"></a>Unione nonencapsulated

|Attributo|Descrizione|
|---------------|-----------------|
|[ms_union](ms-union.md)|Controlla l'allineamento di rappresentazione dei dati di rete di unioni nonencapsulated.|
|[no_injected_text](no-injected-text.md)|Impedisce al compilatore di inserire codice in seguito a uso dell'attributo.|

### <a name="struct"></a>struct

|Attributo|Descrizione|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Indica che la classe supporta l'aggregazione.|
|[aggregates](aggregates.md)|Indica che un controllo viene aggregata la classe di destinazione.|
|[appobject](appobject.md)|Identifica la coclasse come un oggetto applicazione che è associato a un'applicazione completa .exe e indica che le funzioni e le proprietà della coclasse sono disponibili a livello globale in questa libreria dei tipi.|
|[coclass](coclass.md)|Crea un controllo ActiveX.|
|[COM_INTERFACE_ENTRY](com-interface-entry-cpp.md)|Aggiunge una voce di interfaccia a una mappa COM.|
|[control](control.md)|Specifica che il tipo definito dall'utente è un controllo.|
|[custom](custom-cpp.md)|È possibile definire un attributo personalizzato.|
|[db_column](db-column.md)|Associa una colonna specificata al set di righe.|
|[db_command](db-command.md)|Crea un comando OLE DB.|
|[db_param](db-param.md)|Consente di associare la variabile di membro specificato con un parametro di input o output e delimita la variabile.|
|[db_source](db-source.md)|Crea una connessione a un'origine dati.|
|[db_table](db-table.md)|Apre una tabella di OLE DB.|
|[default](default-cpp.md)|Indica che l'interfaccia personalizzata o dispatch definita in una coclasse rappresenta l'interfaccia di programmabilità predefinita.|
|[defaultvtable](defaultvtable.md)|Definisce un'interfaccia come interfaccia predefinita vtable per un controllo.|
|[event_receiver](event-receiver.md)|Crea un ricevitore di eventi.|
|[event_source](event-source.md)|Crea un'origine evento.|
|[export](export.md)|Fa sì che una struttura di dati da inserire nel file IDL.|
|[first_is](first-is.md)|Specifica l'indice del primo elemento della matrice deve essere trasmesso.|
|[hidden](hidden.md)|Indica che l'elemento esiste ma non deve essere visualizzato in un browser orientate all'utente.|
|[implements_category](implements-category.md)|Specifica le categorie di componenti implementate per la classe.|
|[last_is](last-is.md)|Specifica l'indice dell'ultimo elemento di matrice deve essere trasmesso.|
|[length_is](length-is.md)|Specifica il numero di elementi della matrice deve essere trasmesso.|
|[max_is](max-is.md)|Definisce il valore massimo per un indice di matrice valida.|
|[requires_category](requires-category.md)|Specifica le categorie di componenti necessari della classe di destinazione.|
|[size_is](size-is.md)|Specifica le dimensioni della memoria allocata per i puntatori con dimensioni, ridimensionati i puntatori ai puntatori a dimensioni e unidimensionali o le matrici multidimensionali.|
|[source](source-cpp.md)|In una classe specifica le interfacce di origine dell'oggetto COM per i punti di connessione. In una proprietà o metodo, indica che il membro restituisce un oggetto o una variante che rappresenta l'origine degli eventi.|
|[Threading](threading-cpp.md)|Specifica il modello di threading per un oggetto COM.|
|[unique](unique-cpp.md)|Specifica un puntatore univoco.|
|[uuid](uuid-cpp-attributes.md)|Specifica l'ID univoco per una classe o interfaccia.|
|[version](version-cpp.md)|Identifica una particolare versione tra più versioni di una classe.|
|[vi_progid](vi-progid.md)|Specifica una forma indipendente dalla versione di ProgID.|

## <a name="see-also"></a>Vedere anche

[Attributi per utilizzo](attributes-by-usage.md)