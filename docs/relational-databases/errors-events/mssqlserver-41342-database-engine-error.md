---
title: MSSQLSERVER_41342 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 41342 (Database Engine error)
ms.assetid: 28270d98-c543-4e7d-b40c-2200e38dce1c
caps.latest.revision: 8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6b9ee43a6cc137e44e4c772001be7b8640181dd6
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver41342"></a>MSSQLSERVER_41342
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|41342|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|HK_HW_NOT_SUPPORTED|  
|Testo del messaggio|Il modello del processore del sistema non supporta la creazione di *costrutto*. Questo errore si verifica in genere nei processori meno recenti. Per informazioni sui modelli supportati, vedere la documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
## <a name="explanation"></a>Spiegazione  
Per le tabelle con ottimizzazione per la memoria è richiesto un modello di processore che supporta le operazioni di scambio e confronto atomiche su valori a 128 bit, che richiedono l'istruzione di assembly CMPXCHG16B. Alcuni modelli di processore AMD meno recenti non supportano l'istruzione CMPXCHG16B. Inoltre, alcuni ambienti di virtualizzazione non consentono l'utilizzo di questa istruzione per impostazione predefinita.  
  
## <a name="user-action"></a>Azione dell'utente  
Aggiornare il processore. Se il processore supporta l'istruzione e si sta eseguendo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in una macchina virtuale, modificare la configurazione per supportare l'istruzione CMPXCHG16B.  
  
## <a name="see-also"></a>Vedere anche  
[OLTP in memoria &#40;ottimizzazione per la memoria&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
