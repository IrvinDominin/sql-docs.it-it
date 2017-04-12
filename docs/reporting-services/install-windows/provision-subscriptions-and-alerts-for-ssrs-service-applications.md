---
title: "Provisioning di sottoscrizioni e avvisi per le applicazioni di servizio SSRS | Microsoft Docs"
ms.custom: ""
ms.date: "06/03/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Servizio Shared di Reporting Services"
  - "Modalità SharePoint [Reporting Services]"
  - "Modalità SharePoint"
  - "Applicazione di servizio Reporting Services"
  - "Applicazione di servizio SSRS"
ms.assetid: d0de3f1f-4887-47fb-bacf-46aaad74c4be
caps.latest.revision: 20
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 20
---
# Provisioning di sottoscrizioni e avvisi per le applicazioni di servizio SSRS
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Le sottoscrizioni e gli avvisi dati richiedono SQL Server Agent e la configurazione di autorizzazioni per SQL Server Agent. Se vengono visualizzati messaggi di errore indicanti che si richiede SQL Server Agent sebbene sia in esecuzione, aggiornare o verificare le autorizzazioni. L'ambito di questo argomento è [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in modalità SharePoint e vengono descritti tre modi per aggiornare le autorizzazioni di SQL Server Agent con sottoscrizioni di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Le credenziali utilizzata nei passaggi di questo argomento devono disporre delle autorizzazioni sufficienti per concedere autorizzazioni di esecuzione a RSExecRole per gli oggetti nell'applicazione di servizio, il database msdb e database master.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2016 &#124; SharePoint 2013|  
  
 ![SQL Agent permissions to Service Application DBs](../../reporting-services/install-windows/media/rs-provisionsqlagent.gif "SQL Agent permissions to Service Application DBs")  
  
||Descrizione|  
|------|-----------------|  
|**1**|Istanza del motore di database di SQL Server che ospita i database dell'applicazione di servizio Reporting Services.|  
|**2**|Istanza di SQL Server Agent per l'istanza del motore di database SQL.|  
|**3**|Database dell'applicazione di servizio Reporting Services. I nomi si basano sulle informazioni utilizzate per creare l'applicazione di servizio. Di seguito sono riportati esempi di nomi di database:<br /><br /> ReportingService_2fbae157295d49df86d0b85760c704b0<br /><br /> ReportingService_2fbae157295d49df86d0b85760c704b0_Alerting<br /><br /> ReportingService_2fbae157295d49df86d0b85760c704b0TempDB|  
|**4**|Il database master e MSDB dell'istanza del motore di database SQL Server.|  
  
 Utilizzare uno dei tre metodi seguenti per aggiornare le autorizzazioni:  
  
1.  Digitare le credenziali nella pagina **Avvisi e sottoscrizioni provisioning** e fare clic su **OK**.  
  
2.  Nella pagina Avvisi e sottoscrizioni provisioning, fare clic sul pulsante **Download script** per scaricare uno script Transact-SQL che può essere usato per configurare le autorizzazioni.  
  
3.  Eseguire un cmdlet di PowerShell per compilare uno script Transact-SQL che può essere utilizzato per configurare le autorizzazioni.  
  
### Per aggiornare le autorizzazioni utilizzando la pagina di provisioning  
  
1.  Nel gruppo **Gestione applicazioni** di Amministrazione centrale SharePoint fare clic su **Gestisci applicazioni di servizio**.  
  
2.  Individuare l'applicazione di servizio nell'elenco e fare clic sul nome dell'applicazione oppure fare clic sulla colonna **Tipo** per selezionare l'applicazione di servizio e fare clic sul pulsante **Gestisci** nella barra multifunzione di SharePoint.  
  
3.  Fare clic su **Avvisi e sottoscrizioni provisioning** nella pagina **Gestione applicazione di Reporting Services**.  
  
4.  Digitare le credenziali dell'amministratore di SharePoint se sufficienti per accedere al database master e ai database dell'applicazione di servizio.  
  
