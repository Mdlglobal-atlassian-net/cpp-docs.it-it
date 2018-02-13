---
title: CTypedPtrList (classe) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTypedPtrList
- AFXTEMPL/CTypedPtrList
- AFXTEMPL/CTypedPtrList::AddHead
- AFXTEMPL/CTypedPtrList::AddTail
- AFXTEMPL/CTypedPtrList::GetAt
- AFXTEMPL/CTypedPtrList::GetHead
- AFXTEMPL/CTypedPtrList::GetNext
- AFXTEMPL/CTypedPtrList::GetPrev
- AFXTEMPL/CTypedPtrList::GetTail
- AFXTEMPL/CTypedPtrList::RemoveHead
- AFXTEMPL/CTypedPtrList::RemoveTail
- AFXTEMPL/CTypedPtrList::SetAt
dev_langs: C++
helpviewer_keywords:
- CTypedPtrList [MFC], AddHead
- CTypedPtrList [MFC], AddTail
- CTypedPtrList [MFC], GetAt
- CTypedPtrList [MFC], GetHead
- CTypedPtrList [MFC], GetNext
- CTypedPtrList [MFC], GetPrev
- CTypedPtrList [MFC], GetTail
- CTypedPtrList [MFC], RemoveHead
- CTypedPtrList [MFC], RemoveTail
- CTypedPtrList [MFC], SetAt
ms.assetid: c273096e-1756-4340-864b-4a08b674a65e
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 318373755ff05667d94b051dabf42822b34894b0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="ctypedptrlist-class"></a>Classe CTypedPtrList
Fornisce un "wrapper" indipendente dai tipi per gli oggetti della classe `CPtrList`.  
  
## <a name="syntax"></a>Sintassi  
  
```  
template<class BASE_CLASS, class TYPE>  
class CTypedPtrList : public BASE_CLASS  
```  
  
#### <a name="parameters"></a>Parametri  
 `BASE_CLASS`  
 Classe di base della classe elenco puntatore tipizzato. deve essere una classe di elenco puntatore ( `CObList` o `CPtrList`).  
  
 `TYPE`  
 Tipo degli elementi da archiviare nell'elenco di classi di base.  
  
