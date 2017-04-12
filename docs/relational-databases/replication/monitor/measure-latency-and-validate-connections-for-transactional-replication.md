---
title: "Misurazione della latenza e convalida delle connessioni per la replica transazionale | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Replication Monitor, performance"
  - "tracer tokens [SQL Server replication]"
  - "latency [SQL Server replication]"
  - "transactional replication, tracer tokens"
  - "monitoraggio delle prestazioni [replica di SQL Server], token di traccia"
ms.assetid: 4addd426-7523-4067-8d7d-ca6bae4c9e34
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# Misurazione della latenza e convalida delle connessioni per la replica transazionale
  In questo argomento viene descritto come misurare le connessione di convalida e latenza per la replica transazionale in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite Monitoraggio replica, [!INCLUDE[tsql](../../../includes/tsql-md.md)]o RMO (Replication Management Objects). La replica transazionale offre la funzionalità token di traccia, che rappresenta una modalità pratica di misurazione della latenza nelle topologie di replica transazionale e di convalida delle connessioni tra server di pubblicazione, database di distribuzione e Sottoscrittori. Un token, ovvero una piccola quantità di dati, viene scritto nel log delle transazioni del database di pubblicazione, contrassegnato come se fosse una comune transazione replicata e inviato tramite il sistema in modo da consentire:  
  
-   Il calcolo del tempo che trascorre tra l'esecuzione del commit di una transazione nel server di pubblicazione e l'inserimento del comando corrispondente nel database di distribuzione del server di distribuzione.  
  
-   Il calcolo del tempo che trascorre tra l'inserimento di un comando nel database di distribuzione e l'esecuzione del commit della transazione corrispondente nel Sottoscrittore.  
  
 I risultati ottenuti da questi calcoli consentono all'utente di rispondere a una serie di domande, incluse le seguenti:  
  
-   Quali Sottoscrittori hanno richiesto più tempo per ricevere una modifica dal server di pubblicazione?  
  
