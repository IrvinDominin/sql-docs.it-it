---
title: "Creazione di un processo di SQL Server Agent per l&#39;archiviazione di messaggi e log eventi di Posta elettronica database | Microsoft Docs"
ms.custom: ""
ms.date: "08/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "archiviazione di messaggi di posta e allegati [SQL Server]"
  - "rimozione di messaggi di posta e allegati"
  - "posta elettronica database [SQL Server], archiviazione"
  - "salvataggio di messaggi di posta e allegati"
ms.assetid: 8f8f0fba-f750-4533-9b76-a9cdbcdc3b14
caps.latest.revision: 19
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 19
---
# Creazione di un processo di SQL Server Agent per l&#39;archiviazione di messaggi e log eventi di Posta elettronica database
  Oltre al log eventi di Posta elettronica database, nelle tabelle del database **msdb** viene mantenuta una copia dei messaggi di Posta elettronica database e dei relativi allegati. È consigliabile ridurre periodicamente le dimensioni delle tabelle e archiviare i messaggi e gli eventi non più necessari. Nelle procedure seguenti viene illustrato come creare un processo di SQL Server Agent per eseguire queste operazioni in modo automatico.  
  
-   **Prima di iniziare:** [Prerequisiti](#Prerequisites), [Raccomandazioni](#Recommendations), [Autorizzazioni](#Permissions)  
  
-   **Per archiviare messaggi e log di Posta elettronica database utilizzando:**  [SQL Server Agent](#Process_Overview)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Prerequisites"></a> Prerequisiti  
 Le nuove tabelle per archiviare i dati dell'archivio possono trovarsi in un database di archiviazione speciale. In alternativa le righe possono essere esportate in un file di testo.  
   
###  <a name="Recommendations"></a> Indicazioni  
 Nell'ambiente di produzione è consigliabile aggiungere un ulteriore controllo degli errori e inviare un messaggio di posta elettronica agli operatori se l'esecuzione del processo non viene completata.  
  
  
###  <a name="Permissions"></a> Permissions  
 È necessario essere membri del ruolo predefinito del server **sysadmin** per eseguire le stored procedure descritte in questo argomento.  
  
  
###  <a name="Process_Overview"></a> Panoramica del processo  
  
-   La prima procedura consente di creare un processo denominato Archive Database Mail effettuando i passaggi riportati di seguito.  
  
    1.  Copiare tutti i messaggi dalle tabelle di Posta elettronica database in una nuova tabella con il nome basato sul mese precedente nel formato **DBMailArchive_***<anno_mese>*.  
  
    2.  Copiare gli allegati correlati ai messaggi copiati nel primo passaggio dalle tabelle di Posta elettronica database in una nuova tabella con il nome basato sul mese precedente nel formato **DBMailArchive_Attachments_***<anno_mese>*.  
  
    3.  Copiare gli eventi del registro eventi di Posta elettronica database correlati ai messaggi copiati nel primo passaggio dalle tabelle di Posta elettronica database in una nuova tabella con un nome basato sul mese precedente nel formato **DBMailArchive_Log_***<anno_mese>*.  
  
    4.  Eliminare dalle tabelle di Posta elettronica database i record degli elementi di posta trasferiti.  
  
    5.  Eliminare dal log eventi di Posta elettronica database gli eventi correlati agli elementi di posta trasferiti.  
  
-   Pianificare l'esecuzione periodica del processo.  
  
  
## Per creare un processo di SQL Server Agent  
  
1.  In Esplora oggetti, espandere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, fare clic con il pulsante destro del mouse su **Processi**, quindi scegliere **Nuovo processo**.  
  
2.  Nella finestra di dialogo **Nuovo processo** digitare **Archive Database Mail** nella casella **Nome**.  
  
3.  Nella casella **Proprietario** confermare che il proprietario è un membro del ruolo predefinito del server **sysadmin** .  
  
4.  Nella casella **Categoria** fare clic su **Manutenzione database**.  
  
5.  Nella casella **Descrizione** digitare **Archiviazione messaggi di Posta elettronica database**, quindi fare clic su **Passaggi**.  
  
 [Panoramica](#Process_Overview)  
  
## Per creare un passaggio per l'archiviazione dei messaggi di Posta elettronica database  
  
1.  Nella pagina **Passaggi** fare clic su **Nuovo**.  
  
2.  Nella casella **Nome passaggio** digitare **Copy Database Mail Items**.  
  
3.  Nella casella **Tipo** selezionare **Script Transact-SQL (T-SQL)**.  
  
4.  Nella casella **Database** selezionare **msdb**.  
  
5.  Nella casella **Comando** , digitare l'istruzione seguente per creare una tabella con il nome basato sul mese precedente e contenente le righe con una data anteriore all'inizio del mese corrente:  
  
    ```tsql  
    DECLARE @LastMonth nvarchar(12);  
    DECLARE @CopyDate nvarchar(20) ;  
    DECLARE @CreateTable nvarchar(250) ;  
    SET @LastMonth = (SELECT CAST(DATEPART(yyyy,GETDATE()) AS CHAR(4)) + '_' + CAST(DATEPART(mm,GETDATE())-1 AS varchar(2))) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime))  
    SET @CreateTable = 'SELECT * INTO msdb.dbo.[DBMailArchive_' + @LastMonth + '] FROM sysmail_allitems WHERE send_request_date < ''' + @CopyDate +'''';  
    EXEC sp_executesql @CreateTable ;  
    ```  
  
6.  Fare clic su **OK** per salvare il passaggio.  
  
 [Panoramica](#Process_Overview)  
  
## Per creare un passaggio per l'archiviazione degli allegati di Posta elettronica database  
  
1.  Nella pagina **Passaggi** fare clic su **Nuovo**.  
  
2.  Nella casella **Nome passaggio** digitare **Copy Database Mail Attachments**.  
  
3.  Nella casella **Tipo** selezionare **Script Transact-SQL (T-SQL)**.  
  
4.  Nella casella **Database** selezionare **msdb**.  
  
5.  Nella casella **Comando** , digitare la seguente istruzione per creare una tabella di allegati con il nome basato sul mese precedente e contenente gli allegati corrispondenti ai messaggi trasferiti nel passaggio precedente:  
  
    ```tsql  
    DECLARE @LastMonth nvarchar(12);  
    DECLARE @CopyDate nvarchar(20) ;  
    DECLARE @CreateTable nvarchar(250) ;  
    SET @LastMonth = (SELECT CAST(DATEPART(yyyy,GETDATE()) AS CHAR(4)) + '_' + CAST(DATEPART(mm,GETDATE())-1 AS varchar(2))) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime))  
    SET @CreateTable = 'SELECT * INTO msdb.dbo.[DBMailArchive_Attachments_' + @LastMonth + '] FROM sysmail_attachments   
     WHERE mailitem_id in (SELECT DISTINCT mailitem_id FROM [DBMailArchive_' + @LastMonth + '] )';  
    EXEC sp_executesql @CreateTable ;  
    ```  
  
6.  Fare clic su **OK** per salvare il passaggio.  
  
 [Panoramica](#Process_Overview)  
  
## Per creare un passaggio per l'archiviazione del log di Posta elettronica database  
  
1.  Nella pagina **Passaggi** fare clic su **Nuovo**.  
  
2.  Nella casella **Nome passaggio** digitare **Copy Database Mail Log**.  
  
3.  Nella casella **Tipo** selezionare **Script Transact-SQL (T-SQL)**.  
  
4.  Nella casella **Database** selezionare **msdb**.  
  
5.  Nella casella **Comando** digitare l'istruzione seguente per creare una tabella del log con un nome basato sul mese precedente e contenente le voci del log che corrispondono ai messaggi trasferiti nel primo passaggio:  
  
    ```tsql  
    DECLARE @LastMonth nvarchar(12);  
    DECLARE @CopyDate nvarchar(20) ;  
    DECLARE @CreateTable nvarchar(250) ;  
    SET @LastMonth = (SELECT CAST(DATEPART(yyyy,GETDATE()) AS CHAR(4)) + '_' + CAST(DATEPART(mm,GETDATE())-1 AS varchar(2))) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime))  
    SET @CreateTable = 'SELECT * INTO msdb.dbo.[DBMailArchive_Log_' + @LastMonth + '] FROM sysmail_Event_Log   
     WHERE mailitem_id in (SELECT DISTINCT mailitem_id FROM [DBMailArchive_' + @LastMonth + '] )';  
    EXEC sp_executesql @CreateTable ;  
    ```  
  
6.  Fare clic su **OK** per salvare il passaggio.  
  
 [Panoramica](#Process_Overview)  
  
## Per creare un passaggio per la rimozione da Posta elettronica database delle righe archiviate  
  
1.  Nella pagina **Passaggi** fare clic su **Nuovo**.  
  
2.  Nella casella **Nome passaggio** digitare **Remove rows from Database Mail**.  
  
3.  Nella casella **Tipo** selezionare **Script Transact-SQL (T-SQL)**.  
  
4.  Nella casella **Database** selezionare **msdb**.  
  
5.  Nella casella **Comando** digitare l'istruzione seguente per rimuovere dalle tabelle di Posta elettronica database le righe con una data anteriore al mese corrente:  
  
    ```tsql  
    DECLARE @CopyDate nvarchar(20) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime)) ;  
    EXECUTE msdb.dbo.sysmail_delete_mailitems_sp @sent_before = @CopyDate ;  
    ```  
  
6.  Fare clic su **OK** per salvare il passaggio.  
  
 [Panoramica](#Process_Overview)  
  
## Per creare un passaggio per la rimozione dal log eventi di Posta elettronica database degli elementi archiviati  
  
1.  Nella pagina **Passaggi** fare clic su **Nuovo**.  
  
2.  Nella casella **Nome passaggio** digitare **Remove rows from Database Mail event log**.  
  
3.  Nella casella **Tipo** selezionare **Script Transact-SQL (T-SQL)**.  
  
4.  Nella casella **Comando** digitare l'istruzione seguente per rimuovere dal log eventi di Posta elettronica database le righe con una data anteriore al mese corrente:  
  
    ```tsql  
    DECLARE @CopyDate nvarchar(20) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime)) ;  
    EXECUTE msdb.dbo.sysmail_delete_log_sp @logged_before = @CopyDate ;  
    ```  
  
5.  Fare clic su **OK** per salvare il passaggio.  
  
 [Panoramica](#Process_Overview)  
  
## Per pianificare l'esecuzione periodica del processo  
  
1.  Nella finestra di dialogo **Nuovo processo** fare clic su **Pianificazioni**.  
  
2.  Nella pagina **Pianificazioni** fare clic su **Nuova**.  
  
3.  Nella casella **Nome** digitare **Archive Database Mail**.  
  
4.  Nella casella **Tipo pianificazione** selezionare **Periodica**.  
  
5.  Nell'area **Frequenza** selezionare le opzioni che consentono di eseguire il processo periodicamente, ad esempio una volta al mese.  
  
6.  Nell'area **Frequenza giornaliera** selezionare **Una sola volta alle <ora>\>**.  
  
7.  Verificare che le altre opzioni siano configurate come desiderato, quindi fare clic su **OK** per salvare la pianificazione.  
  
8.  Fare clic su **OK** per salvare il processo.  
  
 [Panoramica](#Process_Overview)  
  
  