---
title: Aggiungere una funzione membro
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.classes.member.function
- vc.codewiz.function.overview
helpviewer_keywords:
- member functions, adding to classes
- classes [C++], adding members
- add member function wizard [C++]
ms.assetid: 55b25ddb-541d-44ed-957c-974ef91cfc85
ms.openlocfilehash: 1cd7abbbc43ae56861b3b83451b41933b8b0b4f0
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693412"
---
# <a name="add-a-member-function"></a>Aggiungere una funzione membro

Nella **Visualizzazione classi** è possibile aggiungere una funzione membro a qualsiasi classe. Quando si esegue questa operazione, vengono aggiunti una dichiarazione al file di intestazione e un corpo di funzione membro stub al file di implementazione della classe, che è possibile modificare in seguito.

**Per aggiungere una funzione membro a una classe:**

1. Nella **Visualizzazione classi** espandere il nodo del progetto per visualizzare le classi nel progetto. Per aprire la **Visualizzazione classi**, sulla barra dei menu scegliere **Visualizza**, **Visualizzazione classi**.

1. Aprire il menu di scelta rapida per la classe a cui si vuole aggiungere una funzione membro, quindi scegliere **Aggiungi**, **Aggiungi funzione**.

1. Specificare i dettagli appropriati sulla funzione membro. Per altre informazioni, vedere [Aggiunta guidata funzione membro](#add-member-function-wizard).

1. Scegliere il pulsante **Fine** per generare il codice della funzione membro.

## <a name="in-this-section"></a>Contenuto della sezione

- [Aggiunta guidata funzione membro](#add-member-function-wizard)

## <a name="add-member-function-wizard"></a>Aggiunta guidata funzione membro

Questa procedura guidata consente di aggiungere una dichiarazione di funzione membro al file di intestazione, nonché di aggiungere un'implementazione della funzione membro stub al file di implementazione per la classe selezionata.

Dopo aver aggiunto la funzione membro usando la procedura guidata, è possibile modificare il codice nell'ambiente di sviluppo.

- **Tipo restituito**

  Imposta il tipo restituito per la funzione membro da aggiungere. È possibile specificare un tipo restituito personalizzato oppure selezionarlo dall'elenco dei tipi disponibili. Per altre informazioni sui tipi, vedere [Tipi fondamentali](../cpp/fundamental-types-cpp.md).

  | | | |
  |---|---|---|
  | `char` | `int` | `unsigned int` |
  | `double` | `long` | `unsigned long` |
  | `float` | `short` | `void` |
  | `HRESULT` | `unsigned char` | |

- **Nome funzione**

  Imposta il nome della funzione membro da aggiungere.

- **Tipo parametro**

  Imposta il tipo di parametro da aggiungere per la funzione membro, se la funzione membro include parametri. È possibile specificare un tipo di parametro personalizzato oppure selezionarlo dall'elenco dei tipi disponibili.

  | | | |
  |---|---|---|
  | `char` | `int` | `unsigned char` |
  | `double` | `long` | `unsigned int` |
  | `float` | `short` | `unsigned long` |

- **Nome parametro**

  Imposta il nome del parametro da aggiungere per la funzione membro, se la funzione membro include parametri.

- **Elenco parametri**

  Visualizza un elenco dei parametri aggiunti alla funzione membro. Per aggiungere un parametro all'elenco, specificare un tipo e un nome nella caselle **Tipo parametro** e **Nome parametro** e fare clic su **Aggiungi**. Per rimuovere un parametro dall'elenco, selezionare il parametro e quindi **Rimuovi**.

- **Accesso**

  Imposta l'accesso alla funzione membro. I modificatori di accesso sono parole chiave che specificano l'accesso di altre classi alla funzione membro. Per altre informazioni sulla specifica dell'accesso, vedere [Controllo dell'accesso ai membri](../cpp/member-access-control-cpp.md). Il livello di accesso alla funzione membro è impostato su `public` per impostazione predefinita.

  - [public](../cpp/public-cpp.md)
  - [protected](../cpp/protected-cpp.md)
  - [private](../cpp/private-cpp.md)

  Controllare se la nuova funzione membro è statica o virtuale e se è inline o pura. Se si imposta la funzione membro come pura, la casella di controllo **Virtual** è selezionata e la casella di controllo **Inline** non è più disponibile. L'impostazione predefinita prevede una funzione membro non statica non virtuale.

  | Opzione | Descrizione |
  |--------|-------------|
  | [Static](../cpp/storage-classes-cpp.md) |  Specifica che la funzione è globale e può essere chiamata all'esterno della classe, anche senza la creazione di istanze della classe. La funzione membro non ha accesso a membri non statici. Una funzione membro specificata come `Static` non può essere virtuale. |
  | [Virtual](../cpp/virtual-cpp.md) | Garantisce che venga chiamata la funzione membro corretta per un oggetto, indipendentemente dall'espressione usata per eseguire la chiamata di funzione. Una funzione membro specificata come `Virtual` non può essere statica. |
  | **Pure** | Indica che non viene offerta alcuna implementazione per la funzione membro virtuale dichiarata. Il valore **Pure** può essere specificato solo per le funzioni membro virtuali. Una classe che contiene almeno una funzione membro virtuale pura è considerata una classe astratta. Le classi derivate dalla classe astratta devono implementare la funzione membro virtuale pura o sono anch'esse classi astratte. |
  | [Inline](../cpp/inline-functions-cpp.md) | Indica al compilatore di inserire una copia del corpo della funzione membro in ogni punto in cui viene chiamata la funzione membro. Una funzione membro specificata come **Inline** non può essere pura. |

- **File con estensione cpp**

  Imposta il percorso del file in cui viene scritta l'implementazione della funzione membro stub. Per impostazione predefinita, l'implementazione viene scritta nel file con estensione cpp della classe in cui viene aggiunta la funzione membro. Fare clic sul pulsante con i puntini di sospensione per modificare il nome file. L'implementazione della funzione membro viene aggiunta al contenuto del file selezionato.

- **Commentoo**

  Specifica un commento nel file di intestazione per la funzione membro.

- **Firma funzione**

  Visualizza i valori letterali della funzione membro dal codice quando si seleziona **Fine**. Il testo in questa casella non può essere modificato. Per modificare la funzione membro, modificare le caselle appropriate nella procedura guidata.
