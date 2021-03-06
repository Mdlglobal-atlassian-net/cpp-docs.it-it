---
title: Classe CInstantaneousTransition
ms.date: 11/04/2016
f1_keywords:
- CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::Create
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::m_dblFinalValue
helpviewer_keywords:
- CInstantaneousTransition [MFC], CInstantaneousTransition
- CInstantaneousTransition [MFC], Create
- CInstantaneousTransition [MFC], m_dblFinalValue
ms.assetid: c3d5121f-2c6b-4221-9e57-10e082a31120
ms.openlocfilehash: 15c471d64309cc1358c9c5b0b33577261dd877f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372432"
---
# <a name="cinstantaneoustransition-class"></a>Classe CInstantaneousTransition

Incapsula una transizione istantanea.

## <a name="syntax"></a>Sintassi

```
class CInstantaneousTransition : public CBaseTransition;
```

## <a name="members"></a>Membri

### <a name="public-constructors"></a>Costruttori pubblici

|Nome|Descrizione|
|----------|-----------------|
|[CInstantaneousTransition::CInstantaneousTransition](#cinstantaneoustransition)|Costruisce un oggetto di transizione e ne inizializza il valore finale.|

### <a name="public-methods"></a>Metodi pubblici

|Nome|Descrizione|
|----------|-----------------|
|[CInstantaneousTransition::Create](#create)|Chiama la libreria di transizione per creare un oggetto COM di transizione incapsulato. (Esegue l'override di [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Membri dati pubblici

|Nome|Descrizione|
|----------|-----------------|
|[CInstantaneousTransition::m_dblFinalValue](#m_dblfinalvalue)|Valore della variabile di animazione alla fine della transizione.|

## <a name="remarks"></a>Osservazioni

Durante una transizione istantanea, il valore della variabile di animazione cambia istantaneamente dal valore corrente a un valore finale specificato. La durata di questa transizione è sempre zero. Poiché tutte le transizioni vengono cancellate automaticamente, si consiglia di allocare le autorizzazioni utilizzando operator new. L'oggetto COM IUIAnimationTransition incapsulato viene creato da CAnimationController::AnimateGroup, fino a quel momento è NULL. La modifica delle variabili membro dopo la creazione di questo oggetto COM non ha alcun effetto.

## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition (Transizione di Base](../../mfc/reference/cbasetransition-class.md)

[CInstantaneousTransition](../../mfc/reference/cinstantaneoustransition-class.md)

## <a name="requirements"></a>Requisiti

**Intestazione:** afxanimationcontroller.h

## <a name="cinstantaneoustransitioncinstantaneoustransition"></a><a name="cinstantaneoustransition"></a>CInstantaneousTransition::CInstantaneousTransition

Costruisce un oggetto di transizione e ne inizializza il valore finale.

```
CInstantaneousTransition(DOUBLE dblFinalValue);
```

### <a name="parameters"></a>Parametri

*dblFinalValue (valore dblFinale)*<br/>
Valore della variabile di animazione alla fine della transizione.

## <a name="cinstantaneoustransitioncreate"></a><a name="create"></a>CInstantaneousTransition::Create

Chiama la libreria di transizione per creare un oggetto COM di transizione incapsulato.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Parametri

*pLibreria*<br/>
Puntatore a [un'interfaccia IUIAnimationTransitionLibrary](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), che definisce una libreria di transizioni standard.

### <a name="return-value"></a>Valore restituito

TRUESe la transizione viene creata correttamente. in caso contrario, FALSE.

## <a name="cinstantaneoustransitionm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a>CInstantaneousTransition::m_dblFinalValue

Valore della variabile di animazione alla fine della transizione.

```
DOUBLE m_dblFinalValue;
```

## <a name="see-also"></a>Vedere anche

[Classi](../../mfc/reference/mfc-classes.md)
