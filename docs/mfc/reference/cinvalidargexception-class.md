---
title: Classe CInvalidArgException
ms.date: 11/04/2016
f1_keywords:
- CInvalidArgException
- AFX/CInvalidArgException
- AFX/CInvalidArgException::CInvalidArgException
helpviewer_keywords:
- CInvalidArgException [MFC], CInvalidArgException
ms.assetid: e43d7c67-1157-47f8-817a-804083e8186e
ms.openlocfilehash: d2df9b482fe95ad0a13a85a51037a4cbbc28d057
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392621"
---
# <a name="cinvalidargexception-class"></a>Classe CInvalidArgException

Questa classe rappresenta una condizione di eccezione di argomento non valido.

## <a name="syntax"></a>Sintassi

```
class CInvalidArgException : public CSimpleException
```

## <a name="members"></a>Membri

### <a name="public-constructors"></a>Costruttori pubblici

|Nome|Descrizione|
|----------|-----------------|
|[CInvalidArgException::CInvalidArgException](#cinvalidargexception)|Costruttore.|

## <a name="remarks"></a>Note

Oggetto `CInvalidArgException` oggetto rappresenta una condizione di eccezione di argomento non valido.

Per ulteriori informazioni sulla gestione delle eccezioni, vedere la [classe CException](../../mfc/reference/cexception-class.md) argomento e [gestione delle eccezioni (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CInvalidArgException`

## <a name="requirements"></a>Requisiti

**Intestazione:** afx.h

##  <a name="cinvalidargexception"></a>  CInvalidArgException::CInvalidArgException

Costruttore.

```
CInvalidArgException();
```

### <a name="remarks"></a>Note

Non utilizzare questo costruttore direttamente. chiamare la funzione globale **AfxThrowInvalidArgException**.

## <a name="see-also"></a>Vedere anche

[Grafico della gerarchia](../../mfc/hierarchy-chart.md)<br/>
[Classe CSimpleException](../../mfc/reference/csimpleexception-class.md)