-   Tra i Sottoscrittori destinati a ricevere il token di traccia, quali non lo hanno eventualmente ricevuto?  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
-   **Per misurare la latenza e convalidare le connessioni, utilizzando:**  
  
     [Monitoraggio replica per SQL Server](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [oggetti RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
 I token di traccia possono inoltre essere utili quando si mette un sistema in stato di inattività, il che richiede l'arresto di tutte le attività e la verifica dell'avvenuta ricezione di tutte le modifiche in attesa da parte di tutti i nodi. Per ulteriori informazioni, vedere [mettere una topologia di replica & #40; Programmazione Transact-SQL della replica & #41;](../../../relational-databases/replication/administration/quiesce-a-replication-topology-replication-transact-sql-programming.md).  
  
 Per utilizzare i token di traccia, è necessario utilizzare alcune versioni di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:  
  
-   Il database di distribuzione deve essere [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] o versione successiva.  
  
-   Il server di pubblicazione deve essere [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] o versione successiva, oppure deve essere un server di pubblicazione Oracle.  
  
-   Per le sottoscrizioni push, le statistiche dei token di traccia vengono raccolte dal server di pubblicazione, dal server di distribuzione e dai Sottoscrittori se il Sottoscrittore è [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 7.0 o versione successiva.  
  
-   Per le sottoscrizioni pull, le statistiche dei token di traccia vengono raccolte dai soli Sottoscrittori se il Sottoscrittore è [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] o versione successiva. Se il Sottoscrittore è [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 7.0 o [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)], le statistiche vengono raccolte solo dal server di pubblicazione e dal server di distribuzione.  
  
 È inoltre necessario considerare altre problematiche e limitazioni, ovvero:  
  
-   Per poter ricevere un token di traccia, le sottoscrizioni devono essere attive. Una sottoscrizione è attiva se è stata inizializzata.  
  
-   La reinizializzazione elimina i token di traccia in sospeso per le relative sottoscrizioni.  
  
-   I Sottoscrittori ricevono solo i token di traccia creati dopo la sincronizzazione iniziale.  
  
-   I token di traccia non vengono inoltrati dai Sottoscrittori di ripubblicazione.  
  
-   Dopo il failover a un database secondario, Monitoraggio replica non è in grado di regolare il nome dell'istanza di pubblicazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e continuerà a visualizzare informazioni sulla replica con il nome dell'istanza primaria originale di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Dopo il failover, non è possibile immettere un token di traccia tramite Monitoraggio replica, nondimeno un token di traccia immesso nel nuovo server di pubblicazione tramite [!INCLUDE[tsql](../../../includes/tsql-md.md)]è visibile in Monitoraggio replica.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di Monitoraggio replica per SQL Server  
 Per informazioni sull'avvio di monitoraggio replica, vedere [avviare Monitoraggio replica](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
#### Per inserire un token di traccia e visualizzarne le informazioni  
  
1.  Espandere un gruppo di server di pubblicazione nel riquadro sinistro, espandere un server di pubblicazione e quindi fare clic su una pubblicazione.  
  
2.  Fare clic sulla scheda **Token di traccia** .  
  
3.  Fare clic su **Inserisci utilità di traccia**.  
  
4.  Visualizzare il tempo trascorso per il token di traccia nelle colonne **Dal server di pubblicazione al server di distribuzione**, **Dal server di distribuzione al Sottoscrittore**e **Latenza totale**. Il valore **In sospeso** indica che il token non ha raggiunto un determinato punto.  
  
#### Per visualizzare informazioni su un token di traccia inserito in precedenza  
  
1.  Espandere un gruppo di server di pubblicazione nel riquadro sinistro, espandere un server di pubblicazione e quindi fare clic su una pubblicazione.  
  
2.  Fare clic sulla scheda **Token di traccia** .  
  
3.  Selezionare un'ora dal **ora** elenco a discesa.  
  
4.  Visualizzare il tempo trascorso per il token di traccia nelle colonne **Dal server di pubblicazione al server di distribuzione**, **Dal server di distribuzione al Sottoscrittore**e **Latenza totale**. Il valore **In sospeso** indica che il token non ha raggiunto un determinato punto.  
  
    > [!NOTE]  
    >  Le informazioni sul token di traccia vengono mantenute per lo stesso periodo di tempo degli altri dati cronologici, ovvero in base all'impostazione del periodo di memorizzazione della cronologia del database di distribuzione. Per informazioni sulla modifica delle proprietà del database di distribuzione, vedere [visualizzare e modificare server di distribuzione e le proprietà server di pubblicazione](../../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### Per inviare un token di traccia a una pubblicazione transazionale  
  
1.  (Facoltativo) Server di pubblicazione nel database di pubblicazione, eseguire [sp_helppublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md). Verificare che la pubblicazione esista e che lo stato sia attivo.  
  
2.  (Facoltativo) Server di pubblicazione nel database di pubblicazione, eseguire [sp_helpsubscription & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md). Verificare che la sottoscrizione esista e che lo stato sia attivo.  
  
3.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_posttracertoken & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql.md), specificando **@publication**. Si noti il valore di **@tracer_token_id** parametro di output.  
  
#### Per determinare la latenza e convalidare le connessioni per una pubblicazione transazionale  
  
1.  Inviare un token di traccia alla pubblicazione utilizzando la procedura precedente.  
  
2.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_helptracertokens & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql.md), specificando **@publication**. Viene restituito un elenco di tutti i token di traccia inviati alla pubblicazione. Si noti il valore desiderato **tracer_id** nel set di risultati.  
  
3.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_helptracertokenhistory & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md), specificando **@publication** e l'ID del token di traccia dal passaggio 2 per **@tracer_id**. Vengono restituite le informazioni sulla latenza per il token di traccia selezionato.  
  
#### Per rimuovere token di traccia  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_helptracertokens & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql.md), specificando **@publication**. Viene restituito un elenco di tutti i token di traccia inviati alla pubblicazione. Si noti il **tracer_id** impostato per il token di traccia da eliminare nel risultato.  
  
2.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_deletetracertokenhistory & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-deletetracertokenhistory-transact-sql.md), specificando **@publication** e l'ID del token di traccia da eliminare dal passaggio 2 per **@tracer_id**.  
  
