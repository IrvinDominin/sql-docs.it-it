---
title: Gli strumenti di SQL e le utilità per SQL Server, Database SQL di Azure e Azure SQL Data Warehouse | Microsoft Docs
ms.custom: ''
ms.date: 02/22/2018
ms.prod: sql
ms.prod_service: sql-tools
ms.component: misc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ''
caps.latest.revision: 0
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: a8f31d6479a0a2ba5e5f19f6a0739ab6322de92b
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 08/02/2018
ms.locfileid: "39458985"
---
# <a name="sql-tools-and-utilities-for-sql-server-azure-sql-database-and-azure-sql-data-warehouse"></a>Gli strumenti di SQL e le utilità per SQL Server, Database SQL di Azure e Azure SQL Data Warehouse
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Per gestire (query, monitoraggio e così via) del database è necessario uno strumento. Sono disponibili diversi strumenti di database. Mentre i database possono essere in esecuzione nel cloud, su Windows o su [Linux](../linux/sql-server-linux-overview.md), lo strumento non è necessario per l'esecuzione sulla stessa piattaforma del database. 

Questo articolo fornisce informazioni sugli strumenti disponibili per l'utilizzo dei database SQL. 


## <a name="tools-to-run-queries-and-manage-databases"></a>Strumenti per eseguire query e gestire i database  

