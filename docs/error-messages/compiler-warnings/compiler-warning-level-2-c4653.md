---
title: Avviso del compilatore (livello 2) C4653
ms.date: 11/04/2016
f1_keywords:
- C4653
helpviewer_keywords:
- C4653
ms.assetid: 90ec3317-3d39-4b4c-bcd1-97e7c799e1b6
ms.openlocfilehash: 994e9a4963e7e10af2313b3dcea5bb8b2b93426e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161737"
---
# <a name="compiler-warning-level-2-c4653"></a>Avviso del compilatore (livello 2) C4653

opzione del compilatore ' Option ' non coerente con l'intestazione precompilata; opzione della riga di comando corrente ignorata

Un'opzione specificata con l'opzione Usa intestazioni precompilate ([/Yu](../../build/reference/yu-use-precompiled-header-file.md)) non è coerente con le opzioni specificate al momento della creazione dell'intestazione precompilata. Questa compilazione usava l'opzione specificata al momento della creazione dell'intestazione precompilata.

Questo avviso può verificarsi quando viene specificato un valore diverso per l'opzione di struttura di Pack ([/ZP](../../build/reference/zp-struct-member-alignment.md)) durante la compilazione dell'intestazione precompilata.
