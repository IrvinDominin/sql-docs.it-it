---
title: "Visualizzazione o modifica di word breaker e filtri registrati | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-search"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ricerca full-text [SQL Server], word breaker"
  - "ricerca full-text [SQL Server], filtri"
  - "filtri [ricerca full-text]"
  - "word breaker [ricerca full-text]"
ms.assetid: f88c54df-b1aa-4701-807f-dc92c32363fd
caps.latest.revision: 22
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 22
---
# Visualizzazione o modifica di word breaker e filtri registrati
  Dopo l'installazione o la disinstallazione di word breaker o filtri in un sistema, le modifiche non diventano automaticamente effettive nelle istanze server. In questo argomento viene descritto come visualizzare i word breaker o i filtri registrati, nonché come registrare i word breaker e i filtri appena installati in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### Per visualizzare un elenco delle lingue i cui word breaker sono registrati  
  
1.  Usare la vista del catalogo [sys.fulltext_languages](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md), come illustrato di seguito:  
  
    ```  
    SELECT * FROM sys.fulltext_languages;   
    ```  
  
### Per visualizzare un elenco dei filtri registrati  
  
1.  Usare [sp_help_fulltext_system_components](../../relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql.md), come illustrato di seguito:  
  
    ```  
    EXEC sp_help_fulltext_system_components 'filter';    
    ```  
  
### Per registrare i word breaker e i filtri appena installati  
  
1.  Usare la stored procedure di sistema [sp_fulltext_service](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md) per aggiornare l'elenco di lingue, come illustrato di seguito:  
  
    ```  
    exec sp_fulltext_service 'update_languages';   
    ```  
  
### Per annullare la registrazione di word breaker e filtri disinstallati  
  
1.  Usare **sp_fulltext_service** per aggiornare l'elenco di lingue nel modo seguente:  
  
    ```  
    exec sp_fulltext_service 'update_languages'  
    ```  
  
2.  Usare **sp_fulltext_service** per riavviare i processi host del daemon di filtri (fdhost.exe) nel modo seguente:  
  
    ```  
    exec sp_fulltext_service 'restart_all_fdhosts';  
    ```  
  
### Per sostituire i word breaker o i filtri esistenti dopo averne installati di nuovi  
  
1.  Quando si prepara l'installazione di un file DLL contenente nuovi word breaker o filtri, verificare che il nome sia diverso da quelli di eventuali file DLL installati nell'istanza del server.  
  
2.  Copiare il nuovo file DLL nella directory contenente i file DLL standard di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per l'istanza server. Il percorso predefinito è:  
  
     C:\Programmi\Microsoft SQL Server\MSSQL.*nome_istanza*\MSSQL\Binn  
  
    > [!IMPORTANT]  
    >  Si consiglia di caricare solo componenti firmati e verificati. È inoltre consigliabile eseguire il servizio dell'utilità di avvio FDHOST (MSSQLFDLauncher) con privilegi minimi.  
  
3.  Installare i nuovi word breaker o filtri.  
  
     **Per installare e caricare filtri IFilter di Microsoft Filter Pack**  
  
    -   [Come registrare IFilter di Microsoft Filter Pack con SQL Server](http://go.microsoft.com/fwlink/?LinkId=130439)  
  
4.  Usare **sp_fulltext_service** per caricare i word breaker e i filtri appena installati nell'istanza del server nel modo seguente:  
  
    ```  
    EXEC sp_fulltext_service @action='load_os_resources', @value=1;  
    ```  
  
5.  Usare **sp_fulltext_service** per aggiornare l'elenco di lingue nel modo seguente:  
  
    ```  
    EXEC sp_fulltext_service 'update_languages';  
    ```  
  
6.  Riavviare i processi host del daemon di filtri (fdhost.exe) usando **sp_fulltext_service** nel modo seguente:  
  
    ```  
    EXEC sp_fulltext_service 'restart_all_fdhosts';   
    ```  
  
## Vedere anche  
 [Impostazione dell'account del servizio dell'Utilità di avvio del daemon di filtri full-text](../../relational-databases/search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md)   
 [Configurazione e gestione di filtri per la ricerca](../../relational-databases/search/configure-and-manage-filters-for-search.md)   
 [Configurazione e gestione di word breaker e stemmer per la ricerca](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)  
  
  