---
title: MSSQLSERVER_1457 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 1457 (Database Engine error)
ms.assetid: 28434ba1-b033-4866-ab41-111fccef45a2
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d0cf2eed90e1aea1f636322a0a728720222e0935
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37423480"
---
# <a name="mssqlserver1457"></a>MSSQLSERVER_1457
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|1457|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBM_PAGE_UNDO_PENDING|  
|Testo del messaggio|La sincronizzazione del database mirror '%.*ls' è stata interrotta, lasciando il database in uno stato inconsistente. Comando ALTER DATABASE non riuscito. Verificare che il database mirror sia nuovamente attivo e online, quindi riconnettere l'istanza del server mirror e consentire al database mirror di completare la sincronizzazione.|  
  
## <a name="explanation"></a>Spiegazione  
 Questo messaggio indica che l'istruzione ALTER DATABASE *nome_database* SET PARTNER OFF non è stata eseguita. Il tentativo non riuscito di rimuovere il mirroring del database ha interrotto la sincronizzazione del database mirror. Il database si trova in uno stato inconsistente.  
  
## <a name="user-action"></a>Azione dell'utente  
 Per risolvere il problema, è possibile eseguire una delle operazioni seguenti:  
  
-   Ripristinare il contatto tra il server mirror e il server principale per consentire la sincronizzazione del database mirror.  
  
-   Eliminare il database mirror.  
  
     Dopo aver eliminato il database mirror, sarà possibile crearne uno nuovo dai backup.  
  
    > [!NOTE]  
    >  È possibile eliminare il database mirror quando il mirroring è ancora abilitato solo dopo un'istruzione SET PARTNER OFF non riuscita.  
  
## <a name="see-also"></a>Vedere anche  
 [Mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)   
 [Impostazione del mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md)   
 [Rimozione del mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/removing-database-mirroring-sql-server.md)   
 [Preparazione di un database mirror per il mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
  
