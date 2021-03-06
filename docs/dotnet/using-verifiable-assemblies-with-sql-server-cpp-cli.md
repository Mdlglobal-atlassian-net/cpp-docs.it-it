---
title: Utilizzo di assembly verificabili con SQL Server (C++/CLI)
ms.date: 10/17/2018
helpviewer_keywords:
- verifiable assemblies [C++], with SQL Server
ms.assetid: 5248a60d-aa88-4ff3-b30a-b791c3ea2de9
ms.openlocfilehash: 27dec67cc0932a784cdd041ba346bb8c635b280d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384413"
---
# <a name="using-verifiable-assemblies-with-sql-server-ccli"></a>Utilizzo di assembly verificabili con SQL Server (C++/CLI)

Stored procedure estese, incluso nel pacchetto come librerie a collegamento dinamico (DLL), consentono di estendere le funzionalità di SQL Server tramite le funzioni sviluppate con Visual C++. Le stored procedure estese vengono implementate come funzioni nelle DLL. Oltre alle funzioni, stored procedure estese possono inoltre definire [tipi definiti dall'utente](../cpp/classes-and-structs-cpp.md) e aggregazione di funzioni (ad esempio SUM o AVG).

Quando un client esegue una stored procedure estesa, le ricerche di SQL Server per la DLL associati con la stored procedure estesa e carica la DLL. SQL Server chiama la stored procedure estesa richiesta ed eseguita in un contesto di sicurezza specificato. La stored procedure estesa e set di risultati passate e restituisce parametri al server.

SQL Server fornisce le estensioni di Transact-SQL (T-SQL) per consentire l'installazione di assembly verificabili in SQL Server. Il set di autorizzazioni di SQL Server consente di specificare il contesto di sicurezza, con i livelli di sicurezza seguenti:

- Modalità di senza restrizioni: Eseguire il codice a proprio rischio; codice non deve essere indipendente dai tipi verificabile.

- Modalità sicura: Eseguire effettivamente il codice indipendente dai tipi. compilato con /CLR: safe.

> [!IMPORTANT]
> Deprecato di Visual Studio 2015 e Visual Studio 2017 non supporta il **/clr: pure** e **/CLR: safe** la creazione di progetti verificabile. Se è necessario codice verificabile, è consigliabile che si tradurre il codice in c#.

Per creare e caricare un assembly verificabile in SQL Server, usare i comandi Transact-SQL CREATE ASSEMBLY e DROP ASSEMBLY come indicato di seguito:

```sql
CREATE ASSEMBLY <assemblyName> FROM <'Assembly UNC Path'> WITH
  PERMISSION_SET <permissions>
DROP ASSEMBLY <assemblyName>
```

Il comando si specifica PERMISSION_SET specifica il contesto di sicurezza e può avere i valori senza restrizioni, SAFE o esteso.

Inoltre, è possibile usare il comando CREATE FUNCTION per associare ai nomi di metodo in una classe:

```sql
CREATE FUNCTION <FunctionName>(<FunctionParams>)
RETURNS returnType
[EXTERNAL NAME <AssemblyName>:<ClassName>::<StaticMethodName>]
```

## <a name="example"></a>Esempio

Il seguente script SQL (ad esempio, denominato "MyScript. SQL") consente di caricare un assembly in SQL Server e rende disponibile un metodo di una classe:

```sql
-- Create assembly without external access
drop assembly stockNoEA
go
create assembly stockNoEA
from
'c:\stockNoEA.dll'
with permission_set safe

-- Create function on assembly with no external access
drop function GetQuoteNoEA
go
create function GetQuoteNoEA(@sym nvarchar(10))
returns real
external name stockNoEA:StockQuotes::GetQuote
go

-- To call the function
select dbo.GetQuoteNoEA('MSFT')
go
```

Gli script SQL possono essere eseguiti in modo interattivo in SQL Query Analyzer o dalla riga di comando con l'utilità sqlcmd.exe. La seguente riga di comando si connette al server MyServer, utilizza il database predefinito, utilizza una connessione trusted, Myscript e MyResult.

```cmd
sqlcmd -S MyServer -E -i myScript.sql -o myResult.txt
```

## <a name="see-also"></a>Vedere anche

[Classi e struct](../cpp/classes-and-structs-cpp.md)
