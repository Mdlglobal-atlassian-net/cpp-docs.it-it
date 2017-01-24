---
title: "Funzioni intrinseche InterlockedOr | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_InterlockedOr8_nf"
  - "_InterlockedOr_HLEAcquire"
  - "_InterlockedOr16_nf"
  - "_InterlockedOr64"
  - "_InterlockedOr8_np"
  - "_InterlockedOr64_cpp"
  - "_InterlockedOr8_acq"
  - "_InterlockedOr_nf"
  - "_InterlockedOr64_acq"
  - "_InterlockedOr_np"
  - "_InterlockedOr8"
  - "_InterlockedOr"
  - "_InterlockedOr64_np"
  - "_InterlockedOr_acq"
  - "_InterlockedOr64_HLERelease"
  - "_InterlockedOr16_np"
  - "_InterlockedOr_cpp"
  - "_InterlockedOr8_rel"
  - "_InterlockedOr64_rel"
  - "_InterlockedOr16_acq"
  - "_InterlockedOr_rel"
  - "_InterlockedOr16_rel"
  - "_InterlockedOr_HLERelease"
  - "_InterlockedOr64_HLEAcquire"
  - "_InterlockedOr16"
  - "_InterlockedOr64_nf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_InterlockedOr intrinseco"
  - "_InterlockedOr_acq intrinseco"
  - "_InterlockedOr_HLEAcquire intrinseco"
  - "_InterlockedOr_HLERelease intrinseco"
  - "_InterlockedOr_nf intrinseco"
  - "_InterlockedOr_np intrinseco"
  - "_InterlockedOr_rel intrinseco"
  - "_InterlockedOr16 intrinseco"
  - "_InterlockedOr16_acq intrinseco"
  - "_InterlockedOr16_nf intrinseco"
  - "_InterlockedOr16_np intrinseco"
  - "_InterlockedOr16_rel intrinseco"
  - "_InterlockedOr64 intrinseco"
  - "_InterlockedOr64_acq intrinseco"
  - "_InterlockedOr64_HLEAcquire intrinseco"
  - "_InterlockedOr64_HLERelease intrinseco"
  - "_InterlockedOr64_nf intrinseco"
  - "_InterlockedOr64_np intrinseco"
  - "_InterlockedOr64_rel intrinseco"
  - "_InterlockedOr8 intrinseco"
  - "_InterlockedOr8_acq intrinseco"
  - "_InterlockedOr8_nf intrinseco"
  - "_InterlockedOr8_np intrinseco"
  - "_InterlockedOr8_rel intrinseco"
  - "InterlockedOr intrinseco"
  - "InterlockedOr64 intrinseco"
ms.assetid: 5f265240-7af8-44b7-b952-19f3a9c56186
caps.latest.revision: 19
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Funzioni intrinseche InterlockedOr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Sezione specifica Microsoft**  
  
 Eseguire un'operazione atomica OR bit per bit su una variabile condivisa da più thread.  
  
## Sintassi  
  
```  
long _InterlockedOr(    long volatile * Value,    long Mask ); long _InterlockedOr_acq(    long volatile * Value,    long Mask ); long _InterlockedOr_HLEAcquire(    long volatile * Value,    long Mask ); long _InterlockedOr_HLERelease(    long volatile * Value,    long Mask ); long _InterlockedOr_nf(    long volatile * Value,    long Mask ); long _InterlockedOr_np(    long volatile * Value,    long Mask ); long _InterlockedOr_rel(    long volatile * Value,    long Mask ); char _InterlockedOr8(    char volatile * Value,    long Mask ); char _InterlockedOr8_acq(    char volatile * Value,    char Mask ); char _InterlockedOr8_nf(    char volatile * Value,    char Mask ); char _InterlockedOr8_np(    char volatile * Value,    char Mask ); char _InterlockedOr8_rel(    char volatile * Value,    char Mask ); short _InterlockedOr16(    short volatile * Value,    short Mask ); short _InterlockedOr16_acq(    short volatile * Value,    short Mask ); short _InterlockedOr16_nf(    short volatile * Value,    short Mask ); short _InterlockedOr16_np(    short volatile * Value,    short Mask ); short _InterlockedOr16_rel(    short volatile * Value,    short Mask ); __int64 _InterlockedOr64(    __int64 volatile * Value,    __int64 Mask ); __int64 _InterlockedOr64_acq(    __int64 volatile * Value,    __int64 Mask );  __int64 _InterlockedOr64_HLEAcquire(    __int64 volatile * Value,    __int64 Mask ); __int64 _InterlockedOr64_HLERelease(    __int64 volatile * Value,    __int64 Mask );  __int64 _InterlockedOr64_nf(    __int64 volatile * Value,    __int64 Mask ); __int64 _InterlockedOr64_np(    __int64 volatile * Value,    __int64 Mask ); __int64 _InterlockedOr64_rel(    __int64 volatile * Value,    __int64 Mask );  
```  
  
