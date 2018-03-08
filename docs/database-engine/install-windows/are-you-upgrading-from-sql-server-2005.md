---
title: Aggiornamento da SQL Server 2005 | Microsoft Docs
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: install-windows
ms.reviewer: 
ms.suite: sql
ms.technology:
- setup-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad40e66f-71fe-4ee6-9ce3-17127e7b1d7a
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d582d7d9ca0bc90ca40ee34e946d49bf545024bd
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="are-you-upgrading-from-sql-server-2005"></a>Aggiornamento da SQL Server 2005

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
 
 La fine del supporto esteso per SQL Server 2005 è uno dei motivi per cui si consiglia di aggiornare subito il sistema a una nuova versione di SQL Server e al database SQL di Azure. L'aggiornamento consente di garantire sicurezza e conformità, di raggiungere eccellenti livelli di prestazioni e di ottimizzare l'infrastruttura della piattaforma di dati.  
  
 Per altre informazioni, indicazioni e strumenti per pianificare e automatizzare l'aggiornamento o la migrazione, vedere [SQL Server 2005 end of support](http://www.microsoft.com/en-us/server-cloud/products/sql-server-2005/)(Fine del supporto per SQL Server 2005).  
  
## <a name="why-upgrade"></a>Vantaggi dell'aggiornamento  
  
> [!IMPORTANT]  
>  Il supporto esteso per SQL Server 2005 è terminato il 12 aprile 2016. Se si continua a usare SQL Server 2005 dopo il 12 aprile 2016, non si riceveranno più aggiornamenti della sicurezza.  
  
## <a name="choose-your-upgrade-option"></a>Opzioni di aggiornamento disponibili  
Se si aggiornano i database relazionali da SQL Server 2005, queste di seguito sono le opzioni per l'archiviazione relazionale nella piattaforma Microsoft.  
  
Per un'analisi più completa di queste opzioni, [fare clic qui](http://sql05upgrade.azurewebsites.net/).  
  
