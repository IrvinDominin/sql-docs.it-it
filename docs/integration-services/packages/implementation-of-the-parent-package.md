---
title: "Implementazione del pacchetto padre | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pacchetti padre [Integration Services]"
ms.assetid: d8f94830-fa27-4151-88df-cbdc6bf0fc80
caps.latest.revision: 24
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 24
---
# Implementazione del pacchetto padre
  Quando si esegue il bilanciamento del carico dei pacchetti di SSIS tra più server, dopo la creazione e la distribuzione dei pacchetti figlio e dopo la creazione dei processi remoti di SQL Server Agent per eseguirli, è necessario creare il pacchetto padre. Il pacchetto padre deve contenere più attività Esegui processo di SQL Server Agent, ognuna della quali è responsabile di chiamare un diverso processo di SQL Server Agent che esegue uno dei pacchetti figlio. Le attività Esegui processo di SQL Server Agent nel pacchetto padre eseguono a loro volta i vari processi di SQL Server Agent. Ogni attività nel pacchetto padre contiene informazioni riguardanti ad esempio la modalità di connessione al server remoto e il processo da eseguire su tale server. Per altre informazioni, vedere [Execute SQL Server Agent Job Task](../../integration-services/packages/execute-sql-server-agent-job-task.md).  
  
 Per identificare il pacchetto padre che esegue i pacchetti figlio, in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] fare clic con il pulsante destro del mouse sul pacchetto in Esplora soluzioni, quindi scegliere **Pacchetto punto di ingresso**.  
  
## Elenco di pacchetti figlio  
 Se si distribuisce un progetto contenente un pacchetto padre e pacchetti figlio nel server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], sarà possibile visualizzare un elenco dei pacchetti figlio eseguiti dal pacchetto padre. Quando si esegue il pacchetto padre, un report **Panoramica** per il pacchetto padre è generato automaticamente in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Il report include un elenco dei pacchetti figlio eseguiti dall'attività Esegui pacchetto contenuta nel pacchetto padre, come illustrato nell'immagine seguente.  
  
 ![Report Panoramica con elenco di pacchetti figlio](../../integration-services/packages/media/overviewreport-childpackagelisting.png "Report Panoramica con elenco di pacchetti figlio")  
  
 Per informazioni sull'accesso al report **Panoramica** , vedere [Reports for the Integration Services Server](../../integration-services/performance/reports-for-the-integration-services-server.md).  
  
## Vincoli di precedenza nel pacchetto padre  
 Quando si creano vincoli di precedenza tra le attività Esegui processo di SQL Server Agent nel pacchetto padre, tali vincoli di precedenza controllano solo il momento in cui vengono avviati i processi di SQL Server Agent sui server remoti. I vincoli di precedenza non possono ricevere informazioni sull'esito positivo o negativo dei pacchetti figlio eseguiti dai passaggi dei processi di SQL Server Agent.  
  
 L'esito positivo o negativo di un pacchetto figlio non viene pertanto propagato al pacchetto padre, perché l'attività Esegui processo di SQL Server Agent nel pacchetto padre ha unicamente la funzione di richiedere al processo di SQL Server Agent di eseguire il pacchetto figlio. Se la chiamata al processo di SQL Server Agent viene completata correttamente, il pacchetto padre riceve il risultato <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Success>.  
  
 In questo scenario l'eventuale esito negativo indica solamente che si è verificato un errore durante la chiamata remota al processo di SQL Server Agent. Questa situazione si presenta ad esempio quando il server remoto non è disponibile e l'agente non risponde. Finché l'agente è attivo, tuttavia, il pacchetto padre completa correttamente l'attività.  
  
> [!NOTE]  
>  È possibile usare un'attività Esegui SQL contenente un'istruzione Transact-SQL **sp_start_job N'package_name'**. Per altre informazioni, vedere [sp_start_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md).  
  
## Ambiente di debug  
 Durante il test del pacchetto padre è possibile accedere all'ambiente di debug della finestra di progettazione scegliendo Avvia debug (F5) dal menu Debug. In alternativa, è possibile usare l'utilità della riga di comando **dtexec**. Per altre informazioni, vedere [dtexec Utility](../../integration-services/packages/dtexec-utility.md).  
  
  