## <a name="members"></a>Membri  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CTypedPtrList::AddHead](#addhead)|Aggiunge un elemento (o tutti gli elementi in un altro elenco) all'inizio dell'elenco (effettua un nuovo inizio).|  
|[CTypedPtrList::AddTail](#addtail)|Aggiunge un elemento (o tutti gli elementi in un altro elenco) alla fine dell'elenco (effettua una nuova fine).|  
|[CTypedPtrList::GetAt](#getat)|Ottiene l'elemento in una determinata posizione.|  
|[CTypedPtrList::GetHead](#gethead)|Restituisce l'elemento head dell'elenco (non può essere vuoto).|  
|[CTypedPtrList::GetNext](#getnext)|Ottiene l'elemento successivo per eseguire l'iterazione.|  
|[CTypedPtrList::GetPrev](#getprev)|Ottiene l'elemento precedente per eseguire l'iterazione.|  
|[CTypedPtrList::GetTail](#gettail)|Restituisce l'elemento della parte finale dell'elenco (non può essere vuoto).|  
|[CTypedPtrList::RemoveHead](#removehead)|Rimuove l'elemento head dell'elenco.|  
|[CTypedPtrList::RemoveTail](#removetail)|Rimuove l'elemento dalla coda dell'elenco.|  
|[CTypedPtrList::SetAt](#setat)|Imposta l'elemento in una determinata posizione.|  
  
## <a name="remarks"></a>Note  
 Quando si utilizza `CTypedPtrList` anziché `CObList` o `CPtrList`, la funzionalità di controllo dei tipi C++ consente di eliminare gli errori causati da tipi di puntatore non corrispondenti.  
  
 Inoltre, il `CTypedPtrList` wrapper esegue gran parte del cast che sarebbe necessario se utilizza `CObList` o `CPtrList`.  
  
 Poiché tutti `CTypedPtrList` funzioni inline, utilizzo del modello non in modo significativo la dimensione o velocità del codice.  
  
 Elenchi derivato da `CObList` può essere serializzata, ma quelli derivati da `CPtrList` non è possibile.  
  
 Quando un oggetto `CTypedPtrList` viene eliminato oppure quando gli elementi vengono rimossi, vengono eliminati solo i puntatori e non le entità che referenziano.  
  
 Per ulteriori informazioni sull'utilizzo `CTypedPtrList`, vedere gli articoli [raccolte](../../mfc/collections.md) e [classi basate su modello](../../mfc/template-based-classes.md).  
  
## <a name="example"></a>Esempio  
 Questo esempio viene creata un'istanza di `CTypedPtrList`, aggiunge un oggetto, serializza l'elenco su disco e quindi Elimina l'oggetto:  
  
 [!code-cpp[NVC_MFCCollections#110](../../mfc/codesnippet/cpp/ctypedptrlist-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCCollections#111](../../mfc/codesnippet/cpp/ctypedptrlist-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 `BASE_CLASS`  
  
 `_CTypedPtrList`  
  
 `CTypedPtrList`  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** afxtempl.h  
  
##  <a name="addhead"></a>CTypedPtrList::AddHead  
 Questa funzione membro chiama `BASE_CLASS` **:: AddHead**.  
  
```  
POSITION AddHead(TYPE newElement);  
void AddHead(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```  
  
### <a name="parameters"></a>Parametri  
 *TIPO*  
 Tipo degli elementi da archiviare nell'elenco di classi di base.  
  
 `newElement`  
 Il puntatore all'oggetto da aggiungere a questo elenco. Oggetto **NULL** il valore è consentito.  
  
 `BASE_CLASS`  
 Classe di base della classe elenco puntatore tipizzato. deve essere una classe di elenco puntatore ( [CObList](../../mfc/reference/coblist-class.md) o [CPtrList](../../mfc/reference/cptrlist-class.md)).  
  
 `pNewList`  
 Un puntatore a un altro [CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md) oggetto. Gli elementi in `pNewList` verrà aggiunto all'elenco.  
  
### <a name="return-value"></a>Valore restituito  
 Restituisce la prima versione di **posizione** valore dell'elemento appena inserito.  
  
### <a name="remarks"></a>Note  
 La prima versione aggiunge un nuovo elemento prima l'elemento head dell'elenco. La seconda versione aggiunge un altro elenco di elementi che precedono l'intestazione.  
  
##  <a name="addtail"></a>CTypedPtrList::AddTail  
 Questa funzione membro chiama `BASE_CLASS` **:: AddTail**.  
  
```  
POSITION AddTail(TYPE newElement);  
void AddTail(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```  
  
### <a name="parameters"></a>Parametri  
 *TIPO*  
 Tipo degli elementi da archiviare nell'elenco di classi di base.  
  
 `newElement`  
 Il puntatore all'oggetto da aggiungere a questo elenco. Oggetto **NULL** il valore è consentito.  
  
 `BASE_CLASS`  
 Classe di base della classe elenco puntatore tipizzato. deve essere una classe di elenco puntatore ( [CObList](../../mfc/reference/coblist-class.md) o [CPtrList](../../mfc/reference/cptrlist-class.md)).  
  
 `pNewList`  
 Un puntatore a un altro [CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md) oggetto. Gli elementi in `pNewList` verrà aggiunto all'elenco.  
  
### <a name="return-value"></a>Valore restituito  
 Restituisce la prima versione di **posizione** valore dell'elemento appena inserito.  
  
### <a name="remarks"></a>Note  
 La prima versione aggiunge un nuovo elemento dopo la fine dell'elenco. La seconda versione aggiunge un altro elenco di elementi dopo la fine dell'elenco.  
  
##  <a name="getat"></a>CTypedPtrList::GetAt  
 Una variabile di tipo **posizione** è una chiave per l'elenco.  
  
```  
TYPE& GetAt(POSITION position);  
TYPE GetAt(POSITION position) const;  
```  
  
### <a name="parameters"></a>Parametri  
 *TIPO*  
 Parametro di modello che specifica il tipo di elementi archiviati nell'elenco.  
  
 *posizione*  
 Oggetto **posizione** valore restituito da una precedente `GetHeadPosition` o **trovare** chiamata di funzione membro.  
  
### <a name="return-value"></a>Valore restituito  
 Se l'elenco è accessibile tramite un puntatore a un **CTypedPtrList const**, quindi `GetAt` restituisce un puntatore di tipo specificato dal parametro di modello *tipo*. In questo modo la funzione può essere utilizzato solo sul lato destro di un'istruzione di assegnazione e quindi protegge l'elenco dalla modifica.  
  
 Se l'elenco è possibile accedere direttamente o tramite un puntatore a un `CTypedPtrList`, quindi `GetAt` restituisce un riferimento a un puntatore di tipo specificato dal parametro di modello *tipo*. Questo consente la funzione può essere utilizzata su entrambi i lati di un'istruzione di assegnazione e pertanto le voci dell'elenco da modificare.  
  
### <a name="remarks"></a>Note  
 Non ha lo stesso come un indice e non è possibile operare su un **posizione** valore manualmente. `GetAt`Recupera il `CObject` puntatore associata a una determinata posizione.  
  
 È necessario assicurarsi che il **posizione** valore rappresenta una posizione valida nell'elenco. Se non è valido, la versione di Debug della libreria di classi Microsoft Foundation asserzioni.  
  
 Questa funzione inline chiama `BASE_CLASS` **:: GetAt**.  
  
##  <a name="gethead"></a>CTypedPtrList::GetHead  
 Ottiene il puntatore che rappresenta l'elemento head dell'elenco.  
  
```  
TYPE& GetHead();  
TYPE GetHead() const;  
```  
  
### <a name="parameters"></a>Parametri  
 *TIPO*  
 Parametro di modello che specifica il tipo di elementi archiviati nell'elenco.  
  
### <a name="return-value"></a>Valore restituito  
 Se l'elenco è accessibile tramite un puntatore a un **CTypedPtrList const**, quindi `GetHead` restituisce un puntatore di tipo specificato dal parametro di modello *tipo*. In questo modo la funzione può essere utilizzato solo sul lato destro di un'istruzione di assegnazione e quindi protegge l'elenco dalla modifica.  
  
 Se l'elenco è possibile accedere direttamente o tramite un puntatore a un `CTypedPtrList`, quindi `GetHead` restituisce un riferimento a un puntatore di tipo specificato dal parametro di modello *tipo*. Questo consente la funzione può essere utilizzata su entrambi i lati di un'istruzione di assegnazione e pertanto le voci dell'elenco da modificare.  
  
### <a name="remarks"></a>Note  
 È necessario assicurarsi che l'elenco non è vuota prima di chiamare `GetHead`. Se l'elenco è vuoto, la versione di Debug della libreria di classi Microsoft Foundation asserzioni. Utilizzare [IsEmpty](../../mfc/reference/coblist-class.md#isempty) per verificare che l'elenco contiene elementi.  
  
##  <a name="getnext"></a>CTypedPtrList::GetNext  
 Ottiene l'elemento di elenco, identificato da `rPosition`, quindi imposta `rPosition` per il **posizione** valore della voce successiva nell'elenco.  
  
```  
TYPE& GetNext(POSITION& rPosition);  
TYPE GetNext(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Parametri  
 *TIPO*  
 Parametro di modello che specifica il tipo di elementi contenuti in questo elenco.  
  
 `rPosition`  
 Un riferimento a un **posizione** valore restituito da una precedente `GetNext`, `GetHeadPosition`, o un'altra chiamata di funzione membro.  
  
### <a name="return-value"></a>Valore restituito  
 Se l'elenco è accessibile tramite un puntatore a un **CTypedPtrList const**, quindi `GetNext` restituisce un puntatore di tipo specificato dal parametro di modello *tipo*. In questo modo la funzione può essere utilizzato solo sul lato destro di un'istruzione di assegnazione e quindi protegge l'elenco dalla modifica.  
  
 Se l'elenco è possibile accedere direttamente o tramite un puntatore a un `CTypedPtrList`, quindi `GetNext` restituisce un riferimento a un puntatore di tipo specificato dal parametro di modello *tipo*. Questo consente la funzione può essere utilizzata su entrambi i lati di un'istruzione di assegnazione e pertanto le voci dell'elenco da modificare.  
  
### <a name="remarks"></a>Note  
 È possibile utilizzare `GetNext` in un ciclo di iterazione in avanti, se si stabilisce la posizione iniziale con una chiamata a `GetHeadPosition` o [CPtrList::Find](../../mfc/reference/coblist-class.md#find).  
  
 È necessario assicurarsi che il **posizione** valore rappresenta una posizione valida nell'elenco. Se non è valido, la versione di Debug della libreria di classi Microsoft Foundation asserzioni.  
  
 Se l'elemento recuperato è l'ultimo nell'elenco, quindi il nuovo valore di `rPosition` è impostato su **NULL**.  
  
 È possibile rimuovere un elemento durante un'iterazione. Per vedere l'esempio [CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat).  
  
##  <a name="getprev"></a>CTypedPtrList::GetPrev  
 Ottiene l'elemento di elenco, identificato da `rPosition`, quindi imposta `rPosition` per il **posizione** valore della voce nell'elenco precedente.  
  
```  
TYPE& GetPrev(POSITION& rPosition);  
TYPE GetPrev(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Parametri  
 *TIPO*  
 Parametro di modello che specifica il tipo di elementi contenuti in questo elenco.  
  
 `rPosition`  
 Un riferimento a un **posizione** valore restituito da una precedente `GetPrev` o un'altra chiamata di funzione membro.  
  
### <a name="return-value"></a>Valore restituito  
 Se l'elenco è accessibile tramite un puntatore a un **CTypedPtrList const**, quindi `GetPrev` restituisce un puntatore di tipo specificato dal parametro di modello *tipo*. In questo modo la funzione può essere utilizzato solo sul lato destro di un'istruzione di assegnazione e quindi protegge l'elenco dalla modifica.  
  
 Se l'elenco è possibile accedere direttamente o tramite un puntatore a un `CTypedPtrList`, quindi `GetPrev` restituisce un riferimento a un puntatore di tipo specificato dal parametro di modello *tipo*. Questo consente la funzione può essere utilizzata su entrambi i lati di un'istruzione di assegnazione e pertanto le voci dell'elenco da modificare.  
  
### <a name="remarks"></a>Note  
 È possibile utilizzare `GetPrev` in un ciclo di iterazione inversa se si stabilisce la posizione iniziale con una chiamata a `GetTailPosition` o **trovare**.  
  
 È necessario assicurarsi che il **posizione** valore rappresenta una posizione valida nell'elenco. Se non è valido, la versione di Debug della libreria di classi Microsoft Foundation asserzioni.  
  
 Se l'elemento recuperato è il primo nell'elenco, quindi il nuovo valore di `rPosition` è impostato su **NULL**.  
  
##  <a name="gettail"></a>CTypedPtrList::GetTail  
 Ottiene il puntatore che rappresenta l'elemento head dell'elenco.  
  
```  
TYPE& GetTail();  
TYPE GetTail() const;  
```  
  
### <a name="parameters"></a>Parametri  
 *TIPO*  
 Parametro di modello che specifica il tipo di elementi archiviati nell'elenco.  
  
### <a name="return-value"></a>Valore restituito  
 Se l'elenco è accessibile tramite un puntatore a un **CTypedPtrList const**, quindi `GetTail` restituisce un puntatore di tipo specificato dal parametro di modello *tipo*. In questo modo la funzione può essere utilizzato solo sul lato destro di un'istruzione di assegnazione e quindi protegge l'elenco dalla modifica.  
  
 Se l'elenco è possibile accedere direttamente o tramite un puntatore a un `CTypedPtrList`, quindi `GetTail` restituisce un riferimento a un puntatore di tipo specificato dal parametro di modello *tipo*. Questo consente la funzione può essere utilizzata su entrambi i lati di un'istruzione di assegnazione e pertanto le voci dell'elenco da modificare.  
  
### <a name="remarks"></a>Note  
 È necessario assicurarsi che l'elenco non è vuota prima di chiamare `GetTail`. Se l'elenco è vuoto, la versione di Debug della libreria di classi Microsoft Foundation asserzioni. Utilizzare [IsEmpty](../../mfc/reference/coblist-class.md#isempty) per verificare che l'elenco contiene elementi.  
  
##  <a name="removehead"></a>CTypedPtrList::RemoveHead  
 Rimuove l'elemento head dell'elenco e lo restituisce.  
  
```  
TYPE RemoveHead();
```  
  
### <a name="parameters"></a>Parametri  
 *TIPO*  
 Parametro di modello che specifica il tipo di elementi archiviati nell'elenco.  
  
### <a name="return-value"></a>Valore restituito  
 Il puntatore in precedenza in corrispondenza dell'inizio dell'elenco. Questo puntatore è del tipo specificato dal parametro di modello *tipo*.  
  
### <a name="remarks"></a>Note  
 È necessario assicurarsi che l'elenco non è vuota prima di chiamare `RemoveHead`. Se l'elenco è vuoto, la versione di Debug della libreria di classi Microsoft Foundation asserzioni. Utilizzare [IsEmpty](../../mfc/reference/coblist-class.md#isempty) per verificare che l'elenco contiene elementi.  
  
##  <a name="removetail"></a>CTypedPtrList::RemoveTail  
 Rimuove l'elemento dalla coda dell'elenco e lo restituisce.  
  
```  
TYPE RemoveTail();
```  
  
### <a name="parameters"></a>Parametri  
 *TIPO*  
 Parametro di modello che specifica il tipo di elementi archiviati nell'elenco.  
  
### <a name="return-value"></a>Valore restituito  
 Il puntatore in precedenza nella fase finale dell'elenco. Questo puntatore è del tipo specificato dal parametro di modello *tipo*.  
  
### <a name="remarks"></a>Note  
 È necessario assicurarsi che l'elenco non è vuota prima di chiamare `RemoveTail`. Se l'elenco è vuoto, la versione di Debug della libreria di classi Microsoft Foundation asserzioni. Utilizzare [IsEmpty](../../mfc/reference/coblist-class.md#isempty) per verificare che l'elenco contiene elementi.  
  
##  <a name="setat"></a>CTypedPtrList::SetAt  
 Questa funzione membro chiama `BASE_CLASS` **:: SetAt**.  
  
```  
void SetAt(POSITION pos, TYPE newElement);
```  
  
### <a name="parameters"></a>Parametri  
 `pos`  
 Il **posizione** dell'elemento da impostare.  
  
 *TIPO*  
 Tipo degli elementi da archiviare nell'elenco di classi di base.  
  
 `newElement`  
 Il puntatore all'oggetto da scrivere nell'elenco.  
  
### <a name="remarks"></a>Note  
 Una variabile di tipo **posizione** è una chiave per l'elenco. Non ha lo stesso come un indice e non è possibile operare su un **posizione** valore manualmente. `SetAt`Scrive il puntatore all'oggetto della posizione specificata nell'elenco.  
  
 È necessario assicurarsi che il **posizione** valore rappresenta una posizione valida nell'elenco. Se non è valido, la versione di Debug della libreria di classi Microsoft Foundation asserzioni.  
  
 Per ulteriori osservazioni, vedere [CObList::SetAt](../../mfc/reference/coblist-class.md#setat).  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio MFC COLLECT](../../visual-cpp-samples.md)   
 [Grafico delle gerarchie](../../mfc/hierarchy-chart.md)   
 [Classe CPtrList](../../mfc/reference/cptrlist-class.md)   
 [Classe CObList](../../mfc/reference/coblist-class.md)