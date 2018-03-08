---
title: Utilizzo di progetti SSMA (OracleToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Customizing Project Settings
ms.assetid: ee5d94c0-c7a6-4779-bd32-729bdaf61e1b
caps.latest.revision: "11"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: On Demand
ms.openlocfilehash: 230e3b73b1903a4a74c98fed108600ffd9d5a523
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="working-with-ssma-projects-oracletosql"></a>Lavorare con progetti SSMA (OracleToSQL)
Per eseguire la migrazione di database Oracle a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], creare innanzitutto un progetto SSMA. Il progetto è un file che contiene le informazioni seguenti:  
  
-   I metadati relativi a database Oracle di cui si desidera eseguire la migrazione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
-   I metadati sull'istanza di destinazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] che riceverà la migrazione di oggetti e i dati.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]informazioni di connessione.  
  
-   Le impostazioni del progetto.  
  
Quando si apre un progetto, si viene disconnessi da Oracle e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Che consente di lavorare offline. Per informazioni sulla riconnessione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], vedere [connessione a SQL Server &#40; OracleToSQL &#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md).  
  
## <a name="reviewing-default-project-settings"></a>Verificare le impostazioni di progetto predefinito  
SSMA contiene diverse impostazioni per la conversione e il caricamento di oggetti di database, la migrazione dei dati e la sincronizzazione di SSMA con Oracle e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Le impostazioni predefinite sono appropriate per molti utenti. Tuttavia, prima di creare un nuovo progetto SSMA, è consigliabile verificare le impostazioni. Se si desidera, è possibile modificare le impostazioni predefinite che verranno utilizzate per tutti i nuovi progetti.  
  
**Per controllare le impostazioni di progetto predefinito**  
  
1.  Nel **strumenti** menu, fare clic su **impostazioni di progetto predefinite**.  
  
2.  Selezionare il tipo di progetto in **versione di destinazione della migrazione** elenco a discesa sono necessarie da visualizzare o modificare le impostazioni e quindi fare clic su **generale** scheda.  
  
3.  Nel riquadro a sinistra, fare clic su **conversione**.  
  
4.  Nel riquadro di destra, esaminare e modificare le impostazioni in base alle esigenze. Per ulteriori informazioni su queste impostazioni, vedere [impostazioni progetto &#40; Conversione &#41; &#40; OracleToSQL &#41; ](../../ssma/oracle/project-settings-conversion-oracletosql.md).  
  
5.  Ripetere i passaggi da 1 a 3 per le pagine di migrazione, la sincronizzazione, gli oggetti di sistema durante il caricamento, GUI e Mapping dei tipi.  
  
    -   Per informazioni sulle impostazioni di migrazione, vedere [impostazioni progetto &#40; La migrazione &#41; &#40; OracleToSQL &#41; ](../../ssma/oracle/project-settings-migration-oracletosql.md).  
  
    -   Per informazioni sulle impostazioni di oggetto di sistema, vedere [impostazioni progetto &#40; Il caricamento di oggetti di sistema &#41; &#40; OracleToSQL &#41; ](../../ssma/oracle/project-settings-loading-system-objects-oracletosql.md).  
  
    -   Per informazioni sulle impostazioni per la sincronizzazione con [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], vedere [impostazioni progetto &#40; Sincronizzazione &#41; &#40; OracleToSQL &#41; ](../../ssma/oracle/project-settings-synchronization-oracletosql.md).  
  
    -   Per informazioni sulle impostazioni di interfaccia utente grafica, vedere [impostazioni progetto &#40; GUI &#41; &#40; OracleToSQL &#41; ](../../ssma/oracle/project-settings-gui-oracletosql.md).  
  
    -   Per informazioni sulle impostazioni di mapping dei tipi di dati, vedere [impostazioni progetto &#40; Mapping dei tipi di &#41; &#40; OracleToSQL &#41; ](../../ssma/oracle/project-settings-type-mapping-oracletosql.md).  
  
## <a name="creating-new-projects"></a>Creazione di nuovi progetti  
Eseguire la migrazione di dati da database Oracle a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è innanzitutto necessario creare un progetto.  
  
**Per creare un progetto**  
  
1.  Nel **File** menu, fare clic su **nuovo progetto**.  
  
    Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
2.  Nel **nome** , immettere un nome per il progetto.  
  
3.  Nel **percorso** casella, immettere o selezionare una cartella per il progetto e quindi fare clic su **OK**.  
  
4.  Nel **migrazione a** elenco a discesa, selezionare la versione di destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] usato per la migrazione. Le opzioni disponibili sono:  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016  
  
    -   Database SQL di Azure  
  
## <a name="customizing-project-settings"></a>Personalizzazione delle impostazioni di progetto  
Inoltre, per definire impostazioni predefinite del progetto che si applicano a tutti i nuovi progetti SSMA, è possibile personalizzare le impostazioni per ogni progetto. Per ulteriori informazioni, vedere [OracleToSQL impostazione delle opzioni progetto &#40; &#41;](../../ssma/oracle/setting-project-options-oracletosql.md).  
  
Quando si personalizza il mapping di tipi di dati tra database di origine e di destinazione, è possibile definire i mapping per il progetto, un database o un livello di oggetto. Per ulteriori informazioni, vedere [OracleToSQL Mapping Oracle e tipi di dati di SQL Server &#40; &#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md).  
  
## <a name="saving-projects"></a>Il salvataggio dei progetti  
Quando si salva un progetto, SSMA mantiene le impostazioni di progetto e, facoltativamente, i metadati del database, al file di progetto.  
  
**Per salvare un progetto**  
  
-   Nel **File** menu, fare clic su **Salva progetto**.  
  
    Se gli schemi nel progetto sono state modificate o non sono stati convertiti, SSMA verrà richiesto di caricare e salvare i metadati. Caricare e salvare i metadati consentono di lavorare offline. È anche possibile inviare un file di progetto completo ad altri utenti, come il personale di supporto tecnico. Se viene chiesto di salvare i metadati, eseguire le operazioni seguenti:  
  
    1.  Per ogni schema che viene visualizzato lo stato **metadati mancanti**, selezionare la casella di controllo accanto al nome del database.  
  
        Salvataggio di metadati potrebbe richiedere alcuni minuti. Se non si desidera salvare i metadati, non selezionare le caselle di controllo.  
  
    2.  Fare clic su di **salvare** pulsante.  
  
        SSMA analizzerà gli schemi di Oracle e salvare i metadati del file di progetto.  
  
## <a name="opening-projects"></a>Apertura di progetti  
Quando si apre un progetto, la disconnessione da Oracle e da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Che consente di lavorare offline. Per aggiornare i metadati, caricare gli oggetti di database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Per eseguire la migrazione dei dati, è necessario riconnettersi a Oracle e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
**Per aprire un progetto**  
  
1.  Utilizzare una delle procedure riportate di seguito:  
  
    -   Nel **File** dal menu **progetti recenti**, quindi scegliere il progetto che si desidera aprire.  
  
    -   Nel **File** dal menu **Apri progetto**, individuare il file di progetto .o2ssproj, selezionare il file e quindi fare clic su **aprire**.  
  
2.  Per ristabilire la connessione a Oracle, nel **File** menu, fare clic su **Riconnetti a Oracle**.  
  
3.  Per riconnettersi [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]via il **File** menu, fare clic su **Riconnetti a SQL Server**.  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo del processo di migrazione consiste nel [la connessione al Database Oracle (OracleToSQL)](http://msdn.microsoft.com/en-us/e276cdbf-3ebc-4ba8-b40d-a7a42befa2b6).  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database Oracle a SQL Server &#40; OracleToSQL &#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
[Connessione a Oracle Database &#40; OracleToSQL &#41;](../../ssma/oracle/connecting-to-oracle-database-oracletosql.md)  
[Connessione a SQL Server &#40; OracleToSQL &#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md)  
  
