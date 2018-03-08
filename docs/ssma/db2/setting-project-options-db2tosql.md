---
title: Impostazione delle opzioni progetto (DB2ToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-db2
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: f325a606-97ac-48bc-b344-b55f5e086a48
caps.latest.revision: "5"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a2ffdaea48e85e53a6ba170ab34251a1d26e193f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="setting-project-options-db2tosql"></a>Impostazione delle opzioni progetto (DB2ToSQL)
Per ogni progetto SSMA è possibile impostare opzioni del livello di progetto. Queste opzioni specificano la conversione degli oggetti, il caricamento di oggetti, impostazioni di migrazione di dati e di interfaccia utente. Prima di convertire oggetti [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o la migrazione dei dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], verificare che le opzioni di configurazione siano appropriate per il progetto.  
  
SSMA consente di configurare le opzioni predefinite per tutti i progetti. Queste opzioni vengono applicate a qualsiasi nuovo progetto creato. È quindi possibile personalizzare le opzioni per ogni progetto.  
  
## <a name="configuration-options-and-modes"></a>Modalità e le opzioni di configurazione  
SSMA con cinque set di impostazioni di progetto:  
  
-   Informazioni sul progetto  
  
-   Generale (conversione, la migrazione, il caricamento di oggetti)  
  
-   Synchronization  
  
-   INTERFACCIA UTENTE GRAFICA  
  
-   Mapping dei tipi  
  
Include inoltre quattro modalità per la configurazione di queste impostazioni:  
  
-   Default  
  
-   Optimistic  
  
-   Full  
  
-   Personalizzato  
  
La modalità predefinita è consigliata per la maggior parte degli utenti. La modalità ottimistica mantiene più la sintassi di DB2 corrente e più facile la lettura. Tuttavia, mantenendo la sintassi corrente potrebbe non essere accurata. Se è necessario convertire la sintassi di DB2 equivalente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] sintassi, la modalità completa esegue la conversione più completa, ma il codice risulta potrebbe essere più difficile da leggere. In modalità personalizzata, impostare le opzioni.  
  
Per ulteriori informazioni sulle impostazioni e come le impostazioni vengono applicate in ogni modalità, vedere gli argomenti seguenti:  
  
-   [Le impostazioni del progetto &#40; Conversione &#41; &#40; DB2ToSQL &#41;](../../ssma/db2/project-settings-conversion-db2tosql.md)  
  
-   [Le impostazioni del progetto &#40; La migrazione &#41; &#40; DB2ToSQL &#41;](../../ssma/db2/project-settings-migration-db2tosql.md)  
  
-   [Le impostazioni del progetto &#40; Sincronizzazione &#41; &#40; DB2ToSQL &#41;](../../ssma/db2/project-settings-synchronization-db2tosql.md)  
  
-   [Le impostazioni del progetto &#40; GUI &#41; &#40; DB2ToSQL &#41;](../../ssma/db2/project-settings-gui-db2tosql.md)  
  
-   [Le impostazioni del progetto &#40; Mapping dei tipi di &#41; &#40; DB2ToSQL &#41;](../../ssma/db2/project-settings-type-mapping-db2tosql.md)  
  
## <a name="setting-project-options"></a>Impostazione delle opzioni di progetto  
In SSMA, è possibile configurare le impostazioni predefinite per tutti i progetti. Queste impostazioni vengono salvate nel file di configurazione di SSMA e applicate a qualsiasi nuovo progetto creato.  
  
**Per impostare opzioni di progetto predefinite**  
  
1.  Nel **strumenti** menu, fare clic su **impostazioni di progetto predefinite**.  
  
2.  Nel **impostazioni di progetto predefinite** la finestra di dialogo, utilizzare una delle procedure seguenti:  
  
    -   Selezionare il tipo di progetto di migrazione per i quali impostazioni sono necessarie per essere visualizzati o modificati da **versione di destinazione della migrazione** elenco a discesa fare clic su **generale** nella parte inferiore del riquadro sinistro e quindi selezionare la conversione o la migrazione.  
  
    -   Per selezionare una modalità predefinita, il **modalità** casella di riepilogo a discesa, selezionare **predefinito**, **Optimistic**, o **completo**.  
  
    -   Per specificare le impostazioni personalizzate, selezionare o immettere le nuove impostazioni o i valori.  
  
3.  Fare clic su **OK** per salvare le impostazioni.  
  
È anche possibile personalizzare le impostazioni per il progetto corrente. Queste impostazioni vengono salvate nel file di progetto corrente.  
  
**Per personalizzare le impostazioni per il progetto corrente**  
  
1.  Nel **strumenti** menu, fare clic su **impostazioni progetto**.  
  
2.  Nel **impostazioni progetto** la finestra di dialogo, utilizzare una delle procedure seguenti:  
  
    -   Per selezionare una modalità predefinita, il **modalità** casella di riepilogo a discesa, selezionare **predefinito**, **Optimistic**, o **completo**.  
  
    -   Per specificare una modalità personalizzata, nel **modalità** , quindi selezionare **personalizzato**e quindi selezionare le impostazioni di progetto appropriate.  
  
3.  Fare clic su **OK** per salvare le impostazioni.  
  
## <a name="next-steps"></a>Next Steps  
Il passaggio successivo della migrazione dipende dalle esigenze del progetto:  
  
-   Per personalizzare il mapping dei tipi di dati di origine e di destinazione, vedere [DB2ToSQL Mapping DB2 e tipi di dati di SQL Server &#40; &#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md).  
  
-   In caso contrario, è possibile convertire le definizioni degli oggetti di database di DB2 in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] definizioni di oggetti. Per ulteriori informazioni, vedere [DB2ToSQL la conversione di schemi di DB2 &#40; &#41;](../../ssma/db2/converting-db2-schemas-db2tosql.md).  
  
## <a name="see-also"></a>Vedere anche  
[Mapping DB2ToSQL DB2 e tipi di dati SQL Server &#40; &#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md)  
  