#### Parametri  
 \[in, out\] `Value`  
 Puntatore al primo operando, da sostituire con il risultato.  
  
 \[in\] `Mask`  
 Secondo operando.  
  
## Valore restituito  
 Valore originale a cui punta il primo parametro.  
  
## Requisiti  
  
|Funzione intrinseca|Architettura|Header|  
|-------------------------|------------------|------------|  
|`_InterlockedOr`, `_InterlockedOr8`, `_InterlockedOr16`, `_InterlockedOr64`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_InterlockedOr_acq`, `_InterlockedOr_nf`, `_InterlockedOr_rel`, `_InterlockedOr8_acq`, `_InterlockedOr8_nf`, `_InterlockedOr8_rel`, `_InterlockedOr16_acq`, `_InterlockedOr16_nf`, `_InterlockedOr16_rel`, `_InterlockedOr64_acq`, `_InterlockedOr64_nf`, `_InterlockedOr64_rel`|ARM|\<intrin.h\>|  
|`_InterlockedOr_np`, `_InterlockedOr8_np`, `_InterlockedOr16_np`, `_InterlockedOr64_np`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_InterlockedOr_HLEAcquire`, `_InterlockedOr_HLERelease`, `_InterlockedOr64_HLEAcquire`, `_InterlockedOr64_HLERelease`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h\>|  
  
## Note  
 Il numero nel nome di ogni funzione specifica la dimensione in bit degli argomenti.  
  
 Sulle piattaforme ARM usare le funzioni intrinseche con i suffissi `_acq` e `_rel` per la semantica di acquisizione e di rilascio, ad esempio all'inizio e alla fine di una sezione critica.  Le funzioni intrinseche ARM con suffisso `_nf` \("nessun limite"\) non fungono da barriera di memoria.  
  
 Le funzioni intrinseche con suffisso `_np` \("nessuna prelettura"\) impediscono l'inserimento di una possibile operazione di prelettura da parte del compilatore.  
  
 Sulle piattaforme Intel che supportano le istruzioni HLE \(Hardware Lock Elision\), le funzioni intrinseche con suffissi `_HLEAcquire` e `_HLERelease` includono un hint per il processore che consente di accelerare le prestazioni eliminando un passaggio di blocco scrittura nell'hardware.  Se queste funzioni intrinseche vengono chiamate su piattaforme che non supportano HLE, l'hint viene ignorato.  
  
## Esempio  
  
```  
// _InterlockedOr.cpp  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_InterlockedOr)  
  
int main()  
{  
        long data1 = 0xFF00FF00;  
        long data2 = 0x00FFFF00;  
        long retval;  
        retval = _InterlockedOr(&data1, data2);  
        printf_s("0x%x 0x%x 0x%x", data1, data2, retval);   
}  
```  
  
  **0xffffff00 0xffff00 0xff00ff00**   
## Fine sezione specifica Microsoft  
  
## Vedere anche  
 [Intrinseci del compilatore](../intrinsics/compiler-intrinsics.md)   
 [Conflitti con il compilatore x86](../build/conflicts-with-the-x86-compiler.md)