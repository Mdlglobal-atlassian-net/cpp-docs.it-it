---
title: db_column (attributo COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_column
dev_langs:
- C++
helpviewer_keywords:
- db_column attribute
ms.assetid: 58da4afc-f69c-4ae6-af9a-3f9515f56081
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 52b5c5bea282e4ebb4106d8e9c2fede40f375ae3
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083612"
---
# <a name="dbcolumn"></a>db_column

Associa una colonna specificata a una variabile nel set di righe.

## <a name="syntax"></a>Sintassi

```cpp
[ db_column(ordinal, dbtype, precision, scale, status, length) ]
```

#### <a name="parameters"></a>Parametri

*Numero ordinale*<br/>
Il numero ordinale di colonna (`DBCOLUMNINFO` ordinale) o nome di colonna (stringa ANSI o Unicode) corrispondente a un campo nel set di righe a cui associare i dati. Se si utilizzano numeri, è possibile ignorare gli ordinali consecutivi (ad esempio: 1, 2, 3, 5). Se il provider OLE DB che è usare lo supporta, il nome può contenere spazi. Ad esempio, è possibile usare uno dei formati seguenti:

```cpp
[db_column("2")] TCHAR szCity[30];
[db_column(L"city_name")] TCHAR szCity[30];
```

*DbType*<br/>
(Facoltativo) OLE DB [indicatore del tipo](/previous-versions/windows/desktop/ms711251) per la voce di colonna.

*precision*<br/>
(Facoltativo) La precisione da utilizzare per la voce di colonna. Per informazioni dettagliate, vedere la descrizione del `bPrecision` elemento del [struttura DBBINDING](/previous-versions/windows/desktop/ms716845)

*Scalabilità*<br/>
(Facoltativo) La scala da usare per la voce di colonna. Per informazioni dettagliate, vedere la descrizione del `bScale` dell'elemento di [struttura DBBINDING](/previous-versions/windows/desktop/ms716845)

*status*<br/>
(Facoltativo) Una variabile membro usata per mantenere lo stato di questa colonna. Lo stato indica se il valore della colonna è un valore di dati o un altro valore, ad esempio valori NULL. Per i valori possibili, vedere [lo stato](/previous-versions/windows/desktop/ms722617) nel *riferimento per programmatori OLE DB*.

*length*<br/>
(Facoltativo) Una variabile membro usata per contenere le dimensioni della colonna in byte.

## <a name="remarks"></a>Note

**db_column** associa la colonna della tabella specificato a una variabile nel set di righe. Delimita i dati dei membri che può far parte di OLE DB `IAccessor`-associazione basata su. Questo attributo consente di impostare la mappa delle colonne in genere definita usando le macro di consumer OLE DB [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md), [END_COLUMN_MAP](../../data/oledb/end-column-map.md), e [COLUMN_ENTRY](../../data/oledb/column-entry.md). Questi manipolare OLE DB [struttura DBBINDING](/previous-versions/windows/desktop/ms716845) da associare alla colonna specificata. Ogni membro è contrassegnare con il **db_column** attributo occupa una voce nella mappa colonna sotto forma di una voce di colonna. Pertanto, si chiama questo attributo in cui inserire la mappa delle colonne, vale a dire, nella classe di comando o di tabella.

Uso **db_column** in combinazione con la [db_table](db-table.md) oppure [db_command](db-command.md) attributi.

Quando il provider di attributi del consumer applica questo attributo a una classe, il compilatore Rinomina la classe \_ *NomeClasse*della funzione di accesso, dove *NomeClasse* è il nome è stato assegnato il classe e il compilatore creerà inoltre una classe denominata *NomeClasse*, che deriva da \_ *NomeClasse*della funzione di accesso.  In Visualizzazione classi verranno visualizzate entrambe le classi.

Per esempi di questo attributo usato in un'applicazione, vedere gli esempi [AtlAgent](https://github.com/Microsoft/VCSamples), e [MultiRead](https://github.com/Microsoft/VCSamples).

## <a name="example"></a>Esempio

In questo esempio associa una colonna in una tabella a un **lungo** (membro dati) e specifica i campi stato e lunghezza.

```cpp
// db_column_1.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_command(L"Select * from Products") ]
class CProducts {
   DBSTATUS m_dwProductIDStatus;
   DBLENGTH m_dwProductIDLength;

   [ db_column("1", status="m_dwProductIDStatus", length="m_dwProductIDLength") ] LONG m_ProductID;
};
```

## <a name="example"></a>Esempio

In questo esempio associa le quattro colonne a un **lungo**, una stringa di caratteri, un timestamp e un `DB_NUMERIC` integer, nell'ordine indicato.

```cpp
// db_column_2.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_command(L"Select * from Products") ]
class CProducts {
   [db_column("1")] LONG m_OrderID;
   [db_column("2")] TCHAR m_CustomerID[6];
   [db_column("4")] DB_NUMERIC m_OrderDate;
   [db_column("7", dbtype="DBTYPE_NUMERIC")] DB_NUMERIC m_ShipVia;
};
```

## <a name="requirements"></a>Requisiti

### <a name="attribute-context"></a>Contesto attributo

|||
|-|-|
|**Si applica a**|**classe**, **struct**, membro, metodo|
|**Ripetibile**|No|
|**Attributi obbligatori**|Nessuna|
|**Attributi non validi**|nessuno|

Per altre informazioni sui contesti di attributi, vedere [Contesti di attributi](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vedere anche

[Attributi del consumer OLE DB](ole-db-consumer-attributes.md)<br/>
[Attributi di classe](class-attributes.md)  