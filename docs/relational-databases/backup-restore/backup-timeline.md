---
title: "Sequenza temporale backup | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.SWB.POINTINTIMERESTORE.F1"
  - "sql13.swb.backuptimeline.f1"
helpviewer_keywords: 
  - "Sequenza temporale backup"
ms.assetid: ae3565f2-ddb2-4469-a992-7531d4f9ebb8
caps.latest.revision: 24
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 24
---
# Sequenza temporale backup
  Usare la finestra di dialogo **Cronologia di backup** per trovare e specificare backup ed eseguire il ripristino temporizzato di un database. Per accedere alla finestra di dialogo **Cronologia di backup**, fare clic su **Cronologia** nel riquadro **Ripristina database (pagina Generale)**. In questa finestra di dialogo è possibile visualizzare una cronologia delle operazioni di ripristino effettuate nel database.  
  
 Tramite Database Recovery Advisor viene assicurato che vengano selezionati solo i backup necessari per il ripristino a questa temporizzazione. Questi backup selezionati costituiscono il piano di ripristino consigliato per l'operazione di ripristino. È consigliabile utilizzare solo i backup selezionati. Per informazioni su Database Recovery Advisor, vedere [Panoramica del ripristino e del recupero &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md).  
  
## Ripristina fino a  
 L'opzione **Ultimo backup eseguito** è selezionata per impostazione predefinita. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] selezionerà i backup appropriati per il ripristino del database, che verrà ripristinato nel punto dell'ultimo backup. Fare clic su **Data e ora specifiche** per impostare manualmente la data e l'ora (selezionando un punto nel tempo specifico).  
  
 Attraverso **Data e ora specifiche** è possibile arrestare il ripristino a una data e un'ora specifiche selezionate. La cronologia mostra una rappresentazione delle operazioni di backup eseguite nelle 24 ore prossime alla data e all'ora selezionate.  
  
 **Data**  
 Immettere o selezionare una data dall'elenco a discesa.  
  
 **Time**  
 Immettere o selezionare una data per definire il punto specifico per l'arresto del ripristino.  
  
 **Intervallo temporale**  
 Consente di visualizzare le opzioni per i tipi di intervallo visualizzabili all'interno della sequenza temporale.  
  
## Cronologia e legenda  
 Utilizzare la barra di scorrimento sotto la cronologia per spostare il cursore avanti e indietro lungo la sequenza temporale. Fare clic su un backup per spostare la barra di scorrimento alla fine del backup selezionato. Posizionare il mouse su un marcatore per visualizzare una Descrizione comandi che fornisce informazioni sul set di backup selezionato. Le informazioni sul backup vengono mostrate all'interno della cronologia tramite i seguenti marcatori.  
  
 Triangolo di grandi dimensioni  
 Rappresenta i backup completi eseguiti nel database e indica il momento specifico in cui è stato eseguito ogni backup completo.  
  
 Triangolo di piccole dimensioni  
 Rappresenta i backup differenziali eseguiti nel database e indica il momento specifico in cui è stato eseguito ogni backup differenziale.  
  
 Aree verdi ombreggiate  
 Rappresentano la copertura del backup del log delle transazioni.  
  
 Linea rossa  
 Può essere posizionata lungo la cronologia solo nel punto in cui è possibile effettuare il ripristino. Spostando la linea rossa lungo la cronologia, è possibile regolare data e ora visualizzate nelle caselle **Data** e **Ora**.  
  
## Vedere anche  
 [Ripristina database &#40;pagina Generale&#41;](../../relational-databases/backup-restore/restore-database-general-page.md)  
  
  