###  <a name="TsqlExample"></a> Esempio (Transact-SQL)  
 In questo esempio viene inserito un record di token di traccia e viene utilizzato l'ID restituito del token di traccia inviato per visualizzare le informazioni sulla latenza.  
  
 [!code-sql[HowTo#sp_tracertokens](../../../relational-databases/replication/codesnippet/tsql/measure-latency-and-vali_1.sql)]  
  
##  <a name="RMOProcedure"></a> Utilizzo di RMO (Replication Management Objects)  
  
#### Per inviare un token di traccia a una pubblicazione transazionale  
  
1.  Creare una connessione al server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.TransPublication> (classe).  
  
3.  Impostare il <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> e <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> proprietà per la pubblicazione, quindi impostare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà per la connessione creata nel passaggio 1.  
  
4.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà dell'oggetto. Se questo metodo restituisce **false**, le proprietà della pubblicazione non sono state definite in modo corretto nel passaggio 3 oppure la pubblicazione non esiste.  
  
5.  Chiamare il <xref:Microsoft.SqlServer.Replication.TransPublication.PostTracerToken%2A> metodo. Questo metodo inserisce un token di traccia nel log delle transazioni della pubblicazione.  
  
#### Per determinare la latenza e convalidare le connessioni per una pubblicazione transazionale  
  
1.  Creare una connessione al server di distribuzione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.PublicationMonitor> (classe).  
  
3.  Impostare il <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>, e <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A> proprietà e impostare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà per la connessione creata nel passaggio 1.  
  
4.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà dell'oggetto. Se questo metodo restituisce **false**, le proprietà di monitoraggio della pubblicazione non sono state definite in modo corretto nel passaggio 3 oppure la pubblicazione non esiste.  
  
5.  Chiamare il <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> metodo. Il cast di restituito <xref:System.Collections.ArrayList> oggetto a una matrice di <xref:Microsoft.SqlServer.Replication.TracerToken> oggetti.  
  
6.  Chiamare il <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokenHistory%2A> metodo. Passare il valore <xref:Microsoft.SqlServer.Replication.TracerToken.TracerTokenId%2A> di un token di traccia del passaggio 5. Restituisce informazioni sulla latenza per il token di traccia selezionato come un <xref:System.Data.DataSet> oggetto. Se vengono restituite tutte le informazioni sul token di traccia, la connessione tra server di pubblicazione e server di distribuzione e la connessione tra server di distribuzione e Sottoscrittore esistono e la topologia di replica funziona correttamente.  
  
#### Per rimuovere token di traccia  
  
1.  Creare una connessione al server di distribuzione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.PublicationMonitor> (classe).  
  
3.  Impostare il <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>, e <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A> proprietà e impostare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà per la connessione creata nel passaggio 1.  
  
4.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà dell'oggetto. Se questo metodo restituisce **false**, le proprietà di monitoraggio della pubblicazione non sono state definite in modo corretto nel passaggio 3 oppure la pubblicazione non esiste.  
  
5.  Chiamare il <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> metodo. Il cast di restituito <xref:System.Collections.ArrayList> oggetto a una matrice di <xref:Microsoft.SqlServer.Replication.TracerToken> oggetti.  
  
6.  Chiamare il <xref:Microsoft.SqlServer.Replication.PublicationMonitor.CleanUpTracerTokenHistory%2A> metodo. Passare uno dei valori seguenti:  
  
    -   Il <xref:Microsoft.SqlServer.Replication.TracerToken.TracerTokenId%2A> di un token di traccia del passaggio 5. Vengono eliminate le informazioni per un token selezionato.  
  
    -   Oggetto <xref:System.DateTime> oggetto. Vengono eliminate le informazioni per tutti i token con data e ora precedenti a quelle specificate.  
  
  