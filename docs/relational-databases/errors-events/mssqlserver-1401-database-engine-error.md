---
title: MSSQLSERVER_1401 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1401 (Database Engine error)
ms.assetid: 02928770-aa63-4509-8713-406c73e4cedc
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 23dc13b8dac23914cc4f337e4b39fbf84ee4b782
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47700979"
---
# <a name="mssqlserver1401"></a>MSSQLSERVER_1401
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|1401|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBM_MASTERSTARTUP|  
|Testo del messaggio|Avvio della routine del thread master del mirroring del database non riuscito per il motivo seguente: %ls. Eliminare la causa dell'errore, quindi riavviare il servizio SQL Server.|  
  
## <a name="explanation"></a>Spiegazione  
L'avvio del thread di controllo del mirroring non è riuscito.  
  
## <a name="user-action"></a>Azione dell'utente  
Nel log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cercare l'errore associato che ha preceduto la visualizzazione di questo messaggio. Eliminare la causa dell'errore e quindi riavviare il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER).  
  
## <a name="see-also"></a>Vedere anche  
[Avviare, arrestare, sospendere, riprendere, riavviare il motore di database, SQL Server Agent o SQL Server Browser](~/database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
