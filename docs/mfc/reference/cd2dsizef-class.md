---
title: Classe CD2DSizeF
ms.date: 11/04/2016
f1_keywords:
- CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::IsNull
helpviewer_keywords:
- CD2DSizeF [MFC], CD2DSizeF
- CD2DSizeF [MFC], IsNull
ms.assetid: f486a1e1-997d-4286-8cb9-26369dc82055
ms.openlocfilehash: e9c8d77a9f84abe9a483a0f100e1f52b8768202b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557469"
---
# <a name="cd2dsizef-class"></a>Classe CD2DSizeF

Un wrapper per D2D1_SIZE_F.

## <a name="syntax"></a>Sintassi

```
class CD2DSizeF : public D2D1_SIZE_F;
```

## <a name="members"></a>Membri

### <a name="public-constructors"></a>Costruttori pubblici

|Nome|Descrizione|
|----------|-----------------|
|[CD2DSizeF::CD2DSizeF](#cd2dsizef)|Di overload. Costruisce un `CD2DSizeF` dall'oggetto `D2D1_SIZE_F` oggetto.|

### <a name="public-methods"></a>Metodi pubblici

|Nome|Descrizione|
|----------|-----------------|
|[CD2DSizeF::IsNull](#isnull)|Restituisce un **booleana** valore che indica se un'espressione non contiene dati validi (NULL).|

### <a name="public-operators"></a>Operatori pubblici

|Nome|Descrizione|
|----------|-----------------|
|[CD2DSizeF::operator CSize](#operator_csize)|Consente di convertire `CD2DSizeF` a `CSize` oggetto.|

## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà

`D2D1_SIZE_F`

[CD2DSizeF](../../mfc/reference/cd2dsizef-class.md)

## <a name="requirements"></a>Requisiti

**Intestazione:** afxrendertarget. h

##  <a name="cd2dsizef"></a>  CD2DSizeF::CD2DSizeF

Costruisce un oggetto CD2DSizeF dall'oggetto CSize.

```
CD2DSizeF(const CSize& size);
CD2DSizeF(const D2D1_SIZE_F& size);
  CD2DSizeF(const D2D1_SIZE_F* size);

CD2DSizeF(
    FLOAT cx = 0.,
    FLOAT cy = 0.);
```

### <a name="parameters"></a>Parametri

*size*<br/>
dimensioni di origine

*CX*<br/>
larghezza di origine

*CY*<br/>
altezza di origine

##  <a name="isnull"></a>  CD2DSizeF::IsNull

Restituisce un valore booleano che indica se un'espressione non contiene dati validi (Null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Valore restituito

TRUE se la larghezza e altezza sono vuote; in caso contrario, FALSE.

##  <a name="operator_csize"></a>  CD2DSizeF::operator CSize

Converte un oggetto CSize CD2DSizeF.

```
operator CSize();
```

### <a name="return-value"></a>Valore restituito

Valore corrente della dimensione D2D.

## <a name="see-also"></a>Vedere anche

[Classi](../../mfc/reference/mfc-classes.md)