| Strumento | Descrizione |
|:--|:--|
| [[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md) | [!INCLUDE[name-sos](../includes/name-sos-short.md)] è uno strumento gratuito, leggero, per la gestione di database ogni volta che sono in esecuzione. Questa versione di anteprima fornisce funzionalità di gestione di database, tra cui un editor Transact-SQL esteso e personalizzabile approfondite lo stato operativo dei database. **[!INCLUDE[name-sos](../includes/name-sos-short.md)] viene eseguito in Windows, macOS e Linux**.|
| [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) | Usare SQL Server Management Studio (SSMS) per eseguire una query, progettare e gestire SQL Server, Database SQL di Azure e Azure SQL Data Warehouse. **SQL Server Management Studio viene eseguito in Windows**.|
| [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md) | Trasforma Visual Studio in un ambiente di sviluppo avanzato per SQL Server, Database SQL di Azure e Azure SQL Data Warehouse. **SSDT viene eseguito in Windows**.|
|[MSSQL-cli](mssql-cli.md)|MSSQL-cli è uno strumento da riga di comando interattivo per l'esecuzione di query SQL Server. **MSSQL-cli viene eseguito in Windows, macOS e Linux**|
| [Visual Studio Code](https://code.visualstudio.com/)| Dopo aver installato Visual Studio Code, installare il [estensione mssql](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql) per lo sviluppo di Microsoft SQL Server, Database SQL di Azure e SQL Data Warehouse. **Visual Studio Code viene eseguito in Windows, macOS e Linux**.|

## <a name="which-tool-should-i-choose"></a>Quale strumento devo scegliere?

- Si desidera gestire un'istanza di SQL Server o database, in un editor leggero in Windows, Linux o Mac? Scegliere [[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md)
- Si desidera gestire un'istanza di SQL Server o database in Windows con il supporto di interfaccia utente grafica completo? Scegliere [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)
- Eseguire operazioni che si desidera creare o mantenere il codice di database, tra cui la convalida della fase di compilazione, refactoring e progettazione di supporto in Windows? Scegliere [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md)
- Si desidera eseguire una query SQL Server con uno strumento da riga di comando che offre IntelliSense, illuminazione-sintassi elevata, e così via? Scegliere [mssql-cli](mssql-cli.md)
- Si desidera scrivere gli script T-SQL in un editor leggero in Windows, Linux o Mac? Scegli [Visual Studio Code](https://code.visualstudio.com/) e il [estensione mssql](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)

## <a name="additional-tools"></a>Strumenti aggiuntivi

| Strumento | Descrizione |
|:--|:--|
| [Gestione configurazione](../tools/configuration-manager/sql-server-configuration-manager-help.md) | Utilizzare Gestione configurazione SQL Server per configurare servizi di SQL Server e configurare la connettività di rete. Configuration Manager viene eseguito in Windows|
|[MSSQL-conf](../linux/sql-server-linux-configure-mssql-conf.md)|Usare mssql-conf per configurare SQL Server in esecuzione in Linux.|
| [SQL Server Migration Assistant](../ssma/sql-server-migration-assistant.md) | Usare SQL Server Migration Assistant per automatizzare la migrazione di database a SQL Server da Microsoft Access, DB2, MySQL, Oracle e Sybase.|
| [Riesecuzione distribuita](../tools/distributed-replay/install-distributed-replay-overview.md) | Usare la funzionalità riesecuzione distribuita che consentono di valutare l'impatto dei futuri aggiornamenti di SQL Server. Inoltre, utilizzare Distributed Replay per valutare l'impatto dell'hardware e aggiornamenti del sistema operativo e ottimizzazione di SQL Server. |
| [ssbdiagnose](../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md) | L'utilità ssbdiagnose segnala i problemi in conversazioni di Service Broker o la configurazione dei servizi di Service Broker. |


## <a name="command-line-utilities"></a>Utilità della riga di comando

  Le utilità della riga di comando consentono di generare script di operazioni [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Nella tabella seguente è riportato l'elenco delle utilità del prompt dei comandi fornite con [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
|**Utility**|**Descrizione**|**Posizione di installazione**|  
|-----------------|---------------------|----------------------|  
|[Utilità bcp](../tools/bcp-utility.md)|Usata per copiare i dati tra un'istanza di [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e un file di dati in un formato specificato dall'utente.|\<*unità*:>\Programmi\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn|  
|[Utilità dta](../tools/dta/dta-utility.md)|Consente di analizzare un carico di lavoro e proporre strutture di progettazione fisica per ottimizzare le prestazioni del server per il carico di lavoro specifico.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Utilità dtexec](../integration-services/packages/dtexec-utility.md)|Utilizzata per configurare ed eseguire un pacchetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Una versione di interfaccia utente di questa utilità del prompt dei comandi è denominata **DTExecUI**e visualizza l'Utilità di esecuzione pacchetti.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[Utilità dtutil](../integration-services/dtutil-utility.md)|Consente di gestire i pacchetti SSIS.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[Distribuire soluzioni di modelli con l'utilità di distribuzione](../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md)|Consente di distribuire progetti di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] in istanze di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\VShell\Common7\IDE|  
|[MSSQL-scripter (anteprima pubblica)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/05/17/try-new-sql-server-command-line-tools-to-generate-t-sql-scripts-and-monitor-dynamic-management-views/)|Utilizzato per generare script crea e Inserisci codice T-SQL per oggetti di database di SQL Server, Database SQL di Azure e Azure SQL Data Warehouse.|Vedere la [repository GitHub](https://github.com/Microsoft/sql-xplat-cli) per informazioni su download e utilizzo.| 
|[Utilità osql](../tools/osql-utility.md)|Consente di immettere istruzioni [!INCLUDE[tsql](../includes/tsql-md.md)] , procedure di sistema e file script al prompt dei comandi.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Utilità profiler](../tools/profiler-utility.md)|Consente di avviare [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] dal prompt dei comandi.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Utilità RS.exe &#40;SSRS&#41;](../reporting-services/tools/rs-exe-utility-ssrs.md)|Consente di eseguire script progettati per la gestione di server di report [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[utilità rsconfig &#40;SSRS&#41;](../reporting-services/tools/rsconfig-utility-ssrs.md)|Consente di configurare una connessione a un server di report.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Utilità rskeymgmt &#40;SSRS&#41;](../reporting-services/tools/rskeymgmt-utility-ssrs.md)|Consente di gestire le chiavi di crittografia in un server di report.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Applicazione sqlagent90](../tools/sqlagent90-application.md)|Utilizzata per avviare [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent da un prompt dei comandi.|\<unità>:\Program Files\Microsoft SQL Server\\<*instance_name*>\MSSQL\Binn|  
|[Utilità sqlcmd](../tools/sqlcmd-utility.md)|Consente di immettere istruzioni [!INCLUDE[tsql](../includes/tsql-md.md)] , procedure di sistema e file script al prompt dei comandi.|\<*unità*:>\Programmi\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn|  
|[Utilità SQLdiag](../tools/sqldiag-utility.md)|Utilizzata per raccogliere informazioni di diagnostica per il Servizio Supporto Tecnico Clienti [!INCLUDE[msCoName](../includes/msconame-md.md)] .|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Applicazione sqllogship](../tools/sqllogship-application.md)|Consente di eseguire operazioni di backup, copia e ripristino da altre applicazioni, nonché di eseguire le attività di pulizia associate per una configurazione per il log shipping, senza eseguire i processi di backup, copia e ripristino.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Utilità SqlLocalDB](../tools/sqllocaldb-utility.md)|Modalità di esecuzione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] destinata agli sviluppatori.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\|  
|[Utilità sqlmaint](../tools/sqlmaint-utility.md)|Utilizzata per eseguire i piani di manutenzione dei database creati nelle precedenti versioni di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|\<unità>:\Programmi\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn|  
|[Utilità sqlps](../tools/sqlps-utility.md)|Consente di eseguire comandi e script di PowerShell, nonché di caricare e registrare il provider e i cmdlet di PowerShell per [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[sqlservr](../tools/sqlservr-application.md)|Consente di avviare e arrestare un'istanza di [!INCLUDE[ssDE](../includes/ssde-md.md)] dal prompt dei comandi per la risoluzione dei problemi.|\<unità>:\Programmi\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn|  
|[Utilità Ssms](../tools/sql-server-management-studio/ssms-utility.md)|Consente di avviare [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] dal prompt dei comandi.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\VSShell\Common7\IDE|  
|[Utilità tablediff](../tools/tablediff-utility.md)|Consente di confrontare i dati di due tabelle e rilevare l'eventuale non convergenza dei dati. Risulta particolarmente utile per la risoluzione dei problemi relativi alla topologia di replica.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]COM|  

## <a name="sql-command-prompt-utilities-syntax-conventions"></a>Convenzioni di sintassi per le utilità del prompt dei comandi SQL  
  
|**Convenzione**|**Utilizzo**|  
|--------------------|------------------|  
|MAIUSCOLE|Istruzioni e termini utilizzati a livello di sistema operativo.|  
|`monospace`|Esempi di comandi e codice di programmazione.|  
|*corsivo*|Parametri specificati dall'utente.|  
|**grassetto**|Comandi, parametri e altri elementi della sintassi che devono essere digitati esattamente come indicato.|  



