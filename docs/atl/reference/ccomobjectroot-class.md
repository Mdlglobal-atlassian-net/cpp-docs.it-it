---
title: Classe CComObjectRoot
ms.date: 11/04/2016
f1_keywords:
- CComObjectRoot
- atlcom/ATL::CComObjectRoot
helpviewer_keywords:
- CComObjectRoot class
ms.assetid: f8797c38-6e73-4f67-85c2-71654cffa8eb
ms.openlocfilehash: 9a9ffa1813fb15297d209894050b6bcce6802df2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259365"
---
# <a name="ccomobjectroot-class"></a>Classe CComObjectRoot

Questo typedef dei [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) viene creato un modello predefinito del server del modello di threading.

## <a name="syntax"></a>Sintassi

```
typedef CComObjectRootEx<CComObjectThreadModel> CComObjectRoot;
```

## <a name="remarks"></a>Note

`CComObjectRoot` è un `typedef` dei [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) creato un modello predefinito del server del modello di threading. In questo modo [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) farà riferimento a uno [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) oppure [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md).

`CComObjectRootEx` gestisce gestione di conteggio di riferimento di oggetto per gli oggetti aggregati e non aggregati. Contiene il conteggio dei riferimenti oggetto se l'oggetto non è vengono aggregato e contiene il puntatore a unknown esterno se l'oggetto da aggregare. Per gli oggetti aggregati, `CComObjectRootEx` metodi possono essere utilizzati per gestire l'errore dell'oggetto interno per costruire e per proteggere l'oggetto esterno dall'eliminazione quando vengono rilasciate le interfacce interne o l'oggetto interno viene eliminato.

## <a name="requirements"></a>Requisiti

**Intestazione:** atlcom. h

## <a name="see-also"></a>Vedere anche

[Classe CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[Classe CComAggObject](../../atl/reference/ccomaggobject-class.md)<br/>
[Classe CComObject](../../atl/reference/ccomobject-class.md)<br/>
[Classe CComPolyObject](../../atl/reference/ccompolyobject-class.md)<br/>
[Panoramica della classe](../../atl/atl-class-overview.md)