|Opzione di archiviazione relazionale|Vantaggi|Altri fattori da considerare|  
|-------------------------------|--------------|-------------------------------|  
|**SQL Server locale**<br /><br /> Prendere in considerazione questa opzione per le applicazioni di database di qualsiasi tipo, dai sistemi transazionali ai data warehouse.|Si ha un maggiore controllo sulle funzionalità e la scalabilità perché vengono gestiti sia l'hardware che il software.<br /><br /> Se si esegue l'aggiornamento da SQL Server 2005, questo è l'ambiente più simile.|L'investimento iniziale è elevato ed è necessaria una gestione continua perché è necessario acquistare, mantenere e gestire il proprio hardware e software.<br /><br /> Per altre informazioni, vedere [SQL Server](https://www.microsoft.com/EN-US/server-cloud/products/sql-server-2017/).|  
|**SQL Server ospitato in macchine virtuali di Azure**<br /><br /> Prendere in considerazione questa opzione se si hanno le esigenze seguenti:<br /><br /> Vantaggi associati alla migrazione a un ambiente ospitato.<br /><br /> Controllo sull'ambiente operativo.<br /><br /> Set di funzionalità di SQL Server, già noto.|È possibile eseguire rapidamente la distribuzione da una libreria di immagini della macchina virtuale.<br /><br /> Viene fornito il set di funzionalità completo di SQL Server.<br /><br /> Si risparmiano i costi per l'hardware e il software del server. Si paga per ora in base all'utilizzo.|È necessario configurare e gestire sia SQL Server che il software del sistema operativo.<br /><br /> <br /><br /> Per altre informazioni, vedere [Panoramica di SQL Server in Macchine virtuali di Azure](https://azure.microsoft.com/documentation/articles/virtual-machines-sql-server-infrastructure-services/).<br /><br /> Per informazioni sulla migrazione, vedere [Eseguire la migrazione di un database di SQL Server a SQL Server in una macchina virtuale di Azure](https://azure.microsoft.com/documentation/articles/virtual-machines-migrate-onpremises-database/).|  
|**Servizio di database ospitato nel database SQL di Azure**<br /><br /> Prendere in considerazione questa opzione se si preferisce una soluzione a basso costo che necessita di poca manutenzione.<br /><br /> Questa opzione è particolarmente adatta per le app che non richiedono una capacità costante o che devono fornire un accesso esterno.|La distribuzione è rapida e la scalabilità verticale semplice.<br /><br /> Si paga per ora in base all'utilizzo.<br /><br /> Il costo del servizio include anche la disponibilità elevata e i backup automatici, oltre all'archiviazione.|Il database SQL di Azure non offre alcune delle funzionalità di SQL Server non applicabili a un ambiente cloud ospitato. Per altre informazioni, vedere [Differenze di Transact-SQL del database SQL di Azure](https://azure.microsoft.com/documentation/articles/sql-database-transact-sql-information/).<br /><br /> Anche le dimensioni massime del database SQL di Azure sono di 500 GB, invece dei 524 PB di SQL Server.<br /><br /> Per altre informazioni, vedere [Database SQL](https://azure.microsoft.com/services/sql-database/).<br /><br /> Per informazioni sulla migrazione, vedere [Migrazione di un database SQL Server nel database SQL di Azure](https://azure.microsoft.com/documentation/articles/sql-database-cloud-migrate/).|  
  
 Per alcuni dati e applicazioni si può valutare anche una soluzione non relazionale o NoSQL.  
  
|Soluzione non relazionale|Vantaggi|  
|------------------------------|--------------|  
|**Azure Cosmos DB**<br /><br /> Prendere in considerazione questa opzione per applicazioni moderne, scalabili, mobili e Web che usano i dati JSON e richiedono una combinazione affidabile di funzionalità di query e di elaborazione dei dati transazionali.<br /><br /> Per altre informazioni, vedere [Cosmos DB](http://azure.microsoft.com/services/cosmos-db/).<br /><br /> Per informazioni sull'importazione di dati, vedere [Importare dati in Cosmos DB](http://docs.microsoft.com/azure/cosmos-db/import-data/).|I documenti vengono indicizzati ed è possibile eseguire query usando la sintassi SQL con cui si ha già familiarità.<br /><br /> Il database è senza schema.<br /><br /> È possibile aggiungere proprietà ai documenti senza dover ricompilare gli indici.<br /><br /> Il supporto per JSON e JavaScript viene fornito direttamente all'interno del motore di database.<br /><br /> Il supporto nativo viene fornito per i dati geospaziali e l'integrazione con altri servizi di Azure, inclusi Ricerca di Azure, HDInsight e Data Factory.<br /><br /> Si ottiene un'archiviazione a bassa latenza e ad alte prestazioni con livelli di velocità effettiva riservati.|  
|**Archiviazione tabelle di Azure**<br /><br /> Prendere in considerazione questa opzione per archiviare petabyte di dati semistrutturati in una soluzione conveniente.<br /><br /> Per altre informazioni, vedere [Archivio tabelle](https://azure.microsoft.com/services/storage/tables/).|È possibile sviluppare le app e lo schema della tabella senza disconnettere i dati.<br /><br /> È possibile usare la scalabilità verticale senza partizionamento orizzontale del set di dati.<br /><br /> Si ottiene un'archiviazione con ridondanza geografica che replica i dati in più regioni.|  
  
## <a name="plan-your-upgrade"></a>Pianificare l'aggiornamento  
  
-   Per informazioni su come pianificare l'aggiornamento, vedere la serie seguente di post di blog del team di SQL Server.  
  
    -   [Pianificazione di un aggiornamento efficiente da SQL Server 2005: Passaggio 1 di 3](http://blogs.technet.com/b/dataplatforminsider/archive/2015/12/10/planning-an-efficient-upgrade-from-sql-server-2005-step-1-of-3.aspx)  
  
    -   [Pianificazione di un aggiornamento efficiente da SQL Server 2005: Passaggio 2 di 3](http://blogs.technet.com/b/dataplatforminsider/archive/2015/12/15/planning-an-efficient-upgrade-from-sql-server-2005-step-2-of-3.aspx)  
  
    -   [Pianificazione di un aggiornamento efficiente da SQL Server 2005: Passaggio 3 di 3](http://blogs.technet.com/b/dataplatforminsider/archive/2015/12/17/planning-an-efficient-upgrade-from-sql-server-2005-step-3-of-3.aspx)  
  
-   Vedere i requisiti e le considerazioni in [Pianificazione di un'installazione di SQL Server](../../sql-server/install/planning-a-sql-server-installation.md), oltre a [Requisiti hardware e software per l'installazione di SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   Vedere come eseguire l'aggiornamento.  
  
    -   Esaminare i metodi di aggiornamento disponibili e ottenere informazioni sulla pianificazione e sull'esecuzione dei test nell'articolo [Aggiornare il motore di database](../../database-engine/install-windows/upgrade-database-engine.md).  
  
        > [!IMPORTANT]  
        >  Non è possibile eseguire l'aggiornamento di un'istanza di SQL Server 2005 a un server SQL Server 2017 sul posto. È necessario installare un'istanza di SQL Server 2017, quindi eseguire la migrazione dei database SQL Server 2005 alla nuova installazione. Per altre informazioni, vedere la sezione relativa all'aggiornamento con nuova installazione nell'articolo [Scegliere un metodo di aggiornamento del motore di database](../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md).  
   
  
-   Per altre informazioni, indicazioni e strumenti per pianificare e automatizzare l'aggiornamento o la migrazione, vedere [SQL Server 2005 end of support](http://www.microsoft.com/en-us/server-cloud/products/sql-server-2005/)(Fine del supporto per SQL Server 2005).  
  
## <a name="get-sql-server"></a>Ottieni SQL Server  
 Per scaricare una copia di valutazione di SQL Server, [fare clic qui](http://www.microsoft.com/evalcenter/evaluate-sql-server-2016).  
  
## <a name="next-steps"></a>Next Steps  
 [SQL Server 2017](http://www.microsoft.com/sql-server/sql-server-2017)   
 [Fine del supporto di SQL Server 2005](http://www.microsoft.com/en-us/server-cloud/products/sql-server-2005/)   
  
  
