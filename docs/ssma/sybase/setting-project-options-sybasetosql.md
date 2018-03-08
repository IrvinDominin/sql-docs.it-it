---
title: Impostazione delle opzioni progetto (SybaseToSQL) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-sybase
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords: Project Options Setting
ms.assetid: 97b70fc8-1f68-4f15-8e22-db5b784ea4ec
caps.latest.revision: "9"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 750be041907417b0683633fbe59f88fdb5b53ead
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="setting-project-options-sybasetosql"></a>Impostazione delle opzioni progetto (SybaseToSQL)
Per ogni progetto SSMA, è possibile impostare opzioni del livello di progetto. Queste opzioni specificano la conversione degli oggetti, il caricamento di oggetti, SQL azure, interfaccia utente e le impostazioni di migrazione di dati. Prima di convertire oggetti [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure o la migrazione dei dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, verificare che le opzioni di configurazione siano appropriate per il progetto.  
  
SSMA consente di configurare le opzioni predefinite per tutti i progetti. Queste opzioni vengono applicate a qualsiasi nuovo progetto creato. È quindi possibile personalizzare le opzioni per ogni progetto.  
  
## <a name="configuration-options-and-modes"></a>Modalità e le opzioni di configurazione  
SSMA con cinque set di impostazioni di progetto:  
  
1.  Informazioni sul progetto  
  
2.  Generale (conversione, migrazione e la raccolta dei dati)  
  
3.  Synchronization  
  
4.  INTERFACCIA UTENTE GRAFICA  
  
5.  Mapping dei tipi  
  
Include inoltre quattro modalità per la configurazione di queste impostazioni:  
  
1.  Default  
  
2.  Optimistic  
  
3.  Full  
  
4.  Personalizzato  
  
La modalità predefinita è consigliata per la maggior parte degli utenti. La modalità ottimistica mantiene più la sintassi di Sybase Adaptive Server Enterprise (ASE) corrente e più facile la lettura. Tuttavia, mantenendo la sintassi corrente potrebbe non essere accurata. Se è necessario convertire la sintassi di base equivalente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o sintassi SQL Azure, la modalità completa esegue una conversione completa, ma il codice risulta potrebbe essere più difficile da leggere. In modalità personalizzata, impostare le opzioni.  
  
Le impostazioni sono descritte nella sezione dell'interfaccia utente di questa documentazione. Per ulteriori informazioni sulle impostazioni e come le impostazioni vengono applicate in ogni modalità, vedere gli argomenti seguenti:  
  
-   [Le impostazioni del progetto &#40; Conversione &#41; &#40; SybaseToSQL &#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md)  
  
-   [Le impostazioni del progetto &#40; La migrazione &#41; &#40; SybaseToSQL &#41;](../../ssma/sybase/project-settings-migration-sybasetosql.md)  
  
-   [Le impostazioni del progetto &#40; Sincronizzazione &#41; &#40; SybaseToSQL &#41;](../../ssma/sybase/project-settings-synchronization-sybasetosql.md)  
  
-   [Le impostazioni del progetto &#40; GUI &#41; &#40; SybaseToSQL &#41;](../../ssma/sybase/project-settings-gui-sybasetosql.md)  
  
-   [Le impostazioni del progetto &#40; Mapping dei tipi di &#41; &#40; SybaseToSQL &#41;](../../ssma/sybase/project-settings-type-mapping-sybasetosql.md)  
  
-   [Le impostazioni del progetto &#40; Database SQL di Azure &#41; &#40; SybaseToSQL &#41;](../../ssma/sybase/project-settings-azure-sql-db-sybasetosql.md)  
  
## <a name="setting-project-options"></a>Impostazione delle opzioni di progetto  
In SSMA, è possibile configurare le impostazioni predefinite per tutti i progetti. Queste impostazioni vengono salvate nel file di configurazione di SSMA e applicate a qualsiasi nuovo progetto creato.  
  
**Per impostare opzioni di progetto predefinite**  
  
1.  Nel **strumenti** dal menu **impostazioni di progetto predefinite**.  
  
2.  Nel **impostazioni di progetto predefinite** la finestra di dialogo, utilizzare una delle procedure seguenti:  
  
    -   Selezionare il tipo di progetto di migrazione per i quali impostazioni sono necessarie per essere visualizzati o modificati da **versione di destinazione della migrazione** drop verso il basso fare clic su Generale nella parte inferiore del riquadro a sinistra e quindi selezionare la conversione o la migrazione o SQL Azure.  
  
    -   Per selezionare una modalità predefinita, il **modalità** casella di riepilogo a discesa, selezionare **predefinito**, **Optimistic**, o **completo**.  
  
    -   Per specificare le impostazioni personalizzate, selezionare o immettere le nuove impostazioni o i valori.  
  
3.  Fare clic su **OK** per salvare le impostazioni.  
  
È anche possibile personalizzare le impostazioni per il progetto corrente. Queste impostazioni vengono salvate nel file di progetto corrente.  
  
**Per personalizzare le impostazioni per il progetto corrente**  
  
1.  Nel **strumenti** dal menu **impostazioni progetto**.  
  
2.  Nel **impostazioni progetto** la finestra di dialogo, utilizzare una delle procedure seguenti:  
  
    -   Per selezionare una modalità predefinita, il **modalità** casella di riepilogo a discesa, selezionare **predefinito**, **Optimistic**, o **completo**.  
  
    -   Per specificare una modalità personalizzata, nel **modalità** elenchi a discesa, selezionare **personalizzato**, selezionare un'opzione nel riquadro a sinistra, fare clic sull'impostazione o un valore nel riquadro di destra, quindi selezionare o immettere la nuova impostazione o un valore.  
  
3.  Fare clic su **OK** per salvare le impostazioni.  
  
## <a name="next-steps"></a>Next Steps  
Il passaggio successivo della migrazione dipende dalle esigenze del progetto:  
  
-   Se si desidera personalizzato per il mapping dei tipi di dati di origine e di destinazione, vedere [Mapping Sybase ASE e tipi di dati di SQL Server &#40; SybaseToSQL &#41; ](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
-   In caso contrario, è possibile convertire le definizioni degli oggetti di database Sybase in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o le definizioni degli oggetti di SQL Azure. Per ulteriori informazioni, vedere [convertire gli oggetti di Database di Sybase ASE &#40; SybaseToSQL &#41; ](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md).  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database di Sybase ASE a SQL Server: database SQL di Azure &#40; SybaseToSQL &#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
