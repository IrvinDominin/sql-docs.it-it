---
title: Visualizzare lo stato di un database con mirroring (SQL Server Management Studio) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: database-mirroring
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [SQL Server], database mirroring
- database mirroring [SQL Server], states
ms.assetid: 544f4194-253e-4c57-96ca-31c16301434f
caps.latest.revision: "25"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 1db44478e3b6c8d51e6d66e9dd5a95b7c5059926
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="view-the-state-of-a-mirrored-database-sql-server-management-studio"></a>Visualizzazione dello stato di un database con mirroring (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Durante una sessione di mirroring del database, è possibile visualizzare lo stato nella pagina **Mirroring** della finestra di dialogo **Proprietà database**.  
  
### <a name="to-view-the-status-of-a-database-mirroring-session"></a>Per visualizzare lo stato di una sessione di mirroring del database  
  
1.  Dopo aver attivato la connessione all'istanza del server principale, in Esplora oggetti fare clic sul nome del server per espandere l'albero.  
  
2.  Espandere **Database**e selezionare il database per il mirroring.  
  
3.  Fare clic con il pulsante destro del mouse sul database, scegliere **Attività**e quindi fare clic su **Server mirror**. Viene visualizzata la pagina **Mirroring** della finestra di dialogo **Proprietà database** .  
  
4.  In seguito all'avvio del mirroring, nel pannello **Stato** verrà visualizzato lo stato della sessione di mirroring del database nel momento in cui si è selezionata la pagina **Mirroring** o si è fatto clic sul pulsante **Aggiorna** . Gli stati possibili sono indicati di seguito:  
  
    |Stati|Spiegazione|  
    |------------|-----------------|  
    |\<vuoto>|Non esiste alcuna sessione di mirroring del database e non ci sono attività da segnalare nella pagina **Mirroring** .|  
    |Paused|Il database principale è in esecuzione, ma non viene inviato alcun log al server mirror. La copia mirror del database non è disponibile.|  
    |Nessuna connessione|L'istanza del server principale non può connettersi ai partner o all'istanza del server di controllo del mirroring (se disponibile).|  
    |Sincronizzazione in corso|La posizione del contenuto del database mirror precede quella del database principale. L'istanza del server principale invia record di log all'istanza del server mirror, che applica le modifiche al database mirror per eseguirne il rollforward.<br /><br /> All'avvio della sessione di mirroring del database, i database mirror e principale sono in stato di sincronizzazione.|  
    |Failover|Nell'istanza del server principale è iniziato un failover manuale (inversione di ruolo), che non è stato ancora accettato dal server mirror.|  
    |Sincronizzato|Il database mirror contiene gli stessi dati del database principale. I failover manuale e automatico sono possibili *solo* in stato sincronizzato.|  
  
## <a name="see-also"></a>Vedere anche  
 [Stati di mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/mirroring-states-sql-server.md)  
  
  
