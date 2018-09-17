---
title: 'Esercitazione: Backup e ripristino di SQL Server nel servizio di archiviazione Blob di Azure| Microsoft Docs'
ms.custom: ''
ms.date: 04/09/2018
ms.prod: sql
ms.prod_service: database-engine
ms.component: tutorial
ms.reviewer: ''
ms.suite: sql
ms.technology: performance
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016 Preview
ms.assetid: 9e1d94ce-2c93-45d1-ae2a-2a7d1fa094c4
caps.latest.revision: 11
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 2c3ae93bc044f75f502a357df50495f5041b165e
ms.sourcegitcommit: b8e2e3e6e04368aac54100c403cc15fd4e4ec13a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45563705"
---
# <a name="tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service"></a>Esercitazione: Backup e ripristino di SQL Server nel servizio di archiviazione Blob di Azure
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Questa esercitazione contiene nozioni utili sulla scrittura di backup nel servizio di archiviazione Blob di Azure e sul ripristino dallo stesso.  
  
## <a name="what-you-will-learn"></a>Lezioni dell'esercitazione  
Questa esercitazione illustra come creare un account di archiviazione, un contenitore BLOB, la creazione di credenziali per l'accesso all'account di archiviazione, la scrittura di un backup nel servizio BLOB e l'esecuzione di un ripristino semplice. Questa esercitazione è suddivisa in quattro lezioni:  
  
[Lezione 1: Creare gli oggetti della risorsa di archiviazione di Azure](http://msdn.microsoft.com/library/74edd1fd-ab00-46f7-9e29-7ba3f1a446c5)  
In questa lezione verranno creati un account di archiviazione e un contenitore BLOB di Azure.  
  
[Lezione 2: Creare le credenziali di SQL Server](http://msdn.microsoft.com/library/64f8805c-1ddc-4c96-a47c-22917d12e1ab)  
In questa lezione verranno create le credenziali per archiviare le informazioni di sicurezza usate per accedere all'account di archiviazione di Azure.  
  
[Lezione 3: Scrivere un backup completo del database nel servizio di archiviazione BLOB di Azure](https://technet.microsoft.com/library/jj720552\(v=sql.110\).aspx)  
In questa lezione verrà eseguita un'istruzione T-SQL per scrivere un backup del database AdventureWorks2012 nel servizio di archiviazione BLOB di Azure.  
  
[Lezione 4: Eseguire un ripristino da un backup completo del database](http://msdn.microsoft.com/library/580f76e6-9802-4abc-9043-db6de592c733)  
In questa lezione verrà eseguita un'istruzione T-SQL per il ripristino dal backup del database creato nella lezione precedente.  
  
### <a name="requirements"></a>Requisiti  
Per completare l'esercitazione è necessario conoscere i concetti di backup e ripristino di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e la sintassi T-SQL. Per utilizzare l'esercitazione, il sistema deve soddisfare i requisiti seguenti.  
  
-   Un'istanza di [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] e il database AdventureWorks2012 installati.  
  
    L'istanza di SQL Server può essere in locale o in una macchina virtuale di Azure.  
  
    È possibile utilizzare un database utente al posto di AdventureWorks2012 e modificare la sintassi tsql di conseguenza.  
  
-   All'account utente usato per eseguire i comandi BACKUP o RESTORE deve essere associato il ruolo del database **db_backup operator** con autorizzazioni **Modifica qualsiasi credenziale**.  
  
### <a name="additional-reading"></a>Ulteriori informazioni  
Di seguito sono indicati alcuni argomenti consigliati per comprendere i concetti e le procedure consigliate quando si utilizza il servizio di archiviazione BLOB di Azure per i backup di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
1.  [Backup e ripristino di SQL Server con il servizio di archiviazione BLOB di Microsoft Azure](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
2.  [Procedure consigliate e risoluzione dei problemi per il backup di SQL Server nell'URL](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
## <a name="see-also"></a>Vedere anche  
[Backup e ripristino di SQL Server con il servizio di archiviazione BLOB di Microsoft Azure](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)