5.  Fare clic sul pulsante **OK**.  
  
##  <a name="bkmk_download"></a> Per scaricare lo script Transact-SQL  
  
1.  Nel gruppo **Gestione applicazioni** di Amministrazione centrale SharePoint fare clic su **Gestisci applicazioni di servizio**.  
  
2.  Individuare l'applicazione di servizio nell'elenco e fare clic sul nome dell'applicazione oppure fare clic sulla colonna **Tipo** per selezionare l'applicazione di servizio e fare clic sul pulsante **Gestisci** nella barra multifunzione di SharePoint.  
  
3.  Fare clic su **Avvisi e sottoscrizioni provisioning** nella pagina **Gestione applicazione di Reporting Services**.  
  
4.  Verificare che SQL Server Agent sia in esecuzione nell'area **Visualizzazione stato**.  
  
5.  Fare clic su **Download script** per scaricare uno script Transact-SQL che può essere eseguito in SQL Server Management Studio per concedere le autorizzazioni. Il nome del file script creato contiene il nome dell'applicazione di servizio di Reporting Services, ad esempio **[nome dell'applicazione di servizio]-GrantRights.sql**.  
  
### Per generare l'istruzione Transact-SQL con PowerShell  
  
1.  È possibile utilizzare un cmdlet di Windows PowerShell nella shell di gestione di SharePoint 2016 o SharePoint 2013 anche per creare uno script Transact-SQL.  
  
2.  Scegliere **Tutti i programmi** dal menu **Start**.  
  
3.  Espandere **Prodotti Microsoft SharePoint 2016** e fare clic su **Shell di gestione SharePoint 2016**.
  
4.  Aggiornare il seguente cmdlet di PowerShell sostituendo il nome del database del server di report, l'account del pool di applicazioni e il percorso dell'istruzione.  
  
     **Sintassi del cmdlet:** `Get-SPRSDatabaseRightsScript –DatabaseName <ReportingServices database name> -UserName <app pool account> -IsWindowsUser | Out-File <path of statement>`  
  
     **Cmdlet di esempio:** `Get-SPRSDatabaseRightsScript –DatabaseName ReportingService_46fd00359f894b828907b254e3f6257c –UserName “NT AUTHORITY\NETWORK SERVICE” –IsWindowsUser | Out-File c:\SQLServerAgentrights.sql`  
  
## Utilizzo dello script Transact-SQL  
 Le seguenti procedure possono essere utilizzate con gli script scaricati dalla pagina di provisioning o creati tramite PowerShell.  
  
#### Per caricare lo script Transact-SQL in SQL Server Management Studio  
  
1.  Per aprire SQL Server Management Studio, nel menu **Start** scegliere [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)] e quindi fare clic su **SQL Server Management Studio**.  
  
2.  Nella finestra di dialogo **Connetti al server** impostare le opzioni seguenti:  
  
    -   Nell'elenco **Tipo server** selezionare **Motore di database**.  
  
    -   Nella casella **Nome server** digitare il nome dell'istanza di SQL Server in cui si desidera configurare SQL Server Agent.  
  
    -   Selezionare una modalità di autenticazione.  
  
    -   Se ci si connette utilizzando l'autenticazione di SQL Server, specificare un account e una password.  
  
3.  Fare clic su **Connetti**.  
  
#### Per eseguire l'istruzione Transact-SQL  
  
1.  Fare clic su **Nuova query** nella barra degli strumenti di SQL Server Management Studio.  
  
2.  Scegliere **Apri** dal menu **File** e quindi fare clic su **File**.  
  
3.  Passare alla cartella in cui è stata salvata l'istruzione Transact-SQL generata nella shell di gestione di SharePoint 2016 o SharePoint 2013.  
  
4.  Selezionare il file, quindi fare clic su **Apri**.  
  
     L'istruzione viene aggiunta alla finestra della query.  
  
5.  Fare clic su **Esegui**.  
  
  