---
title: MSSQL_ENG020572 | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MSSQL_ENG020572 error
ms.assetid: 636566db-ffcf-4109-8c11-15b8c7cb9cd9
caps.latest.revision: "11"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4cc87be43811e590e1d455cd61505fcf1f04db21
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="mssqleng020572"></a>MSSQL_ENG020572
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|20572|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|La sottoscrizione del Sottoscrittore '%s' dell'articolo '%s' della pubblicazione '%s' è stata reinizializzata dopo un errore di convalida.|  
  
## <a name="explanation"></a>Spiegazione  
 I dati nel Sottoscrittore sono stati convalidati in base a quelli nel server di pubblicazione e non corrispondono, pertanto la convalida non è stata eseguita. Quando è stato specificato che è necessario eseguire la convalida, è stata selezionata l'opzione che prevede la reinizializzazione di una sottoscrizione in caso di mancata convalida. La reinizializzazione di una sottoscrizione implica l'applicazione di un nuovo snapshot nel Sottoscrittore. Per ulteriori informazioni sulla convalida, vedere [Validate Replicated Data](../../relational-databases/replication/validate-replicated-data.md).  
  
## <a name="user-action"></a>Azione dell'utente  
 I dati nel server di pubblicazione e nel Sottoscrittore corrisponderanno dopo l'applicazione del nuovo snapshot nel Sottoscrittore.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento a errori ed eventi &#40;replica&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
